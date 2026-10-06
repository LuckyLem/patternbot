# Hinweis zu Runde 1: Neuberechnung nach einem Simulatorfehler (06.10.2026)

Nach der ersten Rechnung (03.10.) fiel ein Fehler im Simulator auf. In den ersten drei Minuten nach einem Fill
lösten Fehlkurse Stops aus: Odd Lots von 1 Aktie, außerbörslich gemeldet, zu absurden Preisen. Ein Beispiel ist ELV
am 20.10.2025 mit 310,00 bei einem Markt von 352.

Was danach geschah:
1. Behoben: Es zählen nur noch Abschlüsse innerhalb der offiziellen SIP-Minutenkerze.
2. Neu kalibriert: identisch mit der PC-Referenz, alle 659 Entscheidungen, Trades und Fills (siehe `kalibrierung/`).
3. Das Jahr mit **unveränderten Regeln** neu gerechnet. Die Spielregeln erlauben das ausnahmsweise bei einem
   Simulatorfehler; beide Ergebnisse stehen im Protokoll.

| Rechnung | Trades | Erwartungswert n.K. | PF | max. DD | Summe n.K. | Zufall | Ziel |
|---|---|---|---|---|---|---|---|
| erste (03.10., mit dem Fehler) | 1007 | −0,089R | 0,67 | 96R | −89,5R | 25/100 | nein |
| **korrigiert (06.10., zählt)** | **1009** | **−0,056R** | **0,76** | **65R** | **−56,0R** | **25/100** | **nein** |

Die Dateien in diesem Ordner sind die korrigierte Rechnung. Die erste Rechnung liegt in
`runde-1-erste-rechnung/`. Der Satz „erstes Rechnen“ in `zusammenfassung.md` ist der Standardtext; gemeint ist die
Neuberechnung mit unveränderten Regeln.
