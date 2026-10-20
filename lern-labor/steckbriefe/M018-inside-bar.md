# M018 · Inside-Bar-Ausbruch in Trendrichtung

Neues Muster des Lern-Labors (Fortsetzung, long und short, nur in Trendrichtung), Auftrag des Inhabers vom 20.10.2026 (großes Paket Lerntopf-Lauf 1). Angelegt am 20.10.2026 · **Stufe 0** (Steckbrief liegt vor). Diese Regeln stehen fest, bevor irgendein Ergebnis bekannt ist; eine Änderung ergibt ein neues Muster mit neuer Nummer.

| Feld | Inhalt |
|---|---|
| Name, Quelle | Inside-Bar-Ausbruch in Trendrichtung. Quelle: Lehrbuch-Grundlage Crabel, „Day Trading with Short Term Price Patterns“ (Inside Day), und Bulkowski. Auftrag des Inhabers 20.10.2026. |
| Zeitebene und Zoom | 1, 5 und 15 Minuten. 15 Min: IEX-Kerzen wie live (im Lerntopf split-bereinigt). 1 und 5 Min: aus den SIP-1-Min-Kerzen zusammengesetzt, nur reguläre Handelszeit. Alle Längen und das ATR gelten in Kerzen der jeweiligen Zeitebene; ATR = Wilder-ATR über 14 Kerzen, Wert der Kerze vor der ersten Musterkerze. |
| Vortrend | Trend der Zeitebene, gemessen wie der Tagestrend des Bots, aber auf diesen Kerzen: aufwärts, wenn der Schluss über dem EMA50 liegt und der EMA20 über dem EMA50; abwärts gespiegelt; sonst kein Trend. Gemessen an der Innenkerze. |
| Kerzen- bzw. Linienregeln | Mutterkerze M mit Spanne mindestens 1 ATR; die folgende Innenkerze I liegt ganz in M (Hoch I höchstens Hoch M, Tief I mindestens Tief M). Ankerpunkte: Hoch und Tief von M. |
| Gültig nur, wenn … | M und I erfüllen die Regeln; Trend vorhanden. |
| Auslöser | Innerhalb der 3 Kerzen nach I zählt der erste Schluss außerhalb der Spanne von M: long bei Aufwärtstrend über dem Hoch von M, short bei Abwärtstrend unter dem Tief von M. Einstieg zum Eröffnungskurs der SIP-Minute nach dem Entscheidungszeitpunkt (Kerzenschluss + 33 s), wie in der Vorab-Datei. |
| Stop | Long: Tief von M − 1 Cent; short: Hoch von M + 1 Cent. |
| Ziel | Ausbruchskante ± Spanne von M. |
| Ungültig, wenn … | Kein Schluss außerhalb von M innerhalb von 3 Kerzen; der erste Schluss außerhalb liegt gegen den Trend. |
| Filter | Nur das Zeitfenster: keine Einstiege in den ersten 20 und den letzten 30 Minuten der Sitzung. Keine weiteren Filter (kein Volumen-, Markt- oder Stärkefilter). |
| Haltedauer | Nach der Vorab-Datei Lerntopf-Lauf 1: Varianten H0–H4 (Zeit-Stop in Kerzen, ohne Zeit-Stop, halbes Ziel, über Nacht, Zeit-Stop nach der Entstehungsdauer). In allen Varianten wie live: ab +0,6R Stop auf den Einstieg, ab +1,5R folgt der Stop dem Kurs im Abstand von 1R. Über Nacht nur in Simulation und Schatten. |
| Bewertungsmerkmale | Werden für jedes Signal gespeichert, auf Stufe 0 aber nicht zum Filtern benutzt: Spanne von M in ATR, Spanne von I in % von M, Volumen beim Ausbruch. |
| Darstellung im Bild | Mutter- und Innenkerze markiert, Kanten, Ziel und Stop gestrichelt. |
| Selbstkontrolle | Auf 15 Min (IEX) müssen die Ankerpunkte (siehe Kerzen- bzw. Linienregeln) von SIP bestätigt sein, mit derselben Toleranz wie im Chart-Leser (0,5 Cent). Bestätigt SIP einen Ankerpunkt nicht, ist das Signal ungültig; neu gezeichnet wird nicht. Auf 1 und 5 Min entfällt die Prüfung, die Kerzen kommen schon aus SIP. |

**Bisher gerechnet:** nichts. Getestet wird im Lerntopf (Okt. 2020–Sep. 2023) nach der Vorab-Datei Lerntopf-Lauf 1, auf 1, 5 und 15 Minuten.
