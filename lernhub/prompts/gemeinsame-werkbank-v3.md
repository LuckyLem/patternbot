# Gemeinsame Werkbank v3 · Auftrag Fassung 1

Stand Di 03.11.2026, Claude im Chat, mit dem Inhaber abgestimmt. Diese Datei ist der Gesamtplan. Einzelheiten zum
Doppelboden stehen in `werkbank-doppelboden.md`; wo sich beide widersprechen, gilt **diese** Datei.

## 0. Ziel und Grundsätze

- **Ziel:** ein Muster finden, das nach Kosten einen **echten** Vorteil hat, also nicht durch Zufall positiv ist.
- **Wir probieren viel:** mehrere Muster, Tageskerzen mit Positionen über Nacht, 5 und 15 Minuten, viele Märkte.
- **Damit das nicht im Zufall endet, gilt immer:**
  1. **Ideen-Register:** Jede Idee wird eingetragen, *bevor* sie gerechnet wird. Am Ende kennen wir die Zahl N aller
     Versuche.
  2. **Suchen und Bestätigen getrennt:** Regeln werden auf Such-Daten entwickelt und auf anderen Daten bestätigt (Abschnitt 2).
  3. **Prüftopf ab 01.10.2023 bleibt zu.** Erst ganz am Ende öffnen wir ihn, höchstens dreimal, mit eigener Vorab-Datei und der
     Zufallshürde „Bester von N“.
  4. **Keine Regel nach dem Blick auf ein Ergebnis ändern.** Eine Änderung ist eine neue Idee mit neuem Eintrag im Register.
  5. **Erst verstehen, dann ändern:** Nach jedem Lauf kommt die Analyse (Abschnitt 4). Sie zeigt, ob es an der Erkennung, dem
     Einstieg, dem Ausstieg, der Zeit, den Kosten oder am Markt lag.

## 1. Ideen-Register

- **Datei:** `lernhub/werkbank/ideen-register.json`, öffentlich auf backtest.
- **Je Idee:** Nummer, Datum, Kurzname, Muster, Zeitebene, Einstieg, Zusammenhang, Hash der Regeln, Daten (Suche oder
  Bestätigung), Status (geplant, läuft, verworfen, bestätigt, Prüftopf), Ergebnis in einem Satz.
- **Bereits verbraucht, als erste Einträge nachtragen:**
  - Runde 1;
  - Runde 2;
  - ORB Jahr 1;
  - Lerntopf-Lauf 1;
  - Werkbank Rechteck v1 (8 Varianten).
- **Startliste, Reihenfolge veränderbar:**

| Nr. | Idee | Zeitebenen | Bemerkung |
|---|---|---|---|
| H1 | Doppelboden, dazu gespiegelt der Doppeltop | Tag, 5 Min, 15 Min | zuerst |
| H2 | Rechteck Fassung 3 (verbessert nach der Analyse, Abschnitt 6) | Tag, 5 Min | bleibt zum Analysieren drin |
| H3 | Kopf-Schulter und umgekehrte Kopf-Schulter | Tag, 5 Min | |
| H4 | Bullenflagge und Wimpel, dazu gespiegelt | Tag, 5 Min | |
| H5 | Aufsteigendes und absteigendes Dreieck | Tag, 5 Min | |
| H6 | Tasse mit Henkel | Tag | |
| H7+ | Ideen des Inhabers, Preis-Setups (52-Wochen-Hoch, Innenstab, Kurslücken) | offen | später |

- **Zusammenhang wie bei Profis:** Je Muster auf Tageskerzen gibt es zwei vorab festgelegte Varianten, beide im Register
  gezählt:
  - **ohne** Zusammenhang;
  - **mit** Zusammenhang: long nur, wenn der Schluss über der 50- und der 200-Tage-Linie liegt und die 50-Tage-Linie über der
    200-Tage-Linie; short spiegelbildlich.

  Intraday gilt sinngemäß: long nur über dem VWAP und bei steigendem SPY seit 09:30, short spiegelbildlich.

## 2. Daten: Suchen, Bestätigen, Prüfen

