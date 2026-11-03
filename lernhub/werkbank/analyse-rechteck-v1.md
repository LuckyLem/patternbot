# Analyse rechteck-v1

Nur Information: nichts filtert, nichts ändert eine Regel.

Trades mit Analyse: 13293

## Verlust- und Gewinn-Arten (die erste zutreffende zählt)

| Art | Regel | Anzahl | Anteil | Ø R |
|---|---|---:|---:|---:|
| Fehlausbruch | Stop innerhalb von 3 Kerzen nach dem Einstieg, MFE unter 0,3 R | 1600 | 12 % | -1,22 |
| Stop zu eng | gestoppt, danach Ziel noch erreicht, Stop-Abstand unter 1 ATR | 328 | 2 % | -1,25 |
| Ziel zu weit | MFE mindestens 0,8 des Ziels, danach Stop oder Zeitlimit | 896 | 7 % | +0,07 |
| Zeit | Ausstieg zum Tagesende oder Zeitlimit mit MFE über 0,5 R | 1357 | 10 % | +0,28 |
| Kosten | r_vor über 0, aber r unter 0 | 84 | 1 % | -0,06 |
| Gegen den Markt | SPY bewegt sich im Trade um mehr als 0,5 ATR (in SPY) gegen die Richtung | 3546 | 27 % | -0,94 |
| sauber gewonnen | Ziel erreicht | 3764 | 28 % | +1,32 |
| sonst | alles andere | 1718 | 13 % | -1,01 |

## Arten je Variante, nur Note A

| Gruppe | Trades | Ø R | Fehlausbruch | Stop zu eng | Ziel zu weit | Zeit | Kosten | Gegen den Markt | sauber gewonnen | sonst |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 15 Min · Ausbruch | 45 | -0,20 | 7 % | 0 % | 9 % | 16 % | 0 % | 31 % | 13 % | 24 % |
| 15 Min · Retest | 3 | +0,57 | 0 % | 0 % | 0 % | 33 % | 0 % | 0 % | 67 % | 0 % |
| 15 Min · früher Einstieg | 41 | -0,02 | 24 % | 2 % | 12 % | 29 % | 0 % | 7 % | 12 % | 12 % |
| 15 Min · Fehlschlag | 12 | -0,18 | 8 % | 8 % | 17 % | 8 % | 0 % | 33 % | 8 % | 17 % |
| 5 Min · Ausbruch | 941 | -0,11 | 7 % | 1 % | 7 % | 9 % | 1 % | 30 % | 34 % | 11 % |
| 5 Min · Retest | 188 | -0,31 | 16 % | 4 % | 5 % | 3 % | 2 % | 23 % | 34 % | 14 % |
| 5 Min · früher Einstieg | 599 | -0,27 | 19 % | 7 % | 7 % | 5 % | 0 % | 23 % | 25 % | 14 % |
| 5 Min · Fehlschlag | 354 | -0,23 | 14 % | 2 % | 8 % | 6 % | 0 % | 31 % | 27 % | 11 % |

## Arten je Variante, alle Noten

| Gruppe | Trades | Ø R | Fehlausbruch | Stop zu eng | Ziel zu weit | Zeit | Kosten | Gegen den Markt | sauber gewonnen | sonst |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 15 Min · Ausbruch | 162 | -0,02 | 11 % | 0 % | 9 % | 21 % | 1 % | 17 % | 19 % | 22 % |
| 15 Min · Retest | 11 | +0,25 | 9 % | 0 % | 0 % | 36 % | 0 % | 9 % | 36 % | 9 % |
| 15 Min · früher Einstieg | 128 | -0,03 | 22 % | 2 % | 12 % | 30 % | 0 % | 9 % | 12 % | 13 % |
| 15 Min · Fehlschlag | 37 | -0,12 | 16 % | 3 % | 8 % | 22 % | 0 % | 19 % | 22 % | 11 % |
| 5 Min · Ausbruch | 6055 | -0,10 | 6 % | 0 % | 7 % | 12 % | 1 % | 30 % | 31 % | 12 % |
| 5 Min · Retest | 1306 | -0,20 | 16 % | 3 % | 6 % | 6 % | 1 % | 22 % | 33 % | 13 % |
| 5 Min · früher Einstieg | 3391 | -0,22 | 19 % | 6 % | 6 % | 8 % | 0 % | 24 % | 24 % | 13 % |
| 5 Min · Fehlschlag | 2203 | -0,19 | 15 % | 2 % | 7 % | 10 % | 0 % | 28 % | 26 % | 13 % |

