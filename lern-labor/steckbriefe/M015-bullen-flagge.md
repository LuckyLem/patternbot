# M015 · Bullen-Flagge

Neues Muster des Lern-Labors (Fortsetzung nach einem steilen Anstieg, nur long), Auftrag des Inhabers vom 20.10.2026 (großes Paket Lerntopf-Lauf 1). Angelegt am 20.10.2026 · **Stufe 0** (Steckbrief liegt vor). Diese Regeln stehen fest, bevor irgendein Ergebnis bekannt ist; eine Änderung ergibt ein neues Muster mit neuer Nummer.

| Feld | Inhalt |
|---|---|
| Name, Quelle | Bullen-Flagge. Quelle: Lehrbuch-Grundlage Bulkowski, „Encyclopedia of Chart Patterns“, und Kirkpatrick/Dahlquist, „Technical Analysis“ (Flags). Auftrag des Inhabers 20.10.2026. |
| Zeitebene und Zoom | 1, 5 und 15 Minuten. 15 Min: IEX-Kerzen wie live (im Lerntopf split-bereinigt). 1 und 5 Min: aus den SIP-1-Min-Kerzen zusammengesetzt, nur reguläre Handelszeit. Alle Längen und das ATR gelten in Kerzen der jeweiligen Zeitebene; ATR = Wilder-ATR über 14 Kerzen, Wert der Kerze vor der ersten Musterkerze. |
| Vortrend | Die Fahnenstange ist der Vortrend: ein Anstieg vom tiefsten Tief zum höchsten Hoch innerhalb von höchstens 10 Kerzen um mindestens 4 ATR (ATR vor dem Beginn der Stange). Das Hoch der Stange ist das höchste Hoch der letzten 20 Kerzen. |
| Kerzen- bzw. Linienregeln | Flagge: die 4 bis 20 Kerzen nach dem Hoch der Stange bis zur Kerze vor dem Signal. Gegenkanal: Regressionsgeraden durch die Hochs und durch die Tiefs der Flagge. Die obere Gerade fällt oder ist flach (Steigung höchstens 0); beide Geraden laufen nahezu parallel (Unterschied der Steigungen höchstens 0,1 ATR je Kerze). Die Flagge gibt höchstens die Hälfte der Stange ab (tiefstes Tief der Flagge mindestens Stangen-Hoch − 0,5 × Stangenlänge). Ankerpunkte: Tief und Hoch der Stange, tiefstes Tief der Flagge. |
| Gültig nur, wenn … | Stange, Länge und Rücklauf der Flagge erfüllt; kein Schluss in der Flagge über der oberen Geraden. |
| Auslöser | Die Signalkerze schließt über dem Wert der oberen Geraden an dieser Kerze, die Kerze davor nicht; spätestens 20 Kerzen nach dem Hoch der Stange. Einstieg zum Eröffnungskurs der SIP-Minute nach dem Entscheidungszeitpunkt (Kerzenschluss + 33 s), wie in der Vorab-Datei. |
| Stop | Tiefstes Tief der Flagge − 0,1 ATR. |
| Ziel | Ausbruchskante (Wert der oberen Geraden an der Signalkerze) + Stangenlänge. |
| Ungültig, wenn … | Die Flagge gibt mehr als die Hälfte der Stange ab, dauert länger als 20 Kerzen oder steigt (obere Gerade mit positiver Steigung). |
| Filter | Nur das Zeitfenster: keine Einstiege in den ersten 20 und den letzten 30 Minuten der Sitzung. Keine weiteren Filter (kein Volumen-, Markt- oder Stärkefilter). |
| Haltedauer | Nach der Vorab-Datei Lerntopf-Lauf 1: Varianten H0–H4 (Zeit-Stop in Kerzen, ohne Zeit-Stop, halbes Ziel, über Nacht, Zeit-Stop nach der Entstehungsdauer). In allen Varianten wie live: ab +0,6R Stop auf den Einstieg, ab +1,5R folgt der Stop dem Kurs im Abstand von 1R. Über Nacht nur in Simulation und Schatten. |
| Bewertungsmerkmale | Werden für jedes Signal gespeichert, auf Stufe 0 aber nicht zum Filtern benutzt: Stangenlänge in ATR, Dauer der Stange und der Flagge, Rücklauf in % der Stange, Steigung des Kanals, Volumen in der Stange gegen die Flagge. |
| Darstellung im Bild | Fahnenstange als Pfeil, Kanal der Flagge mit beiden Geraden, Ausbruch, Ziel als Projektion der Stangenlänge, Stop gestrichelt. |
| Selbstkontrolle | Auf 15 Min (IEX) müssen die Ankerpunkte (siehe Kerzen- bzw. Linienregeln) von SIP bestätigt sein, mit derselben Toleranz wie im Chart-Leser (0,5 Cent). Bestätigt SIP einen Ankerpunkt nicht, ist das Signal ungültig; neu gezeichnet wird nicht. Auf 1 und 5 Min entfällt die Prüfung, die Kerzen kommen schon aus SIP. |

**Bisher gerechnet:** nichts. Getestet wird im Lerntopf (Okt. 2020–Sep. 2023) nach der Vorab-Datei Lerntopf-Lauf 1, auf 1, 5 und 15 Minuten.
