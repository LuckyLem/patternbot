# Break-even-Strategien im Vergleich

Stand: 01.10.2026 · 46 Strategien, simuliert über alle 56 Trades vom 10.09. bis 30.09.2026.

**So wurde gerechnet**

- Alle übrigen Regeln bleiben wie im Bot: Stop, Ziel, Zeit-Stop nach 120 Minuten mit 80-%-Regel, harte Grenze 240 Minuten, Tagesende.
- Grundlage sind die 15-Minuten-Kerzen aus `trades/`. Ein neuer Stop wirkt ab der nächsten Kerze, innerhalb einer Kerze gilt Stop vor Ziel.
- Verglichen wird mit der heutigen Regel: ab +0,6R Stop auf Einstieg +0,03R. Diese Regel ergibt in der Simulation +1,98R.
- Dollar: jede Änderung in R mal das tatsächliche Risiko des jeweiligen Trades.
- **Ohne Top-Trade** zeigt die Änderung ohne den einen Trade, der sich am stärksten verändert. Bleibt davon nichts übrig, hängt das Ergebnis an einem einzigen Trade.
- 46 Varianten auf 56 Trades heißt: Die beste Variante sieht fast zwangsläufig auch durch Zufall gut aus. Entschieden wird im Backtest mit mindestens 200 Trades.

## Ergebnis in Kürze

- **Keine Variante ist verlässlich besser als die heutige Regel.** Jede Variante mit Plus verdankt es DHR (t28). Diesen Fall verhindern seit 28.09. der schnelle Einstieg und die Prüfung „Chance zu Risiko mindestens 0,8 am Fill“.
- **Ab +0,6R ist es egal, wohin der Stop wandert oder ob nachgezogen wird.** Kein Trade ist danach zurückgefallen, der Zeit-Stop beendet die Trades vorher.
- **Früher Break-even kostet deutlich:** nach der ersten Kerze im Plus −89 $, nach 0,5 ATR −79 $, ab +0,2R −51 $, nach 30 Minuten −50 $.
- **Einzige Variante ohne Abhängigkeit von einem Trade:** „Nach 90 Minuten auf Einstieg, wenn im Plus“ mit +8,71 $ über drei Trades. Das ist zu klein, um daraus etwas abzuleiten.

## Alle Strategien, sortiert nach Dollar-Wirkung