## Arten je Note

| Gruppe | Trades | Ø R | Fehlausbruch | Stop zu eng | Ziel zu weit | Zeit | Kosten | Gegen den Markt | sauber gewonnen | sonst |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| A | 2183 | -0,19 | 13 % | 3 % | 7 % | 7 % | 0 % | 27 % | 29 % | 13 % |
| B | 3149 | -0,16 | 12 % | 3 % | 6 % | 10 % | 1 % | 26 % | 30 % | 13 % |
| C | 7961 | -0,14 | 12 % | 2 % | 7 % | 11 % | 1 % | 27 % | 27 % | 13 % |

## Arten je Einstieg

| Gruppe | Trades | Ø R | Fehlausbruch | Stop zu eng | Ziel zu weit | Zeit | Kosten | Gegen den Markt | sauber gewonnen | sonst |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| Ausbruch | 6217 | -0,10 | 6 % | 0 % | 7 % | 12 % | 1 % | 29 % | 31 % | 13 % |
| Fehlschlag | 2240 | -0,19 | 15 % | 2 % | 7 % | 10 % | 0 % | 28 % | 25 % | 13 % |
| Retest | 1317 | -0,20 | 16 % | 3 % | 6 % | 6 % | 1 % | 22 % | 33 % | 13 % |
| früher Einstieg | 3519 | -0,21 | 19 % | 6 % | 6 % | 8 % | 0 % | 23 % | 24 % | 13 % |

## Arten je Zeitebene

| Gruppe | Trades | Ø R | Fehlausbruch | Stop zu eng | Ziel zu weit | Zeit | Kosten | Gegen den Markt | sauber gewonnen | sonst |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 15 | 338 | -0,03 | 16 % | 1 % | 10 % | 25 % | 0 % | 14 % | 17 % | 17 % |
| 5 | 12955 | -0,16 | 12 % | 3 % | 7 % | 10 % | 1 % | 27 % | 29 % | 13 % |

## Verlauf im Trade, nur Note A

| Variante | Trades | Ø MFE (R) | Ø MAE (R) | Ziel später erreicht | Ziel | Stop | Tagesende | Abstand zur Kante (ATR) | Muster fertig bis Einstieg |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 15 Min · Ausbruch | 45 | +0,53 | -0,60 | 7 % | 6 | 14 | 25 | +0,44 | 34 |
| 15 Min · Retest | 3 | +0,84 | -0,12 | 0 % | 2 | 0 | 1 | +1,04 | 51 |
| 15 Min · früher Einstieg | 41 | +0,98 | -0,72 | 7 % | 6 | 17 | 18 | +0,44 | 35 |
| 15 Min · Fehlschlag | 12 | +0,65 | -0,69 | 8 % | 1 | 4 | 7 | +0,35 | 57 |
| 5 Min · Ausbruch | 941 | +0,82 | -0,72 | 11 % | 348 | 414 | 179 | +0,43 | 33 |
| 5 Min · Retest | 188 | +0,84 | -0,81 | 16 % | 70 | 108 | 10 | +1,02 | 51 |
| 5 Min · früher Einstieg | 599 | +1,16 | -0,89 | 18 % | 157 | 383 | 59 | +0,47 | 28 |
| 5 Min · Fehlschlag | 354 | +1,06 | -0,85 | 13 % | 100 | 207 | 47 | +0,43 | 40 |

## Erkennung gegen Ergebnis

| Note | Trades | Ø R |
|---|---:|---:|
| A | 2183 | -0,19 |
| B | 3149 | -0,16 |
| C | 7961 | -0,14 |

