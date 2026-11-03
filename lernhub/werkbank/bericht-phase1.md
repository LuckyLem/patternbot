# Gemeinsame Werkbank v3 · Phase 1 · Bericht

Stand Di 03.11.2026, 14:25 deutscher Zeit (08:25 New York). Auftrag: Gemeinsame Werkbank v3, Fassung 1 (Commit 2434c11).

## Kurz

- **Gemeinsame Werkbank gebaut**, das Rechteck ist das erste Muster-Modul.
- **Gleichheitstest bestanden:** 13.293 von 13.293 Trades von Werkbank Rechteck v1 sind gleich.
- **Ideen-Register angelegt:** 12 Einträge, bisher N = 132 Versuche.
- **Analyse-Modul gebaut und getestet.** Es wurde noch nicht auf echten Daten gerechnet; das ist Phase 2.
- **Tageskerzen geladen** (vor 15:30): 1.104 von 1.522 Werten sind vollständig seit 2016, alle 22 Länder-ETFs gehören dazu.
- **SIP-1-Min der übrigen 100 der Liste von 150:** alle vollständig im Cache (Okt. 2020 – Sep. 2023).
- **Werkbank Rechteck v1 abgeschlossen:** Keine Variante überzeugt. Sie bleibt unverändert als Vergleich stehen, der Prüftopf bleibt zu.

## Code-Hashes

| Teil | Hash | Dateien |
|---|---|---|
| gemeinsam | `a4211707b14e` | Kerzen, Wendepunkte, Linien, Reifegrad, Trichter, Schnappschuss, Einstiege, Handel, Zusammenhang, Merkmale, Lauf |
| Muster Rechteck | `28313543ce98` | Erkennung Fassung 2.2 unverändert, mit dem Vergleich zum alten Stand |
| Analyse | `50bfb138ceca` | Analyse-Modul (Abschnitt 4) |
| alter Stand Rechteck | `8454cdc07786` | eingefroren, nur für den Vergleich „derselbe Kasten nach dem alten Stand“ |

Werkbank Rechteck v1 ist unverändert: Erkennung `2489765016f5` und Lauf `e0fe5e0efe43`. Der Gleichheitstest prüft beide Hashes,
bevor er rechnet. Pflichttests: `test_werkbank_v3` mit 14 Gruppen und `test_werkbank_v3_analyse` mit 6 Gruppen, alle grün, nur
auf künstlichen Kursen.

## Gleichheitstest

Die neue Werkbank rechnet Werkbank Rechteck v1 nach: 50 Aktien, 01.10.2021 – 29.09.2023, nur aus dem Cache.

| Zeitebene | Trades v1 | Trades neu | fehlen | dazu | Hash ungleich | r_vor ungleich | r ungleich |
|---|---:|---:|---:|---:|---:|---:|---:|
| 15 Min | 338 | 338 | 0 | 0 | 0 | 0 | 0 |
| 5 Min | 12.955 | 12.955 | 0 | 0 | 0 | 0 | 0 |

Darüber hinaus gleich:
- **Jedes Feld der Trades:** Kasten, Einstieg, Stop, Ziel, Ausgang und Merkmale, nicht nur die drei Pflichtfelder.
- **Die Erkennung je Kerze an jedem Tag:** Kasten, Note, Punkte, Reifegrad und Auslöser, dazu die Hashes aller Erkennungs-
  und Entscheidungs-Schnappschüsse.
- **Die Auswertung der 8 Varianten mit Zufallstest:** Zufall 15 Min 22/88/73/35, 5 Min 83/9/24/32.

Gerechnet habe ich zweimal: zuerst mit dem Bau-Stand, dann mit dem endgültigen Code von Phase 1. Beide Durchgänge sind
bestanden, es gilt der zweite. Datei: `lernhub/werkbank/gleichheitstest-v3.json`.

## Was die gemeinsame Werkbank kann

