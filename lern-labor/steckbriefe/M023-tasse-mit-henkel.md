# M023 · Tasse mit Henkel

Neues Muster des Lern-Labors (Fortsetzung nach einem Aufwärtstrend, nur long), Auftrag des Inhabers vom 20.10.2026 (großes Paket Lerntopf-Lauf 1). Angelegt am 20.10.2026 · **Stufe 0** (Steckbrief liegt vor). Diese Regeln stehen fest, bevor irgendein Ergebnis bekannt ist; eine Änderung ergibt ein neues Muster mit neuer Nummer.

| Feld | Inhalt |
|---|---|
| Name, Quelle | Tasse mit Henkel. Quelle: Lehrbuch-Grundlage O'Neil, „How to Make Money in Stocks“ (Cup with Handle), und Bulkowski. Auftrag des Inhabers 20.10.2026. |
| Zeitebene und Zoom | 1, 5 und 15 Minuten. 15 Min: IEX-Kerzen wie live (im Lerntopf split-bereinigt). 1 und 5 Min: aus den SIP-1-Min-Kerzen zusammengesetzt, nur reguläre Handelszeit. Alle Längen und das ATR gelten in Kerzen der jeweiligen Zeitebene; ATR = Wilder-ATR über 14 Kerzen, Wert der Kerze vor der ersten Musterkerze. |
| Vortrend | Aufwärtstrend vor der Tasse: Der Schlusskurs am linken Rand liegt mindestens 4 ATR über dem Schlusskurs 50 Kerzen davor. |
| Kerzen- bzw. Linienregeln | Linker Rand L = Zickzack-Hoch (2 ATR). Boden B = tiefstes Tief nach L; Tiefe = L − B mindestens 4 ATR. Rechter Rand R = Zickzack-Hoch nach B, höchstens 1 ATR von L entfernt; von L bis R mindestens 20 Kerzen; die Tasse ist rund: B liegt im mittleren Drittel der Zeit von L bis R. Henkel: nach R ein Rücklauf von 3 bis 15 Kerzen, dessen tiefstes Tief höchstens ein Drittel der Tiefe abgibt. Randlinie = höherer Wert von L und R. Ankerpunkte: L, B, R und das Henkel-Tief. |
| Gültig nur, wenn … | Vortrend, Tiefe, Breite, Rundung und Henkel erfüllt; im Henkel kein Schluss über der Randlinie vor der Signalkerze. |
| Auslöser | Die Signalkerze schließt über der Randlinie, die Kerze davor nicht; spätestens 15 Kerzen nach R. Einstieg zum Eröffnungskurs der SIP-Minute nach dem Entscheidungszeitpunkt (Kerzenschluss + 33 s), wie in der Vorab-Datei. |
| Stop | Henkel-Tief − 0,1 ATR. |
| Ziel | Randlinie + Tiefe. |
| Ungültig, wenn … | Der Henkel gibt mehr als ein Drittel der Tiefe ab oder dauert länger als 15 Kerzen; der Boden liegt nicht im mittleren Drittel. |
| Filter | Nur das Zeitfenster: keine Einstiege in den ersten 20 und den letzten 30 Minuten der Sitzung. Keine weiteren Filter (kein Volumen-, Markt- oder Stärkefilter). |
| Haltedauer | Nach der Vorab-Datei Lerntopf-Lauf 1: Varianten H0–H4 (Zeit-Stop in Kerzen, ohne Zeit-Stop, halbes Ziel, über Nacht, Zeit-Stop nach der Entstehungsdauer). In allen Varianten wie live: ab +0,6R Stop auf den Einstieg, ab +1,5R folgt der Stop dem Kurs im Abstand von 1R. Über Nacht nur in Simulation und Schatten. |
| Bewertungsmerkmale | Werden für jedes Signal gespeichert, auf Stufe 0 aber nicht zum Filtern benutzt: Tiefe und Breite in ATR, Rundung (Lage des Bodens), Henkel-Rücklauf in % der Tiefe, Volumen im Henkel gegen die Tasse. |
| Darstellung im Bild | Tasse als Kurve von L über B nach R, Henkel markiert, Randlinie, Tiefe als Pfeil, Ziel und Stop gestrichelt. |
| Selbstkontrolle | Auf 15 Min (IEX) müssen die Ankerpunkte (siehe Kerzen- bzw. Linienregeln) von SIP bestätigt sein, mit derselben Toleranz wie im Chart-Leser (0,5 Cent). Bestätigt SIP einen Ankerpunkt nicht, ist das Signal ungültig; neu gezeichnet wird nicht. Auf 1 und 5 Min entfällt die Prüfung, die Kerzen kommen schon aus SIP. |

**Bisher gerechnet:** nichts. Getestet wird im Lerntopf (Okt. 2020–Sep. 2023) nach der Vorab-Datei Lerntopf-Lauf 1, auf 1, 5 und 15 Minuten.
