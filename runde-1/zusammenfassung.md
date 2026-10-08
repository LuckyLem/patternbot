# Runde 1 · 2025-10-01..2026-09-30

Regel-Version: chase_anchor=close, universe_exclude=BK,MMC,FI (alle übrigen Einstellungen wie live) · Neuberechnung nach Simulatorfehler, Regeln unverändert.

_Kopfzeile korrigiert am 08.10.2026: Hier stand irrtümlich „erstes Rechnen, unverändert“. Alle Zahlen sind unverändert, siehe `protokoll.md`._

**Es zählt der Hauptlauf mit V1 an (Regeln wie live). Der Vergleichslauf mit V1 aus ist Information, keine Prüfung.**

## Ergebnis nach Kosten (0,03R Long / 0,05R Short)

| Kriterium | Ziel | ganzes Jahr (zählt) | erfüllt | 01.10.2025 bis 23.08.2026 (ohne die Wochen, in denen die Regeln entstanden) | erfüllt |
|---|---|---|---|---|---|
| Trades | ≥ 200 | 1009 | ja | 910 | ja |
| Erwartungswert | ≥ +0,10R | -0.056R | nein | -0.065R | nein |
| Profitfaktor | ≥ 1,3 | 0.76 | nein | 0.73 | nein |
| max. Drawdown | ≤ 15R | 65.23R | nein | 65.23R | nein |
| Zufallsvergleich | ≥ 95 von 100 | 25 von 100 | nein | 12 von 100 | nein |

**Ziel nicht erreicht** (ganzes Jahr). Summe -56.00R, -1591.32 $ nach Kosten (-456.78 $ vor Kosten), Trefferquote 42 %. 01.10.2025 bis 23.08.2026: Summe -59.17R, Ziel nicht erreicht.

### Nach Muster

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| AscendingTriangle | 106 | -0.113 | -11.97 | -162.70 | 0.63 |
| DescendingTriangle | 61 | -0.126 | -7.68 | -110.60 | 0.58 |
| DoubleBottom | 13 | -0.049 | -0.64 | -26.68 | 0.48 |
| DoubleTop | 13 | -0.155 | -2.01 | -85.53 | 0.10 |
| HeadShouldersTop | 120 | +0.062 | +7.46 | +156.83 | 1.35 |
| InverseHeadShoulders | 129 | +0.061 | +7.89 | +226.74 | 1.42 |
| Rectangle | 567 | -0.087 | -49.05 | -1589.39 | 0.65 |

### Nach Uhrzeit (Einstieg, New York)

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| 09:00 | 229 | -0.015 | -3.52 | -77.62 | 0.94 |
| 10:00 | 320 | -0.120 | -38.39 | -1146.30 | 0.59 |
| 11:00 | 106 | -0.030 | -3.16 | -180.88 | 0.84 |
| 12:00 | 50 | -0.064 | -3.20 | -33.04 | 0.71 |
| 13:00 | 50 | +0.030 | +1.49 | +39.09 | 1.18 |
| 14:00 | 119 | -0.072 | -8.62 | -180.20 | 0.67 |
| 15:00 | 135 | -0.004 | -0.60 | -12.37 | 0.97 |

### Long / Short

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| long | 560 | -0.054 | -30.15 | -715.57 | 0.76 |
| short | 449 | -0.058 | -25.85 | -875.76 | 0.76 |

### Marktphase (SPY gegen 50-Tage-Schnitt, Vortag)

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| SPY unter SMA50 | 215 | -0.122 | -26.17 | -857.31 | 0.50 |
| SPY über SMA50 | 794 | -0.038 | -29.83 | -734.01 | 0.84 |

### Nach Quartal

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| 2025-Q4 | 279 | -0.048 | -13.48 | -310.52 | 0.79 |
| 2026-Q1 | 252 | -0.068 | -17.18 | -652.89 | 0.71 |
| 2026-Q2 | 240 | -0.082 | -19.71 | -471.99 | 0.69 |
| 2026-Q3 | 238 | -0.024 | -5.63 | -155.92 | 0.89 |

### Getrennt: ab 2026-08-24

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| ab 2026-08-24 | 99 | +0.032 | +3.17 | -1.01 | 1.17 |
| davor | 910 | -0.065 | -59.17 | -1590.31 | 0.73 |

### Filter (Setups und Entscheidungen)

