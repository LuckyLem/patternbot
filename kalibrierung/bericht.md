# Kalibrierung 2026-09-21 bis 2026-10-02

_Erstellt 03.10.2026 17:09 MESZ · Datenabrufe 98 · Simulator und Auswertung `bt/` sha256 `ea1111c0fedf` · Bot-Code `cbfe06cff`_

**Ergebnis: bestanden** (die verbleibenden Abweichungen der alten Version gelten nach Entscheidung des Nutzers vom 03.10. als erklärt)

| Kriterium | Ziel | Ergebnis | erfüllt |
|---|---|---|---|
| echte Orders auch im Replay | alle 11 | 11 | ja |
| zusätzliche Orders im Replay | 0 | 0 | ja |
| gleiche Entscheidungen | ≥ 95 %, Rest erklärt | 100.0 % (659/659) | ja |
| Ausstiege ≤ 0,1R, neue Version (eigene Einstiege) | alle 9 | 9 | ja |
| Ausstiege ≤ 0,1R, alte Version (Einstieg vorgegeben) | alle 46 | 42 + 4 vom Nutzer als erklärt angenommen | ja |
| abgefangene Fehler im Replay | 0 | 0 | ja |

Fill-Preis der eigenen Einstiege (Replay minus echt, + = Replay schlechter): +0.000R bis +0.001R, Mittel +0.0001R.

Ziel-Limits wie Paper (Geld- bzw. Briefkurs muss das Ziel erreichen): 1 Ziel(e) wären nur nach der Regel „durchgehandelt“ gefüllt worden, zusammen +0.42R; 0 später doch am Ziel.

## Entscheidungsabgleich

Grundlage: alle 659 Setups ab 28.09. 17:32 (eigene Entscheidungen des Replays), Schlüssel Symbol · Muster · Seite · Kerze. Jede Zeile einzeln: `entscheidungen.csv`.

| Entscheidung live | Setups | im Replay gleich |
|---|---|---|
| skip-vol | 583 | 583 |
| skip-chase | 34 | 34 |
| order | 11 | 11 |
| skip-stale | 9 | 9 |
| skip-rs | 7 | 7 |
| skip-dup | 5 | 5 |
| skip-rr | 4 | 4 |
| skip-spread | 4 | 4 |
| skip-market | 2 | 2 |

## Trades: echt gegen Replay

R bezogen auf den echten Einstieg und den ersten Stop; Einstieg vorgegeben = Trade der alten Version mit echtem Einstieg (nur der Ausstieg wird verglichen). Dieselbe Tabelle: `trades.csv`.

