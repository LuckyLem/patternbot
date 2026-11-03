# Gemeinsame Werkbank v3 · Phase 2 und 3 · Bericht

Stand Di 03.11.2026, 16:35 deutscher Zeit (10:35 New York). Auftrag: Gemeinsame Werkbank v3 (Commit 2434c11) und
`werkbank-doppelboden.md`, Phase 2 und 3.

## Kurz

**Phase 2 (Analyse Werkbank Rechteck v1) ist fertig**, gerechnet nur auf den vorhandenen 13.293 Trades.
- Vor dem Schreiben wurde jeder Trade mit v1 verglichen (Hash, r_vor, r): alle gleich. Nichts wurde neu gehandelt.
- Die Analyse zeigt vor allem:
  - Die saubere Erkennung bringt nichts. Note A ist über alle Trades schlechter als B und C, und die Kästen mit deinem
    „ja“ schneiden nicht erkennbar besser ab.
  - Häufigste Verlust-Art ist „Gegen den Markt“, häufigste Gewinn-Art „sauber gewonnen“.
  - Kein „Was wäre wenn“ macht eine 5-Min-Variante positiv.
- Die Sichtprüfungen einstieg-1 und verlust-1 sind vorbereitet, aber nicht veröffentlicht.

**Phase 3 (Doppelboden Schritt 1) ist fertig.**
- Die Erkennung läuft für Tag, 15 Min und 5 Min.
- Die Pflichttests sind grün.
- Der Abschneide-Test auf echten Daten ist bestanden: 300 von 300.
- Die Zeitbudget-Regel erlaubt beide Intraday-Zeitebenen: 15 Min 37 % zu spät, 5 Min 19 % zu spät.
- Die Sichtprüfung doppelboden-1 ist vorbereitet, aber nicht veröffentlicht.

**Ideen-Register:** H1 steht auf „läuft“. N bleibt 132; die Varianten kommen erst mit der Vorab-Datei.

**Deine beiden Ergänzungen** sind umgesetzt (Abschnitt 2).

## 1. Code-Hashes

| Teil | Hash | seit Phase 1 |
|---|---|---|
| gemeinsam | `7c92a9b18dfe` | geändert, siehe unten |
| Muster Rechteck | `28313543ce98` | unverändert |
| Muster Doppelboden | `9d6347afba55` | neu |
| Analyse | `4e8c9fb71a68` | Gruppen je Variante, Kurzfassung für die Seite |
| alter Stand Rechteck | `8454cdc07786` | eingefroren |

**Änderungen am gemeinsamen Code:**
1. die Vorlaufzeit auf Tageskerzen (deine Ergänzung);
2. beim frühen Einstieg darf der Stop am Docht der Auslöserkerze hängen. Das braucht der Doppelboden („tieferer Boden −
   0,3 ATR“, wenn die Auslöserkerze selbst der tiefere Boden ist); das Rechteck nutzt es nicht;
3. der Fehlschlag als Bruch löst nur beim ersten Schluss jenseits der Linie aus, nicht an jeder weiteren Kerze.

**Danach habe ich den Gleichheitstest erneut gerechnet:** 13.293 von 13.293 Trades gleich.

**Pflichttests**, alle grün, nur künstliche Kurse:
- `test_werkbank_v3` (15 Gruppen);
- `test_werkbank_v3_analyse` (6);
- `test_doppelboden` (8).

## 2. Deine Ergänzungen

1. **Vorlaufzeit:** Ein Wert gibt auf Tageskerzen erst Signale, wenn er 14 Tage Kerzen hat (ATR 14).
   - Frühere Auslöser werden mit dem Grund „Vorlaufzeit“ verworfen.
   - Die Variante mit Zusammenhang ist erst ab 200 Tagen möglich (Feld `zusammenhang_moeglich` am Trade).
   - Beides ist getestet.
   - In der Doppelboden-Diagnose zählt ein Muster erst ab Tag 14.
2. **Zufallstest und Überlebensverzerrung:** Der Satz steht ab jetzt in jedem Bericht (Vorbehalte).

## 3. Phase 2: Analyse Werkbank Rechteck v1

**Grundlage:**
- die 13.293 Trades von v1 (Okt. 2021 – Sep. 2023, 50 Aktien, die Suchdaten intraday);
- Analyse-Code `4e8c9fb71a68`.

