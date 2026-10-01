# Fehler und Verbesserungen – sortiert nach Geld-Wirkung

Stand: 01.10.2026 · Datenbasis: 56 echte Paper-Trades vom 10.09. bis 30.09.2026, die Setup-Exporte vom 28. bis 30.09. und die Nachsimulationen vom 26.09. bis 01.10.

**So ist die Liste aufgebaut**

- Sortiert nach dem Geld, das der Punkt im beobachteten Zeitraum verändert hat oder laut Simulation verändert hätte.
- 1R ist der Betrag, den ein Trade riskiert. Im Schnitt waren das 28,94 $ in der alten Version und 22,83 $ in der neuen (geplant: 49,87 $). Die Dollarbeträge sind deshalb grob gerundet.
- Simulationen beruhen auf wenigen Tagen. Sie zeigen die Richtung, sind aber kein Beweis.
- Was sich nur per Backtest entscheiden lässt, steht in einem eigenen Abschnitt.

**Pflege:** Neue Punkte an der passenden Stelle einsortieren, immer mit Beleg (Trade-Nummer, Datum oder Simulation). Behobene Punkte nicht löschen, sondern auf ✅ setzen und das Datum eintragen.

**Status:** ✅ behoben · ⏳ gebaut, noch nicht aktiv · ⬜ offen · 🔬 nur per Backtest entscheiden · ❌ geprüft und verworfen

## Übersicht

| # | Thema | Geld-Wirkung | Status |
|---|---|---|---|
| 1 | Einstieg erst Minuten nach Kerzenschluss | +5,4R in 49 Trades, ≈ +155 $ (Simulation) | ✅ seit 28.09. |
| 2 | Anti-Chase-Zone an der Kante statt am Schlusskurs (V1) | +3,0R in 3 Tagen, 13 Trades, ≈ +70 $ (Simulation) | ⏳ |
| 3 | Blinde Fenster bei 5 offenen Positionen | mindestens 1 verpasster Trade: INTU, später +2R, ≈ +58 $ | ⬜ |
| 4 | Orders vor Börsenöffnung (01.09.) | −50 $ | ✅ |
| 5 | Zonengrenzen nicht auf den Cent gerundet (V2) | +1,77R in 3 Tagen, ≈ +40 $ (Simulation) | ⬜ |
| 6 | Rechteck-Muster schwach | −31,55 $ (15 Trades, −1,73R) | 🔬 |
| 7 | Ziele ab 1,5R werden nicht erreicht | −22,29 $ (12 Trades, −0,57R) | 🔬 |
| 8 | Übernacht- und Vorbörsen-Fehler (UAL, NSC) | ≈ −22 $ direkt, die Gefahr war viel größer | ✅ |
| 9 | Einstiege in den letzten 90 Minuten | −13,78 $ (17 Trades, −0,58R) | 🔬 |
| 10 | Eröffnungskerze und Nachholrunde um 09:50 | ≈ −11 $ (11 Trades, −0,39R), dazu CRM ohne Fill | 🔬 |
| 11 | Paper füllt Ziel-Limits erst am Geldkurs (VRTX) | +8,70 $ verpasst | ⬜ |
| 12 | Zeitgrenze nur zu Rundenbeginn geprüft (EMR, HIG nach 15:30) | −5,00 $ | ✅ |
| 13 | Stop-Ausführung hinter dem Stop (NSC, DHR) | ≈ −2 $ | ✅ |
| 14 | Spread-Prüfung mit unbrauchbarem IEX-Orderbuch (V4) | +0,10R, ≈ +2 $ (Simulation) | ⬜ |
| 15 | Ungleiches Risiko pro Trade durch die Wertgrenze | verzerrt Dollar gegen R, Wirkung in beide Richtungen | ⬜ |
| 16 | Technik ohne direkte Geld-Wirkung | 0 $, aber Messfehler und Ausfallrisiko | siehe Details |

## Wirkung noch unbekannt – nur per Backtest

Diese Punkte haben vermutlich die größte Hebelwirkung auf Dauer, lassen sich aus wenigen Tagen aber nicht beziffern.