| Trade | Tag | Symbol | Seite | vorg. | Einstieg echt | Einstieg Replay | Ausstieg echt | Ausstieg Replay | R echt | R Replay | Abw. | Grund echt | Grund Replay |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| t5 | 2026-09-21 | HD | short | ja | 296.4100 | 296.4100 | 297.5500 | 297.5400 | -0.22 | -0.22 | +0.00 | time_stop | time_stop |
| t6 | 2026-09-21 | NVDA | long | ja | 225.3100 | 225.3100 | 226.7150 | 226.7100 | +0.36 | +0.35 | -0.00 | time_stop | time_stop |
| t7 | 2026-09-21 | AMZN | long | ja | 259.3271 | 259.3271 | 258.1257 | 258.3500 | -0.31 | -0.25 | +0.06 | eod | eod |
| t8 | 2026-09-21 | TMO | long | ja | 659.4400 | 659.4400 | 657.4100 | 657.2500 | -0.19 | -0.21 | -0.02 | eod | eod |
| t9 | 2026-09-21 | DHR | long | ja | 215.1200 | 215.1200 | 215.0900 | 215.0200 | -0.01 | -0.04 | -0.03 | eod | eod |
| t10 | 2026-09-22 | VRTX | long | ja | 514.8200 | 514.8200 | 522.8100 | 522.8250 | +1.18 | +1.19 | +0.00 | time_stop | time_stop |
| t11 | 2026-09-22 | MRK | long | ja | 150.7800 | 150.7800 | 152.8100 | 152.8100 | +0.72 | +0.72 | +0.00 | fill | tp |
| t12 | 2026-09-22 | BKNG | short | ja | 165.2209 | 165.2209 | 162.0536 | 161.8700 | +0.72 | +0.76 | +0.04 | time_stop | time_stop |
| t13 | 2026-09-22 | GS | short | ja | 938.7900 | 938.7900 | 950.1700 | 950.2600 | -0.77 | -0.77 | -0.01 | time_stop | time_stop |
| t14 | 2026-09-22 | REGN | long | ja | 811.1700 | 811.1700 | 808.8050 | 808.6400 | -0.14 | -0.16 | -0.01 | time_stop | time_stop |
| t15 | 2026-09-22 | DE | long | ja | 698.7900 | 698.7900 | 702.1500 | 701.5200 | +0.53 | +0.43 | -0.10 | eod | eod |
| t16 | 2026-09-22 | PH | long | ja | 964.2300 | 964.2300 | 965.2100 | 965.4000 | +0.09 | +0.11 | +0.02 | eod | eod |
| t17 | 2026-09-23 | PANW | long | ja | 377.8400 | 377.8400 | 385.4000 | 386.0000 | +0.62 | +0.67 | +0.05 | time_stop | time_stop |
| t18 | 2026-09-23 | COF | short | ja | 198.1200 | 198.1200 | 198.4420 | 198.5600 | -0.06 | -0.09 | -0.02 | time_stop | time_stop |
| t19 | 2026-09-23 | INTU | short | ja | 287.3667 | 287.3667 | 288.1100 | 288.0200 | -0.12 | -0.11 | +0.01 | time_stop | time_stop |
| t20 | 2026-09-23 | BKNG | short | ja | 157.2500 | 157.2500 | 156.6500 | 156.5500 | +0.06 | +0.07 | +0.01 | time_stop | time_stop |
| t21 | 2026-09-23 | AVGO | short | ja | 357.2200 | 357.2200 | 355.8060 | 355.8500 | +0.27 | +0.26 | -0.01 | time_stop | time_stop |
| t22 | 2026-09-23 | HD | short | ja | 298.6100 | 298.6100 | 297.5267 | 297.8600 | +0.14 | +0.10 | -0.04 | eod | eod |
| t23 | 2026-09-23 | ISRG | short | ja | 396.8800 | 396.8800 | 398.4700 | 398.8600 | -0.20 | -0.25 | -0.05 | eod | eod |
| t24 | 2026-09-23 | PLD | short | ja | 134.2800 | 134.2800 | 133.9800 | 134.2200 | +0.31 | +0.06 | -0.25 ✓ | eod | eod |
| t25 | 2026-09-23 | DAL | short | ja | 81.7400 | 81.7400 | 81.6504 | 81.7100 | +0.06 | +0.02 | -0.04 | eod | eod |
| t26 | 2026-09-24 | WMT | short | ja | 109.6700 | 109.6700 | 108.8400 | 108.9000 | +0.74 | +0.69 | -0.05 | time_stop | time_stop |
| t27 | 2026-09-24 | KO | long | ja | 89.2700 | 89.2700 | 88.4400 | 88.4100 | -0.86 | -0.89 | -0.03 | time_stop | time_stop |
| t28 | 2026-09-24 | DHR | long | ja | 224.9100 | 224.9100 | 221.5300 | 221.7100 | -1.06 | -1.00 | +0.06 | fill | sl |
| t29 | 2026-09-24 | IBM | short | ja | 227.0000 | 227.0000 | 227.0700 | 227.1500 | -0.01 | -0.02 | -0.01 | time_stop | time_stop |
| t30 | 2026-09-24 | VZ | long | ja | 47.3200 | 47.3200 | 47.3500 | 47.3900 | +0.05 | +0.12 | +0.07 | time_stop | time_stop |
| t31 | 2026-09-24 | AON | short | ja | 277.7400 | 277.7400 | 277.0500 | 276.7100 | +0.14 | +0.21 | +0.07 | time_stop | time_stop |
| t32 | 2026-09-24 | LUV | long | ja | 41.3600 | 41.3600 | 41.4900 | 41.5200 | +0.17 | +0.20 | +0.04 | time_stop | time_stop |
| t33 | 2026-09-24 | NSC | short | ja | 313.5800 | 313.5800 | 313.1717 | 313.6100 | +0.22 | -0.02 | -0.24 ✓ | orphan_cover | eod |
| t34 | 2026-09-24 | MDT | short | ja | 88.9400 | 88.9400 | 88.5400 | 88.5600 | +0.35 | +0.33 | -0.02 | eod | eod |
| t35 | 2026-09-24 | EMR | long | ja | 155.5800 | 155.5800 | 155.9500 | 155.7900 | +0.14 | +0.08 | -0.06 | eod | eod |
| t36 | 2026-09-24 | SYK | short | ja | 270.5700 | 270.5700 | 270.7400 | 270.8000 | -0.10 | -0.13 | -0.03 | eod | eod |
| t37 | 2026-09-24 | SHW | short | ja | 318.3960 | 318.3960 | 320.4000 | 320.1900 | -0.21 | -0.18 | +0.02 | eod | eod |
| t38 | 2026-09-25 | CRM | short | ja | 237.1600 | 237.1600 | 234.9038 | 234.9100 | +0.46 | +0.46 | -0.00 | fill | tp |
| t39 | 2026-09-25 | WM | short | ja | 206.1900 | 206.1900 | 207.5300 | 207.4800 | -0.62 | -0.60 | +0.02 | time_stop | time_stop |
| t40 | 2026-09-25 | ITW | long | ja | 273.9100 | 273.9100 | 274.9400 | 275.1100 | +0.31 | +0.36 | +0.05 | time_stop | time_stop |
| t41 | 2026-09-25 | NSC | short | ja | 312.7500 | 312.7500 | 313.2500 | 313.6900 | -0.30 | -0.56 | -0.26 ✓ | sl | time_stop |
| t42 | 2026-09-25 | GWW | short | ja | 1243.3300 | 1243.3300 | 1245.7400 | 1245.6700 | -0.25 | -0.24 | +0.01 | eod | eod |
| t43 | 2026-09-25 | PRU | long | ja | 119.4400 | 119.4400 | 119.5000 | 119.4200 | +0.03 | -0.01 | -0.04 | eod | eod |
| t44 | 2026-09-25 | ROP | short | ja | 358.5400 | 358.5400 | 358.8300 | 358.2600 | -0.05 | +0.05 | +0.10 ✓ | eod | eod |
| t45 | 2026-09-25 | EMR | short | ja | 158.3800 | 158.3800 | 158.6100 | 158.6300 | -0.15 | -0.16 | -0.01 | eod | eod |
| t46 | 2026-09-25 | HIG | short | ja | 124.4000 | 124.4000 | 124.5400 | 124.5300 | -0.24 | -0.22 | +0.02 | eod | eod |
| t47 | 2026-09-28 | UAL | short | ja | 109.8300 | 109.8300 | 110.0900 | 110.0900 | -0.05 | -0.05 | +0.00 | time_stop | time_stop |
| t48 | 2026-09-28 | PANW | long | ja | 382.5200 | 382.5200 | 387.7800 | 387.7700 | +0.75 | +0.75 | -0.00 | fill | tp |
| t49 | 2026-09-28 | AMZN | short | ja | 245.4263 | 245.4263 | 246.1350 | 246.1000 | -0.24 | -0.23 | +0.01 | time_stop | time_stop |
| t50 | 2026-09-28 | MS | short | ja | 193.2800 | 193.2800 | 193.9000 | 193.8600 | -0.26 | -0.24 | +0.02 | time_stop | time_stop |
| t51 | 2026-09-28 | C | short | nein | 132.3000 | 132.3000 | 131.4100 | 131.4200 | +1.07 | +1.06 | -0.01 | eod | eod |
| t52 | 2026-09-29 | SCHW | short | nein | 97.5000 | 97.5000 | 98.7500 | 98.7500 | -1.00 | -1.00 | +0.00 | sl | sl |
| t53 | 2026-09-29 | TJX | long | nein | 132.6100 | 132.6100 | 133.6300 | 133.6400 | +0.36 | +0.36 | +0.00 | time_stop | time_stop |
| t55 | 2026-09-30 | MS | short | nein | 190.5100 | 190.5100 | 189.3800 | 189.3200 | +0.50 | +0.52 | +0.03 | time_stop | time_stop |
| t56 | 2026-09-30 | ZTS | short | nein | 69.9400 | 69.9400 | 69.6293 | 69.5900 | +0.54 | +0.61 | +0.07 | eod | eod |
| t57 | 2026-09-30 | PH | short | nein | 961.3900 | 961.3900 | 960.6700 | 961.2500 | +0.08 | +0.02 | -0.06 | eod | eod |
| t58 | 2026-10-01 | ROP | long | nein | 362.7100 | 362.7100 | 362.8200 | 362.7300 | +0.01 | +0.00 | -0.01 | eod | eod |
| t59 | 2026-10-02 | BKNG | short | nein | 158.8825 | 158.8800 | 159.6750 | 159.8200 | -0.23 | -0.27 | -0.04 | time_stop | time_stop |
| t60 | 2026-10-02 | CMCSA | short | nein | 21.5200 | 21.5200 | 21.5600 | 21.5600 | -0.16 | -0.16 | +0.00 | time_stop | time_stop |