**Ablage:**
- Bericht `lernhub/werkbank/analyse-rechteck-v1.md` und `.json`;
- Kurzfassung für die Seite `lernhub/daten/analyse-rechteck-v1.json`.

Alles ist Information, nichts ändert eine Regel.

### Verlust- und Gewinn-Arten, alle Trades (die erste zutreffende zählt)

| Art | Anteil | Ø R |
|---|---:|---:|
| sauber gewonnen (Ziel erreicht) | 28 % | +1,32 |
| Gegen den Markt (SPY im Trade mehr als 0,5 ATR gegen die Richtung) | 27 % | −0,94 |
| sonst | 13 % | −1,01 |
| Fehlausbruch (Stop in den ersten 3 Kerzen, MFE unter 0,3 R) | 12 % | −1,22 |
| Zeit (Tagesende mit MFE über 0,5 R) | 10 % | +0,28 |
| Ziel zu weit (MFE mindestens 0,8 des Ziels, dann Stop oder Tagesende) | 7 % | +0,07 |
| Stop zu eng (gestoppt, Ziel danach erreicht, Stop unter 1 ATR) | 2 % | −1,25 |
| Kosten (vor Kosten positiv, nach Kosten negativ) | 1 % | −0,06 |

### Je Variante, nur Note A

| Variante | Trades | Ø R | Fehlausbruch | Gegen den Markt | sauber | Ø MFE | Ø MAE | Ziel später erreicht | Ziel / Stop / Tagesende |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 15 Min · Ausbruch | 45 | −0,20 | 7 % | 31 % | 13 % | +0,53 | −0,60 | 7 % | 6 / 14 / 25 |
| 15 Min · Retest | 3 | +0,57 | 0 % | 0 % | 67 % | +0,84 | −0,12 | 0 % | 2 / 0 / 1 |
| 15 Min · früher Einstieg | 41 | −0,02 | 24 % | 7 % | 12 % | +0,98 | −0,72 | 7 % | 6 / 17 / 18 |
| 15 Min · Fehlschlag | 12 | −0,18 | 8 % | 33 % | 8 % | +0,65 | −0,69 | 8 % | 1 / 4 / 7 |
| 5 Min · Ausbruch | 941 | −0,11 | 7 % | 30 % | 34 % | +0,82 | −0,72 | 11 % | 348 / 414 / 179 |
| 5 Min · Retest | 188 | −0,31 | 16 % | 23 % | 34 % | +0,84 | −0,81 | 16 % | 70 / 108 / 10 |
| 5 Min · früher Einstieg | 599 | −0,27 | 19 % | 23 % | 25 % | +1,16 | −0,89 | 18 % | 157 / 383 / 59 |
| 5 Min · Fehlschlag | 354 | −0,23 | 14 % | 31 % | 27 % | +1,06 | −0,85 | 13 % | 100 / 207 / 47 |

**Abstand und Zeit, über alle Trades:**
- Der Füllkurs liegt im Mittel **0,52 ATR jenseits der Kante**. Beim Retest sind es **1,02 ATR**, weil erst die Kerze nach
  der Retest-Kerze auslöst.
- Vom fertigen Kasten bis zum Einstieg vergehen im Mittel **38 Minuten**.

### Erkennung gegen Ergebnis

| | Trades | Ø R |
|---|---:|---:|
| Note A | 2.183 | −0,19 |
| Note B | 3.149 | −0,16 |
| Note C | 7.961 | −0,14 |
| Sichtprüfung „ja“ (78 Kästen) | 160 | −0,18 |
| Sichtprüfung „nein“ (12 Kästen) | 23 | −0,29 |
| Sichtprüfung „unsicher“ (8 Kästen) | 18 | −0,09 |
| derselbe Kasten nach altem Stand: Note A | 19 | −0,11 |
| nach altem Stand ungültig (Steigung der Schlusskurse) | 8.363 | −0,15 |
| nach altem Stand ungültig (Pendel ohne Band) | 880 | −0,06 |

- **Noten:** Auf 5 Min ist Note A in keiner der vier Varianten besser als B oder C (beim Ausbruch gleichauf mit B,
  sonst am schlechtesten).
- **Sichtprüfung:** Von den 140 Sichtprüfungs-Bildern ließen sich 98 Kästen Trades zuordnen (gleiche Aktie, Tag, Zeitebene
  und Kastenbeginn).
  - Für „nein“ sind es nur 12 Kästen, zu wenig für eine Aussage.
  - Die „ja“-Kästen sind nicht besser als der Durchschnitt.