| Strategie | Familie | Änderung R | Änderung $ | besser | schlechter | ohne Top-Trade | Top-Trade | alte Version | neue Version |
|---|---|---|---|---|---|---|---|---|---|
| Stufen 0,5→±0 / 0,8→+0,3 / 1,2→+0,6 | Stufen | +1,00 | +25,56 | 1 | 0 | +0,00 | DHR +1,00 | +1,00 | +0,00 |
| Fest ab +0,5R, Stop auf Einstieg | Feste Schwelle | +0,26 | +10,81 | 1 | 1 | −0,77 | DHR +1,03 | +0,26 | +0,00 |
| Bei 60 % des Zielwegs | Zielabstand | +0,60 | +9,50 | 1 | 1 | −0,43 | DHR +1,03 | +0,60 | +0,00 |
| Bei 75 % des Zielwegs | Zielabstand | +0,60 | +9,50 | 1 | 1 | −0,43 | DHR +1,03 | +0,60 | +0,00 |
| Nach 1,5 ATR Bewegung | ATR | +0,60 | +9,50 | 1 | 1 | −0,43 | DHR +1,03 | +0,60 | +0,00 |
| Nach 90 Min, wenn im Plus | Zeit | +0,18 | +8,71 | 2 | 1 | +0,02 | COF +0,16 | +0,14 | +0,04 |
| Bei 50 % des Zielwegs | Zielabstand | +0,47 | +4,62 | 1 | 2 | −0,56 | DHR +1,03 | +0,47 | +0,00 |
| Hälfte bei +0,5R, Rest auf Einstieg | Teilgewinn | −0,09 | +2,24 | 4 | 6 | −1,35 | DHR +1,27 | +0,14 | −0,23 |
| Ab +0,3R Stop knapp hinter die Kante | Kante | −0,17 | +1,92 | 1 | 1 | +0,48 | ZTS −0,66 | +0,48 | −0,66 |
| Trailing ab +0,6R, Abstand 2,0 ATR | Trailing ATR | +0,03 | +0,62 | 1 | 0 | +0,00 | ITW +0,03 | +0,03 | +0,00 |
| Ab +0,6R, Stop auf +0,3R | Stop-Abstand | +0,01 | +0,13 | 0 | 0 | +0,00 | ITW +0,01 | +0,01 | +0,00 |
| Ohne Break-even | keiner | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Fest ab +0,6R, Stop auf Einstieg | Feste Schwelle | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Fest ab +0,7R, Stop auf Einstieg | Feste Schwelle | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Fest ab +0,8R, Stop auf Einstieg | Feste Schwelle | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Fest ab +1,0R, Stop auf Einstieg | Feste Schwelle | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Ab +0,6R, Stop auf −0,3R | Stop-Abstand | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Ab +0,6R, Stop auf −0,2R | Stop-Abstand | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Ab +0,6R, Stop auf −0,1R | Stop-Abstand | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Ab +0,6R, Stop auf +0,0R | Stop-Abstand | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Ab +0,6R, Stop auf +0,1R | Stop-Abstand | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Ab +0,6R, Stop auf +0,2R | Stop-Abstand | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Nach 2,0 ATR Bewegung | ATR | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Ab +0,6R Stop knapp hinter die Kante | Kante | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Trailing ab +0,6R, Abstand 0,75R | Trailing R | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Trailing ab +0,6R, Abstand 1,0R | Trailing R | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Trailing ab +1,0R, Abstand 0,5R | Trailing R | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Stufen 0,6→±0 / 1,0→+0,5 | Stufen | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Stufen 0,6→±0 / 0,9→+0,4 | Stufen | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Heute + Trailing 0,5R ab +1,0R | Kombi | +0,00 | +0,00 | 0 | 0 | +0,00 | – | +0,00 | +0,00 |
| Hälfte bei +0,8R, Rest auf Einstieg | Teilgewinn | −0,29 | −1,67 | 2 | 2 | +0,11 | VRTX −0,40 | −0,26 | −0,03 |
| Fest ab +0,4R, Stop auf Einstieg | Feste Schwelle | −0,48 | −3,58 | 1 | 3 | −1,51 | DHR +1,03 | +0,02 | −0,50 |
| Trailing ab +0,6R, Abstand 1,0 ATR | Trailing ATR | −0,26 | −8,63 | 2 | 3 | +0,11 | WMT −0,37 | −0,36 | +0,10 |
| Trailing ab +0,6R, Abstand 0,3R | Trailing R | −0,31 | −9,13 | 1 | 2 | +0,03 | WMT −0,34 | −0,31 | +0,00 |
| Hälfte bei +0,6R, Rest auf Einstieg | Teilgewinn | −0,54 | −9,40 | 3 | 6 | −0,04 | VRTX −0,50 | −0,51 | −0,03 |
| Hälfte bei +0,4R, Rest auf Einstieg | Teilgewinn | −0,87 | −16,13 | 4 | 10 | −2,09 | DHR +1,22 | −0,14 | −0,73 |
| Trailing ab +0,6R, Abstand 0,5R | Trailing R | −0,66 | −18,51 | 0 | 2 | −0,18 | WMT −0,48 | −0,66 | +0,00 |
| Bei 40 % des Zielwegs | Zielabstand | −0,80 | −18,88 | 1 | 4 | −1,83 | DHR +1,03 | −0,30 | −0,50 |
| Bei 30 % des Zielwegs | Zielabstand | −1,03 | −24,98 | 1 | 5 | −2,06 | DHR +1,03 | −0,53 | −0,50 |
| Fest ab +0,3R, Stop auf Einstieg | Feste Schwelle | −1,34 | −29,02 | 1 | 6 | −2,37 | DHR +1,03 | −0,84 | −0,50 |
| Nach 1,0 ATR Bewegung | ATR | −1,58 | −31,48 | 3 | 8 | −2,61 | DHR +1,03 | −1,08 | −0,50 |
| Nach 60 Min, wenn im Plus | Zeit | −1,58 | −32,74 | 2 | 7 | −1,08 | ZTS −0,50 | −1,12 | −0,46 |
| Nach 30 Min, wenn im Plus | Zeit | −2,30 | −49,88 | 3 | 9 | −1,75 | ZTS −0,54 | −1,32 | −0,97 |
| Fest ab +0,2R, Stop auf Einstieg | Feste Schwelle | −2,18 | −50,80 | 3 | 10 | −3,21 | DHR +1,03 | −1,24 | −0,94 |
| Nach 0,5 ATR Bewegung | ATR | −2,29 | −78,70 | 7 | 16 | −3,32 | DHR +1,03 | −1,35 | −0,94 |
| Nach erster Kerze im Plus | Kerze | −3,01 | −89,36 | 6 | 13 | −4,04 | DHR +1,03 | −2,11 | −0,90 |

„Alte Version“ sind die Trades bis 25.09., „neue Version“ die ab 28.09.