- **Kerzen:** 5 Min, 15 Min und Tag, mit Börsenkalender und Halbtagen.
  - Die Sperre ab 01.10.2023 gilt für alle Zeitebenen (Test 9).
- **ATR:**
  - intraday je Tageszeit wie bisher;
  - auf Tageskerzen ATR 14 als Mittel der wahren Spanne der 14 Tage bis einschließlich des Tages.
- **Wendepunkte:** erst k Kerzen später bekannt (intraday 2 Kerzen und 0,5 ATR, Tag 3 Kerzen und 1 ATR).
- **Linien und Toleranzen:** Linien als Median der Berührungen, Toleranzen in ATR.
- **Trichter:** je Regel „übrig“, „nur diese“, „insgesamt“, dazu die Zeitbudget-Regel.
- **Reifegrad und Noten:** Reifegrad 0–4; Noten aus harten Bedingungen (die Punktzahl ordnet nur).
- **Schnappschuss** mit Hash im Moment der Entscheidung.
- **Die vier Einstiege** mit Namen: Ausbruch, Retest, früher Einstieg, Fehlschlag.
  - Das Muster-Modul liefert nur die Kante, den Abpraller bzw. den Bruch.
  - Der Fehlschlag kennt beide Formen:
    - Rückkehr nach dem Ausbruch (Rechteck);
    - Bruch des tieferen Bodens (Doppelboden), schon getestet.
- **Ausstiege:**
  - intraday Ziel, Stop oder 15:50;
  - Tag Ziel, Stop oder Zeitlimit; Einstieg zur Eröffnung des nächsten Tages, Kurslücke über Nacht zum Eröffnungskurs.
- **Kosten, Kostenstress, Zufallstest** wie v1.
  - Mindest-Stop intraday max(0,5 ATR; 0,15 %), Tag max(0,5 ATR; 0,5 %).
  - Der Zufallstrade auf Tageskerzen nimmt einen anderen Einstiegstag (± 20 Handelstage) mit gleichem Stop in %, Ziel in R und
    Zeitlimit.
- **Zusammenhang** als zweite Variante je Muster:
  - Tag: 50- und 200-Tage-Linie;
  - intraday: VWAP und SPY seit 09:30.
- **Ganzer Lauf:** schreibt die Trades und danach automatisch die Analyse.

**Meine Festlegungen, wo der Auftrag keine Formel vorgibt** (bitte prüfen):
1. **Filter je Tag:** Der Wert für einen Tag nutzt nur die Tage davor. Er gilt am Entscheidungstag.
2. **Zeitlimit Tag:** Der Einstiegstag ist Haltetag 1. Der Ausstieg ist der Schluss des 20. Haltetags.
3. **Kein Trade über das Ende eines Zeitraums:** Ein Trade auf Tageskerzen wird nur eröffnet, wenn sein Zeitlimit vor dem Ende
   des Zeitraums liegt. So nutzt ein Such-Trade keine Kurse der Bestätigungsdaten, und kein Trade berührt den Prüftopf.
4. **Doppelte Trades:** Auf Tageskerzen gibt es höchstens einen Trade je Einstieg, Note und Muster. Intraday bleibt es wie in v1:
   je Einstieg und Note der erste Auslöser des Tages.

## Ideen-Register

Datei: `lernhub/werkbank/ideen-register.json`.
- Status: geplant, läuft, verworfen, bestätigt, Prüftopf.
- N = Summe der gezählten Varianten, für „Bester von N“.

