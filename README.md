# PatternBot – Backtest-Ergebnisse

Dieser Branch enthält nur Ergebnisse des Backtests, keinen Code. Der Backtest ist ein Replay des unveränderten
Live-Codes auf historischen Daten. Der Branch ist vom Dashboard (`main`) getrennt.

- `protokoll.md`: Protokoll aller Kalibrierungen und Runden. Es wird nur ergänzt, nie geändert.
- `kalibrierung/`: Abgleich des Replays mit dem echten Paper-Konto (21.09.–02.10.2026).
  - `bericht.md`: Ergebnis, Tabelle pro Trade, Ursachen.
  - `trades.csv`: echt gegen Replay je Trade.
  - `entscheidungen.csv`: jedes Setup, Entscheidung live gegen Replay.
  - `details.json`
- `runde-N/`: Jahresrunden.
  - `zusammenfassung.md`: Kriterien für das ganze Jahr, das zählt, und für die Zeit vor den Live-Wochen;
    Aufschlüsselungen; Ziele nur „durchgehandelt“; Stops mit Kurslücke.
  - `trades.json`: je Trade Tag, Signalkerze (New York), Symbol, Muster, Richtung, SPY über/unter SMA50,
    R vor und nach Kosten, Ausstiegsgrund.
  - `verlauf.csv`: je Handelstag Trades, kumuliertes R nach Kosten, Drawdown und das Zufallsband p5/p50/p95.
  - `zufall.csv`: Endergebnis jedes der 100 Zufallsläufe.
  - `setups.csv.gz`: alle Setups mit Entscheidung.
  - `v1-aus/`: dieselben Dateien für den Vergleichslauf mit V1 aus. Dieser Lauf ist nur Information.
  - `hinweis.md`: Fehler oder Besonderheiten, die nach der Runde auffielen.

Erfolgskriterien je Runde (fest):
- mindestens 200 Trades
- Erwartungswert nach Kosten mindestens +0,10R
- Profitfaktor mindestens 1,3
- maximaler Drawdown höchstens 15R
- besser als mindestens 95 von 100 Zufallsläufen

Kosten: 0,03R je Long, 0,05R je Short.
