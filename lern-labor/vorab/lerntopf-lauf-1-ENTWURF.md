# Vorab-Datei · Lerntopf-Lauf 1 · ENTWURF

**Entwurf vom 19.10.2026, mit den Entscheidungen des Inhabers vom selben Tag. Noch nicht festgelegt.**

Festgelegt wird nach der Prüfung durch Claude im Chat:
- als `lern-labor/vorab/lerntopf-lauf-1.md` auf backtest;
- mit Commit und SHA-256 im Logbuch.

Erst danach läuft irgendetwas auf echten Daten: keine Signale, keine Ergebnisse, keine Zufallsläufe. Bis dahin sind
nur Downloads und Tests auf künstlichen Kursen erlaubt. Nach der Festlegung ändert sich an den Regeln nichts mehr. Eine
Änderung ergibt eine neue Fassung mit neuer Nummer, und das nur, bevor Ergebnisse da sind.

## 1. Frage

Welche der 10 Muster M001–M010 haben im Lerntopf einen Vorteil? Und welcher Umgang mit Ziel und Haltedauer passt zu
ihrer Zeitebene? Das ist die erste Lerntopf-Frage (Fahrplan 4.8.21).

Befund aus Runde 1, der zu dieser Frage führt (nur Zählung, ohne Auswahl nach Ergebnis):
- 86 % der Trades enden durch Zeit-Stop oder Tagesende;
- 3,8 % erreichen das Ziel;
- die Ziele liegen im Median 1,49R entfernt.

## 2. Daten

| Teil | Zeitraum | Wofür |
|---|---|---|
| IEX 15 Min, split-bereinigt | 01.10.2020–29.09.2023, dazu der Vorlauf ab 01.09.2020 | Erkennung, Volumen, ATR, relative Stärke (wie im kalibrierten Replay) |
| IEX-Tageskerzen, split-bereinigt | ab 27.07.2020 | Tagestrend (EMA20/EMA50 aus 120 Sitzungen) |
| SIP-Tageskerzen, split-bereinigt | 2020 als Vorlauf, solange IEX noch keine 120 Sitzungen hat | Tagestrend am Anfang. Gemessen am 08.10. (Fahrplan 4.0.26): 0,46 % Abweichung, also gilt der SIP-Vorlauf, und der Lerntopf beginnt am 01.10.2020 |
| IEX 1 Min, nur SPY | jeder Handelstag | „SPY heute“ für den Marktfilter, wie im Replay |
| SIP 1 Min, split-bereinigt | jeder Handelstag, alle Werte | Einstieg, Stop, Ziel, Zeit-Stop, Tagesende, Kurslücken, Zufallsläufe |

- **Werte:** die 150 Werte der heutigen Liste wie in den Jahresrunden, dazu SPY. Werte ohne Kerzen in einem Zeitraum
  (z. B. nach einem Tickerwechsel) werden gezählt und im Bericht genannt.
- **Keine Quotes und keine einzelnen Abschlüsse im Lauf.** Spread und Schlupf laufen über das Kostenmodell
  (Abschnitt 6). Für die Gegenprobe (Abschnitt 8) gibt es eine Ausnahme: IEX-Abschlüsse und -Quotes, nur für Setups nach
  dem Volumenfilter. Sie werden nach dem Hauptdownload geladen, mit derselben Drosselung.
- **Downloads:**
  - nur auf dem PC;
  - gedrosselt auf höchstens 100 Abrufe je Minute;
  - an Handelstagen erst ab 22:30, nach dem Setup-Export des Bots um 22:20;
  - nie zwischen 15:30 und 22:00.
- **Split-bereinigt statt unbereinigt:** Die Steckbriefe sagen „unbereinigt, wie live“. Über drei Jahre ergäbe das an
  jedem Split falsche Kanten und einen falschen Tagestrend (Befund 1.13). Das kalibrierte Replay rechnet ebenfalls
  bereinigt.
- **Prüftopf:** Er bleibt zu. Aus der Zeit ab dem 01.10.2023 wird nichts geladen und nichts gelesen. Der
  Download-Auftrag verweigert jeden Abruf, der dort hineinreicht.
