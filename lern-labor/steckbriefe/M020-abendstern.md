# M020 · Abendstern nach Aufwärtstrend

Neues Muster des Lern-Labors (Umkehr nach einem Aufwärtstrend, nur short; Spiegel von M019), Auftrag des Inhabers vom 20.10.2026 (großes Paket Lerntopf-Lauf 1). Angelegt am 20.10.2026 · **Stufe 0** (Steckbrief liegt vor). Diese Regeln stehen fest, bevor irgendein Ergebnis bekannt ist; eine Änderung ergibt ein neues Muster mit neuer Nummer.

| Feld | Inhalt |
|---|---|
| Name, Quelle | Abendstern nach Aufwärtstrend. Quelle: Lehrbuch-Grundlage Nison, „Japanese Candlestick Charting Techniques“, und Bulkowski, „Encyclopedia of Candlestick Charts“ (Evening Star). Auftrag des Inhabers 20.10.2026. |
| Zeitebene und Zoom | 1, 5 und 15 Minuten. 15 Min: IEX-Kerzen wie live (im Lerntopf split-bereinigt). 1 und 5 Min: aus den SIP-1-Min-Kerzen zusammengesetzt, nur reguläre Handelszeit. Alle Längen und das ATR gelten in Kerzen der jeweiligen Zeitebene; ATR = Wilder-ATR über 14 Kerzen, Wert der Kerze vor der ersten Musterkerze. |
| Vortrend | Aufwärtstrend: Vom letzten bestätigten Zickzack-Tief vor dem Muster bis zum höchsten Hoch des Musters ist der Kurs um mindestens 3 ATR gestiegen, und dieses Hoch ist das höchste Hoch der letzten 20 Kerzen. Gemessen am höchsten Hoch der drei Kerzen. |
| Kerzen- bzw. Linienregeln | Kerze 1 steigt mit Körper mindestens 0,6 ATR. Kerze 2 hat einen kleinen Körper (höchstens 30 % von Körper 1), der ganz über dem Schluss von Kerze 1 liegt. Kerze 3 fällt und schließt unter der Mitte des Körpers von Kerze 1. Ankerpunkt: das höchste Hoch der drei Kerzen. Wendepunkte nach dem Zickzack des Chart-Lesers (Teil 1), Größe 2 ATR; ein Wendepunkt zählt erst ab der Kerze, an der er bestätigt ist. |
| Gültig nur, wenn … | Vortrend erfüllt; alle drei Kerzen erfüllen die Regeln; der Einstieg liegt über dem Ziel. |
| Auslöser | Der Schluss von Kerze 3. Einstieg zum Eröffnungskurs der SIP-Minute nach dem Entscheidungszeitpunkt (Kerzenschluss + 33 s), wie in der Vorab-Datei. |
| Stop | 1 Cent über dem höchsten Hoch der drei Kerzen. |
| Ziel | Der Preis des letzten bestätigten Zickzack-Tiefs vor dem Muster. |
| Ungültig, wenn … | Eine der Kerzenregeln fehlt; der Einstieg liegt am oder unter dem Ziel. |
| Filter | Nur das Zeitfenster: keine Einstiege in den ersten 20 und den letzten 30 Minuten der Sitzung. Keine weiteren Filter (kein Volumen-, Markt- oder Stärkefilter). |
| Haltedauer | Nach der Vorab-Datei Lerntopf-Lauf 1: Varianten H0–H4 (Zeit-Stop in Kerzen, ohne Zeit-Stop, halbes Ziel, über Nacht, Zeit-Stop nach der Entstehungsdauer). In allen Varianten wie live: ab +0,6R Stop auf den Einstieg, ab +1,5R folgt der Stop dem Kurs im Abstand von 1R. Über Nacht nur in Simulation und Schatten. |
| Bewertungsmerkmale | Werden für jedes Signal gespeichert, auf Stufe 0 aber nicht zum Filtern benutzt: Wie M019, gespiegelt. |
| Darstellung im Bild | Die drei Kerzen markiert, Ziel und Stop gestrichelt. |
| Selbstkontrolle | Auf 15 Min (IEX) müssen die Ankerpunkte (siehe Kerzen- bzw. Linienregeln) von SIP bestätigt sein, mit derselben Toleranz wie im Chart-Leser (0,5 Cent). Bestätigt SIP einen Ankerpunkt nicht, ist das Signal ungültig; neu gezeichnet wird nicht. Auf 1 und 5 Min entfällt die Prüfung, die Kerzen kommen schon aus SIP. |

**Bisher gerechnet:** nichts. Getestet wird im Lerntopf (Okt. 2020–Sep. 2023) nach der Vorab-Datei Lerntopf-Lauf 1, auf 1, 5 und 15 Minuten.