| Variante | Note A | Note B | Note C |
|---|---:|---:|---:|
| 15 Min · Ausbruch | -0,20 (45) | +0,13 (34) | +0,01 (83) |
| 15 Min · Retest | +0,57 (3) | – | +0,13 (8) |
| 15 Min · früher Einstieg | -0,02 (41) | -0,03 (30) | -0,03 (57) |
| 15 Min · Fehlschlag | -0,18 (12) | -0,30 (9) | +0,02 (16) |
| 5 Min · Ausbruch | -0,11 (941) | -0,11 (1402) | -0,09 (3712) |
| 5 Min · Retest | -0,31 (188) | -0,19 (310) | -0,18 (808) |
| 5 Min · früher Einstieg | -0,27 (599) | -0,21 (845) | -0,21 (1947) |
| 5 Min · Fehlschlag | -0,23 (354) | -0,19 (519) | -0,18 (1330) |

| derselbe Kasten nach dem alten Stand 8454cdc07786 | Trades | Ø R |
|---|---:|---:|
| Note A | 19 | -0,11 |
| Note B | 1349 | -0,16 |
| Note C | 291 | -0,18 |
| Note C (gelockert) | 2391 | -0,18 |
| ungültig: Pendel ohne Band | 880 | -0,06 |
| ungültig: Steigung der Schlusskurse | 8363 | -0,15 |

Sichtprüfung: 140 Bilder, 98 Kästen mit 201 Trades zugeordnet (gleiche Aktie, gleicher Tag, gleiche Zeitebene, gleicher Kastenbeginn).

| Antwort | Kästen | Trades | Ø R |
|---|---:|---:|---:|
| ja | 78 | 160 | -0,18 |
| nein | 12 | 23 | -0,29 |
| unsicher | 8 | 18 | -0,09 |

## Einstiege auf denselben Kästen (4166 Kästen mit mehr als einem Einstieg)

| Einstieg | Trades | Ø R | Fehlausbruch | Stop zu eng | Ziel zu weit | Zeit | Kosten | Gegen den Markt | sauber gewonnen | sonst |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| Ausbruch | 4508 | -0,17 | 372 | 17 | 314 | 558 | 29 | 1426 | 1200 | 592 |
| Fehlschlag | 2223 | -0,20 | 335 | 50 | 147 | 219 | 10 | 613 | 562 | 287 |
| Retest | 1310 | -0,20 | 205 | 39 | 77 | 79 | 17 | 293 | 431 | 169 |
| früher Einstieg | 2183 | -0,53 | 553 | 166 | 69 | 38 | 0 | 563 | 455 | 339 |

## Was wäre wenn (nur Suchdaten, keine Regel)

Nur Suchdaten, nur Information, keine Regel. Was auffällt, wird eine neue Idee im Register und muss auf den Bestätigungsdaten bestehen.

Ø R nach Kosten je Variante (nur Note A) und über alle Trades:

| Variante | wie gerechnet | Stop 1,5 ATR | Stop 1 ATR | Ziel 1 R | Ziel 2 R | ohne Einstieg nach 14:30 |
|---|---:|---:|---:|---:|---:|---:|
| 15 Min · Ausbruch | -0,20 (45) | -0,25 | -0,24 | -0,23 | -0,19 | -0,45 (10) |
| 15 Min · Retest | +0,57 (3) | +0,43 | +0,65 | +0,60 | +0,34 | – (0) |
| 15 Min · früher Einstieg | -0,02 (41) | +0,10 | +0,07 | -0,03 | -0,01 | -0,24 (10) |
| 15 Min · Fehlschlag | -0,18 (12) | -0,01 | -0,04 | -0,05 | -0,13 | +1,36 (1) |
| 5 Min · Ausbruch | -0,11 (941) | -0,11 | -0,18 | -0,11 | -0,10 | -0,10 (674) |
| 5 Min · Retest | -0,31 (188) | -0,22 | -0,29 | -0,25 | -0,32 | -0,24 (123) |
| 5 Min · früher Einstieg | -0,27 (599) | -0,17 | -0,21 | -0,29 | -0,24 | -0,31 (441) |
| 5 Min · Fehlschlag | -0,23 (354) | -0,23 | -0,30 | -0,24 | -0,24 | -0,19 (250) |
| alle Trades | -0,15 (13293) | -0,13 | -0,20 | -0,16 | -0,15 | -0,16 (8966) |
