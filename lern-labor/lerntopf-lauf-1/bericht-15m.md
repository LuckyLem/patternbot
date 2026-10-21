# Lerntopf-Lauf 1 · Zwischenstand 15 Min

Stand 21.10.2026 17:44 deutscher Zeit (11:44 New York).

| | |
|---|---|
| Vorab-Datei | Lerntopf-Lauf 1, Fassung 3, SHA-256 `96e06e84c61bcdd3cc0f5c39785149b3059aeef280fc17efd0bed30040885934` |
| Code-Hashes | Labor `435020e128b3` · Bot `bfe06cff` · Chart-Leser `c5ca9efa1343` · bt `61750fbbc22e` |
| Daten | Lerntopf 01.10.2020–29.09.2023 (J1, J2, J3). IEX 15 Min und Tageskerzen, SIP 1 Min, alles split-bereinigt; geladen am 19./20.10.2026 (9.947 Abrufe), SIP-Vorlauf 01.–30.09.2020 nur zum Zurückschauen am 21.10.2026 (168 Abrufe). Der Prüftopf (ab 01.10.2023) ist zu. |
| Kandidaten | 115 (15 Min, 23 Muster × H0–H4) |

**Zwischenstand 15 Min:** Top 10, Flop 10 und die Latte gelten hier nur unter diesen Kandidaten. Die endgültigen Top 10 von Lauf 1 kommen nach dem Lauf auf 5 Min aus allen 230 Kandidaten (Vorab-Datei Fassung 3, Abschnitt 8).

## 1. Vorbehalte

**Überlebensverzerrung:** Die Liste der 150 Werte stammt von heute. Werte, die 2020–2023 groß waren und heute fehlen (Übernahmen, Abstiege, Pleiten), sind nicht dabei. Das macht alle Ergebnisse eher zu gut, besonders bei Long-Mustern.

**Ohne Quotes:** Bei M001–M010 (Filter des Bots) handelt das Labor Setups, die live an Spread oder Kursalter scheitern würden. Gemessen in der Gegenprobe J3 an M001 und M003: 1.446 von 8.802 Setups (16 %) scheiterten im Replay daran (Spread 1.022, Kursalter 424); davon handelt das Labor 971 (11 % aller Setups), die übrigen lässt es aus anderen Gründen aus (Anti-Chase, Chance-Risiko, 1 Signal je Tag, fehlende Minute). Dort ist der Spread größer als im Kostenmodell, die Ergebnisse dieser Muster sind also eher etwas zu gut.

**Fehlende Werte:**

- 15 Min: 150 Werte gerechnet; ohne Kerzen im Lerntopf: keiner; mit Setups an weniger als 50 Tagen: keiner.

**Weitere Hinweise:**

- Ein Gewinner auf 5 Min bräuchte live Echtzeitdaten von SIP oder einen Zusatztest auf IEX-Kerzen.
- Für M001–M007 auf 15 Min sind die Jahre 2024–2026 aus den Jahresrunden schon bekannt.
- M017 und M018 feuern auch auf trendlosem Rauschen (ihr Trend kommt nur aus EMA20/EMA50, Pflichttest 20.10.).
- H4 ohne nachgebaute Entstehungsdauer (nicht gerechnet): 0 Signale.

**Zur Auswertung (Diagnose, nur Information, ändert keine Einstufung):**

*Kosten-Ausreißer.* Für M011–M023 gibt es keinen Mindest-Stop (Vorab-Datei, Abschnitt 6). Liegt der Stop fast auf dem Einstieg, werden die Kosten je Aktie durch einen winzigen Stop-Abstand geteilt, und ein einzelner Trade kostet Tausende oder Billionen R. Dann bestimmt dieser eine Trade den Erwartungswert nach Kosten. Nach den Regeln ist das richtig gerechnet; die Spalte „ohne Ausreißer“ zeigt nur, wie der Rest aussieht.

| Kandidat (H0) | Trades | davon Kosten über 1R | größte Kosten | kleinster Stop-Abstand | EV nach Kosten | EV ohne Ausreißer (nur Info) |
|---|---|---|---|---|---|---|
| M008-15m-H0 | 507 | 1 | 1.5R | 0.0265 % | -0.116 | -0.114 |
| M011-15m-H0 | 5722 | 10 | 6.9R | 0.0058 % | -0.085 | -0.082 |
| M012-15m-H0 | 5675 | 18 | 3.2e+12R | 0.0000 % | -556154874.794 | -0.094 |
| M013-15m-H0 | 13497 | 43 | 18.3R | 0.0022 % | -0.090 | -0.088 |
| M014-15m-H0 | 14618 | 45 | 3.5e+12R | 0.0000 % | -454657761.102 | -0.108 |
| M015-15m-H0 | 7850 | 122 | 693.2R | 0.0001 % | -0.164 | -0.162 |
| M016-15m-H0 | 7176 | 116 | 181.0R | 0.0003 % | -0.203 | -0.138 |
| M017-15m-H0 | 5056 | 5 | 16.5R | 0.0024 % | -0.103 | -0.097 |
| M018-15m-H0 | 35365 | 24 | 2.6e+12R | 0.0000 % | -72523681.343 | -0.083 |
| M019-15m-H0 | 2493 | 2 | 1.5R | 0.0273 % | -0.073 | -0.071 |
| M020-15m-H0 | 2515 | 4 | 6.6R | 0.0060 % | -0.103 | -0.095 |

Dieselben Trades stecken in allen 5 Varianten eines Musters (44 weitere Varianten betroffen).

*Zufall in derselben Richtung.* Die Zufallsminute liegt laut Vorab-Datei irgendwo in derselben Stunde, also auch vor dem echten Einstieg. Die Richtung kommt vom echten Signal, das den Ausbruch schon gesehen hat. Zufalls-Einstiege vor dem echten Einstieg nehmen diesen Ausbruch mit; der Vergleich schaut damit zum Teil in die Zukunft und ist für die echten Trades unfair. Die Regel bleibt für Lauf 1, wie sie ist. Gemessen (Variante H0, jede 3. Minute der Stunde, ohne Kosten-Ausreißer):

| Kandidat | echt, nach Kosten | Zufall vor dem echten Einstieg | Zufall ab dem echten Einstieg |
|---|---|---|---|
| M021-15m-H0 | -0.035 | +0.082 (4277) | -0.029 (5384) |
| M007-15m-H0 | -0.039 | +0.146 (5813) | -0.020 (6994) |
| M003-15m-H0 | -0.043 | +0.137 (28867) | -0.034 (34622) |

## 2. Signale je Muster und Jahr

Alle 5 Varianten eines Musters handeln dieselben Signale. „Signale“ = Einstiege nach allen Filtern (höchstens 1 je Muster, Aktie und Tag); daneben die häufigsten Gründe, aus denen ein Setup nicht gehandelt wurde.

| Muster | Zeitebene | J1 | J2 | J3 | gesamt | nicht gehandelt (häufigste Gründe) |
|---|---|---|---|---|---|---|
| M001 | 15 Min | 456 | 201 | 256 | 913 | skip-chase 562, skip-rs 526, skip-rr 239 |
| M002 | 15 Min | 121 | 242 | 170 | 533 | skip-rs 287, skip-chase 276, skip-rr 109 |
| M003 | 15 Min | 1451 | 1154 | 1152 | 3757 | skip-chase 1999, skip-rs 945, skip-rr 381 |
| M004 | 15 Min | 39 | 45 | 42 | 126 | skip-rr 1024, skip-chase 718, skip-rs 618, skip-market 180 |
| M005 | 15 Min | 62 | 51 | 68 | 181 | skip-rr 994, skip-rs 765, skip-chase 690 |
| M006 | 15 Min | 265 | 221 | 220 | 706 | skip-chase 439, skip-rs 285, skip-rr 212 |
| M007 | 15 Min | 293 | 227 | 245 | 765 | skip-chase 442, skip-rs 374, skip-rr 246 |
| M008 | 15 Min | 213 | 129 | 165 | 507 | skip-steckbrief 2900, skip-rs 399, skip-rr-schluss 200 |
| M009 | 15 Min | 86 | 128 | 102 | 316 | skip-steckbrief 2487, skip-rs 286, skip-rr-schluss 127 |
| M010 | 15 Min | 4 | 3 | 4 | 11 | skip-steckbrief 6464, skip-rr-schluss 218, skip-chase 32, skip-rr 23 |
| M011 | 15 Min | 1931 | 1925 | 1866 | 5722 | skip-geometry 288, skip-tag 121, skip-daten 114 |
| M012 | 15 Min | 2032 | 1818 | 1825 | 5675 | skip-geometry 247, skip-tag 101, skip-daten 96 |
| M013 | 15 Min | 4569 | 4737 | 4191 | 13497 | skip-tag 930, skip-geometry 524, skip-daten 204 |
| M014 | 15 Min | 5188 | 4398 | 5032 | 14618 | skip-tag 1004, skip-geometry 518, skip-daten 246 |
| M015 | 15 Min | 2727 | 2517 | 2606 | 7850 | skip-tag 2028, skip-daten 183, skip-geometry 127 |
| M016 | 15 Min | 2341 | 2471 | 2364 | 7176 | skip-tag 1836, skip-geometry 135, skip-daten 126 |
| M017 | 15 Min | 1603 | 1747 | 1706 | 5056 | skip-geometry 219, skip-daten 128, skip-tag 85 |
| M018 | 15 Min | 11853 | 11851 | 11661 | 35365 | skip-tag 8265, skip-geometry 4123, skip-daten 946 |
| M019 | 15 Min | 830 | 879 | 784 | 2493 | skip-geometry 174, skip-daten 70, skip-tag 22 |
| M020 | 15 Min | 857 | 801 | 857 | 2515 | skip-geometry 95, skip-daten 60, skip-tag 21 |
| M021 | 15 Min | 175 | 196 | 196 | 567 | skip-geometry 13, skip-daten 7, skip-tag 1 |
| M022 | 15 Min | 228 | 182 | 214 | 624 | skip-geometry 26, skip-daten 21, skip-tag 1 |
| M023 | 15 Min | 569 | 442 | 519 | 1530 | skip-daten 52, skip-tag 34, skip-geometry 8 |