## Ausstiege mehr als 0,1R daneben: Ursache

⚠ = offen, ✓ = vom Nutzer am 03.10. als erklärt angenommen.

| Trade | Symbol | Abweichung | Ursache | |
|---|---|---|---|---|
| t24 | PLD | -0.25R | Zeitpunkt: echt 15:51:43, Replay 15:50:02 (alte Version: Verwaltung im ~4-Min-Takt); zum echten Zeitpunkt gibt der Simulator 133.98 = +0.31R, echt +0.31R | ✓ Glattstellung 15:50 statt 15:51 (alte Version) |
| t33 | NSC | -0.24R | bekannter Fehler der alten Version: NSC-Waise lief über Nacht und wurde am 25.09. gedeckt; die neue Version schließt verifiziert zum Tagesende | ✓ bekannter Fehler der alten Version (NSC-Waise) |
| t41 | NSC | -0.26R | bekannter Fehler der alten Version: Einstieg auf der NSC-Waise, Mischposition; der echte Ausstieg gehört zur gemeinsamen Glattstellung | ✓ bekannter Fehler der alten Version (NSC-Mischposition) |
| t44 | ROP | +0.10R | Zeitpunkt: echt 15:50:51, Replay 15:50:02 (alte Version: Verwaltung im ~4-Min-Takt); zum echten Zeitpunkt gibt der Simulator 358.8 = -0.05R, echt -0.05R | ✓ Glattstellung 15:50 statt 15:51 (alte Version) |

