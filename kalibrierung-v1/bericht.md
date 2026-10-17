# Kalibrierung 2026-10-05 bis 2026-10-09

_Erstellt 17.10.2026 17:43 MESZ · Datenabrufe 559 · Simulator und Auswertung `bt/` sha256 `61750fbbc22e` · Bot-Code `cbfe06cff`_

**Ergebnis: NICHT bestanden**

| Kriterium | Ziel | Ergebnis | erfüllt |
|---|---|---|---|
| echte Orders auch im Replay | alle 19 | 19 | ja |
| zusätzliche Orders im Replay | 0 | 0 | ja |
| gleiche Entscheidungen | ≥ 95 %, Rest erklärt | 99.9 % (722/723) | NEIN |
| Ausstiege ≤ 0,1R, neue Version (eigene Einstiege) | alle 19 | 18 | NEIN |
| Ausstiege ≤ 0,1R, alte Version (Einstieg vorgegeben) | alle 0 | 0 | ja |
| abgefangene Fehler im Replay | 0 | 0 | ja |

Fill-Preis der eigenen Einstiege (Replay minus echt, + = Replay schlechter): -0.036R bis +0.035R, Mittel -0.0035R.

Ziel-Limits wie Paper (Geld- bzw. Briefkurs muss das Ziel erreichen): 0 Ziel(e) wären nur nach der Regel „durchgehandelt“ gefüllt worden, zusammen +0.00R; 0 später doch am Ziel.

## Entscheidungsabgleich

Grundlage: alle 723 Setups ab 28.09. 17:32 (eigene Entscheidungen des Replays), Schlüssel Symbol · Muster · Seite · Kerze. Jede Zeile einzeln: `entscheidungen.csv`.

| Entscheidung live | Setups | im Replay gleich |
|---|---|---|
| skip-vol | 575 | 575 |
| skip-spread | 39 | 38 |
| skip-chase | 26 | 26 |
| skip-stale | 22 | 22 |
| order | 19 | 19 |
| skip-rs | 12 | 12 |
| skip-maxopen | 11 | 11 |
| skip-rr | 10 | 10 |
| skip-dup | 6 | 6 |
| skip-market | 3 | 3 |

**Abweichende Entscheidungen (zu erklären):**

| Kerze (NY) | Symbol | Muster | live | Replay | live Detail | Replay Detail |
|---|---|---|---|---|---|---|
| 2026-10-06 10:30 | KLAC | Rectangle | skip-spread | – | 4.37 | – |

## Trades: echt gegen Replay

R bezogen auf den echten Einstieg und den ersten Stop; Einstieg vorgegeben = Trade der alten Version mit echtem Einstieg (nur der Ausstieg wird verglichen). Dieselbe Tabelle: `trades.csv`.

