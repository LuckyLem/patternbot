# Diagnose des Chart-Lesers auf Runde 1 · nur Geometrie

Auftrag des Inhabers vom 15.10.2026. Runde 1 (Okt. 2025 – Sep. 2026) gehört zum Prüftopf: gezählt wird nur die Geometrie, **kein Vorher/Nachher in R, keine Auswahl nach Ergebnis**.

Chart-Leser Teil 1, Festlegung v1 (`chartleser/CHARTLESER.md`), auf den Kerzen des Replays (IEX 15 Min, split-bereinigt) mit SIP-1-Min-Kerzen als zweiter Quelle.

| Zählung | Wert |
|---|---|
| Trades der Runde | 1009 |
| Signal nachgebaut, gleich dem Replay (Kante, Stop, Ziel) | 1009 von 1009 |
| Ankerpunkte geprüft | 6639 (davon 6639 mit SIP-Kerze) |
| Ankerpunkte verworfen | 1 (SIP: 1) |
| Trades mit mindestens einer Linie an einem verworfenen Punkt | 1 |
| davon nach der Korrektur kein Muster mehr | 0 |
| Kante geändert (Anzahl, Median der Änderung in ATR) | 0, None |
| Gegenkante geändert | 0, None |
| Stop geändert | 0, None |
| Ziel geändert | 0, None |
| Signalkerze mit Abzug (Lücke über 1 ATR und Durchfall über 0,5 ATR) | 8 |
| Ankerpunkte ohne Maßstab (zu wenig Vergleichskerzen) | 0 |

**Bilder:** 40 Trades, zufällig gezogen mit dem festen Seed 20261015 (alle Trades gleich wahrscheinlich, ohne Blick auf das Ergebnis): `bilder/`.

## Wie die Trades enden (nur Zählung, kein R)

| Ausstieg | Trades | Anteil |
|---|---|---|
| Ziel erreicht | 38 | 3.8 % |
| Zeit-Stop (120 bzw. 240 Minuten) | 616 | 61.1 % |
| Tagesende (Glattstellung 10 Minuten vor Schluss) | 250 | 24.8 % |
| Stop, Anfangsstop | 74 | 7.3 % |
| Stop, nachgezogen auf den Einstieg | 31 | 3.1 % |

Ziel erreicht je Muster: Rechteck 21 von 567, Inverse Schulter-Kopf-Schulter 5 von 129, Schulter-Kopf-Schulter 7 von 120, Aufsteigendes Dreieck 4 von 106, Absteigendes Dreieck 1 von 61, Doppelboden 0 von 13, Doppeltop 0 von 13.

## Trades mit verworfenen Ankerpunkten

| Nr. | Tag | Wert | Muster | Punkt | IEX | SIP | Grund |
|---|---|---|---|---|---|---|---|
| 293 | 2026-01-06 | WMT | Rechteck | Berührung oben | 113.445 | 113.425 | SIP bestätigt den Kurs nicht (SIP-Hoch 113.42 statt 113.44), ersetzt durch den SIP-Wert |