## Ziele, die nur nach „durchgehandelt“ gefüllt worden wären

| Replay-Trade | Tag | Symbol | durchgehandelt um (NY) | R dann | R im Replay | Unterschied | Ausstieg Replay |
|---|---|---|---|---|---|---|---|
| 6 | 2026-09-22 | VRTX | 11:16:00 | +1.61 | +1.19 | +0.42 | time_stop |

## Simulator-Korrekturen dieser Kalibrierung (nur Simulator, keine Regel)

1. Letzter Kurs wie Alpacas /trades/latest: ohne Odd Lots (Bedingung I). Vorher: 9 skip-stale-Abweichungen und CRM 30.09. Jetzt 62 von 62 Live-Kursabfragen exakt (Preis und Alter).
2. Moment der Kursabfrage: geloggter Prüfbeginn + 0,14 s, ältere Zeilen: Zeitstempel minus gemessene Verzögerung je Entscheidung. Vorher: Zeitstempel der Zeile (bei Orders 0,5 s zu spät).
3. Die simulierte Uhr läuft im Suchlauf mit. Vorher stand sie: Kursalter zu klein (PCAR 44 statt 64 s), Orders zu früh gesendet.
4. Einstieg wie Paper: Ankunft 0,26 s nach der Kursabfrage; sofort ausführbar -> Geld-/Briefkurs bei Ankunft, sonst nur wenn durchgehandelt. Vorher: erster Trade im Limit, im Mittel 0,01-0,05R zu günstig.
5. Glattstellung wie Paper: Geld-/Briefkurs bei Ankunft. Vorher: nächster Trade.
6. Ziel-Limit wie Paper (Vorgabe des Nutzers 03.10.): Verkauf erst, wenn das Bid das Ziel erreicht, Rückkauf erst, wenn das Ask es erreicht. Vorher: durchgehandelt (VRTX t10 +0,42R).
7. Testaufbau: jede Rechnung mit frischer Replay-DB; Uhr in ganzen Mikrosekunden (ein Nanosekunden-Rest ließ jeden Scan still scheitern); abgefangene Ausnahmen der Live-Schleife machen ein Replay ungültig.
8. Symbolschreibweise wie Alpaca (gefunden im ersten Versuch von Runde 1): BRK-B aus dem Universum heißt beim Broker BRK.B. Vorher fand der Live-Code die Position nicht, buchte den Trade als 'unresolved' (0 $) und schloss die Position als Waise (24.06.2026).
9. Testaufbau und Auswertung (03.10., ändert keine Rechnung): Abrufpause nur an NYSE-Handelstagen 15:30-22:00 (Vorgabe des Nutzers); Zufallsläufe je Trade, Tagesverlauf, Stops mit Kurslücke.

## Hinweise

- Moment der Kursabfrage: ab 30.09. 17:20 der geloggte Prüfbeginn + 0.14 s, davor der Zeitstempel der Setup-Zeile minus der gemessenen Verzögerung je Entscheidung (order 0.63 s, skip-chase 0.21 s, skip-dup 0.07 s, skip-market 0.08 s, skip-rr 0.34 s, skip-rs 0.07 s, skip-spread 0.40 s, skip-stale 0.20 s, skip-vol 0.07 s). Das IEX-Buch eine Laufzeit (0,14 s) später.
- Fills wie Paper: sofort ausführbar zum SIP-Geld-/Briefkurs bei Ankunft (0,26 s nach der Kursabfrage), sonst nur wenn durchgehandelt; Glattstellungen zum Geld-/Briefkurs; Ziel-Limit erst, wenn Bid (Verkauf) bzw. Ask (Rückkauf) es erreicht; Stop auf SIP-Ticks bzw. 1-Min-Kerzen, in derselben Minute zählt der Stop.
- Nicht nachstellbar: der Takt der Verwaltung (live alle 60 s ab Prozessstart, Replay ab :00 + 2 s), Teilausführungen, Warteschlange.
- Bot-Code: lokale Arbeitskopie inkl. Technik-Paket (live ab 04.10.); dessen Entscheidungslogik ist unverändert, die Regeln je Tag kommen aus dem Änderungsprotokoll.
