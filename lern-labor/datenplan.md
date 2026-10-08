# Datenplan Lern-Labor

Entwurf vom 08.10.2026. Die Größen sind auf dem PC gemessen, im Cache der Jahresrunde 1 (150 Werte und SPY, ein Jahr).
Sie werden je Wert und Monat bzw. Tag hochgerechnet.

## Töpfe

| Topf | Zeitraum | Laden |
|---|---|---|
| Such- und Lerntopf | 01.10.2020–30.09.2023 | jetzt (Sa/So 10.–11.10.), auf dem PC |
| Prüftopf | 01.10.2023–30.09.2026 | erst nach Freigabe der ersten Vorab-Datei |
| Zukunft | ab dem Einfrieren | jede Nacht die Daten des Tages |

Teile des Prüftopfs liegen schon im Cache der Jahresrunden 1 und 2. Die Runden sind eine eigene Spur. Das Labor greift
auf diese Jahre erst nach der Freigabe zu.

**Universum:**
- die 150 Werte wie live und SPY;
- die 1.500er-Liste wie bei ORB folgt später (Größe siehe unten);
- jeder Bericht nennt die Überlebensverzerrung: Die heutige Liste enthält keine Werte, die früher gelistet waren und
  heute fehlen.

## Teile und Größen (Lerntopf, 3 Jahre, 151 Werte)

| Teil | Wofür | Auflösung | Messgröße | Größe |
|---|---|---|---|---|
| IEX 15 Min, split-bereinigt | Erkennung wie live; die Formen in Etappe 2 auf genau diesen Kerzen | 15 Min, reguläre Handelszeit | 21,8 KB je Wert und Monat | ≈ 120 MB |
| IEX-Tageskerzen, split-bereinigt und roh | Tagestrend wie live (EMA20/EMA50 aus 120 Tageskerzen), Kurslücke, Split-Faktor | 1 Tag | 2 × 5,2 KB je Wert und Monat | ≈ 60 MB |
| IEX 1 Min SPY | Marktfilter „SPY heute“ wie live | 1 Min | 15,8 KB je Tag | ≈ 12 MB |
| IEX letzter Abschluss und IEX-Quote zum Entscheidungszeitpunkt | Kurs-Frische, Spread, Chance-Risiko am Fill; nur für Setups nach dem Volumenfilter, wie live | einzelne Abfragen | ≈ 12.400 Abfragen je Jahr, je 0,1 KB | ≈ 5 MB Inhalt |
| SIP 1 Min, split-bereinigt, 05:00–21:00 New York | Ergebnis jedes Setups (Stop, Ziel, Zeitstopp, Tagesende); Vorbörse für die Kurslücke | 1 Min | 19,5 KB je Wert und Tag | ≈ 2,2 GB |
| SIP-Abschlüsse in kurzen Fenstern nach einem Fill | Stop und Ziel in den ersten Minuten (Tick-Pfad des Replays) | Abschlüsse | 32,9 KB je Fenster, ≈ 1.600 Fenster je Jahr | ≈ 150 MB |
| SIP-Quotes am Ziel | Ziel-Limit füllt wie Paper erst am Geld- bzw. Briefkurs | Quotes | < 0,1 MB je Jahr | < 1 MB |
| Setups 2020–2023 aus dem Replay | Lerndaten Etappe 1: alle Setups, auch die verworfenen | – | 3,5 MB je Jahr, gepackt | ≈ 11 MB |
| Nachrichten (erster Veröffentlichungszeitpunkt) | Situation zur Form | – | geschätzt, noch nicht gemessen | 25–75 MB |
| Termine der Quartalszahlen (SEC-EDGAR, Annahmezeit) | Situation zur Form | – | ≈ 1.800 Meldungen | < 5 MB |
| Universum zum Stichtag | Überlebensverzerrung | – | – | < 1 MB |
| **Summe Lerntopf** | | | | **≈ 2,7 GB** |

Der Prüftopf braucht später noch einmal etwa dieselbe Größe. Die 1.500er-Liste über 3 Jahre bräuchte etwa 22 GB
(SIP 1 Min) und 1,2 GB (IEX 15 Min). Sie läuft deshalb nur auf dem PC (77 GB frei).

## Was dabei auffällt

1. **Tagestrend am Anfang des Lerntopfs.**
   - IEX-Tageskerzen gibt es erst ab August 2020. Der Bot braucht für den Tagestrend mindestens 55 Tageskerzen und
     lädt live 120.
   - Bis Mitte Oktober 2020 gibt es deshalb keinen Tagestrend, alle Signale fielen weg. Bis etwa Februar 2021 ist die
     Historie kürzer als live.
   - Zu entscheiden in der Vorab-Datei von Etappe 1:
     - **a)** SIP-Tageskerzen (ab 2016) nur zum Aufwärmen, gekennzeichnet;
     - **b)** Oktober 2020 bis Januar 2021 nur zum Aufwärmen nutzen, nicht zum Lernen.
   - Empfehlung: b), weil sie nichts nachbildet, was live anders wäre.
2. **Viele kleine Dateien.**
   - Die Abfragen zum Entscheidungszeitpunkt sind winzig, ergeben aber etwa 37.000 Dateien in drei Jahren.
   - Im Labor werden sie je Wert und Tag zusammengefasst, die 1-Min-Kerzen je Wert und Monat. Das spart auf dem Pi
     Platz und Zeit.
3. **IEX-Kurse nur, wo die Filter sie brauchen.**
   - Live fragt der Bot den letzten Kurs und das Buch erst nach dem Volumenfilter ab. Für die übrigen Setups gibt es
     diese Werte auch live nicht.
   - Das Lernmodell bekommt dort nur, was aus den Kerzen folgt.

## Abrufe und Dauer

- Nur außerhalb der Handelszeit, gedrosselt auf höchstens 100 Abrufe je Minute.
- Auf dem Pi nur mit eigenen Schlüsseln des Labors, nie mit denen des Bots.
- Die SIP-1-Min-Kerzen kommen mit mehreren Werten je Abruf. Das sind etwa 7.000 Abrufe, rund 70 Minuten.
- Alle Teile zusammen brauchen geschätzt 2 bis 3 Stunden.
- Zwischenstände bleiben im Cache, nichts wird doppelt geholt.

## Wo was liegt und gerechnet wird

**PC** (Ryzen 7, 63 GB Arbeitsspeicher, Grafikkarte):
- alle Downloads des Lerntopfs;
- Etappe 2 (Fenster, Gruppen);
- große Trainingsläufe.

Die Fensterbildung umfasst etwa 3 Millionen 15-Min-Kerzen. Fenster mit 32 Kerzen ergeben etwa 1,9 GB im Arbeitsspeicher.

**Pi** (3,8 GB Arbeitsspeicher):
- nächtlicher Schatten;
- kleine Modelle;
- die Daten des Tages.

Der Labor-Ordner auf dem Pi:
- bekommt eine feste Obergrenze, Vorschlag 12 GB, als eigenes Dateisystem in einer Datei;
- wer sie füllt, stoppt das Labor, nicht den Bot;
- zusätzlich stoppt das Labor, wenn auf dem System weniger als 5 GB frei sind.
