# ORB-Studie · Jahr 2025-10-01..2026-09-30

Regeln vorab festgelegt am 05.10.2026 (Commit `d48250c2` auf diesem Branch, `orb-studie/VORAB-REGELN.md`), vor jedem Test. Es zählt nur die Hauptvariante: 5-Minuten-Opening-Range, Stop 10 % ATR, Top 5 nach relativem Volumen.

## Ergebnis nach Kosten (Hauptvariante)

| Kriterium | Ziel | Ergebnis | erfüllt |
|---|---|---|---|
| Trades | ≥ 200 | 973 | ja |
| Erwartungswert | ≥ +0,10R | -0.465R | nein |
| Profitfaktor | ≥ 1,3 | 0.57 | nein |
| max. Drawdown | ≤ 15R | 469.65R | nein |
| Zufallsvergleich | ≥ 95 von 100 | 0 von 100 | nein |

**Ziel nicht erreicht.** Summe -452.68R nach Kosten (-288.20R vor Kosten), Trefferquote 7 %, Kosten im Mittel 0.169R je Trade, -4403.84 $ nach Kosten bei 0,5 % Risiko und höchstens 20 % Positionswert (10.000 $ Kapital).

## Nachbarwerte (nur Information: ein Wert ist nur gut, wenn die Nachbarn auch gut sind)

| Variante | Trades | Erwartungswert n.K. | PF | max. DD | Summe R n.K. | Trefferquote |
|---|---|---|---|---|---|---|
| Hauptvariante: 5 Min · 10 % ATR · Top 5 (zählt) | 973 | -0.465R | 0.57 | 469.65R | -452.68R | 7 % |
| Opening Range 15 Min | 891 | -0.386R | 0.64 | 363.09R | -344.25R | 9 % |
| Opening Range 30 Min | 815 | -0.448R | 0.57 | 388.73R | -365.05R | 10 % |
| Stop 5 % ATR | 973 | -1.072R | 0.18 | 1043.12R | -1043.12R | 2 % |
| Stop 20 % ATR | 973 | -0.196R | 0.78 | 218.05R | -190.82R | 18 % |
| Top 10 | 1956 | -0.349R | 0.67 | 705.15R | -681.95R | 10 % |
| Top 20 (wie die Studie) | 3952 | -0.433R | 0.59 | 1776.34R | -1713.06R | 9 % |

### Long / Short

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| long | 491 | -0.589 | -289.02 | -2488.23 | 0.46 |
| short | 482 | -0.340 | -163.66 | -1915.62 | 0.68 |

### Rang nach relativem Volumen

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| Rang 01 | 198 | +0.218 | +43.14 | -4.65 | 1.21 |
| Rang 02 | 182 | -0.721 | -131.27 | -1041.06 | 0.34 |
| Rang 03 | 193 | -0.844 | -162.96 | -1384.50 | 0.25 |
| Rang 04 | 208 | -0.538 | -111.97 | -1079.33 | 0.50 |
| Rang 05 | 192 | -0.467 | -89.62 | -894.31 | 0.56 |

### Uhrzeit des Einstiegs (New York)

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| 09:00 | 819 | -0.467 | -382.25 | -3901.42 | 0.57 |
| 10:00 | 81 | -0.469 | -37.98 | -288.75 | 0.57 |
| 11:00 | 31 | -0.467 | -14.46 | -91.38 | 0.55 |
| 12:00 | 20 | -0.516 | -10.32 | -52.04 | 0.51 |
| 13:00 | 12 | -0.066 | -0.79 | -14.66 | 0.92 |
| 14:00 | 6 | -1.236 | -7.42 | -56.55 | 0.00 |
| 15:00 | 4 | +0.136 | +0.54 | +0.96 | 1.42 |

### Ausstieg

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| eod | 78 | +7.659 | +597.36 | +4448.42 | 485.69 |
| sl | 895 | -1.173 | -1050.04 | -8852.26 | 0.00 |

### Marktphase (SPY gegen 50-Tage-Schnitt, Vortag)

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| SPY unter SMA50 | 213 | -0.565 | -120.28 | -1034.10 | 0.48 |
| SPY über SMA50 | 725 | -0.439 | -318.41 | -3212.52 | 0.59 |
| unbekannt | 35 | -0.400 | -13.99 | -157.22 | 0.64 |

### Nach Quartal

| Gruppe | Trades | Ø R n.K. | Summe R n.K. | $ n.K. | PF |
|---|---|---|---|---|---|
| 2025-Q4 | 250 | -0.529 | -132.37 | -1402.38 | 0.52 |
| 2026-Q1 | 239 | -0.642 | -153.53 | -1283.82 | 0.41 |
| 2026-Q2 | 245 | -0.379 | -92.85 | -915.44 | 0.64 |
| 2026-Q3 | 239 | -0.309 | -73.93 | -802.20 | 0.71 |