| Thema | Warum wichtig | Status |
|---|---|---|
| Ausbrüche laufen kaum weiter | Bester Zwischenstand im Median nur +0,19R, 2 von 42 Zielen erreicht. In der Woche 21.–25.09. lagen theoretisch rund 12R „auf dem Tisch“, realisiert wurden 2R. | 🔬 |
| Teilgewinn plus Trailing-Stop statt festem Ziel | Lässt einzelne große Gewinner zu. Heute endet fast jeder Trade per Zeit-Stop oder Tagesende. | 🔬 |
| Marktfilter (Richtung des Gesamtmarkts, SPY) | Am 28.09. verloren drei Shorts, während der Markt ab Mittag stieg. | 🔬 |
| Enge Seitwärtsphase vor dem Ausbruch | Klassischer Qualitätsfilter für Ausbrüche, bisher nicht im Regelwerk. | 🔬 |
| Vergleich mit zufälligen Einstiegen | Zeigt, ob die Muster überhaupt besser sind als Zufall. Wichtigster Test überhaupt. | 🔬 |
| Kosten realistisch abziehen | Paper-Ausführungen sind zu freundlich. Pauschal 0,03R bis 0,05R pro Trade abziehen. | ⬜ |

## Geprüft und verworfen

| Idee | Ergebnis | Status |
|---|---|---|
| Volumenfilter auf 1,25 lockern (V5) | −2,03R in 3 Tagen (+7 Orders) | ❌ |
| Volumen nach Tageszeit normieren (V5) | −5,23R in 3 Tagen (+27 Orders) | ❌ |
| Frische-Grenze 180 statt 60 Sekunden (V3) | 0 zusätzliche Orders, die Fälle scheitern danach an der Zone | ❌ |
| Stop-Order direkt am Ausbruchsniveau („10R“) | Bestfall +10,2R, mit früheren Durchstichen +2,4R, über alle 150 Aktien etwa 0R pro Trade | ❌ vorerst, nur per Backtest neu bewerten |
| Zeit-Stop nach 60 statt 120 Minuten | −1,2R statt +2,4R in 49 Trades | ❌ |
| Ohne Zeit-Stop, ohne Break-even, Ziel halb so weit | +2,3R, +2,4R und +2,1R statt +2,4R, also kein Gewinn | ❌ |
| Long und Short vertauscht | −1,6R statt +2,4R. Alle 53 geprüften Trades waren in der richtigen Richtung. | ❌ |
| Alle Break-even-Strategien (46 Varianten in 11 Familien, Details in [break-even-vergleich.md](break-even-vergleich.md)) | Keine ist verlässlich besser als „ab +0,6R auf Einstieg“. Jedes Plus hängt an DHR, früher Break-even kostet bis −89 $. | ❌ |
| Break-even früher: ab +0,5R / +0,4R / +0,3R statt +0,6R | +0,26R / −0,48R / −1,34R in 56 Trades. Rettet DHR, schneidet aber ein bis sechs Gewinner ab. | ❌ |
| Break-even bei 40 % / 50 % / 60 % / 75 % des Wegs zum Ziel statt fest bei +0,6R | −0,80R / +0,47R / +0,60R / +0,60R in 56 Trades (−18,86 $ / +4,63 $ / +9,50 $ / +9,50 $). Der Gewinn kommt allein von DHR, dafür werden CRM und LUV abgeschnitten. Seit 28.09. deckt die Prüfung „Chance zu Risiko mindestens 0,8 am Fill“ den DHR-Fall ab. | 🔬 im Backtest erneut prüfen |
| Fehlausbruch-Ausstieg: raus, sobald eine 15-Min-Kerze wieder hinter der Kante schließt | −0,71R in 52 Trades. Alte Version +1,01R, neue Version −1,73R, weil Einstiege jetzt direkt an der Kante liegen und kurze Rücksetzer normal sind. | ❌ |
| Teilgewinn: Hälfte bei +0,4R bis +0,8R schließen, Rest mit Stop auf Einstieg | −0,20R bis −1,06R in 52 Trades. Der Zeit-Stop mit 80-%-Regel sichert die Gewinne schon ähnlich ab. | ❌ |

## Details

### 1. Einstieg erst Minuten nach Kerzenschluss ✅