| Arm | Werte | Suchen | Bestätigen | Prüftopf (zu) |
|---|---|---|---|---|
| Tag | 1.500 US-Werte und Länder-ETFs, Filter je Tag aus Vortagen: Kurs über 5 $, Ø Tagesumsatz 20 Tage mindestens 10 Mio. $ | 01.10.2016 – 30.09.2020 | 01.10.2020 – 30.09.2023 | ab 01.10.2023 |
| 5 und 15 Min | die 50 der Werkbank | 01.10.2021 – 30.09.2023 | 01.10.2020 – 30.09.2021 auf den 50, dazu 01.10.2021 – 30.09.2023 auf den übrigen 100 der Liste von 150 | ab 01.10.2023 |

- **Vorläufe:** Tag ab 01.01.2016; intraday ab 01.09.2020.
- **Sperre:** `daten.py` sperrt jeden Tag ab 01.10.2023, für alle Zeitebenen.
- **Downloads:** nur außerhalb 15:30–22:00 deutscher Zeit, gedrosselt, nur Marktdaten.
- **Bestätigungsdaten werden erst angefasst,** wenn eine Idee auf den Suchdaten die Hürde aus Abschnitt 7 nimmt.

## 3. Die gemeinsame Werkbank (ein Code für alle Muster)

**Gemeinsame Bausteine:**
- Kerzen 5 Min, 15 Min und Tag mit Börsenkalender und Halbtagen;
- ATR je Tageszeit (intraday) und ATR 14 (Tag);
- bestätigte Wendepunkte (k Kerzen, Mindest-Schwung, erst k Kerzen später bekannt);
- Linien als Median der Berührungen;
- Toleranzen in ATR;
- der Diagnose-Trichter (je Regel: übrig, nur diese, insgesamt);
- Reifegrad 0–4;
- Noten aus harten Bedingungen (die Punktzahl ordnet nur);
- Schnappschuss mit Hash im Moment der Entscheidung.

**Muster-Module:** `rechteck.py`, `doppelboden.py` usw. Jedes Modul liefert:
- die Kandidaten;
- seine Regeln mit Namen (für den Trichter);
- Reifegrad und Note;
- die **Kante** für die Einstiege (Rechteck: obere oder untere Linie; Doppelboden: Nackenlinie);
- die Linien für die Bilder.

**Einstiege, gemeinsam für alle Muster.** Auf Seite und im Bericht heißen sie nur mit Namen, ohne Buchstaben:
- Ausbruch;
- Retest;
- früher Einstieg (Abpraller bzw. zweiter Boden);
- Fehlschlag.

Die Regeln dazu stehen in Werkbank Rechteck v1 bzw. `werkbank-doppelboden.md`.

**Ausstiege:**
- **intraday:** Ziel, Stop oder 15:50;
- **Tag:** Ziel, Stop oder Zeitlimit;
  - Entscheidung am Tagesschluss, Einstieg zur Eröffnung des nächsten Tages;
  - Kurslücke über Nacht jenseits des Stops: Ausstieg zum Eröffnungskurs.

**Zeitbudget-Regel (vorab festgelegt):** Kommen in der Diagnose eines Musters mehr als die Hälfte der Bestätigungen nach der
letzten Einstiegszeit (15:30), wird diese Zeitebene für das Muster **nur gemessen, nicht gehandelt**.

**Kosten, Kostenstress, Mindest-Stop, Zufallstest:** wie Werkbank Rechteck v1. Auf Tageskerzen gilt der Mindest-Stop
max(0,5 ATR; 0,5 %). Der Zufallstrade auf Tageskerzen nimmt dieselbe Aktie, dieselbe Richtung und einen zufälligen anderen
Tag im Abstand von höchstens 20 Handelstagen, mit gleichem Stop-Abstand in %, gleichem Ziel in R und gleichem Zeitlimit.

**Gleichheitstest, Pflicht vor allem anderen:** Die neue Werkbank rechnet Werkbank Rechteck v1 nach. Alle 13.293 Trades müssen
gleich sein (Schnappschuss-Hash, r_vor, r). Erst dann ist der Umbau fertig.

## 4. Analyse-Modul: Warum Gewinn, warum Verlust

Läuft nach **jedem** Lauf automatisch und schreibt `analyse-<lauf>.json` und `analyse-<lauf>.md`.

