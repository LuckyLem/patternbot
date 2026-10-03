# Hinweis zu Runde 1 – Simulatorfehler nach der Runde gefunden (03.10.2026)

Die Zahlen in `zusammenfassung.md` sind so gerechnet, wie die Runde lief. Erst beim Prüfen der Ergebnisse fiel ein
Fehler im Simulator auf, der die Stops verfälscht.

**Der Fehler:** In den ersten drei Minuten nach einem Fill prüft der Simulator Stops Tick für Tick auf SIP-Trades.
Dabei zählten auch Abschlüsse, die den Kurs nicht setzen, vor allem Odd Lots: einzelne Aktien, außerbörslich
gemeldet, zu absurden Preisen. Beispiele:

| Symbol | Zeitpunkt (New York) | Abschluss (1 Aktie) | Markt | Tief der SIP-Minutenkerze |
|---|---|---|---|---|
| ELV | 20.10.2025 10:16:16 | 310,00 | ~352 | 351,92 |
| TMO | 20.10.2025 10:16:56 | 480,74 | ~544 | 543,76 |
| MET | 23.06.2026 13:47:06 | 85,41 | ~88,2 | 88,21 |

Die offiziellen SIP-Minutenkerzen dieser Minuten liegen weit über dem Stop. Echt wären diese Stops nicht ausgelöst
worden.

**Betroffen:** im Hauptlauf 8 Trades (ELV, TMO, AMZN, TSLA, KO, ABBV, MET, NVDA), im Vergleichslauf V1 aus 2 Trades.

**Geschätzte Wirkung:** Die betroffenen Trades sind mit dem Minuten-Simulator nachgerechnet, ohne Folgeeffekte.

| Lauf | Summe nach Kosten | Erwartungswert je Trade |
|---|---|---|
| Hauptlauf | −89,5R → ca. −53,4R | −0,089R → ca. −0,053R |
| V1 aus | −48,7R → ca. −44,7R | – |

Am Ergebnis „Ziel nicht erreicht“ ändert das nichts.

**Vorgeschlagen (wartet auf das OK des Nutzers):**
1. Im Tick-Pfad nur Abschlüsse verwenden, die in der offiziellen SIP-Minutenkerze liegen; dazu Tests.
2. Neu kalibrieren.
3. Runde 1 mit unveränderten Regeln neu rechnen. Die Spielregeln erlauben das ausnahmsweise bei einem
   Simulatorfehler; beide Ergebnisse kommen ins Protokoll.