### Die Einstiege auf denselben Kästen

4.166 Kästen hatten mehr als einen Einstieg.

| Einstieg | Trades | Ø R |
|---|---:|---:|
| Ausbruch | 4.508 | −0,17 |
| Fehlschlag | 2.223 | −0,20 |
| Retest | 1.310 | −0,20 |
| früher Einstieg | 2.183 | −0,53 |

Auf denselben Kästen verliert der frühe Einstieg am meisten. Er scheitert dort oft „gegen den Markt“ (563) und als
Fehlausbruch (553), und deutlich öfter als die anderen Einstiege an „Stop zu eng“ (166).

### Was wäre wenn (nur Suchdaten, nur Information, keine Regel)

Ø R nach Kosten, Note A.

| Variante | wie gerechnet | Stop 1 ATR | Stop 1,5 ATR | Ziel 1 R | Ziel 2 R | ohne Einstieg nach 14:30 |
|---|---:|---:|---:|---:|---:|---:|
| 5 Min · Ausbruch | −0,11 | −0,18 | −0,11 | −0,11 | −0,10 | −0,10 |
| 5 Min · Retest | −0,31 | −0,29 | −0,22 | −0,25 | −0,32 | −0,24 |
| 5 Min · früher Einstieg | −0,27 | −0,21 | −0,17 | −0,29 | −0,24 | −0,31 |
| 5 Min · Fehlschlag | −0,23 | −0,30 | −0,23 | −0,24 | −0,24 | −0,19 |
| alle 13.293 Trades | −0,15 | −0,20 | −0,13 | −0,16 | −0,15 | −0,16 |

- **5 Min:** Keine Änderung macht eine Variante positiv.
- **15 Min:** Die Zahlen stehen im Analyse-Bericht. Dort gibt es nur 3 bis 45 Trades je Variante.
- **Wenn etwas davon weiterverfolgt wird,** ist es eine neue Idee im Register und muss auf den Bestätigungsdaten bestehen.

### Was ich daraus lese (Information für Rechteck Fassung 3, keine Regel)

1. **Saubere Erkennung bringt nichts.** Note A ist nicht besser als C, und dein „ja“ trennt nicht. Am Kastenbild allein liegt
   der Verlust also nicht.
2. **Der Markt dominiert.** „Gegen den Markt“ ist mit 27 % die größte Verlust-Art.
   - Vorbehalt: Gemessen wird an 0,5 SPY-ATR der eigenen Zeitebene. Auf 5 Min ist das eine kleine Bewegung für einen Trade
     über Stunden. Die Art fängt deshalb breit.
   - So war es in Phase 1 festgelegt. Ich ändere es nach dem Ergebnis nicht.
3. **Der frühe Einstieg und der Retest scheitern oft sofort.** Der Anteil Fehlausbrüche liegt bei 16–19 %. Ein weiterer Stop
   (1,5 ATR) mildert beide am stärksten, macht sie aber nicht positiv.
4. **Der Kurs läuft oft erst einmal in die richtige Richtung.** Im Mittel erreicht ein Trade +0,95 R, aber nur 31 % treffen
   das Ziel. 12 % erreichen es erst nach dem Ausstieg.

### Für die Seite abgelegt

- `lernhub/daten/analyse-rechteck-v1.json`: Kurzfassung mit Anteilen je Art, je Variante (Note A und alle Noten), je Note
  und je Einstieg, dazu MFE/MAE, „Ziel später“, Ausgänge, Sichtprüfung, alter Stand, gleiche Kästen und Was wäre wenn.
- `lernhub/daten/ideen-register.json`: Kopie des Registers. Das Register-Werkzeug schreibt sie ab jetzt bei jeder Änderung
  mit.
- `lernhub/daten/ergebnisse.json`: je Variante das Feld `"ausgaenge": {"ziel", "stop", "tagesende"}`.
  - Gezählt sind die Trades mit Note A, also dieselben, die in `trades` der Variante stehen.

### Sichtprüfungen vorbereitet (nicht als sichtpruefung.json veröffentlicht)

**`lernhub/daten/einstieg-1.json`** (art `einstieg`):
- Auswahl: 30 Trades mit Note A, gemischt aus allen 8 Varianten (je Variante zufällig, dann reihum), Startwert 20261103.
- Bild im Moment des Einstiegs mit:
  - Kasten;
  - Einstieg;
  - Stop nach Regel und nach Mindest-Stop;
  - Ziel;
  - Ausbruchs- bzw. Retest-Kerze;
  - dem Regeltext des Einstiegs.