- **Überlebensverzerrung:** Die Liste stammt von heute. Werte, die 2020–2023 groß waren und heute fehlen (Übernahmen,
  Abstiege, Pleiten), sind nicht dabei. Das macht die Ergebnisse eher zu gut. Der Bericht nennt das an erster Stelle.

## 3. Kandidaten: 10 Muster × 4 Varianten = 40

Die Muster sind die Steckbriefe M001–M010 in der Fassung vom 19.10.2026, mit SHA-256 je Datei in Anhang A.
- **M001–M007:** Erkennung mit dem Code des Live-Bots (Stand cbfe06cff), genau wie im Replay.
- **M008–M010:** Erkennung mit dem Chart-Leser Teil 2, Festlegung v1.1 (Code-Hash c5ca9efa1343).

Jede Variante bekommt eine eigene Nummer, z. B. M003-H0 bis M003-H3. **Je Muster handeln alle 4 Varianten dieselben
Signale zum selben Einstieg.** Auch Auswahl und Filter rechnen bei allen 4 mit dem Ziel aus dem Steckbrief. Anders ist
nur der Ausstieg, und zwar je Variante nur eine Sache:

| Variante | Ziel | Haltedauer und Ausstieg |
|---|---|---|
| **H0** wie live | aus dem Steckbrief | wie der Live-Bot (Abschnitt 5) |
| **H1** ohne Zeit-Stop | aus dem Steckbrief | wie H0, nur ohne Zeit-Stop: bis Ziel, Stop oder Tagesende |
| **H2** halbe Musterhöhe | Kante + ½ × (Ziel aus dem Steckbrief − Kante), d. h. der halbe Weg von der Kante zum Ziel | sonst wie H0 |
| **H3** über Nacht | aus dem Steckbrief | wie H0, aber ohne Zeit-Stop und ohne Tagesende an Tag 1 und 2: bis Ziel oder Stop, höchstens 3 Handelstage (der Einstiegstag zählt als Tag 1), Ausstieg 10 Minuten vor Schluss des 3. Tages. Über Nacht gehalten, Kurslücken zählen voll. Spätestens Ausstieg am 29.09.2023 10 Minuten vor Schluss, damit kein Trade in den Prüftopf hineinläuft. Nur Simulation |

## 4. Signale

- **Point-in-time:** Jede 15-Min-Kerze wird nach ihrem Schluss bewertet, nur mit den Kerzen bis dahin. Es gilt dasselbe
  Fenster wie live: 200 Kerzen aus 14 Tagen, Tagestrend aus abgeschlossenen Sitzungen.
  - Die Eröffnungskerze wird wie live um 09:50 New York bewertet.
- **Abschneide-Test:** Er ist Pflicht und läuft vor dem ersten Lauf. Für zufällig gezogene Zeitpunkte gibt die
  Signalfunktion mit allen Daten und mit Daten nur bis zum Zeitpunkt genau dasselbe aus. Das Ergebnis kommt ins
  Logbuch.
- **Höchstens 1 Signal je Muster, Aktie und Tag:** Es zählt das erste Signal des Tages, das alle Filter besteht. Spätere
  Signale desselben Musters an derselben Aktie und demselben Tag werden nur gezählt.
- **Jedes Signal wird einzeln gewertet:** keine 5-Plätze-Grenze, keine Reihenfolge der Aktienliste. Verschiedene Muster
  an derselben Aktie zählen jedes für sich.

**Filter: wie im jeweiligen Steckbrief, mit den Funktionen des Bots auf denselben Kerzen.**