| Entscheidung | Setups |
|---|---|
| skip-vol | 26714 |
| skip-spread | 1214 |
| skip-chase | 1092 |
| order | 1010 |
| skip-maxopen | 716 |
| skip-stale | 637 |
| skip-rs | 606 |
| skip-dup | 428 |
| skip-rr | 425 |
| skip-market | 348 |

### Vergleichslauf V1 aus (Zone an der Kante) – nur Information

| Lauf | Trades | Erwartungswert | PF | max. DD | Summe R | $ n.K. | Zufall |
|---|---|---|---|---|---|---|---|
| V1 an (zählt) | 1009 | -0.056 | 0.76 | 65.23 | -56.00 | -1591.32 | 25 von 100 |
| V1 aus | 543 | -0.082 | 0.66 | 50.70 | -44.62 | -1448.59 | 8 von 100 |

### Ziel-Limits wie Paper

Ein Ziel füllt erst, wenn der Geldkurs (Verkauf) bzw. der Briefkurs (Rückkauf) es erreicht. Ausgewiesen: Ziele, die nur nach der alten Regel „durchgehandelt“ gefüllt worden wären, und was das je Trade in R ausgemacht hätte (ohne Folgeeffekte wie früher frei werdende Plätze). Grundlage für eine spätere Ziel-Order einen Cent vor dem Ziel.

| Lauf | Trades | Ziele am Bid/Ask gefüllt | nur nach „durchgehandelt“ | Unterschied gesamt | je betroffenem Trade | später doch am Ziel |
|---|---|---|---|---|---|---|
| regeln | 1009 | 38 | 0 | +0.00R | – | 7 |
| v1-aus | 543 | 16 | 0 | +0.00R | – | 2 |

### Stops mit Kurslücke

Stop-Ausstiege, die schlechter als zum Stop gefüllt wurden (die Minute öffnete jenseits des Stops oder der Kurs sprang darüber), und was die Lücke über den Stop hinaus gekostet hat.

| Lauf | Stop-Ausstiege | davon mit Lücke | Kosten der Lücken | schlimmster Fall |
|---|---|---|---|---|
| regeln | 105 | 2 | -0.06R | CDNS 2026-06-17 -0.05R |
| v1-aus | 53 | 1 | -0.05R | CDNS 2026-06-17 -0.05R |

### Zufallsvergleich

Strategie mit dem schnellen Simulator: -0.046R je Trade (volles Replay: -0.056R). Zufall: Median -0.033R, bester Lauf +0.023R. Die Strategie schlägt 25 von 100 Zufallsläufen. 01.10.2025 bis 23.08.2026: 12 von 100.

### Dateien

- `trades.json`: je Trade Tag, Uhrzeit der Signalkerze (Beginn der 15-Min-Kerze, New York), Symbol, Muster, Richtung, SPY über/unter SMA50 (Vortag), R vor und nach Kosten, Ausstiegsgrund.
- `verlauf.csv`: je Handelstag Trades bis hier, kumuliertes R nach Kosten (volles Replay), Drawdown zum Tagesende, dieselbe Strategie im schnellen Simulator (`r_kum_schnell`) und das 5/50/95-%-Band der Zufallsläufe (schneller Simulator, dieselben Ziehungen wie der Zufallsvergleich – direkt vergleichbar mit `r_kum_schnell`).
- `zufall.csv`: Endergebnis jedes der 100 Zufallsläufe (Summe und Erwartungswert in R nach Kosten).
- `v1-aus/`: dieselben drei Dateien für den Vergleichslauf V1 aus.

### Nicht nachstellbar (dokumentiert statt geraten)

- Teilausführungen, Warteschlange im Orderbuch.
- Universum = heutige Liste der 150 Werte (Überlebensverzerrung: früher gelistete, heute fehlende Werte fehlen).
- Kursalter und IEX-Buch aus historischen Ticks (letzter Kurs ohne Odd Lots, wie live); Kursabfrage 33 s nach Kerzenschluss (live Median), die simulierte Uhr läuft mit.
- Fills wie Paper (Kalibrierung 03.10.): sofort ausführbar zum SIP-Geld-/Briefkurs bei Ankunft, sonst nur wenn durchgehandelt; Glattstellungen zum Geld-/Briefkurs; Ziel erst, wenn Bid/Ask es erreicht. Takt der Verwaltung bis 60 s versetzt.
- Zufallsvergleich: Zufallseinstiege zum Minuten-Open ohne Spread – leicht zugunsten des Zufalls (streng).
- Alarme im Replay: 0.
- Code: Simulator und Auswertung `bt/` sha256 `61750fbbc22e` (kalibriert), Bot-Code `cbfe06cff`.

