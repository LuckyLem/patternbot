# Entwurf: Lernzeit-Wächter und Einrichtung auf dem Pi (Etappe 0)

Stand 08.10.2026. Gebaut und getestet ist die Zeitlogik. Die Einrichtung auf dem Pi folgt am Wochenende
10.–11.10., außerhalb der Handelszeit. Der Inhaber führt die Befehle mit Administratorrechten selbst aus.

## 1. Zeitlogik (gebaut)

- **Lernzeit:** an Handelstagen 16:30–09:00 New York, am Wochenende und an NYSE-Feiertagen durchgehend.
- **Zeitzone im Code:** nur New-York-Zeit, mit dem echten NYSE-Kalender (Feiertage, Halbtage). Deutsche Zeit
  erscheint nur in Anzeigen und Nachrichten.
- **Zeitumstellung:**
  - 25.10.–01.11. öffnet die Börse um 14:30 deutscher Zeit, das Labor startet dann um 21:30 und stoppt um 14:00.
  - Das stimmt automatisch, weil in New-York-Zeit gerechnet wird.
- **Halbtage** (27.11., 24.12.): Die Lernzeit beginnt trotzdem erst um 16:30 New York. So bleiben die Abendroutinen
  des Bots (Review 16:05, Export 16:20 New York) auch dort ungestört.
- **Zeiten ohne Zeitzone** werden abgelehnt.
- **Prüfungen:** 17 grün (Logbuch 08.10.).

## 2. Isolation auf dem Pi (Entwurf)

**Labor-Ordner:**
- außerhalb des Home-Bereichs, damit ProtectHome den Bot abschirmt, ohne das Labor auszusperren;
- feste Obergrenze als eigenes Dateisystem in einer Datei, Vorschlag 12 GB;
- darin: Code mit eigenem Code-Hash, Cache, Ergebnisse, Zwischenstände und eine eigene `.env`.

**Eigener Linux-Nutzer** ohne Zugriff auf das Bot-Verzeichnis.

**Eigene `.env` des Labors**, nur lesbar für den Labor-Nutzer:
- eigene Alpaca-Schlüssel (zweites Paper-Konto) mit eigenem Abruflimit;
- eigener GitHub-Token, nur für Ergebnisse;
- eigener Telegram-Bot;
- Kontakt für den SEC-User-Agent.

Ohne eigene Alpaca-Schlüssel holt das Labor auf dem Pi keine Daten. Die Schlüssel des Bots werden nie kopiert.

**systemd-Slice `lernlabor.slice`:**

| Einstellung | Wert |
|---|---|
| MemoryMax | 40 % des Arbeitsspeichers |
| MemorySwapMax | 0 |
| CPUWeight | 10 |
| CPUQuota | 200 % (2 von 4 Kernen) |
| IOWeight | 10 |

**Dienst `lernlabor.service`:**

| Einstellung | Wert |
|---|---|
| Slice | lernlabor.slice |
| User | Labor-Nutzer |
| Nice | 19 |
| IOSchedulingClass | idle |
| OOMScoreAdjust | 1000 (bei Speichernot wird zuerst das Labor beendet) |
| ProtectSystem | strict |
| ProtectHome | yes |
| PrivateTmp | yes |
| NoNewPrivileges | yes |
| InaccessiblePaths | Bot-Verzeichnis und alle Dateien mit Schlüsseln |
| ReadWritePaths | nur der Labor-Ordner |

**Bot-Schutz** über ein Drop-in für den Bot-Dienst, kommt mit dem Technik-Paket am Fr 09.10.:
- MemoryLow;
- negatives OOMScoreAdjust.

**Zugriffstest vor dem ersten Lauf:**
- als Labor-Nutzer das Bot-Verzeichnis und die Schlüssel lesen; das muss scheitern;
- das Ergebnis kommt ins Logbuch.

## 3. Start und Stopp

**Start-Timer:**
- Mo–Fr 16:30 America/New_York, dazu nach jedem Neustart des Pi;
- der Job prüft selbst mit dem Kalender, ob Lernzeit ist;
- ein Fenster am Freitag läuft bis Montag 09:00 durch, Feiertage liegen im Fenster.

**Sanftes Ende:** um 08:55 New York sichert der Job seinen Zwischenstand und beendet sich.

**Harter Stopp-Timer:**
- Mo–Fr 09:00 America/New_York stoppt den Dienst, egal was läuft;
- lief noch ein Job, kommt ein Alarm per Telegram.

**Deploy-Pause:** Liegt die Pause-Datei, startet nichts, und ein laufender Job sichert und endet.

**Immer nur ein schwerer Job,** mit Vorrang: Live-Bot, Runde 2, ORB, Lern-Labor. Die Runden laufen derzeit auf dem
PC.

**Zwischenstände:** Ein gestoppter Job macht beim nächsten Start dort weiter.

## 4. Speicherwächter

- Er prüft jede Minute.
- Er stoppt das Labor, wenn auf dem System weniger als 5 GB frei sind oder der Labor-Ordner zu 95 % voll ist.
- Vorher sichert er den Zwischenstand.
- Danach kommt ein Alarm per Telegram.

## 5. Harte Sperre

- Wie im Replay: nur Lesen von Marktdaten, keine Trading-Schnittstelle. Der echte Broker lässt sich im Labor nicht
  erzeugen.
- **Sperrliste des Labors:**
  - Alpaca-Marktdaten;
  - SEC-EDGAR mit höchstens 10 Abrufen je Sekunde, User-Agent mit Kontakt aus der `.env`;
  - GitHub nur für den Ergebnis-Upload.
- Downloads nur außerhalb der Handelszeit, gedrosselt.

## Offene Entscheidungen für den Inhaber

1. Obergrenze des Labor-Ordners: 12 GB? (24 GB sind frei, der Datenplan braucht für den Lerntopf etwa 2,7 GB.)
2. Zweites Paper-Konto für die eigenen Alpaca-Schlüssel des Labors.
3. Eigener Telegram-Bot und eigener GitHub-Token. Beides nur in die `.env` des Labors, nie in den Chat.
