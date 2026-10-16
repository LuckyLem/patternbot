# Prüfung der Eröffnungskerzen: IEX gegen SIP · Stand 2026-10-16 14:20

Auftrag des Inhabers vom 15.10.2026, Teil A4. Nur gelesen, am Bot ändert sich nichts.

**Regeln (Inhaber, 15.10.):**
- Verdächtig ist nur ein IEX-Wert **außerhalb** der SIP-Spanne derselben 15 Minuten: IEX-Hoch über dem SIP-Hoch oder IEX-Tief unter dem SIP-Tief. SIP umfasst alle Börsen, eine breitere SIP-Spanne ist normal.
- **Ausreißer** heißt: außerhalb, und dabei mehr als 0,5 % vom Kurs **oder** mehr als das Doppelte der mittleren Spanne der Eröffnungskerzen der 20 Handelstage davor.
- Werte: die 147 Werte des Live-Bots. Geprüft wird nur der Live-Zeitraum, darum gibt es hier keine Überlebensverzerrung.
- Daten bis 2026-10-15, 0 Abrufe.

## a) AMD 05.10. und 06.10.

| Tag | IEX-Eröffnungskerze (O / H / T / S) | SIP 09:30–09:44 (O / H / T / S) | Frage | SIP-Wert | von SIP bestätigt |
|---|---|---|---|---|---|
| 2026-10-05 | 630,06 / 631,00 / 620,05 / 630,84 | 630,61 / 631,71 / 619,99 / 631,61 | Tief 620,05 | 619,99 | ja |
| 2026-10-06 | 648,98 / 649,74 / 628,21 / 637,25 | 648,00 / 649,88 / 628,00 / 637,30 | Eröffnung 648,98 | 648,00 | **nein** |
| 2026-10-06 | 648,98 / 649,74 / 628,21 / 637,25 | 648,00 / 649,88 / 628,00 / 637,30 | Tief 628,21 | 628,00 | ja |

SIP-Minuten 2026-10-05 (New York):

| Minute | O | H | T | S | Volumen |
|---|---|---|---|---|---|
| 09:30 | 630,61 | 630,90 | 620,27 | 621,02 | 524.112 |
| 09:31 | 620,58 | 625,79 | 619,99 | 623,53 | 259.659 |
| 09:32 | 623,54 | 627,02 | 623,00 | 625,91 | 118.072 |
| 09:33 | 625,53 | 628,28 | 625,14 | 627,87 | 133.850 |
| 09:34 | 628,28 | 628,48 | 626,60 | 627,53 | 57.380 |
| 09:35 | 627,49 | 628,25 | 626,60 | 627,38 | 81.838 |
| 09:36 | 627,63 | 628,50 | 626,75 | 627,85 | 56.535 |
| 09:37 | 627,84 | 628,71 | 627,30 | 628,01 | 50.515 |
| 09:38 | 628,00 | 628,00 | 625,23 | 625,63 | 68.443 |
| 09:39 | 625,57 | 627,33 | 625,57 | 626,94 | 30.864 |
| 09:40 | 626,85 | 628,55 | 626,77 | 628,19 | 70.201 |
| 09:41 | 627,87 | 629,66 | 627,00 | 629,51 | 119.164 |
| 09:42 | 629,47 | 630,76 | 628,76 | 630,76 | 92.842 |
| 09:43 | 630,29 | 630,91 | 629,00 | 630,60 | 67.508 |
| 09:44 | 630,73 | 631,71 | 630,34 | 631,61 | 86.429 |

SIP-Minuten 2026-10-06 (New York):

| Minute | O | H | T | S | Volumen |
|---|---|---|---|---|---|
| 09:30 | 648,00 | 649,81 | 646,62 | 648,82 | 616.780 |
| 09:31 | 648,76 | 649,88 | 642,36 | 643,26 | 226.172 |
| 09:32 | 643,26 | 643,28 | 635,35 | 635,88 | 280.128 |
| 09:33 | 635,99 | 636,40 | 632,55 | 634,00 | 263.635 |
| 09:34 | 634,19 | 634,72 | 630,66 | 632,12 | 320.359 |
| 09:35 | 631,84 | 633,10 | 628,75 | 629,55 | 268.150 |
| 09:36 | 629,26 | 633,97 | 628,00 | 633,64 | 277.255 |
| 09:37 | 633,33 | 633,99 | 629,57 | 631,64 | 147.549 |
| 09:38 | 631,38 | 635,34 | 631,38 | 635,14 | 175.892 |
| 09:39 | 635,14 | 636,88 | 634,95 | 636,17 | 215.124 |
| 09:40 | 635,92 | 636,00 | 633,38 | 634,32 | 144.214 |
| 09:41 | 634,56 | 635,37 | 633,96 | 634,24 | 76.641 |
| 09:42 | 634,87 | 637,49 | 634,02 | 637,13 | 144.204 |
| 09:43 | 636,95 | 638,63 | 636,85 | 638,52 | 161.133 |
| 09:44 | 638,67 | 638,73 | 636,60 | 637,30 | 95.296 |

## b) 147 Werte seit 21.09.

- Symbol-Tage: 2788, davon mit SIP-Vergleich 2788 (147 Werte, 19 Tage).
- IEX außerhalb der SIP-Spanne: Hoch 0×, Tief 0×.
- Davon mehr als 0,5 % vom Kurs: Hoch 0×, Tief 0×; mehr als 2× die mittlere Spanne: Hoch 0×, Tief 0×.
- **Ausreißer: Hoch 0×, Tief 0×; Symbol-Tage mit Ausreißer: 0 von 2788 (0,0 %).**


## c) Setups seit 28.09.: Linien an einem Ausreißer

- Setups: 1912; mit den Detektoren des Bots nachgebaut: 1903; nicht nachgebaut: 9.
- Ankerpunkte an Eröffnungskerzen: 799; Setups mit einer Linie an einem Ausreißer (wie in b): **0**.


Nicht nachgebaut (Gründe, höchstens 40):

- MA 2026-10-15 14:15 DoubleBottom: Signalkerze fehlt
- DIS 2026-10-15 14:15 AscendingTriangle: Signalkerze fehlt
- GS 2026-10-15 14:15 DoubleBottom: Signalkerze fehlt
- SYK 2026-10-15 14:15 InverseHeadShoulders: Signalkerze fehlt
- PRU 2026-10-15 14:15 InverseHeadShoulders: Signalkerze fehlt
- AFL 2026-10-15 14:30 DoubleTop: Detektor meldet kein Signal
- ROP 2026-10-15 14:30 HeadShouldersTop: Detektor meldet kein Signal
- META 2026-10-15 14:45 InverseHeadShoulders: Detektor meldet kein Signal
- ADBE 2026-10-15 14:45 DescendingTriangle: Detektor meldet kein Signal