**Zu wenig Daten** (in mindestens einem Jahr unter 30 Trades; das ist nicht „durchgefallen“): 5 von 115 Kandidaten.

- M010-15m: H0, H1, H2, H3, H4

## 3. Rangliste aller 115 Kandidaten

Sortiert nach dem schwächsten der drei Jahre (Erwartungswert nach Kosten); Kandidaten mit einem Jahr ohne Trades stehen unten. EV in R je Trade. Ausgänge: Z Ziel, S Anfangsstop, NS nachgezogener Stop, ZS Zeit-Stop, TE Tagesende, HD Ende der Haltedauer, DE Datenende. Max. DD: größter Rückgang Trade für Trade in R.

| Rang | Kandidat | Einstufung | J1 Trades / EV | J2 Trades / EV | J3 Trades / EV | schwächstes Jahr | gesamt Trades | EV nach Kosten | EV vor Kosten | Kostenstress | PF | Treffer | max. DD (R) | Ausgänge |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | M010-15m-H2 | zu wenig Daten | 4 / +0.114 | 3 / +0.098 | 4 / +0.035 | +0.035 | 11 | +0.081 | +0.112 | +0.051 | 3.42 | 73 % | 0.2 | ZS 8 · TE 3 |
| 2 | M010-15m-H0 | zu wenig Daten | 4 / +0.114 | 3 / +0.098 | 4 / +0.035 | +0.035 | 11 | +0.081 | +0.112 | +0.051 | 3.42 | 73 % | 0.2 | ZS 8 · TE 3 |
| 3 | M021-15m-H0 | Stufe 0, nicht bestanden | 175 / -0.028 | 196 / -0.043 | 196 / -0.034 | -0.043 | 567 | -0.035 | -0.002 | -0.065 | 0.79 | 47 % | 22.6 | Z 74 · S 14 · ZS 403 · TE 76 |
| 4 | M007-15m-H0 | Stufe 0, nicht bestanden | 293 / -0.036 | 227 / -0.037 | 245 / -0.045 | -0.045 | 765 | -0.039 | +0.005 | -0.069 | 0.82 | 48 % | 34.2 | Z 18 · S 68 · NS 41 · ZS 396 · TE 242 |
| 5 | M003-15m-H2 | Stufe 0, nicht bestanden | 1451 / -0.049 | 1154 / -0.042 | 1152 / -0.030 | -0.049 | 3757 | -0.041 | -0.002 | -0.071 | 0.79 | 47 % | 155.5 | Z 640 · S 188 · NS 35 · ZS 2170 · TE 724 |
| 6 | M022-15m-H1 | Stufe 0, nicht bestanden | 228 / -0.050 | 182 / -0.050 | 214 / -0.003 | -0.050 | 624 | -0.034 | +0.017 | -0.064 | 0.83 | 48 % | 28.3 | Z 127 · S 37 · NS 16 · TE 444 |
| 7 | M022-15m-H4 | Stufe 0, nicht bestanden | 228 / -0.050 | 182 / -0.051 | 214 / -0.003 | -0.051 | 624 | -0.034 | +0.017 | -0.064 | 0.83 | 47 % | 28.6 | Z 127 · S 37 · NS 16 · ZS 8 · TE 436 |
| 8 | M003-15m-H1 | Stufe 0, nicht bestanden | 1451 / -0.053 | 1154 / -0.038 | 1152 / -0.034 | -0.053 | 3757 | -0.042 | -0.003 | -0.072 | 0.82 | 45 % | 159.8 | Z 140 · S 405 · NS 245 · TE 2967 |
| 9 | M003-15m-H4 | Stufe 0, nicht bestanden | 1451 / -0.053 | 1154 / -0.038 | 1152 / -0.033 | -0.053 | 3757 | -0.042 | -0.003 | -0.072 | 0.82 | 45 % | 160.1 | Z 140 · S 404 · NS 244 · ZS 44 · TE 2925 |
| 10 | M022-15m-H2 | Stufe 0, nicht bestanden | 228 / -0.048 | 182 / -0.056 | 214 / -0.039 | -0.056 | 624 | -0.047 | +0.003 | -0.077 | 0.66 | 46 % | 31.8 | Z 277 · S 6 · NS 1 · ZS 277 · TE 63 |
| 11 | M003-15m-H0 | Stufe 0, nicht bestanden | 1451 / -0.056 | 1154 / -0.049 | 1152 / -0.021 | -0.056 | 3757 | -0.043 | -0.004 | -0.073 | 0.78 | 45 % | 162.6 | Z 74 · S 191 · NS 88 · ZS 2646 · TE 758 |
| 12 | M009-15m-H4 | Stufe 0, nicht bestanden | 86 / -0.057 | 128 / -0.008 | 102 / +0.000 | -0.057 | 316 | -0.019 | +0.028 | -0.049 | 0.93 | 47 % | 19.3 | Z 4 · S 40 · NS 42 · TE 230 |
| 13 | M009-15m-H1 | Stufe 0, nicht bestanden | 86 / -0.057 | 128 / -0.008 | 102 / +0.000 | -0.057 | 316 | -0.019 | +0.028 | -0.049 | 0.93 | 47 % | 19.3 | Z 4 · S 40 · NS 42 · TE 230 |
| 14 | M022-15m-H0 | Stufe 0, nicht bestanden | 228 / -0.058 | 182 / -0.046 | 214 / -0.035 | -0.058 | 624 | -0.047 | +0.004 | -0.077 | 0.72 | 43 % | 33.7 | Z 84 · S 8 · NS 3 · ZS 449 · TE 80 |
| 15 | M005-15m-H1 | Stufe 0, nicht bestanden | 62 / -0.024 | 51 / -0.039 | 68 / -0.061 | -0.061 | 181 | -0.042 | -0.012 | -0.072 | 0.65 | 45 % | 8.5 | Z 2 · S 2 · TE 177 |
| 16 | M021-15m-H2 | Stufe 0, nicht bestanden | 175 / -0.048 | 196 / -0.061 | 196 / -0.027 | -0.061 | 567 | -0.045 | -0.012 | -0.075 | 0.68 | 46 % | 26.8 | Z 223 · S 13 · ZS 271 · TE 60 |
| 17 | M004-15m-H2 | Stufe 0, nicht bestanden | 39 / -0.013 | 45 / -0.045 | 42 / -0.061 | -0.061 | 126 | -0.040 | +0.010 | -0.070 | 0.64 | 44 % | 6.1 | Z 9 · S 1 · ZS 52 · TE 64 |
| 18 | M005-15m-H4 | Stufe 0, nicht bestanden | 62 / -0.038 | 51 / -0.042 | 68 / -0.062 | -0.062 | 181 | -0.048 | -0.018 | -0.078 | 0.60 | 44 % | 9.3 | Z 2 · S 2 · ZS 20 · TE 157 |
| 19 | M005-15m-H2 | Stufe 0, nicht bestanden | 62 / -0.062 | 51 / -0.016 | 68 / -0.053 | -0.062 | 181 | -0.046 | -0.016 | -0.076 | 0.59 | 41 % | 9.5 | Z 11 · S 1 · ZS 73 · TE 96 |
| 20 | M023-15m-H0 | Stufe 0, nicht bestanden | 569 / -0.063 | 442 / -0.043 | 519 / -0.016 | -0.063 | 1530 | -0.041 | +0.007 | -0.071 | 0.83 | 49 % | 88.6 | Z 34 · S 149 · NS 90 · ZS 1049 · TE 208 |
| 21 | M005-15m-H0 | Stufe 0, nicht bestanden | 62 / -0.063 | 51 / -0.020 | 68 / -0.059 | -0.063 | 181 | -0.050 | -0.019 | -0.080 | 0.55 | 41 % | 9.8 | S 1 · ZS 82 · TE 98 |
| 22 | M002-15m-H2 | Stufe 0, nicht bestanden | 121 / -0.064 | 242 / +0.020 | 170 / -0.057 | -0.064 | 533 | -0.023 | +0.036 | -0.053 | 0.90 | 51 % | 18.7 | Z 126 · S 49 · NS 29 · ZS 151 · TE 178 |
| 23 | M003-15m-H3 | Stufe 0, nicht bestanden | 1451 / -0.052 | 1154 / -0.049 | 1152 / -0.065 | -0.065 | 3757 | -0.055 | -0.015 | -0.085 | 0.87 | 41 % | 215.2 | Z 777 · S 1358 · NS 1170 · HD 452 |
| 24 | M009-15m-H0 | Stufe 0, nicht bestanden | 86 / -0.066 | 128 / -0.025 | 102 / -0.023 | -0.066 | 316 | -0.035 | +0.012 | -0.065 | 0.85 | 48 % | 16.9 | Z 2 · S 29 · NS 24 · ZS 204 · TE 57 |
| 25 | M007-15m-H4 | Stufe 0, nicht bestanden | 293 / -0.060 | 227 / -0.052 | 245 / -0.069 | -0.069 | 765 | -0.061 | -0.016 | -0.091 | 0.77 | 48 % | 46.4 | Z 29 · S 109 · NS 74 · ZS 3 · TE 550 |
| 26 | M007-15m-H1 | Stufe 0, nicht bestanden | 293 / -0.060 | 227 / -0.052 | 245 / -0.069 | -0.069 | 765 | -0.060 | -0.016 | -0.090 | 0.77 | 48 % | 46.3 | Z 29 · S 109 · NS 74 · TE 553 |
| 27 | M023-15m-H2 | Stufe 0, nicht bestanden | 569 / -0.071 | 442 / -0.047 | 519 / -0.040 | -0.071 | 1530 | -0.053 | -0.005 | -0.083 | 0.78 | 49 % | 97.9 | Z 187 · S 148 · NS 87 · ZS 911 · TE 197 |
| 28 | M004-15m-H0 | Stufe 0, nicht bestanden | 39 / -0.017 | 45 / -0.046 | 42 / -0.072 | -0.072 | 126 | -0.045 | +0.005 | -0.075 | 0.60 | 44 % | 6.7 | Z 1 · S 1 · ZS 57 · TE 67 |
| 29 | M007-15m-H2 | Stufe 0, nicht bestanden | 293 / -0.022 | 227 / -0.031 | 245 / -0.072 | -0.072 | 765 | -0.041 | +0.003 | -0.071 | 0.81 | 50 % | 34.0 | Z 147 · S 67 · NS 20 · ZS 313 · TE 218 |
| 30 | M007-15m-H3 | Stufe 0, nicht bestanden | 293 / -0.052 | 227 / -0.034 | 245 / -0.073 | -0.073 | 765 | -0.054 | -0.010 | -0.084 | 0.88 | 47 % | 49.1 | Z 166 · S 282 · NS 271 · HD 46 |
| 31 | M019-15m-H1 | Stufe 0, nicht bestanden | 830 / -0.068 | 879 / -0.058 | 784 / -0.079 | -0.079 | 2493 | -0.068 | +0.022 | -0.098 | 0.82 | 54 % | 193.9 | Z 420 · S 771 · NS 720 · TE 582 |
| 32 | M005-15m-H3 | Stufe 0, nicht bestanden | 62 / +0.033 | 51 / +0.037 | 68 / -0.080 | -0.080 | 181 | -0.008 | +0.022 | -0.038 | 0.97 | 46 % | 10.9 | Z 50 · S 42 · NS 23 · HD 66 |
| 33 | M021-15m-H1 | Stufe 0, nicht bestanden | 175 / -0.028 | 196 / -0.070 | 196 / -0.081 | -0.081 | 567 | -0.061 | -0.028 | -0.091 | 0.72 | 49 % | 38.2 | Z 100 · S 44 · NS 13 · TE 410 |
| 34 | M021-15m-H4 | Stufe 0, nicht bestanden | 175 / -0.029 | 196 / -0.070 | 196 / -0.081 | -0.081 | 567 | -0.061 | -0.028 | -0.091 | 0.72 | 49 % | 38.4 | Z 100 · S 44 · NS 13 · ZS 4 · TE 406 |
| 35 | M019-15m-H0 | Stufe 0, nicht bestanden | 830 / -0.076 | 879 / -0.062 | 784 / -0.082 | -0.082 | 2493 | -0.073 | +0.017 | -0.103 | 0.80 | 53 % | 207.4 | Z 336 · S 653 · NS 569 · ZS 695 · TE 240 |
| 36 | M001-15m-H0 | Stufe 0, nicht bestanden | 456 / -0.082 | 201 / -0.053 | 256 / -0.072 | -0.082 | 913 | -0.073 | -0.020 | -0.103 | 0.72 | 44 % | 67.8 | Z 27 · S 103 · NS 58 · ZS 395 · TE 330 |
| 37 | M006-15m-H4 | Stufe 0, nicht bestanden | 265 / -0.056 | 221 / -0.084 | 220 / -0.056 | -0.084 | 706 | -0.065 | -0.009 | -0.095 | 0.76 | 43 % | 51.2 | Z 27 · S 93 · NS 70 · ZS 5 · TE 511 |
| 38 | M006-15m-H1 | Stufe 0, nicht bestanden | 265 / -0.055 | 221 / -0.084 | 220 / -0.057 | -0.084 | 706 | -0.065 | -0.009 | -0.095 | 0.76 | 43 % | 51.7 | Z 28 · S 94 · NS 70 · TE 514 |
| 39 | M006-15m-H2 | Stufe 0, nicht bestanden | 265 / -0.041 | 221 / -0.085 | 220 / -0.054 | -0.085 | 706 | -0.059 | -0.004 | -0.089 | 0.74 | 46 % | 43.6 | Z 136 · S 57 · NS 26 · ZS 256 · TE 231 |
| 40 | M001-15m-H2 | Stufe 0, nicht bestanden | 456 / -0.086 | 201 / -0.056 | 256 / -0.073 | -0.086 | 913 | -0.076 | -0.022 | -0.106 | 0.70 | 46 % | 71.0 | Z 181 · S 101 · NS 32 · ZS 298 · TE 301 |
| 41 | M002-15m-H1 | Stufe 0, nicht bestanden | 121 / -0.077 | 242 / +0.123 | 170 / -0.087 | -0.087 | 533 | +0.011 | +0.070 | -0.019 | 1.04 | 48 % | 23.1 | Z 33 · S 67 · NS 82 · TE 351 |
| 42 | M006-15m-H0 | Stufe 0, nicht bestanden | 265 / -0.045 | 221 / -0.091 | 220 / -0.062 | -0.091 | 706 | -0.064 | -0.009 | -0.094 | 0.72 | 44 % | 47.7 | Z 16 · S 58 · NS 41 · ZS 339 · TE 252 |
| 43 | M001-15m-H1 | Stufe 0, nicht bestanden | 456 / -0.089 | 201 / -0.013 | 256 / -0.092 | -0.092 | 913 | -0.073 | -0.020 | -0.103 | 0.75 | 46 % | 67.7 | Z 44 · S 140 · NS 107 · TE 622 |
| 44 | M001-15m-H4 | Stufe 0, nicht bestanden | 456 / -0.089 | 201 / -0.012 | 256 / -0.093 | -0.093 | 913 | -0.073 | -0.020 | -0.103 | 0.75 | 46 % | 67.7 | Z 44 · S 140 · NS 105 · ZS 29 · TE 595 |
| 45 | M009-15m-H2 | Stufe 0, nicht bestanden | 86 / -0.093 | 128 / -0.027 | 102 / -0.030 | -0.093 | 316 | -0.046 | +0.002 | -0.076 | 0.80 | 49 % | 19.1 | Z 40 · S 29 · NS 24 · ZS 171 · TE 52 |
| 46 | M023-15m-H4 | Stufe 0, nicht bestanden | 569 / -0.093 | 442 / +0.021 | 519 / -0.025 | -0.093 | 1530 | -0.037 | +0.012 | -0.067 | 0.87 | 51 % | 73.6 | Z 53 · S 250 · NS 195 · TE 1032 |
| 47 | M023-15m-H1 | Stufe 0, nicht bestanden | 569 / -0.093 | 442 / +0.021 | 519 / -0.025 | -0.093 | 1530 | -0.037 | +0.012 | -0.067 | 0.87 | 51 % | 73.6 | Z 53 · S 250 · NS 195 · TE 1032 |
| 48 | M019-15m-H2 | Stufe 0, nicht bestanden | 830 / -0.094 | 879 / -0.028 | 784 / -0.092 | -0.094 | 2493 | -0.070 | +0.019 | -0.100 | 0.79 | 55 % | 192.1 | Z 789 · S 631 · NS 443 · ZS 464 · TE 166 |
| 49 | M019-15m-H4 | Stufe 0, nicht bestanden | 830 / -0.071 | 879 / -0.071 | 784 / -0.094 | -0.094 | 2493 | -0.078 | +0.011 | -0.108 | 0.79 | 52 % | 220.0 | Z 336 · S 675 · NS 604 · ZS 545 · TE 333 |
| 50 | M002-15m-H0 | Stufe 0, nicht bestanden | 121 / -0.095 | 242 / +0.062 | 170 / -0.069 | -0.095 | 533 | -0.016 | +0.044 | -0.046 | 0.93 | 48 % | 21.9 | Z 22 · S 50 · NS 54 · ZS 203 · TE 204 |
| 51 | M002-15m-H4 | Stufe 0, nicht bestanden | 121 / -0.075 | 242 / +0.124 | 170 / -0.096 | -0.096 | 533 | +0.008 | +0.068 | -0.022 | 1.04 | 48 % | 24.1 | Z 32 · S 67 · NS 81 · ZS 16 · TE 337 |
| 52 | M019-15m-H3 | Stufe 0, nicht bestanden | 830 / -0.093 | 879 / -0.025 | 784 / -0.097 | -0.097 | 2493 | -0.071 | +0.019 | -0.101 | 0.84 | 53 % | 209.5 | Z 569 · S 939 · NS 982 · HD 3 |
| 53 | M013-15m-H2 | Stufe 0, nicht bestanden | 4569 / -0.109 | 4737 / -0.048 | 4191 / -0.104 | -0.109 | 13497 | -0.086 | +0.027 | -0.116 | 0.78 | 54 % | 1166.1 | Z 3449 · S 4007 · NS 3232 · ZS 2046 · TE 763 |
| 54 | M011-15m-H4 | Stufe 0, nicht bestanden | 1931 / -0.110 | 1925 / -0.039 | 1866 / -0.097 | -0.110 | 5722 | -0.082 | +0.017 | -0.112 | 0.78 | 52 % | 473.6 | Z 658 · S 1568 · NS 1482 · ZS 1355 · TE 659 |
| 55 | M004-15m-H4 | Stufe 0, nicht bestanden | 39 / +0.013 | 45 / -0.060 | 42 / -0.112 | -0.112 | 126 | -0.055 | -0.005 | -0.085 | 0.58 | 40 % | 7.9 | Z 1 · S 2 · ZS 8 · TE 115 |
| 56 | M011-15m-H3 | Stufe 0, nicht bestanden | 1931 / -0.102 | 1925 / -0.019 | 1866 / -0.112 | -0.112 | 5722 | -0.078 | +0.022 | -0.108 | 0.83 | 54 % | 456.7 | Z 1170 · S 2175 · NS 2365 · HD 12 |
| 57 | M013-15m-H0 | Stufe 0, nicht bestanden | 4569 / -0.114 | 4737 / -0.056 | 4191 / -0.101 | -0.114 | 13497 | -0.090 | +0.024 | -0.120 | 0.78 | 53 % | 1215.3 | Z 1402 · S 4093 · NS 4011 · ZS 2983 · TE 1008 |
| 58 | M011-15m-H1 | Stufe 0, nicht bestanden | 1931 / -0.114 | 1925 / -0.029 | 1866 / -0.085 | -0.114 | 5722 | -0.076 | +0.023 | -0.106 | 0.81 | 55 % | 439.2 | Z 864 · S 1830 · NS 1798 · TE 1230 |
| 59 | M013-15m-H4 | Stufe 0, nicht bestanden | 4569 / -0.115 | 4737 / -0.061 | 4191 / -0.098 | -0.115 | 13497 | -0.091 | +0.022 | -0.121 | 0.77 | 52 % | 1235.1 | Z 1324 · S 4077 · NS 4113 · ZS 2593 · TE 1390 |
| 60 | M011-15m-H0 | Stufe 0, nicht bestanden | 1931 / -0.117 | 1925 / -0.039 | 1866 / -0.100 | -0.117 | 5722 | -0.085 | +0.014 | -0.115 | 0.77 | 53 % | 492.3 | Z 695 · S 1554 · NS 1448 · ZS 1560 · TE 465 |
| 61 | M020-15m-H2 | Stufe 0, nicht bestanden | 857 / -0.118 | 801 / -0.083 | 857 / -0.103 | -0.118 | 2515 | -0.102 | +0.004 | -0.132 | 0.73 | 53 % | 263.4 | Z 717 · S 687 · NS 487 · ZS 496 · TE 128 |
| 62 | M004-15m-H1 | Stufe 0, nicht bestanden | 39 / +0.019 | 45 / -0.049 | 42 / -0.118 | -0.118 | 126 | -0.051 | -0.001 | -0.081 | 0.61 | 40 % | 7.7 | Z 1 · S 2 · TE 123 |
| 63 | M013-15m-H1 | Stufe 0, nicht bestanden | 4569 / -0.119 | 4737 / -0.056 | 4191 / -0.103 | -0.119 | 13497 | -0.092 | +0.021 | -0.122 | 0.78 | 54 % | 1244.0 | Z 1687 · S 4597 · NS 4906 · TE 2307 |
| 64 | M020-15m-H4 | Stufe 0, nicht bestanden | 857 / -0.121 | 801 / -0.096 | 857 / -0.095 | -0.121 | 2515 | -0.104 | +0.001 | -0.134 | 0.73 | 51 % | 267.3 | Z 308 · S 702 · NS 672 · ZS 578 · TE 255 |
| 65 | M020-15m-H0 | Stufe 0, nicht bestanden | 857 / -0.127 | 801 / -0.089 | 857 / -0.092 | -0.127 | 2515 | -0.103 | +0.003 | -0.133 | 0.74 | 51 % | 262.9 | Z 335 · S 710 · NS 623 · ZS 687 · TE 160 |
| 66 | M011-15m-H2 | Stufe 0, nicht bestanden | 1931 / -0.127 | 1925 / -0.046 | 1866 / -0.104 | -0.127 | 5722 | -0.092 | +0.007 | -0.122 | 0.74 | 51 % | 529.2 | Z 1967 · S 1476 · NS 1056 · ZS 883 · TE 340 |
| 67 | M010-15m-H4 | zu wenig Daten | 4 / +0.110 | 3 / +0.094 | 4 / -0.128 | -0.128 | 11 | +0.019 | +0.050 | -0.011 | 1.22 | 73 % | 0.9 | TE 11 |
| 68 | M010-15m-H1 | zu wenig Daten | 4 / +0.110 | 3 / +0.094 | 4 / -0.128 | -0.128 | 11 | +0.019 | +0.050 | -0.011 | 1.22 | 73 % | 0.9 | TE 11 |
| 69 | M013-15m-H3 | Stufe 0, nicht bestanden | 4569 / -0.125 | 4737 / -0.072 | 4191 / -0.128 | -0.128 | 13497 | -0.107 | +0.006 | -0.137 | 0.77 | 53 % | 1449.2 | Z 2152 · S 5225 · NS 6108 · HD 12 |
| 70 | M023-15m-H3 | Stufe 0, nicht bestanden | 569 / -0.129 | 442 / -0.025 | 519 / -0.021 | -0.129 | 1530 | -0.062 | -0.013 | -0.092 | 0.86 | 50 % | 134.0 | Z 169 · S 561 · NS 715 · HD 85 |
| 71 | M020-15m-H1 | Stufe 0, nicht bestanden | 857 / -0.129 | 801 / -0.076 | 857 / -0.099 | -0.129 | 2515 | -0.102 | +0.004 | -0.132 | 0.75 | 53 % | 262.4 | Z 394 · S 841 · NS 818 · TE 462 |
| 72 | M001-15m-H3 | Stufe 0, nicht bestanden | 456 / -0.119 | 201 / -0.023 | 256 / -0.148 | -0.148 | 913 | -0.106 | -0.052 | -0.136 | 0.79 | 47 % | 98.3 | Z 193 · S 353 · NS 333 · HD 34 |
| 73 | M017-15m-H2 | Stufe 0, nicht bestanden | 1603 / -0.126 | 1747 / -0.027 | 1706 / -0.153 | -0.153 | 5056 | -0.101 | -0.012 | -0.131 | 0.68 | 48 % | 511.1 | Z 1322 · S 911 · NS 557 · ZS 1143 · TE 1123 |
| 74 | M017-15m-H0 | Stufe 0, nicht bestanden | 1603 / -0.124 | 1747 / -0.034 | 1706 / -0.153 | -0.153 | 5056 | -0.103 | -0.014 | -0.133 | 0.69 | 49 % | 523.9 | Z 368 · S 965 · NS 746 · ZS 1548 · TE 1429 |
| 75 | M020-15m-H3 | Stufe 0, nicht bestanden | 857 / -0.157 | 801 / -0.076 | 857 / -0.145 | -0.157 | 2515 | -0.127 | -0.021 | -0.157 | 0.73 | 52 % | 325.2 | Z 500 · S 975 · NS 1037 · HD 3 |
| 76 | M022-15m-H3 | Stufe 0, nicht bestanden | 228 / -0.161 | 182 / -0.021 | 214 / +0.034 | -0.161 | 624 | -0.053 | -0.003 | -0.083 | 0.86 | 50 % | 52.9 | Z 302 · S 193 · NS 71 · HD 58 |
| 77 | M017-15m-H4 | Stufe 0, nicht bestanden | 1603 / -0.124 | 1747 / -0.031 | 1706 / -0.164 | -0.164 | 5056 | -0.105 | -0.017 | -0.135 | 0.70 | 49 % | 533.6 | Z 432 · S 1144 · NS 951 · ZS 379 · TE 2150 |
| 78 | M017-15m-H1 | Stufe 0, nicht bestanden | 1603 / -0.119 | 1747 / -0.032 | 1706 / -0.166 | -0.166 | 5056 | -0.105 | -0.017 | -0.135 | 0.71 | 49 % | 532.7 | Z 445 · S 1188 · NS 976 · TE 2447 |
| 79 | M008-15m-H4 | Stufe 0, nicht bestanden | 213 / -0.170 | 129 / -0.134 | 165 / -0.030 | -0.170 | 507 | -0.115 | -0.054 | -0.145 | 0.64 | 45 % | 69.5 | Z 6 · S 97 · NS 76 · TE 328 |
| 80 | M008-15m-H1 | Stufe 0, nicht bestanden | 213 / -0.170 | 129 / -0.134 | 165 / -0.030 | -0.170 | 507 | -0.115 | -0.054 | -0.145 | 0.64 | 45 % | 69.5 | Z 6 · S 97 · NS 76 · TE 328 |
| 81 | M008-15m-H2 | Stufe 0, nicht bestanden | 213 / -0.172 | 129 / -0.121 | 165 / -0.001 | -0.172 | 507 | -0.103 | -0.041 | -0.133 | 0.62 | 45 % | 59.6 | Z 43 · S 67 · NS 36 · ZS 267 · TE 94 |
| 82 | M009-15m-H3 | Stufe 0, nicht bestanden | 86 / +0.015 | 128 / -0.175 | 102 / -0.166 | -0.175 | 316 | -0.120 | -0.073 | -0.150 | 0.74 | 45 % | 51.6 | Z 32 · S 117 · NS 121 · HD 46 |
| 83 | M021-15m-H3 | Stufe 0, nicht bestanden | 175 / +0.064 | 196 / -0.187 | 196 / -0.112 | -0.187 | 567 | -0.084 | -0.051 | -0.114 | 0.79 | 52 % | 65.3 | Z 255 · S 190 · NS 53 · HD 69 |
| 84 | M008-15m-H0 | Stufe 0, nicht bestanden | 213 / -0.190 | 129 / -0.134 | 165 / -0.007 | -0.190 | 507 | -0.116 | -0.055 | -0.146 | 0.58 | 43 % | 66.9 | Z 1 · S 67 · NS 44 · ZS 298 · TE 97 |
| 85 | M006-15m-H3 | Stufe 0, nicht bestanden | 265 / -0.168 | 221 / -0.196 | 220 / -0.020 | -0.196 | 706 | -0.131 | -0.075 | -0.161 | 0.73 | 33 % | 107.5 | Z 146 · S 288 · NS 244 · HD 28 |
| 86 | M015-15m-H2 | Stufe 0, nicht bestanden | 2727 / -0.098 | 2517 / -0.219 | 2606 / -0.177 | -0.219 | 7850 | -0.163 | +0.137 | -0.193 | 0.67 | 51 % | 1280.7 | Z 529 · S 2762 · NS 2882 · ZS 1188 · TE 489 |
| 87 | M015-15m-H0 | Stufe 0, nicht bestanden | 2727 / -0.101 | 2517 / -0.221 | 2606 / -0.176 | -0.221 | 7850 | -0.164 | +0.135 | -0.194 | 0.67 | 51 % | 1293.7 | Z 63 · S 2766 · NS 3050 · ZS 1413 · TE 558 |
| 88 | M015-15m-H4 | Stufe 0, nicht bestanden | 2727 / -0.112 | 2517 / -0.222 | 2606 / -0.166 | -0.222 | 7850 | -0.165 | +0.134 | -0.195 | 0.68 | 52 % | 1299.6 | Z 72 · S 2889 · NS 3390 · ZS 458 · TE 1041 |
| 89 | M015-15m-H1 | Stufe 0, nicht bestanden | 2727 / -0.108 | 2517 / -0.226 | 2606 / -0.165 | -0.226 | 7850 | -0.165 | +0.135 | -0.195 | 0.68 | 52 % | 1294.9 | Z 75 · S 2931 · NS 3499 · TE 1345 |
| 90 | M017-15m-H3 | Stufe 0, nicht bestanden | 1603 / -0.188 | 1747 / -0.080 | 1706 / -0.243 | -0.243 | 5056 | -0.169 | -0.081 | -0.199 | 0.68 | 47 % | 863.3 | Z 966 · S 2010 · NS 2065 · HD 15 |
| 91 | M015-15m-H3 | Stufe 0, nicht bestanden | 2727 / -0.148 | 2517 / -0.274 | 2606 / -0.195 | -0.274 | 7850 | -0.204 | +0.096 | -0.234 | 0.64 | 51 % | 1603.4 | Z 190 · S 3233 · NS 4426 · HD 1 |
| 92 | M002-15m-H3 | Stufe 0, nicht bestanden | 121 / -0.234 | 242 / +0.098 | 170 / -0.293 | -0.293 | 533 | -0.102 | -0.042 | -0.132 | 0.79 | 37 % | 71.8 | Z 122 · S 203 · NS 200 · HD 8 |
| 93 | M016-15m-H4 | Stufe 0, nicht bestanden | 2341 / -0.167 | 2471 / -0.155 | 2364 / -0.296 | -0.296 | 7176 | -0.205 | +0.026 | -0.235 | 0.61 | 51 % | 1542.0 | Z 74 · S 2699 · NS 3148 · ZS 385 · TE 870 |
| 94 | M016-15m-H1 | Stufe 0, nicht bestanden | 2341 / -0.162 | 2471 / -0.152 | 2364 / -0.296 | -0.296 | 7176 | -0.203 | +0.028 | -0.233 | 0.62 | 51 % | 1524.6 | Z 82 · S 2737 · NS 3257 · TE 1100 |
| 95 | M016-15m-H2 | Stufe 0, nicht bestanden | 2341 / -0.166 | 2471 / -0.159 | 2364 / -0.297 | -0.297 | 7176 | -0.207 | +0.024 | -0.237 | 0.60 | 51 % | 1544.2 | Z 575 · S 2544 · NS 2652 · ZS 975 · TE 430 |
| 96 | M016-15m-H0 | Stufe 0, nicht bestanden | 2341 / -0.167 | 2471 / -0.145 | 2364 / -0.300 | -0.300 | 7176 | -0.203 | +0.028 | -0.233 | 0.61 | 51 % | 1523.6 | Z 61 · S 2554 · NS 2869 · ZS 1192 · TE 500 |
| 97 | M008-15m-H3 | Stufe 0, nicht bestanden | 213 / -0.314 | 129 / -0.153 | 165 / -0.150 | -0.314 | 507 | -0.219 | -0.158 | -0.249 | 0.57 | 33 % | 113.5 | Z 39 · S 216 · NS 214 · HD 38 |
| 98 | M016-15m-H3 | Stufe 0, nicht bestanden | 2341 / -0.205 | 2471 / -0.200 | 2364 / -0.326 | -0.326 | 7176 | -0.243 | -0.012 | -0.273 | 0.58 | 49 % | 1786.3 | Z 181 · S 3007 · NS 3988 |
| 99 | M004-15m-H3 | Stufe 0, nicht bestanden | 39 / -0.018 | 45 / -0.358 | 42 / -0.126 | -0.358 | 126 | -0.175 | -0.125 | -0.205 | 0.62 | 35 % | 26.2 | Z 38 · S 41 · NS 20 · HD 27 |
| 100 | M010-15m-H3 | zu wenig Daten | 4 / -0.212 | 3 / -0.487 | 4 / -0.216 | -0.487 | 11 | -0.288 | -0.257 | -0.318 | 0.32 | 45 % | 4.1 | Z 1 · S 4 · NS 1 · HD 5 |
| 101 | M018-15m-H4 | Stufe 0, nicht bestanden | 11853 / -216384036.862 | 11851 / -0.062 | 11661 / -0.076 | -216384036.862 | 35365 | -72523681.339 | +0.000 | -72523681.369 | 0.00 | 49 % | 2564799990556.2 | Z 11236 · S 3132 · NS 951 · ZS 19673 · TE 373 |
| 102 | M018-15m-H0 | Stufe 0, nicht bestanden | 11853 / -216384036.862 | 11851 / -0.070 | 11661 / -0.079 | -216384036.862 | 35365 | -72523681.343 | -0.004 | -72523681.373 | 0.00 | 56 % | 2564799990687.9 | Z 15948 · S 7090 · NS 1929 · ZS 8751 · TE 1647 |
| 103 | M018-15m-H2 | Stufe 0, nicht bestanden | 11853 / -216384036.864 | 11851 / -0.071 | 11661 / -0.083 | -216384036.864 | 35365 | -72523681.345 | -0.005 | -72523681.375 | 0.00 | 50 % | 2564799990753.7 | Z 26451 · S 4686 · NS 393 · ZS 3303 · TE 532 |
| 104 | M018-15m-H1 | Stufe 0, nicht bestanden | 11853 / -216384036.866 | 11851 / -0.065 | 11661 / -0.077 | -216384036.866 | 35365 | -72523681.341 | -0.002 | -72523681.371 | 0.00 | 59 % | 2564799990644.8 | Z 18047 · S 9160 · NS 2389 · TE 5769 |
| 105 | M018-15m-H3 | Stufe 0, nicht bestanden | 11853 / -216384036.870 | 11851 / -0.070 | 11661 / -0.087 | -216384036.870 | 35365 | -72523681.348 | -0.008 | -72523681.378 | 0.00 | 62 % | 2564799990860.9 | Z 20672 · S 11759 · NS 2848 · HD 86 |
| 106 | M014-15m-H1 | Stufe 0, nicht bestanden | 5188 / -0.132 | 4398 / -793544392.162 | 5032 / -627221564.856 | -793544392.162 | 14618 | -454657761.101 | +0.010 | -454657761.131 | 0.00 | 53 % | 6646187151774.0 | Z 1919 · S 5057 · NS 5339 · TE 2303 |
| 107 | M014-15m-H0 | Stufe 0, nicht bestanden | 5188 / -0.136 | 4398 / -793544392.164 | 5032 / -627221564.855 | -793544392.164 | 14618 | -454657761.102 | +0.009 | -454657761.132 | 0.00 | 52 % | 6646187151795.1 | Z 1581 · S 4471 · NS 4431 · ZS 3232 · TE 903 |
| 108 | M014-15m-H4 | Stufe 0, nicht bestanden | 5188 / -0.137 | 4398 / -793544392.164 | 5032 / -627221564.855 | -793544392.164 | 14618 | -454657761.103 | +0.008 | -454657761.133 | 0.00 | 52 % | 6646187151804.7 | Z 1539 · S 4472 · NS 4566 · ZS 2677 · TE 1364 |
| 109 | M014-15m-H2 | Stufe 0, nicht bestanden | 5188 / -0.129 | 4398 / -793544392.166 | 5032 / -627221564.860 | -793544392.166 | 14618 | -454657761.102 | +0.008 | -454657761.132 | 0.00 | 54 % | 6646187151797.3 | Z 3593 · S 4354 · NS 3628 · ZS 2275 · TE 768 |
| 110 | M014-15m-H3 | Stufe 0, nicht bestanden | 5188 / -0.150 | 4398 / -793544392.193 | 5032 / -627221564.871 | -793544392.193 | 14618 | -454657761.122 | -0.011 | -454657761.152 | 0.00 | 52 % | 6646187152090.4 | Z 2389 · S 5705 · NS 6506 · HD 18 |
| 111 | M012-15m-H0 | Stufe 0, nicht bestanden | 2032 / -0.103 | 1818 / -0.105 | 1825 / -1729413103.593 | -1729413103.593 | 5675 | -556154874.794 | +0.010 | -556154874.824 | 0.00 | 52 % | 3156178914460.9 | Z 702 · S 1585 · NS 1470 · ZS 1603 · TE 315 |
| 112 | M012-15m-H1 | Stufe 0, nicht bestanden | 2032 / -0.097 | 1818 / -0.087 | 1825 / -1729413103.596 | -1729413103.596 | 5675 | -556154874.788 | +0.017 | -556154874.818 | 0.00 | 53 % | 3156178914426.6 | Z 867 · S 1874 · NS 1877 · TE 1057 |
| 113 | M012-15m-H2 | Stufe 0, nicht bestanden | 2032 / -0.101 | 1818 / -0.111 | 1825 / -1729413103.599 | -1729413103.599 | 5675 | -556154874.797 | +0.007 | -556154874.827 | 0.00 | 51 % | 3156178914477.5 | Z 1925 · S 1496 · NS 1108 · ZS 916 · TE 230 |
| 114 | M012-15m-H4 | Stufe 0, nicht bestanden | 2032 / -0.105 | 1818 / -0.093 | 1825 / -1729413103.603 | -1729413103.603 | 5675 | -556154874.794 | +0.010 | -556154874.824 | 0.00 | 52 % | 3156178914463.6 | Z 648 · S 1571 · NS 1557 · ZS 1349 · TE 550 |
| 115 | M012-15m-H3 | Stufe 0, nicht bestanden | 2032 / -0.131 | 1818 / -0.115 | 1825 / -1729413103.615 | -1729413103.615 | 5675 | -556154874.814 | -0.010 | -556154874.844 | 0.00 | 52 % | 3156178914576.9 | Z 1103 · S 2183 · NS 2378 · HD 11 |

