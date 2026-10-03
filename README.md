# PatternBot – Backtest-Ergebnisse

Dieser Branch enthält nur Ergebnisse des Backtests (Replay des unveränderten Live-Codes auf historischen Daten),
keinen Code. Er ist vom Dashboard (`main`) getrennt.

- `protokoll.md` – Protokoll aller Kalibrierungen und Runden, wird nur ergänzt.
- `kalibrierung/` – Abgleich des Replays mit dem echten Paper-Konto (21.09.–02.10.2026):
  `bericht.md` (Ergebnis, Tabelle pro Trade, Ursachen), `trades.csv` (echt gegen Replay je Trade),
  `entscheidungen.csv` (jedes Setup: Entscheidung live gegen Replay), `details.json`.
- `runde-N/` – Jahresrunden: `zusammenfassung.md`, `trades.json`, `setups.csv.gz`.

Erfolgskriterien je Runde (fest): ≥ 200 Trades, Erwartungswert nach Kosten ≥ +0,10R, Profitfaktor ≥ 1,3,
max. Drawdown ≤ 15R, besser als ≥ 95 von 100 Zufallsläufen. Kosten: 0,03R je Long, 0,05R je Short.