| Filter | M001–M007 | M008–M010 |
|---|---|---|
| Tagestrend in Handelsrichtung, wie im Code: nur für die Fortsetzungsmuster M001–M003; die Umkehrmuster M004–M007 laufen ohne diesen Filter | ja (M001–M003) | **nein**, stattdessen der Vortrend aus dem Steckbrief (4 ATR über bzw. unter dem Schluss 50 Kerzen davor) |
| Mindest-Stop 0,3 % vom Schlusskurs (enger wird aufgeweitet) | ja | ja |
| Chance-Risiko am Schlusskurs mindestens 0,8 | ja | ja |
| Volumen der Signalkerze mindestens 1,5 × Schnitt der letzten 20 Kerzen | ja | ja |
| Relative Stärke gegen SPY über 13 Kerzen in Handelsrichtung | ja | ja |
| SPY am Tag höchstens 0,5 % gegen die Handelsrichtung | ja | ja |
| Keine Einstiege in den ersten 20 und den letzten 30 Minuten | ja | ja |
| Anti-Chase-Zone V1 (max(0,4 × ATR; 0,1 %), am Schlusskurs verankert), gemessen am Einstiegskurs aus Abschnitt 5 | ja | ja |
| Chance-Risiko am Einstiegskurs mindestens 0,8 | ja | ja |
| Kursalter höchstens 60 s, Spread höchstens 0,25R | ohne Quotes nicht nachgebildet; das Kostenmodell deckt den Spread ab | ebenso |
| 5 Plätze, Risiko 0,5 %, Positionswert 20 % | nicht angewendet: jedes Signal einzeln, Ergebnis in R | ebenso |

**Nebenzählung, zählt nicht (Fahrplan 4.8.20):** Bei M008–M010 wird für jeden Ankerpunkt mit SIP-Kerze gezählt, wie oft
die 3×-Regel einen von SIP bestätigten Docht verworfen hätte und wie oft einen nicht bestätigten. Die Zählung ist
Grundlage für die Entscheidung über Chart-Leser v1.2.

## 5. Ausführung (Simulation auf SIP 1 Min)

- **Einstieg:** zum Eröffnungskurs der SIP-Minute nach dem Entscheidungszeitpunkt (Kerzenschluss + 33 s, wie live im
  Median). Bei einer Kerze bis 10:15 ist das die Minute 10:16. Für die Eröffnungskerze gilt die Minute 09:51.
- **Stop und Ziel:** auf 1-Min-SIP-Kerzen.
  - Berühren Stop und Ziel dieselbe Minute, zählt der Stop.
  - Der Stop füllt zum Stopkurs, oder zum Eröffnungskurs der Minute, wenn sie schon jenseits des Stops öffnet
    (Kurslücke voll).
  - Das Ziel füllt nur, wenn der Kurs durch das Ziel handelt, also nicht schon bei bloßer Berührung (wie im schnellen
    Simulator). Öffnet die Minute schon jenseits des Ziels, zählt ihr Eröffnungskurs.
- **Verwaltung wie live, in allen 4 Varianten** (die Werte stehen in der Einstellung des Bots):
  - **Break-even:** ab einem Minutenschluss bei +0,6R Stop auf den Einstieg ± 0,05 %;
  - **Trailing:** ab +1,5R folgt der Stop dem besten Minutenschluss im Abstand von 1R, nur in Gewinnrichtung;
  - **Zeit-Stop** (nur H0 und H2): ab 120 Minuten raus, wenn R ≤ 0 oder unter 80 % des besten R; nach 240 Minuten raus;
  - **Tagesende** (H0, H1, H2; H3 nur am 3. Tag): 10 Minuten vor Börsenschluss, an Halbtagen 12:50 New York.
  - Ausstiege nach den Prüfungen am Minutenschluss erfolgen zum Eröffnungskurs der nächsten Minute.
- **Steckbriefe:** Die Steckbriefe M001–M010 nannten den Trailing-Stop zunächst nicht. Er ist am 19.10. ergänzt, als
  Korrektur der Beschreibung des Codes, ohne neue Nummer (Logbuch).
- **H3 über Nacht:**
  - Über Nacht gibt es keine Prüfung. Die erste Minute des nächsten Tages kann jenseits von Stop oder Ziel öffnen.
    Dann zählt ihr Eröffnungskurs voll; beim Ziel ist das nie schlechter als das Ziel.
  - Vor- und Nachbörse werden nicht simuliert.
- **Schneller Simulator:** Grundlage ist `bt/exits.py`, für H1 und H3 erweitert. Seine Abweichung vom vollen Replay ist
  aus den Runden bekannt und wird im Bericht genannt (Runde 2: −0,059R gegen −0,083R je Trade).

## 6. Kosten und Kostenstress