| Trade | Tag | Symbol | Seite | vorg. | Einstieg echt | Einstieg Replay | Ausstieg echt | Ausstieg Replay | R echt | R Replay | Abw. | Grund echt | Grund Replay |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| t62 | 2026-10-05 | PEP | short | nein | 124.6425 | 124.7000 | 124.7800 | 124.7500 | -0.09 | -0.03 | +0.05 | time_stop | time_stop |
| t63 | 2026-10-05 | TSLA | long | nein | 376.0300 | 376.0400 | 376.9500 | 377.0900 | +0.08 | +0.09 | +0.01 | time_stop | time_stop |
| t64 | 2026-10-05 | MPC | long | nein | 429.8275 | 430.1400 | 431.7100 | 431.7100 | +0.21 | +0.17 | -0.04 | time_stop | time_stop |
| t65 | 2026-10-05 | META | long | nein | 744.6550 | 744.6400 | 744.3100 | 744.3500 | -0.03 | -0.03 | +0.00 | time_stop | time_stop |
| t66 | 2026-10-05 | FIS | long | nein | 32.9700 | 32.9600 | 33.0800 | 33.0900 | +0.17 | +0.20 | +0.03 | time_stop | time_stop |
| t67 | 2026-10-05 | WMT | long | nein | 104.9600 | 104.9600 | 104.8200 | 104.7900 | -0.25 | -0.30 | -0.05 | eod | eod |
| t68 | 2026-10-05 | TT | long | nein | 471.6900 | 471.6900 | 471.4200 | 471.0000 | -0.10 | -0.25 | -0.15 ⚠ | eod | eod |
| t69 | 2026-10-05 | PFE | long | nein | 27.4900 | 27.4900 | 27.4300 | 27.4300 | -0.36 | -0.36 | +0.00 | eod | eod |
| t70 | 2026-10-06 | AMD | long | nein | 637.4000 | 637.4000 | 651.6800 | 651.6700 | +1.51 | +1.51 | -0.00 | tp | tp |
| t71 | 2026-10-06 | MSFT | long | nein | 533.7200 | 533.6300 | 532.0733 | 532.0200 | -0.15 | -0.15 | +0.00 | time_stop | time_stop |
| t72 | 2026-10-06 | AMZN | long | nein | 256.3686 | 256.3100 | 256.3300 | 256.3100 | -0.02 | +0.00 | +0.02 | eod | eod |
| t73 | 2026-10-07 | AAL | short | nein | 12.7000 | 12.7000 | 12.7600 | 12.7600 | -0.17 | -0.17 | +0.00 | time_stop | time_stop |
| t74 | 2026-10-07 | BSX | short | nein | 41.8200 | 41.8200 | 42.3500 | 42.3200 | -0.76 | -0.71 | +0.04 | time_stop | time_stop |
| t75 | 2026-10-07 | QCOM | short | nein | 176.2000 | 176.2000 | 177.5800 | 177.5900 | -0.36 | -0.37 | -0.00 | time_stop | time_stop |
| t76 | 2026-10-08 | CVX | long | nein | 210.9700 | 210.9800 | 211.5100 | 211.4000 | +0.15 | +0.12 | -0.03 | time_stop | time_stop |
| t77 | 2026-10-08 | IBM | short | nein | 218.9200 | 218.9200 | 220.3300 | 220.2500 | -0.63 | -0.60 | +0.04 | time_stop | time_stop |
| t78 | 2026-10-08 | COF | long | nein | 196.9000 | 196.9000 | 199.1500 | 199.2200 | +0.96 | +0.99 | +0.03 | eod | eod |
| t79 | 2026-10-09 | PFE | long | nein | 28.1061 | 28.1000 | 28.0300 | 28.0400 | -0.12 | -0.09 | +0.02 | time_stop | time_stop |
| t80 | 2026-10-09 | FISV | short | nein | 45.3402 | 45.3400 | 45.4000 | 45.4000 | -0.20 | -0.20 | -0.00 | eod | eod |

## Ausstiege mehr als 0,1R daneben: Ursache

⚠ = offen, ✓ = vom Nutzer am 03.10. als erklärt angenommen.

| Trade | Symbol | Abweichung | Ursache | |
|---|---|---|---|---|
| t68 | TT | -0.15R | UNERKLÄRT (Simulator zum echten Zeitpunkt: 471.15 -> -0.19R) | ⚠ |

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
10. Fehlkurse im Tick-Pfad (gefunden nach Runde 1, 03.10.): In den ersten 3 Minuten nach dem Fill zählten auch Abschlüsse, die den Kurs nicht setzen - z. B. 1 Aktie außerbörslich zu 310,00 bei ELV (Markt 352). Jetzt zählen nur Abschlüsse innerhalb der offiziellen SIP-Minutenkerze. Vorher: 8 Trades in Runde 1 fälschlich ausgestoppt.

## Hinweise

- Moment der Kursabfrage: ab 30.09. 17:20 der geloggte Prüfbeginn + 0.14 s, davor der Zeitstempel der Setup-Zeile minus der gemessenen Verzögerung je Entscheidung (order 0.64 s, skip-chase 0.21 s, skip-dup 0.07 s, skip-market 0.09 s, skip-maxopen 0.10 s, skip-rr 0.34 s, skip-rs 0.06 s, skip-spread 0.34 s, skip-stale 0.20 s, skip-vol 0.07 s). Das IEX-Buch eine Laufzeit (0,14 s) später.
- Fills wie Paper: sofort ausführbar zum SIP-Geld-/Briefkurs bei Ankunft (0,26 s nach der Kursabfrage), sonst nur wenn durchgehandelt; Glattstellungen zum Geld-/Briefkurs; Ziel-Limit erst, wenn Bid (Verkauf) bzw. Ask (Rückkauf) es erreicht; Stop auf SIP-Ticks bzw. 1-Min-Kerzen, in derselben Minute zählt der Stop.
- Nicht nachstellbar: der Takt der Verwaltung (live alle 60 s ab Prozessstart, Replay ab :00 + 2 s), Teilausführungen, Warteschlange.
- Bot-Code: lokale Arbeitskopie inkl. Technik-Paket (live ab 04.10.); dessen Entscheidungslogik ist unverändert, die Regeln je Tag kommen aus dem Änderungsprotokoll.