- Frage: „Ist der Einstieg nach der Regel richtig gesetzt?“

**`lernhub/daten/verlust-1.json`** (art `verlust`):
- Auswahl: 30 zufällige Verlust-Trades mit Note A (gleichmäßig aus allen), Startwert 20261104.
- Bild: ganzer Tag mit Ausstieg, dazu die SPY-Schlusskurse des Tages für „Gegen den Markt“.
- Antworten über `optionen` wie in Abschnitt 5.
- Die automatische Zuordnung bleibt im lokalen Schlüssel, damit dein Blick unbeeinflusst bleibt.

**Für beide gilt:**
- Ids b01–b30.
- Die Schlüssel mit Trade-Kennung und Hash bleiben lokal.
- Online erst, wenn die neue Seite auf main ist.

## 4. Phase 3: Doppelboden Schritt 1

### Erkennung

Code `muster/doppelboden.py`, Hash `9d6347afba55`. Die Regeln sind die aus Abschnitt 3. **Meine Festlegungen, wo der
Auftrag keine Formel vorgibt** (bitte prüfen):

1. **Muster-ATR:** das Mittel der ATR von B1 bis B2. P ist das höchste Hoch zwischen den Böden.
2. **Bodentoleranz:** Für „dazwischen“ und im Bild ist sie die Toleranz der gleichen Höhe (0,5 | 0,3 ATR, gelockert 1 | 0,6).
3. **Note A:**
   - „klarer Vortrend“ heißt mindestens das 1,5-Fache des Mindest-Rückgangs (Tag 4,5 ATR, intraday 3 ATR);
   - „höchstens ein weiterer Wendepunkt“ zählt bekannte Wendepunkte strikt zwischen B1 und B2, ohne P.
4. **Wann ein W reif ist:**
   - Ein W ist ab B2 + 3 (Tag) bzw. B2 + 2 Kerzen (intraday) bekannt und dann reif (Reifegrad 2).
   - Schließt der Kurs schon vorher über P + 0,1 ATR oder mehr als 0,3 ATR unter dem tieferen Boden, wird das W nur gezählt
     („vor der Reife erledigt“), ohne Einstieg.
5. **Ende eines W:** Es ist höchstens ein W gleichzeitig aktiv. Es endet:
   - mit der Bestätigung;
   - mit dem Scheitern (Schluss mehr als 0,3 ATR unter dem tieferen Boden);
   - mit der Frist.
6. **Reifegrad 1** (B1 nach Vortrend, P steht) liefert nur den frühen Einstieg an der Bodenlinie. Ziel P − 0,15 ATR,
   Stop „tieferer Boden − 0,3 ATR“.
7. **Merkmale** (nur mitgeschrieben) nutzen keine Kerzen nach dem Moment, in dem das W bekannt wird.
   - Ein solcher Fall (Breite des zweiten Bodens) fiel im Abschneide-Test auf. Ich habe ihn vor der Diagnose behoben und als
     eigenen Test aufgenommen.
8. **Doppeltop** (gespiegelt) kommt mit der Vorab-Datei; Schritt 1 deckt nur den Doppelboden ab.

### Pflichttests (künstliche Kurse, alle grün)

- **Grundfälle:**
  - Ein lehrbuchreines W wird A, auf 5 Min und auf Tageskerzen.
  - Ohne Vortrend gibt es keinen Doppelboden.
  - Böden 0,8 ATR auseinander ergeben höchstens C (Tag: C; intraday: keiner, gelockert ist dort nur 0,6 ATR erlaubt).
  - Ein W über zwei Tage wird intraday nicht erkannt.
  - Eine Bestätigung nach der Frist zählt nicht.
- **Abschneide-Test:** Mit Daten nur bis zur Entscheidung entstehen dieselben Muster.
- **Die vier Einstiege:**
  - Ausbruch: Stop P − H/2, Ziel P + H;
  - früher Einstieg: Stop am Boden − 0,3 ATR, Ziel P − 0,15 ATR;
  - Fehlschlag: Stop höchstes Hoch seit B2 + 0,1 ATR, Ziel Boden − H;
  - Retest.
- **Daten im Bild:** Trichter, Linien und das Datum bei Tageskerzen.

### Abschneide-Test auf echten Daten