- **Problem:** Die Order ging im Median 4,2 Minuten (bis 13,6 Minuten) nach dem Schluss der Signalkerze raus. Der Einstieg lag im Median 0,16R hinter der Ausbruchskante, bei DHR (t28) sogar 0,87R.
- **Beleg:** Nachsimulation der 49 Trades vom 21. bis 29.09.: so wie gehandelt +2,4R, mit Order direkt bei Kerzenschluss +7,7R. 37 von 42 Trades der ersten Woche wären besser gelaufen. Die Bot-Session kam auf 1-Minuten-Daten unabhängig auf +6,16R gegenüber +2,00R.
- **Lösung:** Seit 28.09. geht die Order 32 bis 38 Sekunden nach Kerzenschluss raus, der Fill liegt 0,05R bis 0,11R hinter der Kante.

### 2. Anti-Chase-Zone an der Kante statt am Schlusskurs (V1) ⏳

- **Problem:** Die neue Version verankert die Zone an der Ausbruchskante. Lag der Schlusskurs schon weiter weg, war der Trade per Konstruktion verloren. Das betraf 17 der 47 Trades vom 21. bis 28.09.
- **Beleg:** Unabhängige Nachrechnung auf den Setup-Exporten: 13 zusätzliche Trades vom 28. bis 30.09., zusammen +3,00R, 10 davon Gewinner. Die Bot-Session rechnete +9 Orders und +2,34R. Der Simulator trifft die echten Trades auf 0,05R genau.
- **Lösung:** Schalter `PATTERNBOT_CHASE_ANCHOR=close` ist gebaut, war am 30.09. aber noch aus. Einschalten nach Handelsschluss bei flachem Broker.

### 3. Blinde Fenster bei 5 offenen Positionen ⬜

- **Problem:** Sind 5 Positionen offen, bewertet und protokolliert der Bot keine Setups mehr. Die Reihenfolge der Kandidaten folgt der Sortierung nach Börsenwert, nicht der Qualität.
- **Beleg:** Am 24.09. von 09:53 bis 11:52 New York blind. Das INTU-Rechteck lief später +2R und wurde nie angesehen (Analyse vom 27.09.).
- **Lösung:** Auch bei voller Kapazität alles bewerten und als `skip-maxopen` protokollieren. Später Kandidaten nach Qualität ordnen, nur per Backtest.

### 4. Orders vor Börsenöffnung (01.09.) ✅

- **Problem:** Um 04:00 New York wurden auf dünnen Vorbörsen-Daten 5 Orders angelegt, die alle zur Eröffnung ausgeführt wurden.
- **Wirkung:** −50 $ direkt zur Eröffnung.
- **Lösung:** Harte Sperre, solange die Börse geschlossen ist. Eine leere Börsenuhr blockiert ebenfalls.

### 5. Zonengrenzen nicht auf den Cent gerundet (V2) ⬜

- **Problem:** Setups scheiterten um einen halben bis zwei Cent an der Zone, zum Beispiel NOW (½ Cent unter der Kante), HIG (1 Cent), SYK.
- **Beleg:** Simulation der Bot-Session: +2 Orders, +1,77R in 3 Tagen. Das überlappt teilweise mit V1, alle Vorschläge V1 bis V4 zusammen ergaben +3,18R.
- **Lösung:** Zonengrenzen auf den Cent runden. Das ist ein Rundungsfehler, keine Strategiefrage.

### 6. Rechteck-Muster schwach 🔬

- **Beleg:** Woche 21.–25.09.: 15 Rechtecke, −1,73R, Trefferquote 33 %. Alle anderen Muster zusammen: 27 Trades, +3,73R. Seit 28.09. mit der neuen Version: 3 Rechtecke, −0,42R.
- **Nächster Schritt:** Im Backtest getrennt auswerten. Erst streichen, wenn es sich über mindestens 100 Rechtecke bestätigt.

### 7. Ziele ab 1,5R werden nicht erreicht 🔬

- **Beleg:** Woche 21.–25.09.: 12 Trades mit Ziel ab 1,5R, −0,57R. Kein einziges Ziel ab 1,5R wurde erreicht, beide erreichten Ziele lagen unter 0,75R.
- **Nächster Schritt:** Hängt mit „Ausbrüche laufen kaum weiter“ zusammen. Im Backtest Ziel nach typischer Bewegung oder Teilgewinn plus Trailing testen.

