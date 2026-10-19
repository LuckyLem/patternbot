# ORB-Studie · Jahr 2025-10-01..2026-09-30 · mit Ticks

Regeln vorab festgelegt am 05.10.2026 (Commit `d48250c2` auf diesem Branch, `orb-studie/VORAB-REGELN.md`), vor jedem Test. Es zählt nur die Hauptvariante: 5-Minuten-Opening-Range, Stop 10 % ATR, Top 5 nach relativem Volumen.

## Ergebnis nach Kosten (Hauptvariante)

| Kriterium | Ziel | Ergebnis | erfüllt |
|---|---|---|---|
| Trades | ≥ 200 | 973 | ja |
| Erwartungswert | ≥ +0,10R | -0.404R | nein |
| Profitfaktor | ≥ 1,3 | 0.69 | nein |
| max. Drawdown | ≤ 15R | 434.35R | nein |
| Zufallsvergleich | ≥ 95 von 100 | 0 von 100 | nein |

**Ziel nicht erreicht.** Summe -392.98R nach Kosten (-228.50R vor Kosten), Trefferquote 10 %, Kosten im Mittel 0.169R je Trade, -3640.36 $ nach Kosten bei 0,5 % Risiko und höchstens 20 % Positionswert (10.000 $ Kapital).

## Neuberechnung mit Ticks (TICK-METHODE.md, Commit `21f93abe`)

- Füllkurs und Stop aus den SIP-Abschlüssen, Handelsregeln unverändert. Die erste Rechnung auf Minutenkerzen steht im Protokoll (−0,465R, 594 von 973 Trades in der Einstiegsminute gestoppt).
- Trefferquote 10.1 %, längste Verlustserie 46 Trades (-79.9R), Ergebnis durch Drawdown -0.90.
- Stopps in der Einstiegsminute: 425 von 973.
- Ersatz durch Minutenkerzen: 0 Trades ohne Ticks für den Einstieg; 39 Trades nach dem Ende der Ticks auf Minutenkerzen gestoppt; Zufallstrades ohne Ticks 24651 von 97300.
- Daten: 4193 Tick-Fenster für 4108 Werte-Tage, 226.515.100 gefilterte Abschlüsse; 6.568.263 Abschlüsse außerhalb ihrer offiziellen Minutenkerze verworfen; 29 Werte-Tage mit Split-Faktor.

## Nachbarwerte (nur Information: ein Wert ist nur gut, wenn die Nachbarn auch gut sind)

| Variante | Trades | Erwartungswert n.K. | PF | max. DD | Summe R n.K. | Trefferquote |
|---|---|---|---|---|---|---|
| Hauptvariante: 5 Min · 10 % ATR · Top 5 (zählt) | 973 | -0.404R | 0.69 | 434.35R | -392.98R | 10 % |
| Opening Range 15 Min | 891 | -0.333R | 0.72 | 347.11R | -296.29R | 11 % |
| Opening Range 30 Min | 815 | -0.435R | 0.63 | 382.59R | -354.44R | 11 % |
| Stop 5 % ATR | 973 | -1.407R | 0.26 | 1404.88R | -1368.58R | 3 % |
| Stop 20 % ATR | 973 | -0.147R | 0.84 | 208.94R | -142.71R | 19 % |
| Top 10 | 1956 | -0.283R | 0.77 | 576.64R | -554.49R | 12 % |
| Top 20 (wie die Studie) | 3952 | -0.341R | 0.72 | 1405.27R | -1347.54R | 12 % |

### Long / Short

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| long | 491 | -0.601 | -295.13 | -2238.24 | 0.55 |
| short | 482 | -0.203 | -97.85 | -1402.11 | 0.84 |

### Rang nach relativem Volumen

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| Rang 01 | 198 | +0.385 | +76.19 | +299.31 | 1.32 |
| Rang 02 | 182 | -0.711 | -129.36 | -913.23 | 0.46 |
| Rang 03 | 193 | -0.816 | -157.39 | -1171.49 | 0.39 |
| Rang 04 | 208 | -0.420 | -87.34 | -887.16 | 0.68 |
| Rang 05 | 192 | -0.495 | -95.08 | -967.79 | 0.62 |

### Uhrzeit des Einstiegs (New York)

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| 09:00 | 819 | -0.422 | -345.37 | -3257.70 | 0.68 |
| 10:00 | 81 | -0.117 | -9.50 | -116.81 | 0.90 |
| 11:00 | 31 | -0.540 | -16.74 | -111.61 | 0.51 |
| 12:00 | 20 | -0.613 | -12.25 | -67.08 | 0.47 |
| 13:00 | 12 | -0.103 | -1.24 | -18.94 | 0.88 |
| 14:00 | 6 | -1.818 | -10.91 | -84.43 | 0.00 |
| 15:00 | 4 | +0.756 | +3.02 | +16.21 | 18.79 |

### Ausstieg

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| eod | 106 | +8.117 | +860.38 | +6708.21 | 657.15 |
| sl | 867 | -1.446 | -1253.36 | -10348.56 | 0.00 |

### Marktphase (SPY gegen 50-Tage-Schnitt, Vortag)

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| SPY unter SMA50 | 213 | -0.641 | -136.55 | -1199.24 | 0.51 |
| SPY über SMA50 | 725 | -0.328 | -237.46 | -2253.97 | 0.75 |
| unbekannt | 35 | -0.542 | -18.97 | -187.14 | 0.57 |

### Nach Quartal

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| 2025-Q4 | 250 | -0.722 | -180.48 | -1583.85 | 0.47 |
| 2026-Q1 | 239 | -0.617 | -147.53 | -1259.63 | 0.52 |
| 2026-Q2 | 245 | -0.063 | -15.52 | -260.61 | 0.95 |
| 2026-Q3 | 239 | -0.207 | -49.45 | -536.27 | 0.83 |

### Zufallsvergleich

Hauptvariante -0.404R je Trade; Zufall (gleiche Aktie und Stunde, Richtung gelost, gleicher Stop in %, gleiche Ausstiege und Kosten) Median +0.056R, bester Lauf +0.291R. Die Strategie schlägt 0 von 100 Zufallsläufen.

### Daten

- 251 Handelstage; Aktien im Spiel (RV ≥ 1 und Filter) im Mittel 20.0 je Tag in den Top 20 erfasst; Datenabrufe 8115.
- `trades.json`: je Trade Tag, Signalkerze (Opening Range ab 09:30), Einstiegszeit, Symbol, Muster, Richtung, SPY über/unter SMA50, R vor und nach Kosten, Ausstieg, relatives Volumen und Rang.
- `verlauf.csv`: je Handelstag Trades, kumuliertes R nach Kosten, Drawdown, Zufallsband p5/p50/p95.
- `zufall.csv`: Endergebnis der 100 Zufallsläufe. `auswahl.csv.gz`: die Aktien im Spiel jedes Tages (Top 20).

### Nicht nachstellbar (siehe Vorab-Regeln)

- Universum = heutige Liste mit 1.500 Werten (Überlebensverzerrung); keine Nachrichtendaten (RV als Ersatz); Leihbarkeit für Shorts nicht modelliert; Fills und Stopps aus SIP-Abschlüssen in den Tick-Fenstern, danach Minutenkerzen.
- Code: ORB `orb/` sha256 `54e2b77872ef`, Daten und Auswertung `bt/` sha256 `61750fbbc22e`.