Je Zeitebene 100 zufällige Entscheidungen (Startwert 20261105): **300 von 300** liefern mit Daten nur bis zur Entscheidung
denselben Schnappschuss-Hash.

### Suchdaten und Universum

| | Tag | 15 Min | 5 Min |
|---|---|---|---|
| Zeitraum | 01.10.2016 – 30.09.2020 | 01.10.2021 – 29.09.2023 | 01.10.2021 – 29.09.2023 |
| Werte | 1.333 mit Kerzen in diesem Zeitraum (189 ohne) | die 50 | die 50 |
| Filter | je Tag (Kurs über 5 $, Ø Umsatz 20 Tage mindestens 10 Mio. $), Vorlaufzeit 14 Tage | – | – |

Kurse nach dem 30.09.2020 (Tag) bzw. nach dem 29.09.2023 (intraday) wurden nicht geladen.

### Trichter (Paare B1/B2 bekannter Wendepunkte, streng geprüft; „übrig“ in Reihenfolge)

| Regel | Tag übrig | nur diese | 15 Min übrig | nur diese | 5 Min übrig | nur diese |
|---|---:|---:|---:|---:|---:|---:|
| Kandidaten | 1.617.172 | | 70.527 | | 998.944 | |
| Filter je Tag und Vorlaufzeit | 1.274.865 | 7.261 | – | – | – | – |
| Abstand B1 → B2 | 580.109 | 8.604 | 51.442 | 2.013 | 815.436 | 18.978 |
| Zwischenhoch | 576.623 | 671 | 49.028 | 633 | 807.781 | 1.434 |
| Böden gleich hoch | 53.199 | 224.246 | 6.052 | 28.970 | 62.188 | 454.797 |
| Vortrend | 34.224 | 10.709 | 4.874 | 983 | 52.648 | 5.900 |
| dazwischen | 23.006 | 10.110 | 4.603 | 224 | 34.498 | 16.166 |
| Umkehr an B1 | 22.475 | 482 | 4.493 | 100 | 33.517 | 905 |
| Umkehr an B2 | 21.922 | 540 | 4.373 | 120 | 32.495 | 1.022 |
| nicht vor der Reife erledigt | 20.671 | 1.251 | 4.021 | 352 | 31.503 | 992 |

- **Einheit:** Gezählt wird je Paar. Zu einem B2 gehören oft mehrere mögliche B1, die Erkennung nimmt davon eines. Deshalb
  liegen die Muster unten unter der letzten Zeile.
- **Größte Bremse:** die gleiche Höhe der Böden.

### Muster je Note und Jahr (W im Reifegrad 2, Suchdaten)

| | Jahr 1 A / B / C | Jahr 2 | Jahr 3 | Jahr 4 | zusammen | davon A |
|---|---|---|---|---|---:|---:|
| Tag | 175 / 1.730 / 1.820 | 176 / 1.817 / 1.911 | 196 / 1.957 / 2.116 | 183 / 2.062 / 2.227 | 16.370 | 730 (4 %) |
| 15 Min | 362 / 1.313 / 1.752 | 375 / 1.447 / 1.764 | – | – | 7.013 | 737 (11 %) |
| 5 Min | 800 / 7.796 / 8.336 | 796 / 7.966 / 8.312 | – | – | 34.006 | 1.596 (5 %) |

### Bestätigt oder gescheitert

| | bestätigt | gescheitert | abgelaufen | offen | vor der Reife bestätigt |
|---|---:|---:|---:|---:|---:|
| Tag | 6.786 (41 %) | 6.066 (37 %) | 3.073 | 445 | 1.619 |
| 15 Min | 1.132 (16 %) | 942 (13 %) | 2.926 | 2.013 | 682 |
| 5 Min | 7.052 (21 %) | 10.173 (30 %) | 12.727 | 4.054 | 1.726 |

- **„offen“:** auf Tageskerzen am Zeitraumende, intraday am Tagesende vor der Frist.
- **Nur Note A:** Tag 330 bestätigt gegen 307 gescheitert; 15 Min 128 gegen 123; 5 Min 352 gegen 517.

### Zeitbudget (intraday)

| | Bestätigungen | zu spät für einen Einstieg (ab 15:30) | Anteil | Regel |
|---|---:|---:|---:|---|
| 15 Min | 1.132 | 421 | 37 % | wird gehandelt (nicht mehr als die Hälfte) |
| 5 Min | 7.052 | 1.327 | 19 % | wird gehandelt |