### 8. Übernacht- und Vorbörsen-Fehler (UAL, NSC) ✅

- **UAL (t1, 10./11.09.):** Position blieb über Nacht offen, der Stop brach vorbörslich. Der Bot löschte die echte Stop-Order und schickte eine Market-Order, die erst zur Eröffnung ausgeführt wurde. Ergebnis −66,91 $ (−1,43R), davon rund −20 $ allein durch den Fehler. Der größte Einzelverlust im ganzen Log.
- **NSC (t33/t41, 24./25.09.):** Die Glattstellung am Tagesende schlug fehl, 6 Aktien liefen ohne Stop über Nacht. Am nächsten Tag eröffnete der Bot auf dieser Waise eine zweite Position. Buchungsdifferenz −2,02 $ (DB +83,83 $ gegen Broker +81,81 $), korrigiert am 28.09.
- **Lösung:**
  - Glattstellung nur mit bestätigter Ausführung
  - Tagesende über die echten Broker-Positionen
  - Abgleich Broker gegen Bot jede Minute, Waisen werden geschlossen
  - Sperre für Symbole mit offener Position
  - Stops ruhen beim Broker
- **Hinweis:** Das Geld war hier gering, die Gefahr einer ungeschützten Position über Nacht aber unbegrenzt. Deshalb hatte dieser Punkt beim Beheben Vorrang.

### 9. Einstiege in den letzten 90 Minuten 🔬

- **Beleg:** Woche 21.–25.09.: 17 späte Trades −0,58R, die 25 früheren +2,58R.
- **Nächster Schritt:** Restzeit gegen Zielabstand im Backtest prüfen.

### 10. Eröffnungskerze und Nachholrunde um 09:50 🔬

- **Beleg:**
  - Alte Version: 11 von 42 Trades aus der Eröffnungskerze, zusammen −0,39R.
  - 30.09.: In der Nachholrunde war der Kurs bei drei Setups schon wieder hinter der Kante.
  - CRM blieb ohne Fill, weil das Limit aus einem 27 Sekunden alten IEX-Kurs stammte. Laut Simulation hätte CRM +0,45R gebracht.
  - Die universumweite Analyse vom 27.09. fand Füllungen zwischen 09:30 und 09:50 klar negativ.
- **Nächster Schritt:** Im Backtest getrennt auswerten. Limit aus der Zone setzen, nicht aus dem letzten IEX-Kurs.

### 11. Paper füllt Ziel-Limits erst am Geldkurs (VRTX) ⬜

- **Beleg:** VRTX (t10, 22.09.): Ziel 525,67, gehandelt wurde bis 525,97, das Verkaufs-Limit wurde trotzdem nicht ausgeführt, weil der Geldkurs nur bis 525,63 kam. Ergebnis +1,18R statt +1,61R, also 8,70 $ verpasst.
- **Lösung:** Ziel-Order minimal vor das Ziel legen, zum Beispiel einen Cent. Nach jedem Stop-Nachzug prüfen, dass beide Teile der Bracket-Order noch leben.

### 12. Zeitgrenze nur zu Rundenbeginn geprüft ✅

- **Beleg:** EMR (t45) und HIG (t46) wurden am 25.09. um 15:30:54 New York eröffnet, obwohl in den letzten 30 Minuten keine Einstiege erlaubt sind. Zusammen −5,00 $ (−0,39R).
- **Lösung:** Zeitgrenzen werden direkt vor jeder Order geprüft.

### 13. Stop-Ausführung hinter dem Stop ✅

- **Beleg:** DHR (t28) wurde 0,185 $ unter dem Stop ausgeführt. Bei NSC (t41) lag der Ausstieg hinter dem nachgezogenen Stop, weil der Bot nur alle 3–4 Minuten prüfte. Zusammen etwa −2 $.
- **Lösung:** Stop- und Ziel-Orders ruhen jetzt beim Broker. Der Stop-Nachzug benutzt die neue Order-Nummer.

### 14. Spread-Prüfung mit unbrauchbarem IEX-Orderbuch (V4) ⬜