| Nr. | Idee | Daten | Status | Versuche | Ergebnis |
|---|---|---|---|---:|---|
| V1 | Runde 1 | Okt. 2025 – Sep. 2026 | verworfen | 1 | 1.009 Trades, −0,056 R, Zufall 25 |
| V2 | Runde 2 (ohne Rechteck) | Okt. 2024 – Sep. 2025 | verworfen | 1 | 511 Trades, −0,083 R, Zufall 27 |
| V3 | ORB Jahr 1 | Okt. 2025 – Sep. 2026 | verworfen | 7 | −0,465 R (mit Ticks −0,404 R), Zufall 0 |
| V4 | Lerntopf-Lauf 1 | Okt. 2020 – Sep. 2023, 150 Werte | verworfen | 115 | 15 Min: keiner erreicht Stufe 1 |
| V5 | Werkbank Rechteck v1 | Okt. 2021 – Sep. 2023, 50 Werte | verworfen | 8 | keine Variante überzeugt |
| H1–H6 | Doppelboden/Doppeltop, Rechteck Fassung 3, Kopf-Schulter, Flagge und Wimpel, Dreiecke, Tasse mit Henkel | Suche | geplant | – | – |
| H7+ | Ideen des Inhabers, Preis-Setups | – | geplant | – | – |

So habe ich gezählt:
- **ORB:** Hauptvariante plus die 6 Nachbarwerte, die wir angesehen haben.
- **Lerntopf:** die 115 ausgewerteten Kandidaten auf 15 Min. Den 5-Min-Teil haben wir nie ausgewertet.
- **H1 bis H6:** Varianten, Regeln und Hash kommen erst mit der Vorab-Datei.

## Analyse-Modul (gebaut, noch nicht gerechnet)

**Je Trade misst es:**
- MFE und MAE in R, jeweils mit der Zeit bis dahin;
- ob das Ziel nach dem Ausstieg noch erreicht wurde (intraday bis Börsenschluss, Tag 20 Tage);
- Abstand des Füllkurses zur Kante in ATR;
- Zeit vom fertigen Muster bis zum Einstieg;
- wie weit SPY im Trade gegen die Richtung lief.

**Verlust- und Gewinn-Arten** nach der Tabelle in Abschnitt 4; die erste zutreffende zählt.

**Auswertungen:**
- Anteile je Art, Muster, Zeitebene, Note und Einstieg;
- Erkennung gegen Ergebnis (Noten A/B/C, Sichtprüfung ja gegen nein, derselbe Kasten nach dem alten Stand);
- die Einstiege auf denselben Kästen nebeneinander;
- „Was wäre wenn“, nur auf den Suchdaten: Stop 1 und 1,5 ATR, Ziel 1 und 2 R, ohne Einstieg nach 14:30, Tag 10 statt 20 Tage.

**Meine Festlegungen** (bitte prüfen):
1. **„Innerhalb von 3 Kerzen“:** Der Ausstieg liegt in der 1. bis 3. Kerze ab der Einstiegsminute.
2. **„Gegen den Markt“:** die Nettobewegung von SPY vom Einstieg bis zum Ausstieg, geteilt durch die SPY-ATR derselben
   Tageszeit (Tag: SPY-ATR 14).
3. **„Stop-Abstand unter 1 ATR“:** gemessen an der Muster-ATR, also der Kasten-ATR beim Rechteck.
4. **Sichtprüfung:** Ein Trade gehört zu einem Bild bei gleicher Aktie, gleichem Tag, gleicher Zeitebene und gleichem
   Kastenbeginn.

## Datenlage

### Tageskerzen (SIP, bereinigt und roh, 01.01.2016 – 30.09.2023)

Geladen am Di 03.11. von 13:56 bis 14:02 deutscher Zeit, mit 528 Abrufen und ohne Drosselung durch den Anbieter.

| Klasse | Werte |
|---|---:|
| vollständig seit 2016 (jeder Handelstag 04.01.2016 – 29.09.2023) | 1.104 |
| vollständig ab späterem Beginn (Börsengang oder neuer Ticker) | 399 |
| mit Lücken oder früher zu Ende | 4 |
| keine Daten | 15 |
| zusammen (1.500 und 22 Länder-ETFs) | 1.522 |