**Je Trade zusätzlich messen:**
- größter Buchgewinn (MFE) und größter Buchverlust (MAE) in R, jeweils mit der Zeit bis dahin;
- ob das Ziel nach dem Ausstieg noch erreicht wurde: intraday bis 16:00, auf Tageskerzen in den 20 Tagen danach. Das ist nur
  Information;
- Abstand des Füllkurses zur Kante in ATR;
- Zeit vom fertigen Muster bis zum Einstieg.

**Verlust- und Gewinn-Arten, automatisch zugeordnet; die erste zutreffende zählt:**

| Art | Regel |
|---|---|
| Fehlausbruch | Stop innerhalb von 3 Kerzen nach dem Einstieg, MFE unter 0,3 R |
| Stop zu eng | gestoppt, danach Ziel noch erreicht, Stop-Abstand unter 1 ATR |
| Ziel zu weit | MFE mindestens 0,8 des Ziels, danach Stop oder Zeitlimit |
| Zeit | Ausstieg zum Tagesende oder Zeitlimit mit MFE über 0,5 R |
| Kosten | r_vor über 0, aber r unter 0 |
| Gegen den Markt | SPY bewegt sich im Trade um mehr als 0,5 ATR (in SPY gemessen) gegen die Richtung |
| sauber gewonnen | Ziel erreicht |
| sonst | alles andere |

**Auswertungen, nur Information:**
1. Anteile je Art, je Muster, je Zeitebene und je Note.
2. **Erkennung gegen Ergebnis:**
   - Haben Kästen, die der Inhaber in der Sichtprüfung mit „ja“ bewertet hat, besser abgeschnitten als „nein“?
   - Haben Note A, B und C unterschiedlich abgeschnitten?
   - Wie hätte derselbe Kasten nach dem alten Stand abgeschnitten?
3. **Einstieg gegen Ergebnis:** die vier Einstiege auf denselben Kästen nebeneinander, also welcher Einstieg bei welcher
   Verlust-Art scheitert.
4. **„Was wäre wenn“** für den Stop (1 ATR, 1,5 ATR), das Ziel (1 R, 2 R) und das Zeitlimit (intraday bis 15:50 gegen ohne
   Einstieg nach 14:30; Tag 10 gegen 20 Tage).
   - Das wird **nur auf den Suchdaten** gerechnet und ist **keine Regel**.
   - Was davon auffällt, wird eine neue Idee im Register und muss auf den Bestätigungsdaten bestehen.

## 5. Neue Sichtprüfungen

- **Präzision** (wie bisher): „Ist das ein sauberer <Muster>?“, mindestens 80 % „ja“.
- **Einstieg prüfen** (`art: "einstieg"`): 30 zufällige Trades im Moment des Einstiegs, mit Einstieg, Stop und Ziel.
  - Frage: „Ist der Einstieg nach der Regel richtig gesetzt?“ So prüft der Inhaber selbst, ob die Einstiege stimmen.
  - Bei unter 90 % „ja“ werden die Nein-Fälle einzeln untersucht, bevor gerechnet wird.
- **Verlust-Prüfung** (`art: "verlust"`): 30 zufällige Verlust-Trades mit Ausgang.
  - Statt ja und nein gibt es die Gründe als Knöpfe, aus dem Feld `optionen` der Datei: `[{"key":"fehlausbruch","text":"Fehlausbruch"}, {"key":"kein_muster","text":"Kein echtes Muster"}, {"key":"stop_zu_eng","text":"Stop zu eng"}, {"key":"ziel_zu_weit","text":"Ziel zu weit"}, {"key":"zeit","text":"Zu wenig Zeit"}, {"key":"gegen_markt","text":"Gegen den Markt"}, {"key":"anderes","text":"Anderes"}]`.
  - Danach wird das Auge des Inhabers mit der automatischen Zuordnung aus Abschnitt 4 verglichen.
- **Trefferquote:** ganze Tage ohne Linien, mit Zeichnungen (gibt es schon).
- **Die Seite baut Claude.** Sie bekommt dafür:
  - Antwort-Knöpfe aus `optionen`;
  - die W-Form und weitere Formen über ein Feld `linien` (Liste mit `von {i,p}`, `bis {i,p}`, `art`);
  - Daten statt Uhrzeiten bei `zeitebene: 1440`;
  - je Variante die Zahlen für Ziel, Stop und Tagesende, und einen Filter „Ausgang“;
  - Einstiege nur mit Namen;
  - das Ideen-Register als Tabelle.

  Neue Sichtprüfungs-Arten gehen erst online, wenn diese Seite auf main ist.