### Auffällig (Information)

- **Intraday sehr viele W:** Auf 5 Min sind es 34.006 W in zwei Jahren auf 50 Aktien, also etwa 1,4 je Aktie und Tag.
  Fast alle haben Note B oder C. Ob das saubere Doppelböden sind, zeigt erst deine Sichtprüfung. Bei unter 80 % „ja“ werden
  die Nein-Bilder untersucht, bevor eine Regel geändert wird.
- **Tag:** 16.370 W auf 1.333 Werten in vier Jahren; 1.180 Werte haben mindestens eines.

### Sichtprüfung doppelboden-1 (vorbereitet, nicht veröffentlicht)

`lernhub/daten/doppelboden-1.json`.

**Auswahl:**
- 30 Bilder, je 10 Tag, 15 Min und 5 Min, Startwert 20261106.
- Gezogen aus den Entscheidungen bei einem W im Reifegrad 2 (Ausbruch über P oder Fehlschlag). Je Wert (Tag) bzw. Wert und
  Tag (intraday) höchstens ein Bild.
- Tag nur an handelbaren Tagen.

**Bild:**
- blind, ohne Note und Punkte; das Bild endet an der Signalkerze.
- Tag: 120 Kerzen vor der Entscheidung, früher, wenn das Vortrend-Fenster davor liegt.

**Datenvertrag wie in Abschnitt 6:**
- `muster: "Doppelboden"`;
- `zeitebene` 5, 15 oder 1440;
- bei 1440 ist das erste Feld jeder Kerze das Datum;
- `oben` = P, `unten` = Bodenlinie, `box_von` = B1, `box_bis` = B2, `toleranz` = Bodentoleranz;
- `beruehrungen` = B1, P, B2;
- dazu `linien` mit `von {i,p}`, `bis {i,p}` und `art` „boden“ (B1 → B2), „nacken“ (P bis zur Signalkerze) und „form“ (das
  W vom Beginn des Vortrends bis zur Signalkerze).

Der Schlüssel mit Note, Punkten und Hash bleibt lokal. Online erst, wenn die Seite das W zeichnet und auf main ist.

## 5. Ideen-Register

- H1 (Doppelboden und Doppeltop) steht auf „läuft“, Regel-Hash Erkennung `9d6347afba55`, noch ohne Einstiege.
- N bleibt 132; die Varianten kommen mit der Vorab-Datei.
- Kopie für die Seite: `lernhub/daten/ideen-register.json`.

## 6. Vorbehalte

1. **Überlebensverzerrung** (vor allem auf Tageskerzen): Die Liste der 1.500 ist von heute. 189 Werte hatten im Suchzeitraum
   noch keine Kerzen, abgemeldete Werte fehlen ganz. Der Zufallstest nimmt dieselbe Aktie an anderen Tagen und gleicht so
   einen Teil der Überlebensverzerrung aus. Ganz beseitigt ist sie nicht.
2. **Keine frischen Daten:** Die Analyse von Rechteck v1 läuft auf denselben Daten, auf denen v1 gerechnet wurde. „Was wäre
   wenn“ ist deshalb nur Information; jede Idee daraus muss auf den Bestätigungsdaten bestehen.
3. **„Gegen den Markt“ fängt breit** (siehe Abschnitt 3).
4. **Alte Sichtprüfungen:** Die Runden 1 und 2 waren mit älterem Code. Die Zuordnung über den Kastenbeginn findet deshalb
   nicht jedes Bild wieder (98 von 140).
5. **Leihgebühren** für short sind nicht modelliert.

## 7. Was nicht angefasst wurde

- Pi, Live-Bot und main: unberührt. Kein Bot-Code auf GitHub.
- Prüftopf ab 01.10.2023: zu. Auf Tageskerzen wurden auch die Bestätigungsjahre (ab Okt. 2020) nicht geladen.
- Keine neuen Trades, keine Doppelboden-Trades, kein R für den Doppelboden.

**STOPP.**

**Als Nächstes, nach deinem OK:**
- die neue Seite mit:
  - den Knöpfen aus `optionen`;
  - dem W über `linien`;
  - Datum bei 1440;
  - dem Register als Tabelle;
  - den Ausgängen je Variante;
- danach die Sichtprüfungen doppelboden-1, einstieg-1 und verlust-1;
- dann die Vorab-Datei des Doppelbodens (Phase 4).
