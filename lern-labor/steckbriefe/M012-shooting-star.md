# M012 · Shooting Star nach Aufwärtstrend

Neues Muster des Lern-Labors (Umkehr nach einem Aufwärtstrend, nur short; Spiegel von M011), Auftrag des Inhabers vom 20.10.2026 (großes Paket Lerntopf-Lauf 1). Angelegt am 20.10.2026 · **Stufe 0** (Steckbrief liegt vor). Diese Regeln stehen fest, bevor irgendein Ergebnis bekannt ist; eine Änderung ergibt ein neues Muster mit neuer Nummer.

| Feld | Inhalt |
|---|---|
| Name, Quelle | Shooting Star nach Aufwärtstrend. Quelle: Lehrbuch-Grundlage Nison, „Japanese Candlestick Charting Techniques“, und Bulkowski, „Encyclopedia of Candlestick Charts“. Spiegel von M011 (Auftrag des Inhabers 20.10.2026). |
| Zeitebene und Zoom | 1, 5 und 15 Minuten. 15 Min: IEX-Kerzen wie live (im Lerntopf split-bereinigt). 1 und 5 Min: aus den SIP-1-Min-Kerzen zusammengesetzt, nur reguläre Handelszeit. Alle Längen und das ATR gelten in Kerzen der jeweiligen Zeitebene; ATR = Wilder-ATR über 14 Kerzen, Wert der Kerze vor der ersten Musterkerze. |
| Vortrend | Aufwärtstrend: Vom letzten bestätigten Zickzack-Tief vor dem Muster bis zum höchsten Hoch des Musters ist der Kurs um mindestens 3 ATR gestiegen, und dieses Hoch ist das höchste Hoch der letzten 20 Kerzen. Gemessen am Hoch der Stern-Kerze. |
| Kerzen- bzw. Linienregeln | Stern-Kerze S: Spanne mindestens 0,5 ATR; oberer Docht mindestens 2 × Körper; unterer Docht höchstens 10 % der Spanne. Ankerpunkt: das Hoch von S. Wendepunkte nach dem Zickzack des Chart-Lesers (Teil 1), Größe 2 ATR; ein Wendepunkt zählt erst ab der Kerze, an der er bestätigt ist. |
| Gültig nur, wenn … | Vortrend erfüllt; S erfüllt alle Kerzenregeln; der Einstieg liegt über dem Ziel. |
| Auslöser | Nur die direkt auf S folgende Kerze zählt: Sie schließt unter dem Tief von S. Einstieg zum Eröffnungskurs der SIP-Minute nach dem Entscheidungszeitpunkt (Kerzenschluss + 33 s), wie in der Vorab-Datei. |
| Stop | 1 Cent über dem Hoch von S. |
| Ziel | Der Preis des letzten bestätigten Zickzack-Tiefs vor S. |
| Ungültig, wenn … | Die Folgekerze schließt nicht unter dem Tief von S; der Einstieg liegt am oder unter dem Ziel. |
| Filter | Nur das Zeitfenster: keine Einstiege in den ersten 20 und den letzten 30 Minuten der Sitzung. Keine weiteren Filter (kein Volumen-, Markt- oder Stärkefilter). |
| Haltedauer | Nach der Vorab-Datei Lerntopf-Lauf 1: Varianten H0–H4 (Zeit-Stop in Kerzen, ohne Zeit-Stop, halbes Ziel, über Nacht, Zeit-Stop nach der Entstehungsdauer). In allen Varianten wie live: ab +0,6R Stop auf den Einstieg, ab +1,5R folgt der Stop dem Kurs im Abstand von 1R. Über Nacht nur in Simulation und Schatten. |
| Bewertungsmerkmale | Werden für jedes Signal gespeichert, auf Stufe 0 aber nicht zum Filtern benutzt: Dochtlänge in Körpern und in ATR, Spanne in ATR, Höhe des Vortrends in ATR, Volumen von S. |
| Darstellung im Bild | Stern-Kerze und Folgekerze markiert, Zickzack-Tief als Ziel, Stop gestrichelt. |
| Selbstkontrolle | Auf 15 Min (IEX) müssen die Ankerpunkte (siehe Kerzen- bzw. Linienregeln) von SIP bestätigt sein, mit derselben Toleranz wie im Chart-Leser (0,5 Cent). Bestätigt SIP einen Ankerpunkt nicht, ist das Signal ungültig; neu gezeichnet wird nicht. Auf 1 und 5 Min entfällt die Prüfung, die Kerzen kommen schon aus SIP. |

**Bisher gerechnet:** nichts. Getestet wird im Lerntopf (Okt. 2020–Sep. 2023) nach der Vorab-Datei Lerntopf-Lauf 1, auf 1, 5 und 15 Minuten.
