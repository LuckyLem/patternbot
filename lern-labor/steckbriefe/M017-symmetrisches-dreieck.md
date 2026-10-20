# M017 · Symmetrisches Dreieck mit Ausbruch in Trendrichtung

Neues Muster des Lern-Labors (Fortsetzung, long und short, nur in Trendrichtung), Auftrag des Inhabers vom 20.10.2026 (großes Paket Lerntopf-Lauf 1). Angelegt am 20.10.2026 · **Stufe 0** (Steckbrief liegt vor). Diese Regeln stehen fest, bevor irgendein Ergebnis bekannt ist; eine Änderung ergibt ein neues Muster mit neuer Nummer.

| Feld | Inhalt |
|---|---|
| Name, Quelle | Symmetrisches Dreieck mit Ausbruch in Trendrichtung. Quelle: Lehrbuch-Grundlage Bulkowski, „Encyclopedia of Chart Patterns“, und Kirkpatrick/Dahlquist, „Technical Analysis“ (Symmetrical Triangles). Auftrag des Inhabers 20.10.2026. |
| Zeitebene und Zoom | 1, 5 und 15 Minuten. 15 Min: IEX-Kerzen wie live (im Lerntopf split-bereinigt). 1 und 5 Min: aus den SIP-1-Min-Kerzen zusammengesetzt, nur reguläre Handelszeit. Alle Längen und das ATR gelten in Kerzen der jeweiligen Zeitebene; ATR = Wilder-ATR über 14 Kerzen, Wert der Kerze vor der ersten Musterkerze. |
| Vortrend | Trend der Zeitebene, gemessen wie der Tagestrend des Bots, aber auf diesen Kerzen: aufwärts, wenn der Schluss über dem EMA50 liegt und der EMA20 über dem EMA50; abwärts gespiegelt; sonst kein Trend. Gemessen an der Kerze vor der ersten Berührung. Long nur bei Aufwärtstrend, short nur bei Abwärtstrend. |
| Kerzen- bzw. Linienregeln | Wendepunkte nach dem Zickzack des Chart-Lesers, Größe 1 ATR. Obere Linie durch mindestens 2 fallende Wendepunkt-Hochs, untere Linie durch mindestens 2 steigende Wendepunkt-Tiefs, beide durch die Dochte; Berührung innerhalb 0,5 ATR (mindestens 0,1 % vom Kurs). Die Linien laufen zusammen: Breite an der Signalkerze höchstens 70 % der Breite an der ersten Berührung. Erste bis letzte Berührung mindestens 10 Kerzen. Ankerpunkte: alle Berührungen. |
| Gültig nur, wenn … | Je Linie mindestens 2 Berührungen; zwischen erster Berührung und der Kerze vor dem Signal kein Schluss jenseits einer Linie; die Linien schneiden sich nicht vor dem Signal. |
| Auslöser | Long: Schluss über der oberen Linie, die Kerze davor nicht; short gespiegelt. Nur in Trendrichtung. Einstieg zum Eröffnungskurs der SIP-Minute nach dem Entscheidungszeitpunkt (Kerzenschluss + 33 s), wie in der Vorab-Datei. |
| Stop | Long: letzte Berührung der unteren Linie − 0,1 ATR; short gespiegelt. |
| Ziel | Ausbruchskante ± Breite des Dreiecks an der ersten Berührung. |
| Ungültig, wenn … | Ausbruch gegen den Trend; ein Schluss jenseits einer Linie vor dem Signal; die Linien schneiden sich vorher. |
| Filter | Nur das Zeitfenster: keine Einstiege in den ersten 20 und den letzten 30 Minuten der Sitzung. Keine weiteren Filter (kein Volumen-, Markt- oder Stärkefilter). |
| Haltedauer | Nach der Vorab-Datei Lerntopf-Lauf 1: Varianten H0–H4 (Zeit-Stop in Kerzen, ohne Zeit-Stop, halbes Ziel, über Nacht, Zeit-Stop nach der Entstehungsdauer). In allen Varianten wie live: ab +0,6R Stop auf den Einstieg, ab +1,5R folgt der Stop dem Kurs im Abstand von 1R. Über Nacht nur in Simulation und Schatten. |
| Bewertungsmerkmale | Werden für jedes Signal gespeichert, auf Stufe 0 aber nicht zum Filtern benutzt: Berührungen und Passgüte je Linie, Verengung, Breite in ATR, Dauer, Volumen beim Ausbruch. |
| Darstellung im Bild | Beide Linien mit Berührungskreisen, Ausbruch, Breite als Pfeil, Ziel und Stop gestrichelt. |
| Selbstkontrolle | Auf 15 Min (IEX) müssen die Ankerpunkte (siehe Kerzen- bzw. Linienregeln) von SIP bestätigt sein, mit derselben Toleranz wie im Chart-Leser (0,5 Cent). Bestätigt SIP einen Ankerpunkt nicht, ist das Signal ungültig; neu gezeichnet wird nicht. Auf 1 und 5 Min entfällt die Prüfung, die Kerzen kommen schon aus SIP. |

**Bisher gerechnet:** nichts. Getestet wird im Lerntopf (Okt. 2020–Sep. 2023) nach der Vorab-Datei Lerntopf-Lauf 1, auf 1, 5 und 15 Minuten.