### Zufallsvergleich

Hauptvariante -0.465R je Trade; Zufall (gleiche Aktie und Stunde, Richtung gelost, gleicher Stop in %, gleiche Ausstiege und Kosten) Median +0.126R, bester Lauf +0.374R. Die Strategie schlägt 0 von 100 Zufallsläufen.

### Daten

- 251 Handelstage; Aktien im Spiel (RV ≥ 1 und Filter) im Mittel 20.0 je Tag in den Top 20 erfasst; Datenabrufe 228.
- `trades.json`: je Trade Tag, Signalkerze (Opening Range ab 09:30), Einstiegszeit, Symbol, Muster, Richtung, SPY über/unter SMA50, R vor und nach Kosten, Ausstieg, relatives Volumen und Rang.
- `verlauf.csv`: je Handelstag Trades, kumuliertes R nach Kosten, Drawdown, Zufallsband p5/p50/p95.
- `zufall.csv`: Endergebnis der 100 Zufallsläufe. `auswahl.csv.gz`: die Aktien im Spiel jedes Tages (Top 20).

### Nicht nachstellbar (siehe Vorab-Regeln)

- Universum = heutige Liste mit 1.500 Werten (Überlebensverzerrung); keine Nachrichtendaten (RV als Ersatz); Leihbarkeit für Shorts nicht modelliert; Fills auf Minutenkerzen.
- Code: ORB `orb/` sha256 `59213253980c`, Daten und Auswertung `bt/` sha256 `61750fbbc22e`.

## Zusätzlich verlangt (Auftrag vom 07.10.)

| Kennzahl | Hauptvariante (zählt) |
|---|---|
| Trefferquote | 7,3 % (71 von 973 Trades nach Kosten im Plus) |
| Längste Verlustserie | 46 Trades in Folge, zusammen −54,1R (endete am 15.12.2025) |
| Ergebnis geteilt durch max. Drawdown | −452,68R / 469,65R = −0,96 |

## Diagnose: Wie stark entscheidet die Einstiegsminute?

Nur zur Information; gezählt wird das Ergebnis oben.

Vorab-Regel 7 lautet: „Erreicht die Einstiegsminute auch den Stop, zählt der Stop (vorsichtig gerechnet).“

**Warum das hier so stark wirkt:**
- Ein Ausbruch füllt auf dem Weg durch die Kante.
- Das Tief (long) bzw. das Hoch (short) der Einstiegsminute liegt deshalb meist vor dem Fill.
- Der Stop liegt nur 10 % ATR entfernt, bei diesen Aktien etwa 0,2–0,4 % vom Kurs.
- Damit liegt das Tief oft schon jenseits des Stops, und der Trade gilt in der Minute seines Fills als ausgestoppt.

Unten stehen dieselben Trades mit derselben Auswahl, nur die Einstiegsminute ist anders behandelt
(`diagnose_einstiegsminute.json`):

| Annahme für die Einstiegsminute | gestoppt in der Einstiegsminute | Erwartungswert n.K. | PF | max. DD | Trefferquote | längste Verlustserie |
|---|---|---|---|---|---|---|
| V: vorab festgelegt (zählt) | 594 von 973 | −0,465R | 0,57 | 472R* | 7,3 % | 46 |
| A: Kerzenpfad (steigende Minute: Eröffnung, Tief, Hoch, Schluss; fallende umgekehrt) | 176 von 973 | +0,329R | 1,32 | 119R | 12,7 % | 34 |
| B: günstigste Grenze (gestoppt nur, wenn die Minute hinter dem Stop schließt) | 142 von 973 | +0,400R | 1,39 | 119R | 13,1 % | 34 |

\* Trade für Trade in Einstiegsreihenfolge gerechnet; die offizielle Zahl oben ist 469,65R.

**Einordnung:**
- Das Vorzeichen des Ergebnisses hängt daran, was innerhalb einer Minute zuerst kam. Minutenkerzen können das nicht
  entscheiden, nur Ticks.
- Auch im günstigsten Fall liegt der Drawdown bei etwa 119R, weit über 15R.
  - Mit einem Stop von 10 % ATR schwankt das Ergebnis in R stark: Gewinner bringen im Mittel mehrere R, Verlustserien
    gehen bis 34 Trades.
  - Das Kriterium K4 würde deshalb auch dann klar verfehlt.
- Der Zufallsvergleich ist davon nicht betroffen. Zufallstrades steigen zur Eröffnung einer Minute ein, die ganze
  Minute liegt also nach dem Fill.
- **Vorschlag (braucht ein OK):** Jahr 1 mit Ticks für die Einstiegsminute neu rechnen.
  - Die Handelsregeln bleiben dabei unverändert.
  - Beide Ergebnisse kommen ins Protokoll.
  - Weil Regel 7 vorab festgelegt war, entscheidet der Inhaber, ob das als Simulatorfehler gilt.