## 4. Stufe 1

Stufe 1 verlangt alle drei Bedingungen: (1) jedes Jahr mindestens 30 Trades und Erwartungswert nach Kosten über 0; (2) über alle 3 Jahre mit Kostenstress (+0,03R) über 0; (3) Zufall in derselben Richtung in mindestens 95 von 100 Läufen geschlagen (Startwert 20261020). Die Latte „Bester von N“ ist nur Information.

**Kandidaten mit Stufe 1: 0 von 115** (keiner).

Latte „Bester von N“ (nur Information): N = 110 Kandidaten mit mindestens 30 Trades in jedem Jahr. Die Spalte „Latte“ zeigt, in wie vielen der 100 Läufe der Kandidat über dem besten Zufall aller N liegt.

Alle 110 Kandidaten mit genug Daten:

| Kandidat | (1) jedes Jahr > 0 | (2) Kostenstress > 0 | (3) Zufall gleiche Richtung | Stufe | Latte (Info) | fehlt |
|---|---|---|---|---|---|---|
| M021-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.028R; J2: Erwartungswert -0.043R; J3: Erwartungswert -0.034R; Kostenstress: -0.065R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M007-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.036R; J2: Erwartungswert -0.037R; J3: Erwartungswert -0.045R; Kostenstress: -0.069R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M003-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.049R; J2: Erwartungswert -0.042R; J3: Erwartungswert -0.030R; Kostenstress: -0.071R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M022-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.050R; J2: Erwartungswert -0.050R; J3: Erwartungswert -0.003R; Kostenstress: -0.064R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M022-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.050R; J2: Erwartungswert -0.051R; J3: Erwartungswert -0.003R; Kostenstress: -0.064R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M003-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.053R; J2: Erwartungswert -0.038R; J3: Erwartungswert -0.034R; Kostenstress: -0.072R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M003-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.053R; J2: Erwartungswert -0.038R; J3: Erwartungswert -0.033R; Kostenstress: -0.072R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M022-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.048R; J2: Erwartungswert -0.056R; J3: Erwartungswert -0.039R; Kostenstress: -0.077R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M003-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.056R; J2: Erwartungswert -0.049R; J3: Erwartungswert -0.021R; Kostenstress: -0.073R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M009-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 4/100 | J1: Erwartungswert -0.057R; J2: Erwartungswert -0.008R; Kostenstress: -0.049R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M009-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 4/100 | J1: Erwartungswert -0.057R; J2: Erwartungswert -0.008R; Kostenstress: -0.049R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M022-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.058R; J2: Erwartungswert -0.046R; J3: Erwartungswert -0.035R; Kostenstress: -0.077R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M005-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.024R; J2: Erwartungswert -0.039R; J3: Erwartungswert -0.061R; Kostenstress: -0.072R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M021-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.048R; J2: Erwartungswert -0.061R; J3: Erwartungswert -0.027R; Kostenstress: -0.075R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M004-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.013R; J2: Erwartungswert -0.045R; J3: Erwartungswert -0.061R; Kostenstress: -0.070R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M005-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.038R; J2: Erwartungswert -0.042R; J3: Erwartungswert -0.062R; Kostenstress: -0.078R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M005-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.062R; J2: Erwartungswert -0.016R; J3: Erwartungswert -0.053R; Kostenstress: -0.076R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M023-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.063R; J2: Erwartungswert -0.043R; J3: Erwartungswert -0.016R; Kostenstress: -0.071R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M005-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.063R; J2: Erwartungswert -0.020R; J3: Erwartungswert -0.059R; Kostenstress: -0.080R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M002-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 1/100 | J1: Erwartungswert -0.064R; J3: Erwartungswert -0.057R; Kostenstress: -0.053R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M003-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.052R; J2: Erwartungswert -0.049R; J3: Erwartungswert -0.065R; Kostenstress: -0.085R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M009-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.066R; J2: Erwartungswert -0.025R; J3: Erwartungswert -0.023R; Kostenstress: -0.065R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M007-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.060R; J2: Erwartungswert -0.052R; J3: Erwartungswert -0.069R; Kostenstress: -0.091R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M007-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.060R; J2: Erwartungswert -0.052R; J3: Erwartungswert -0.069R; Kostenstress: -0.090R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M023-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.071R; J2: Erwartungswert -0.047R; J3: Erwartungswert -0.040R; Kostenstress: -0.083R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M004-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.017R; J2: Erwartungswert -0.046R; J3: Erwartungswert -0.072R; Kostenstress: -0.075R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M007-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.022R; J2: Erwartungswert -0.031R; J3: Erwartungswert -0.072R; Kostenstress: -0.071R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M007-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.052R; J2: Erwartungswert -0.034R; J3: Erwartungswert -0.073R; Kostenstress: -0.084R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M019-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.068R; J2: Erwartungswert -0.058R; J3: Erwartungswert -0.079R; Kostenstress: -0.098R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M005-15m-H3 | nein | nein | nein (2/100) | Stufe 0, nicht bestanden | 16/100 | J3: Erwartungswert -0.080R; Kostenstress: -0.038R; Zufall in derselben Richtung: 2 von 100 (nötig 95) |
| M021-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.028R; J2: Erwartungswert -0.070R; J3: Erwartungswert -0.081R; Kostenstress: -0.091R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M021-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.029R; J2: Erwartungswert -0.070R; J3: Erwartungswert -0.081R; Kostenstress: -0.091R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M019-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.076R; J2: Erwartungswert -0.062R; J3: Erwartungswert -0.082R; Kostenstress: -0.103R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M001-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.082R; J2: Erwartungswert -0.053R; J3: Erwartungswert -0.072R; Kostenstress: -0.103R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M006-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.056R; J2: Erwartungswert -0.084R; J3: Erwartungswert -0.056R; Kostenstress: -0.095R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M006-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.055R; J2: Erwartungswert -0.084R; J3: Erwartungswert -0.057R; Kostenstress: -0.095R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M006-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.041R; J2: Erwartungswert -0.085R; J3: Erwartungswert -0.054R; Kostenstress: -0.089R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M001-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.086R; J2: Erwartungswert -0.056R; J3: Erwartungswert -0.073R; Kostenstress: -0.106R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M002-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 39/100 | J1: Erwartungswert -0.077R; J3: Erwartungswert -0.087R; Kostenstress: -0.019R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M006-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.045R; J2: Erwartungswert -0.091R; J3: Erwartungswert -0.062R; Kostenstress: -0.094R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M001-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.089R; J2: Erwartungswert -0.013R; J3: Erwartungswert -0.092R; Kostenstress: -0.103R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M001-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.089R; J2: Erwartungswert -0.012R; J3: Erwartungswert -0.093R; Kostenstress: -0.103R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M009-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.093R; J2: Erwartungswert -0.027R; J3: Erwartungswert -0.030R; Kostenstress: -0.076R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M023-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.093R; J3: Erwartungswert -0.025R; Kostenstress: -0.067R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M023-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.093R; J3: Erwartungswert -0.025R; Kostenstress: -0.067R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M019-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.094R; J2: Erwartungswert -0.028R; J3: Erwartungswert -0.092R; Kostenstress: -0.100R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M019-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.071R; J2: Erwartungswert -0.071R; J3: Erwartungswert -0.094R; Kostenstress: -0.108R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M002-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 7/100 | J1: Erwartungswert -0.095R; J3: Erwartungswert -0.069R; Kostenstress: -0.046R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M002-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 36/100 | J1: Erwartungswert -0.075R; J3: Erwartungswert -0.096R; Kostenstress: -0.022R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M019-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.093R; J2: Erwartungswert -0.025R; J3: Erwartungswert -0.097R; Kostenstress: -0.101R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M013-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.109R; J2: Erwartungswert -0.048R; J3: Erwartungswert -0.104R; Kostenstress: -0.116R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M011-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.110R; J2: Erwartungswert -0.039R; J3: Erwartungswert -0.097R; Kostenstress: -0.112R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M004-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J2: Erwartungswert -0.060R; J3: Erwartungswert -0.112R; Kostenstress: -0.085R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M011-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.102R; J2: Erwartungswert -0.019R; J3: Erwartungswert -0.112R; Kostenstress: -0.108R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M013-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.114R; J2: Erwartungswert -0.056R; J3: Erwartungswert -0.101R; Kostenstress: -0.120R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M011-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.114R; J2: Erwartungswert -0.029R; J3: Erwartungswert -0.085R; Kostenstress: -0.106R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M013-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.115R; J2: Erwartungswert -0.061R; J3: Erwartungswert -0.098R; Kostenstress: -0.121R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M011-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.117R; J2: Erwartungswert -0.039R; J3: Erwartungswert -0.100R; Kostenstress: -0.115R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M020-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.118R; J2: Erwartungswert -0.083R; J3: Erwartungswert -0.103R; Kostenstress: -0.132R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M004-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J2: Erwartungswert -0.049R; J3: Erwartungswert -0.118R; Kostenstress: -0.081R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M013-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.119R; J2: Erwartungswert -0.056R; J3: Erwartungswert -0.103R; Kostenstress: -0.122R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M020-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.121R; J2: Erwartungswert -0.096R; J3: Erwartungswert -0.095R; Kostenstress: -0.134R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M020-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.127R; J2: Erwartungswert -0.089R; J3: Erwartungswert -0.092R; Kostenstress: -0.133R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M011-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.127R; J2: Erwartungswert -0.046R; J3: Erwartungswert -0.104R; Kostenstress: -0.122R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M013-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.125R; J2: Erwartungswert -0.072R; J3: Erwartungswert -0.128R; Kostenstress: -0.137R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M023-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.129R; J2: Erwartungswert -0.025R; J3: Erwartungswert -0.021R; Kostenstress: -0.092R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M020-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.129R; J2: Erwartungswert -0.076R; J3: Erwartungswert -0.099R; Kostenstress: -0.132R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M001-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.119R; J2: Erwartungswert -0.023R; J3: Erwartungswert -0.148R; Kostenstress: -0.136R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M017-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.126R; J2: Erwartungswert -0.027R; J3: Erwartungswert -0.153R; Kostenstress: -0.131R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M017-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.124R; J2: Erwartungswert -0.034R; J3: Erwartungswert -0.153R; Kostenstress: -0.133R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M020-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.157R; J2: Erwartungswert -0.076R; J3: Erwartungswert -0.145R; Kostenstress: -0.157R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M022-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.161R; J2: Erwartungswert -0.021R; Kostenstress: -0.083R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M017-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.124R; J2: Erwartungswert -0.031R; J3: Erwartungswert -0.164R; Kostenstress: -0.135R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M017-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.119R; J2: Erwartungswert -0.032R; J3: Erwartungswert -0.166R; Kostenstress: -0.135R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M008-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.170R; J2: Erwartungswert -0.134R; J3: Erwartungswert -0.030R; Kostenstress: -0.145R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M008-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.170R; J2: Erwartungswert -0.134R; J3: Erwartungswert -0.030R; Kostenstress: -0.145R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M008-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.172R; J2: Erwartungswert -0.121R; J3: Erwartungswert -0.001R; Kostenstress: -0.133R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M009-15m-H3 | nein | nein | nein (1/100) | Stufe 0, nicht bestanden | 0/100 | J2: Erwartungswert -0.175R; J3: Erwartungswert -0.166R; Kostenstress: -0.150R; Zufall in derselben Richtung: 1 von 100 (nötig 95) |
| M021-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J2: Erwartungswert -0.187R; J3: Erwartungswert -0.112R; Kostenstress: -0.114R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M008-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.190R; J2: Erwartungswert -0.134R; J3: Erwartungswert -0.007R; Kostenstress: -0.146R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M006-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.168R; J2: Erwartungswert -0.196R; J3: Erwartungswert -0.020R; Kostenstress: -0.161R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M015-15m-H2 | nein | nein | nein (86/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.098R; J2: Erwartungswert -0.219R; J3: Erwartungswert -0.177R; Kostenstress: -0.193R; Zufall in derselben Richtung: 86 von 100 (nötig 95) |
| M015-15m-H0 | nein | nein | nein (86/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.101R; J2: Erwartungswert -0.221R; J3: Erwartungswert -0.176R; Kostenstress: -0.194R; Zufall in derselben Richtung: 86 von 100 (nötig 95) |
| M015-15m-H4 | nein | nein | nein (86/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.112R; J2: Erwartungswert -0.222R; J3: Erwartungswert -0.166R; Kostenstress: -0.195R; Zufall in derselben Richtung: 86 von 100 (nötig 95) |
| M015-15m-H1 | nein | nein | nein (86/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.108R; J2: Erwartungswert -0.226R; J3: Erwartungswert -0.165R; Kostenstress: -0.195R; Zufall in derselben Richtung: 86 von 100 (nötig 95) |
| M017-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.188R; J2: Erwartungswert -0.080R; J3: Erwartungswert -0.243R; Kostenstress: -0.199R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M015-15m-H3 | nein | nein | nein (86/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.148R; J2: Erwartungswert -0.274R; J3: Erwartungswert -0.195R; Kostenstress: -0.234R; Zufall in derselben Richtung: 86 von 100 (nötig 95) |
| M002-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.234R; J3: Erwartungswert -0.293R; Kostenstress: -0.132R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M016-15m-H4 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.167R; J2: Erwartungswert -0.155R; J3: Erwartungswert -0.296R; Kostenstress: -0.235R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M016-15m-H1 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.162R; J2: Erwartungswert -0.152R; J3: Erwartungswert -0.296R; Kostenstress: -0.233R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M016-15m-H2 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.166R; J2: Erwartungswert -0.159R; J3: Erwartungswert -0.297R; Kostenstress: -0.237R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M016-15m-H0 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.167R; J2: Erwartungswert -0.145R; J3: Erwartungswert -0.300R; Kostenstress: -0.233R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M008-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.314R; J2: Erwartungswert -0.153R; J3: Erwartungswert -0.150R; Kostenstress: -0.249R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M016-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.205R; J2: Erwartungswert -0.200R; J3: Erwartungswert -0.326R; Kostenstress: -0.273R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M004-15m-H3 | nein | nein | nein (0/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.018R; J2: Erwartungswert -0.358R; J3: Erwartungswert -0.126R; Kostenstress: -0.205R; Zufall in derselben Richtung: 0 von 100 (nötig 95) |
| M018-15m-H4 | nein | nein | nein (83/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -216384036.862R; J2: Erwartungswert -0.062R; J3: Erwartungswert -0.076R; Kostenstress: -72523681.369R; Zufall in derselben Richtung: 83 von 100 (nötig 95) |
| M018-15m-H0 | nein | nein | nein (83/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -216384036.862R; J2: Erwartungswert -0.070R; J3: Erwartungswert -0.079R; Kostenstress: -72523681.373R; Zufall in derselben Richtung: 83 von 100 (nötig 95) |
| M018-15m-H2 | nein | nein | nein (83/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -216384036.864R; J2: Erwartungswert -0.071R; J3: Erwartungswert -0.083R; Kostenstress: -72523681.375R; Zufall in derselben Richtung: 83 von 100 (nötig 95) |
| M018-15m-H1 | nein | nein | nein (83/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -216384036.866R; J2: Erwartungswert -0.065R; J3: Erwartungswert -0.077R; Kostenstress: -72523681.371R; Zufall in derselben Richtung: 83 von 100 (nötig 95) |
| M018-15m-H3 | nein | nein | nein (83/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -216384036.870R; J2: Erwartungswert -0.070R; J3: Erwartungswert -0.087R; Kostenstress: -72523681.378R; Zufall in derselben Richtung: 83 von 100 (nötig 95) |
| M014-15m-H1 | nein | nein | nein (49/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.132R; J2: Erwartungswert -793544392.162R; J3: Erwartungswert -627221564.856R; Kostenstress: -454657761.131R; Zufall in derselben Richtung: 49 von 100 (nötig 95) |
| M014-15m-H0 | nein | nein | nein (49/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.136R; J2: Erwartungswert -793544392.164R; J3: Erwartungswert -627221564.855R; Kostenstress: -454657761.132R; Zufall in derselben Richtung: 49 von 100 (nötig 95) |
| M014-15m-H4 | nein | nein | nein (49/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.137R; J2: Erwartungswert -793544392.164R; J3: Erwartungswert -627221564.855R; Kostenstress: -454657761.133R; Zufall in derselben Richtung: 49 von 100 (nötig 95) |
| M014-15m-H2 | nein | nein | nein (49/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.129R; J2: Erwartungswert -793544392.166R; J3: Erwartungswert -627221564.860R; Kostenstress: -454657761.132R; Zufall in derselben Richtung: 49 von 100 (nötig 95) |
| M014-15m-H3 | nein | nein | nein (49/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.150R; J2: Erwartungswert -793544392.193R; J3: Erwartungswert -627221564.871R; Kostenstress: -454657761.152R; Zufall in derselben Richtung: 49 von 100 (nötig 95) |
| M012-15m-H0 | nein | nein | nein (41/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.103R; J2: Erwartungswert -0.105R; J3: Erwartungswert -1729413103.593R; Kostenstress: -556154874.824R; Zufall in derselben Richtung: 41 von 100 (nötig 95) |
| M012-15m-H1 | nein | nein | nein (41/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.097R; J2: Erwartungswert -0.087R; J3: Erwartungswert -1729413103.596R; Kostenstress: -556154874.818R; Zufall in derselben Richtung: 41 von 100 (nötig 95) |
| M012-15m-H2 | nein | nein | nein (41/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.101R; J2: Erwartungswert -0.111R; J3: Erwartungswert -1729413103.599R; Kostenstress: -556154874.827R; Zufall in derselben Richtung: 41 von 100 (nötig 95) |
| M012-15m-H4 | nein | nein | nein (41/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.105R; J2: Erwartungswert -0.093R; J3: Erwartungswert -1729413103.603R; Kostenstress: -556154874.824R; Zufall in derselben Richtung: 41 von 100 (nötig 95) |
| M012-15m-H3 | nein | nein | nein (41/100) | Stufe 0, nicht bestanden | 0/100 | J1: Erwartungswert -0.131R; J2: Erwartungswert -0.115R; J3: Erwartungswert -1729413103.615R; Kostenstress: -556154874.844R; Zufall in derselben Richtung: 41 von 100 (nötig 95) |

## 5. Top 10 und Flop 10 (nur innerhalb von 15 Min)

### Top 10 (Stufe 1, nach dem schwächsten Jahr, höchstens 2 je Muster)

| Rang | Kandidat | Einstufung | J1 Trades / EV | J2 Trades / EV | J3 Trades / EV | schwächstes Jahr | gesamt Trades | EV nach Kosten | EV vor Kosten | Kostenstress | PF | Treffer | max. DD (R) | Ausgänge |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| – | keiner | | | | | | | | | | | | | |

Für die Top 10 wird nichts im Prüftopf geöffnet; das entscheidet der Inhaber (eigene Vorab-Datei).

### Flop 10 (vor Kosten klar verlierend: jedes Jahr unter 0 mit mindestens 30 Trades, gesamt höchstens −0,10R)

| Rang | Kandidat | Einstufung | J1 Trades / EV | J2 Trades / EV | J3 Trades / EV | schwächstes Jahr | gesamt Trades | EV nach Kosten | EV vor Kosten | Kostenstress | PF | Treffer | max. DD (R) | Ausgänge |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | M008-15m-H3 | Stufe 0, nicht bestanden | 213 / -0.314 | 129 / -0.153 | 165 / -0.150 | -0.314 | 507 | -0.219 | -0.158 | -0.249 | 0.57 | 33 % | 113.5 | Z 39 · S 216 · NS 214 · HD 38 |

### Nebenzählung 3×-Regel (zählt nicht, Fahrplan 4.8.20)

Ankerpunkte von M008–M010 auf 15 Min mit SIP-Kerze: 77224. Die 3×-Regel hätte 109 von SIP bestätigte und 0 nicht bestätigte Dochte verworfen.