- **Kosten nach den Erfolgskriterien** (Lern-Labor): je Trade der höhere Wert aus
  - 0,03R (long) bzw. 0,05R (short) und
  - der Slippage = 2 Seiten × max(0,01 $; 0,02 % vom Kurs) je Aktie, geteilt durch den Stop-Abstand je Aktie.
- **Kostenstress:** zusätzlich +0,03R je Trade.

## 7. Auswertung und Stufe 1

**Je Kandidat und je Jahr:**
- **Jahre:** J1 = 01.10.2020–30.09.2021, J2 = 01.10.2021–30.09.2022, J3 = 01.10.2022–29.09.2023. Ein Trade zählt im Jahr
  seines Einstiegs.
- **Kennzahlen:** Trades, Erwartungswert nach Kosten, Profitfaktor nach Kosten, Trefferquote, max. Drawdown (Trade für
  Trade in R, nach Einstiegszeit sortiert).
- **Ausgänge:** Ziel, Stop (Anfangsstop), Stop nach Break-even bzw. Trailing, Zeit-Stop, Tagesende, Ende der Haltedauer
  (H3), Datenende.
- **Zusätzlich:** Erwartungswert mit Kostenstress.
- **Über alle 3 Jahre zusammen:** dieselben Kennzahlen und die Zufallslatte.

**Zufallslatte „Bester von 40“ über alle 3 Jahre zusammen** (Erfolgskriterium K5 bei mehreren Kandidaten):
- **Zufallstrades:** Je Kandidat gibt es 100 Zufallsläufe, gebaut wie der bestehende Zufallsvergleich:
  - je echtem Trade derselbe Wert, derselbe Tag, eine zufällige Minute in derselben Stunde (nicht in den letzten
    30 Minuten);
  - die Richtung wird ausgelost;
  - Stop-Abstand in % und Ziel in R wie beim echten Trade;
  - dieselben Ausstiegsregeln der Variante (H3 mehrtägig) und dieselben Kosten.
- **Startwerte:** Fester Startwert 20261019. Lauf k zieht für alle Kandidaten mit demselben Startwert.
- **Latte:** In Lauf k ist die Latte der beste Zufalls-Erwartungswert über alle 3 Jahre unter allen 40 Kandidaten (nur
  Kandidaten mit Trades). Ein Kandidat liegt über der Latte, wenn sein Erwartungswert über alle 3 Jahre in mindestens
  95 von 100 Läufen höher ist als die Latte dieses Laufs.

**Stufe 1 (Lerntopf bestanden)** nur, wenn alle drei Bedingungen gelten:
1. **Jedes Jahr positiv:** J1, J2 und J3 je mit mindestens 30 Trades und Erwartungswert nach Kosten > 0;
2. **Zufallslatte:** über alle 3 Jahre über der Latte „Bester von 40“, also in mindestens 95 von 100 Läufen;
3. **Kostenstress:** über alle 3 Jahre mit +0,03R Kostenstress noch > 0.

**Einstufung in der Rangliste:**
- **„Stufe 1“:** alle drei Bedingungen erfüllt.
- **„zu wenig Daten“:** In mindestens einem Jahr gab es weniger als 30 Trades. Das gilt nicht als durchgefallen und
  steht so in der Rangliste. Die Kennzahlen werden trotzdem gezeigt.
- **„Stufe 0, nicht bestanden“:** sonst. Dazu steht, welche Bedingung fehlt.
- **Sortierung:** nach dem schwächsten der drei Jahre (Erwartungswert nach Kosten), damit ein einzelnes gutes Jahr
  nichts verdecken kann.

## 8. Gegenprobe vor dem Lauf

Sie läuft vor dem eigentlichen Lauf. Sie wertet nichts und wählt nichts aus.
- **M001-H0 und M003-H0** werden auf einem Lerntopf-Jahr (J3) gegen das Replay verglichen. Das Replay ist auf diese
  beiden Detektoren beschränkt.
- **Daten:** Für Kursalter und Spread braucht das Replay IEX-Abschlüsse und -Quotes, nur für Setups nach dem
  Volumenfilter. Sie werden nach dem Hauptdownload mit derselben Drosselung geladen.