## 6. Rechteck Fassung 3 (verbessern, nicht retten)

- **Grundlage ist die Analyse von Werkbank Rechteck v1** (Phase 2) und die Verlust-Prüfung des Inhabers.
- **Verbessert werden darf alles:** Erkennung, Einstiege, Stop, Ziel, Zeitebene (auch Tag), Zusammenhang. Dabei gilt:
  - Jede Änderung wird vorher im Register eingetragen und mit Hash festgelegt.
  - Die Erkennung bekommt wieder eine Sichtprüfung auf **neuen** Bildern.
  - Das Urteil fällt **nicht** auf den 50 Aktien von Okt. 2021 bis Sep. 2023, denn dort ist alles schon gesehen. Es fällt
    auf den Bestätigungsdaten aus Abschnitt 2.
- **Werkbank Rechteck v1 bleibt unverändert** als Vergleich stehen.

## 7. Hürden

- **Auf den Suchdaten** (Signal, um weiterzumachen):
  - nach Kosten positiv;
  - Kostenstress positiv;
  - Zufallstest mindestens 95 von 100;
  - Note A nicht schlechter als Note C;
  - genug Trades: Tag mindestens 200, intraday mindestens 50 je Jahr.
- **Auf den Bestätigungsdaten** (Bestätigung):
  - dieselben Kriterien;
  - dazu jedes Bestätigungsjahr positiv;
  - Vorzeichen und Größenordnung wie auf den Suchdaten.
- **Im Prüftopf** (Urteil): Kriterien K1–K5 aus `FAHRPLAN.md`, jedes Jahr positiv und die Zufallshürde „Bester von N“ mit N
  aus dem Register. Höchstens drei Öffnungen.

## 8. Phasen (jede endet mit Bericht und STOPP bis zum Okay des Inhabers)

| Phase | Inhalt |
|---|---|
| 1 | Gemeinsame Werkbank bauen; Gleichheitstest gegen Rechteck v1; Ideen-Register mit den verbrauchten Einträgen; Analyse-Modul; Tageskerzen laden (1.500 und Länder-ETFs) |
| 2 | Analyse Werkbank Rechteck v1 (Abschnitt 4) mit Bericht; Einstiegs-Prüfung und Verlust-Prüfung vorbereiten (online erst mit neuer Seite) |
| 3 | Doppelboden Schritt 1: Erkennung Tag, 5 und 15 Min, Pflichttests, Trichter, Zeitbudget-Regel, Sichtprüfung 1 vorbereiten |
| 4 | Doppelboden: Vorab-Datei, Lauf auf den Suchdaten, Analyse; bei bestandener Hürde Bestätigung |
| 5 | Rechteck Fassung 3 aus der Analyse von Phase 2, Vorab-Datei, Lauf |
| 6 und folgende | Die nächsten Muster aus dem Register, jeweils wie Phase 3–4 |
| optional | Prüfer-KI: ein Modell, geeicht an den Sichtprüfungs-Antworten des Inhabers, nimmt ihm Bilder ab. Nur nach eigener Freigabe, mit API-Schlüssel in der `.env`. |

## 9. Was immer gilt

- Nur Paper, keine Live-Freigabe. Risiko 0,5 % je Trade, höchstens 5 Positionen, 20-%-Wertgrenze unverändert.
- Nie zwei Instanzen auf einem Konto. Schlüssel nie ausgeben.
- Pi, Live-Bot und main bleiben unberührt; main nur für die Seite und nur nach Freigabe des Inhabers.
- Bot-Code kommt nicht auf GitHub. Öffentliche Dateien enthalten keine IP-Adressen, Hostnamen, Nutzernamen, Pfade, Schlüssel
  oder Kontonummern.
- Niemals force-push.
- Keine Läufe über Nacht auf dem Hauptrechner. Ein Lauf startet nur, wenn er vor 23:00 deutscher Zeit fertig ist.
- Nach jedem Schritt: Logbuch, `status.json` (Plan und Phase), kurzer Bericht an den Inhaber.