- **Später begonnen:** 372 der 399 Werte gibt es erst nach dem 01.10.2016.
- **Mit Lücken:** CNXC (3 fehlende Tage), AMTB (2), SYNH (endet 28.09.2023), MCG (endet 17.03.2023).
- **Keine Daten:** ARKB, AXNX, BIRK, BYON, CEIX, CON, DOW, FI, GBTC, GRAL, GUTS, HAFN, MEDS, NCRI, TCEHY. Das sind
  spätere Börsengänge, umbenannte oder inzwischen abgemeldete Werte (FI heißt heute FISV, BYON hieß bis Nov. 2023 OSTK) und ein
  OTC-Wert (TCEHY).
- **Bereinigt und roh** haben überall dieselben Tage.

### Länder-ETFs

Alle 22 gibt es seit 2016, und alle sind vollständig.

Die Spalte „handelbar“ ist der Anteil der Tage 01.10.2016 – 29.09.2023, an denen der Filter je Tag den Wert zulässt
(Kurs über 5 $, Ø Umsatz 20 Tage mindestens 10 Mio. $).

| ETF | Ø Umsatz Mio. $ | handelbar | | ETF | Ø Umsatz Mio. $ | handelbar |
|---|---:|---:|---|---|---:|---:|
| FXI | 1.044 | 100 % | | EWU | 89 | 100 % |
| EWZ | 946 | 100 % | | EWA | 65 | 100 % |
| EWJ | 428 | 100 % | | EWL | 42 | 100 % |
| EWY | 237 | 100 % | | EWQ | 29 | 100 % |
| EWT | 182 | 100 % | | EWI | 28 | 95 % |
| EWW | 143 | 100 % | | EWP | 28 | 91 % |
| INDA | 143 | 100 % | | EZA | 25 | 86 % |
| EWG | 113 | 100 % | | EWS | 16 | 87 % |
| EWH | 107 | 100 % | | TUR | 13 | 56 % |
| EWC | 99 | 100 % | | EWD | 12 | 59 % |
| | | | | EWN | 7 | 14 % |
| | | | | EPOL | 6 | 7 % |

**Mit genug Umsatz** sind 18 der 22 ETFs fast immer handelbar. TUR und EWD fallen an etwa 40 % der Tage durch den Filter,
EWN und EPOL fast immer. Der Filter gilt für alle Werte gleich; ich nehme keinen ETF aus.

### SIP-1-Min für die Bestätigung (übrige 100 der Liste von 150)

01.10.2020 – 29.09.2023, 754 Handelstage: alle 100 Werte vollständig im Cache. Nichts davon ist ausgewertet.

Datei: `lernhub/werkbank/datenlage-v3.json`.

## Vorbehalte

1. **Überlebensverzerrung:** Die Liste der 1.500 ist von heute. Abgemeldete Werte fehlen ganz (15 liefern keine Daten), und 372
   Werte sind erst nach Okt. 2016 dazugekommen. Über 7 Jahre wiegt das schwerer als beim Rechteck. Ergebnisse auf
   Tageskerzen sehen dadurch eher zu gut aus.
2. **Schon benutzte Zeiträume:**
   - V1–V3 liefen auf Okt. 2024 – Sep. 2026, also heute im Prüftopf-Zeitraum.
   - V4 nutzte Okt. 2020 – Sep. 2023 auf den 150, also auch die heutigen Bestätigungsdaten intraday, mit anderer, lockerer
     Erkennung.
   - Für neue Regeln sind diese Daten nicht ausgewertet; im Bericht zur Bestätigung schreibe ich das dazu.
3. **Stand der Bereinigung:** Die bereinigten Tageskurse entsprechen dem Stand vom 03.11.2026 und sind im Cache eingefroren.
   Der Filter rechnet mit den rohen Kursen.
4. **Leihgebühren** für short sind nicht modelliert.

## Was nicht angefasst wurde

- Pi, Live-Bot und main: unberührt. Kein Bot-Code auf GitHub.
- Prüftopf ab 01.10.2023: zu, für alle Zeitebenen gesperrt.
- Keine Muster auf Tageskerzen gerechnet, keine Trades, kein R, keine Analyse auf echten Daten.

**STOPP.** Phase 2 (Analyse von Werkbank Rechteck v1) beginnt erst nach deinem OK.