- **Signale:** müssen 1:1 übereinstimmen (Wert, Muster, Seite, Kerze, Kante, Stop, Ziel).
- **Abweichungen:** werden einzeln erklärt. Erwartet sind sie nur bei den Filtern ohne Quotes (Kursalter, Spread), durch
  die fehlende 5-Plätze-Grenze und durch den Einstieg zur Minute statt am echten Fill.

## 9. Was festgehalten wird

- **Kennungen:** SHA-256 dieser Datei und der Steckbriefe M001–M010.
- **Code-Hashes:** Bot cbfe06cff, Chart-Leser v1.1 c5ca9efa1343, `bt/` 61750fbbc22e und der Code-Hash des
  Labor-Simulators, den der Logbuch-Eintrag vor dem Lauf nennt.
- **Daten:** Stand der Daten (Ladezeitpunkt) und fehlende Werte.
- **Bericht:** `lern-labor/lerntopf-lauf-1/` auf backtest, je Kandidat und Jahr, dazu die Rangliste.
  - Die Labor-Seite zeigt die Rangliste erst nach dem OK des Inhabers zum Diff.
- **Danach:** Nach dem Lauf wird an diesen Regeln nichts geändert. Neue Ideen aus dem Ergebnis werden neue Steckbriefe
  mit neuer Nummer und gehen in einen späteren Lauf.

## 10. Entscheidungen des Inhabers (19.10.2026)

1. Break-even und Trailing bleiben auch bei H1 und H3, damit je Variante nur eine Sache anders ist.
2. Die Filter rechnen auch bei H2 mit dem Ziel des Steckbriefs, also handeln alle 4 Varianten dieselben Signale.
3. Mindestens 30 Trades je Jahr. Darunter heißt es „zu wenig Daten“, nicht „durchgefallen“, und so steht es in der
   Rangliste.
4. IEX-Abschlüsse und -Quotes für die Gegenprobe, nach dem Hauptdownload und mit gleicher Drosselung.
5. Download-Start an Handelstagen um 22:30.
6. Die Zufallslatte „Bester von 40“ gilt über alle 3 Jahre zusammen, nicht je Jahr. Stufe 1 wie in Abschnitt 7.
7. H3 endet spätestens am 29.09.2023 zehn Minuten vor Schluss.
8. Trailing-Stop (ab 1,5R, Abstand 1R) in M001–M010 ergänzt, als Korrektur der Beschreibung des Codes ohne neue Nummer.
   Im Logbuch als Korrektur.
9. Für M008–M010 ist ausdrücklich genannt, welche Filter gelten (Tabelle in Abschnitt 4).

## Anhang A · SHA-256 der Steckbriefe (Fassung 19.10.2026)

| Steckbrief | SHA-256 |
|---|---|
| M001-aufsteigendes-dreieck.md | `a556401ca3674deb6ff20b8b3ad98164d95dc990a2b60973c7d720085ac683d2` |
| M002-absteigendes-dreieck.md | `9d861687ad2e1f72f415636ab87037f8e4ae4af62fffea41d81da510519383dc` |
| M003-rechteck.md | `a600a114d8788efae29e25fde1730c9e6f1467f51a6b8b149837a896fecba8b4` |
| M004-doppeltop.md | `089d7d1e9069aec03910b291a84ddd6d26391eb8be8aca0442ea2ac4e8a43f55` |
| M005-doppelboden.md | `bf5341c3d933198d24ddc47ea0aa7cec5e54fae211b5df83f137187fe9ee115e` |
| M006-schulter-kopf-schulter.md | `4cb3b796431460f2525a02716b8d13c2ef7aebc8f4caba4512af184a818e218a` |
| M007-inverse-schulter-kopf-schulter.md | `35bf948413845a01ddfbfec0a62c739fcd9a5be2803d0ee396fd65dff05dfb49` |
| M008-keil-steigend.md | `ea04a6698e4de7ce74b3e22dfb68ffe6f47e0d1a1eb9c0b4b7fa34ac5fb9d96e` |
| M009-keil-fallend.md | `da4c8e2629354e7c5a50d5f45f8279e9fd7ab2efd215039950e1726e668b761e` |
| M010-doppelboden-mit-kaufkraft.md | `d0ab6beac91b2228773346c19f1b542ca511385859e76f6ea746f84de3186ae2` |
