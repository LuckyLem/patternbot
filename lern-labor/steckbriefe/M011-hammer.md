# M011 · Hammer nach Abwärtstrend

Neues Muster des Lern-Labors (Umkehr nach einem Abwärtstrend, nur long), Auftrag des Inhabers vom 20.10.2026 (großes Paket Lerntopf-Lauf 1). Angelegt am 20.10.2026 · **Stufe 0** (Steckbrief liegt vor). Diese Regeln stehen fest, bevor irgendein Ergebnis bekannt ist; eine Änderung ergibt ein neues Muster mit neuer Nummer.

| Feld | Inhalt |
|---|---|
| Name, Quelle | Hammer nach Abwärtstrend. Quelle: Reel von SmartForexPips auf Instagram (Kennung des Reels Dc-2SMemlGt), Idee des Inhabers vom 19.10.2026; Lehrbuch-Grundlage Nison, „Japanese Candlestick Charting Techniques“, und Bulkowski, „Encyclopedia of Candlestick Charts“. Regeln in eigenen Worten, vom Inhaber am 20.10. vorgegeben. |
| Zeitebene und Zoom | 1, 5 und 15 Minuten. 15 Min: IEX-Kerzen wie live (im Lerntopf split-bereinigt). 1 und 5 Min: aus den SIP-1-Min-Kerzen zusammengesetzt, nur reguläre Handelszeit. Alle Längen und das ATR gelten in Kerzen der jeweiligen Zeitebene; ATR = Wilder-ATR über 14 Kerzen, Wert der Kerze vor der ersten Musterkerze. |
| Vortrend | Abwärtstrend: Vom letzten bestätigten Zickzack-Hoch vor dem Muster bis zum tiefsten Tief des Musters ist der Kurs um mindestens 3 ATR gefallen, und dieses Tief ist das tiefste Tief der letzten 20 Kerzen. Gemessen am Tief der Hammer-Kerze. |
| Kerzen- bzw. Linienregeln | Hammer-Kerze H: Spanne (Hoch − Tief) mindestens 0,5 ATR; Körper = |Schluss − Eröffnung|; unterer Docht (kleinerer Wert von Eröffnung und Schluss − Tief) mindestens 2 × Körper; oberer Docht (Hoch − größerer Wert von Eröffnung und Schluss) höchstens 10 % der Spanne. Ankerpunkt: das Tief von H. Wendepunkte nach dem Zickzack des Chart-Lesers (Teil 1), Größe 2 ATR; ein Wendepunkt zählt erst ab der Kerze, an der er bestätigt ist. |
| Gültig nur, wenn … | Vortrend erfüllt; H erfüllt alle Kerzenregeln; der Einstieg liegt unter dem Ziel. |
| Auslöser | Nur die direkt auf H folgende Kerze zählt: Sie schließt über dem Hoch von H. Bewertet bei ihrem Schluss. Einstieg zum Eröffnungskurs der SIP-Minute nach dem Entscheidungszeitpunkt (Kerzenschluss + 33 s), wie in der Vorab-Datei. |
| Stop | 1 Cent unter dem Tief von H. |
| Ziel | Der Preis des letzten bestätigten Zickzack-Hochs vor H (Beginn des Abwärtstrends). |
| Ungültig, wenn … | Die Folgekerze schließt nicht über dem Hoch von H; der Einstieg liegt am oder über dem Ziel. |
| Filter | Nur das Zeitfenster: keine Einstiege in den ersten 20 und den letzten 30 Minuten der Sitzung. Keine weiteren Filter (kein Volumen-, Markt- oder Stärkefilter). |
| Haltedauer | Nach der Vorab-Datei Lerntopf-Lauf 1: Varianten H0–H4 (Zeit-Stop in Kerzen, ohne Zeit-Stop, halbes Ziel, über Nacht, Zeit-Stop nach der Entstehungsdauer). In allen Varianten wie live: ab +0,6R Stop auf den Einstieg, ab +1,5R folgt der Stop dem Kurs im Abstand von 1R. Über Nacht nur in Simulation und Schatten. |
| Bewertungsmerkmale | Werden für jedes Signal gespeichert, auf Stufe 0 aber nicht zum Filtern benutzt: Dochtlänge in Körpern und in ATR, Spanne in ATR, Tiefe des Vortrends in ATR, Volumen von H gegen den Schnitt der 20 Kerzen davor. |
| Darstellung im Bild | Hammer-Kerze und Folgekerze markiert, Zickzack-Hoch als Ziel, Stop gestrichelt, Vortrend als Linie vom Hoch zum Tief. |
| Selbstkontrolle | Auf 15 Min (IEX) müssen die Ankerpunkte (siehe Kerzen- bzw. Linienregeln) von SIP bestätigt sein, mit derselben Toleranz wie im Chart-Leser (0,5 Cent). Bestätigt SIP einen Ankerpunkt nicht, ist das Signal ungültig; neu gezeichnet wird nicht. Auf 1 und 5 Min entfällt die Prüfung, die Kerzen kommen schon aus SIP. |

**Bisher gerechnet:** nichts. Getestet wird im Lerntopf (Okt. 2020–Sep. 2023) nach der Vorab-Datei Lerntopf-Lauf 1, auf 1, 5 und 15 Minuten.