- **Beleg:** Am 30.09. wurde PH einmal mit einem „Spread“ von 62,93R abgelehnt, MPC mit 20,53R, AVGO mit 4,26R. Das kostenlose IEX-Orderbuch ist für diese Prüfung zu dünn.
- **Lösung:** Spread-Prüfung nur mit plausiblem Orderbuch, sonst schützt das Limit allein. Simulation: +1 Order, +0,10R.

### 15. Ungleiches Risiko pro Trade durch die Wertgrenze ⬜

- **Beleg:** Geplant sind 49,87 $ Risiko pro Trade. Tatsächlich waren es im Schnitt 28,94 $ (alte Version) bzw. 22,83 $ (neue), einzelne Trades lagen bei 7 $ bis 16 $. Der beste Trade vom 28.09. (C, +1,07R) brachte deshalb nur 13,35 $.
- **Wirkung:** Ergebnisse in R und in Dollar laufen auseinander. Bei einem Vorteil halbiert das den Gewinn, ohne Vorteil den Verlust.
- **Lösung:** Gleiches tatsächliches Risiko für jeden Trade, zum Beispiel ein niedrigeres Risiko, das die Wertgrenze nie erreicht.

### 16. Technik ohne direkte Geld-Wirkung

| Thema | Wirkung | Status |
|---|---|---|
| Break-even vermeintlich defekt (geprüft 01.10.): In allen 9 Fällen ab +0,6R wurde der Stop korrekt nachgezogen. DHR (t28) scheiterte, weil das Ziel nach dem späten Fill nur 0,6R entfernt lag, genau auf Höhe der Break-even-Schwelle. | Kein Fehler im Break-even. Seit 28.09. verhindern der schnelle Einstieg und die Prüfung „Chance zu Risiko mindestens 0,8 am Fill“ solche Fälle. | ✅ |
| Webseite zeigt den nachgezogenen Stop nicht: In der Trade-Detailansicht stehen nur der ursprüngliche Stop und die ursprüngliche Stop-Linie. `final_stop` aus `trades/tNN.json` wird nirgends angezeigt, zum Beispiel WMT 110,79 → 109,62, MS 192,78 → 190,42. | Kein Geld, aber man hält den Break-even für defekt. Lösung: zweite Stop-Linie „Stop nachgezogen“ und eine Zeile „Break-even gesetzt, +x R gesichert“. Der Bot sollte dafür auch den Zeitpunkt des Nachziehens speichern. | ⬜ |
| Phantom-Gewinne durch Buchungsfehler (26.08.): DB +595 $, Broker etwa ±0 | Falsche Messung | ✅ |
| Bot lief 9 Handelstage nicht (11.–21.09., BIOS „Last State“) | Zwei Wochen Daten verloren | ✅ |
| Trichter zählte gesendete statt gefüllte Orders | Falsche Messung | ✅ 30.09. |
| Stop-Nachzug ab dem zweiten Mal wirkungslos (neue Order-Nummer verworfen) | Gefahr: Stop bleibt zu weit weg | ✅ |
| Fill-Zuordnung nur nach Symbol, Seite und Zeit | Falsche Ergebnisse bei NSC | ✅ |
| Einstiegspreis aus dem Positionsdurchschnitt statt aus der eigenen Order | Falscher Einstieg bei t41 | ✅ |
| API-Aussetzer galten als „Position geschlossen“ | Gefahr: lebende Position ohne Überwachung | ✅ |
| Absturz zwischen Absenden und DB-Eintrag | Gefahr: unbekannte Position | ✅ |
| Kill-Switch sperrte Symbole dauerhaft | Fehlende Trades | ✅ |
| Tagestrend aus einer halben Tageskerze | Nicht reproduzierbare Signale | ✅ |
| Protokolle gingen verloren, keine Rotation | Fehlende Daten | ✅ |
| IEX liefert für BK, MMC und FI keine Kerzen | Tote Symbole im Universum | ⬜ |
| Kein Echtzeit-SIP (veraltete Kurse, dünnes Orderbuch) | Für Paper verkraftbar, für Echtgeld nötig | ⬜ |
| Bot-Version wird nicht bei jedem Trade gespeichert | Änderungen lassen sich nicht sauber vergleichen | ⬜ |
| Kein schriftlicher Notfallplan (Strom, Internet, API) | Gefahr bei Ausfall mit offener Position | ⬜ |
