# Werkbank Doppelboden · Auftrag Fassung 1

Stand Di 03.11.2026, Claude im Chat. Grundlage ist die Werkbank Rechteck (`grosse-umstellung-v2-zielsetzung.md`,
Erkennung Fassung 2.2, Lauf `e0fe5e0efe43`). Alles hier ist **vor jedem Ergebnis** festgelegt. Gerechnet werden in
Schritt 1 nur Geometrie und Bilder, keine Trades und kein R.

## 1. Ziel

- **Ein Muster:** der Doppelboden. Zwei Tiefs etwa auf gleicher Höhe nach einem Rückgang, dazwischen ein Zwischenhoch
  (die Nackenlinie). Bestätigt ist er erst, wenn der Kurs über der Nackenlinie schließt.
- **Eine eigene, strenge Erkennung** wie beim Rechteck: Wendepunkte in ATR, Reifegrad 0–4, Note A/B/C, Schnappschuss im
  Moment der Entscheidung, geeicht mit dem Auge des Inhabers.
- **Zwei Arme mit derselben Erkennung:**
  - **Tag:** Tageskerzen, Positionen über mehrere Tage. Hier sind die Kosten im Verhältnis zum Stop klein.
  - **Intraday:** 5 und 15 Minuten, alles an einem Tag, wie beim Rechteck.
- Die alten Doppelboden-Ergebnisse (Runde 2, Lerntopf-Lauf 1) stammen aus der alten, lockeren Erkennung. Sie gelten hier
  nicht als Beleg, weder dafür noch dagegen.

## 2. Was wir vom Rechteck übernehmen (fest)

1. Alle Abstände und Toleranzen in **ATR**, nie in Prozent. Intraday: ATR je Tageszeit (20 Vortage). Tag: ATR 14.
2. Ein Wendepunkt ist erst bekannt, wenn er bestätigt ist (k Kerzen später). Keine Rückschau.
3. **Die Punktzahl ordnet nur.** Noten entstehen aus harten Bedingungen.
4. **Diagnose-Trichter von Anfang an:** je Regel „übrig, nur diese, insgesamt“, je Zeitebene. So sehen wir sofort,
   welche Regel wie viele Kandidaten kostet.
5. **Sichtprüfungen:** Präzision mindestens 80 % „ja“, blind und allein. Danach Grenzfälle und Trefferquote mit Zeichnungen.
6. **Kriterium „Note A besser als Note C“ bleibt.** Es prüft direkt, ob die saubere Erkennung etwas bringt. Beim Rechteck
   brachte sie nichts.
7. Mindest-Stop, Kostenmodell, Kostenstress und Zufallstest wie in Werkbank Rechteck v1.
8. Intraday: das Zeitbudget von Anfang an zählen. Beim Rechteck kamen auf 15 Min 53 von 99 Ausbrüchen zu spät.

## 3. Erkennung (Startwerte, werden mit dem Auge geeicht)

Bezeichnungen: **B1** erster Boden, **P** Zwischenhoch (Nackenlinie), **B2** zweiter Boden,
**Bodenlinie** = Mittel aus B1 und B2, **Höhe H** = P − tieferer Boden.

| Regel | Tag | 5 Min / 15 Min |
|---|---|---|
| Wendepunkt | 3 Kerzen je Seite und mindestens 1 ATR Schwung zum vorigen Gegen-Wendepunkt | 2 Kerzen je Seite und mindestens 0,5 ATR |
| Vortrend vor B1 | Rückgang mindestens 3 ATR in den 30 Kerzen vor B1 | Rückgang mindestens 2 ATR, nur am selben Tag |
| Gleiche Höhe der Böden | \|B2 − B1\| höchstens 0,5 ATR | höchstens 0,3 ATR |
| Zwischenhoch | P mindestens 2 ATR über dem tieferen Boden | mindestens 1,5 ATR |
| Abstand B1 → B2 | 10 bis 80 Kerzen | 5 Min mindestens 10, 15 Min mindestens 6 Kerzen; alles am selben Tag, B1 frühestens 09:45 |
| Dazwischen | kein Schluss unter dem tieferen Boden − Toleranz, kein Schluss über P | ebenso |
| Echte Umkehr an B1 und B2 | Kerze schließt in der oberen Hälfte ihrer Spanne oder die nächste Kerze schließt höher | ebenso |
| Bestätigung | Schluss mindestens 0,1 ATR über P, höchstens 30 Kerzen nach B2 | höchstens 12 (5 Min) bzw. 6 (15 Min) Kerzen nach B2 |
| Ungültig | Schluss mehr als 0,3 ATR unter dem tieferen Boden vor der Bestätigung (das ist ein Fehlschlag, siehe Einstieg D) | ebenso |

**Reifegrad (der Indikator):**
- 0 nichts;
- 1 B1 nach Vortrend, P steht;
- 2 B2 bestätigt, das W ist sichtbar, die Nackenlinie steht fest;
- 3 Auslöser eines Einstiegs;
- 4 im Trade.

**Noten:**
- **A:** alle Regeln streng. Dazu:
  - Böden höchstens 0,25 ATR (Tag) bzw. 0,15 ATR (intraday) auseinander;
  - klarer Vortrend;
  - zwischen B1 und B2 höchstens ein weiterer Wendepunkt (kein Zickzack).
- **B:** alle Regeln streng, aber nicht A.
- **C:** nur mit gelockerter Bodentoleranz gültig (bis 1 ATR Tag, 0,6 ATR intraday). Gemessen, nie gehandelt.

**Merkmale mitschreiben, nicht filtern:**
- Volumen an B1 gegen B2 (laut Bulkowski ist es am linken Boden meist höher);
- Form der Böden (spitz oder rund, gemessen als Breite des Bodens in Kerzen);
- Abstand B1–B2;
- H in ATR und in Prozent;
- Tag: Lage zum 50- und 200-Tage-Durchschnitt, Lücke am Ausbruchstag;
- intraday: Uhrzeit und Morgenlücke;
- SPY-Richtung;
- die Punktzahl.

## 4. Vier Einstiege (dieselben Muster, nur der Einstieg ist anders)

**Für alle gilt:**
- **Muster:** Das Muster ist an der Kerze vor dem Auslöser eingefroren: Linien, Toleranz und Note ändern sich nicht mehr.
- **Tag:**
  - Entscheidung am Tagesschluss, Einstieg zur Eröffnung des nächsten Handelstags.
  - Ausstieg bei Ziel, Stop oder nach 20 Handelstagen zum Schluss.
  - Öffnet ein Tag jenseits des Stops, gilt der Eröffnungskurs (Kurslücke über Nacht).
- **Intraday:** genau wie beim Rechteck. Entscheidung am Kerzenschluss + 33 s, Einstieg zur nächsten SIP-Minute, keine
  Einstiege in den ersten 20 und den letzten 30 Minuten, Ausstieg spätestens 15:50.
- **Mindest-Stop:** intraday max(0,5 ATR; 0,15 %), Tag max(0,5 ATR; 0,5 %). Ein engerer Stop wird aufgeweitet, das Ziel bleibt.
- **Höchstens ein Trade** je Einstieg, Zeitebene, Note, Aktie und Muster.

**Die vier Einstiege:**
- **A · Ausbruch über die Nackenlinie:**
  - Auslöser: Schluss mindestens 0,1 ATR über P.
  - Stop: P − H/2.
  - Ziel: P + H.
- **B · Retest der Nackenlinie:**
  - Zuerst ein Ausbruch wie A, ohne Einstieg.
  - Innerhalb von 10 Kerzen (Tag), 12 (5 Min) bzw. 6 (15 Min) kommt ein Docht auf höchstens 0,15 ATR an P zurück, ohne
    Schluss unter P.
  - Auslöser: Die nächste Kerze schließt über dem Hoch der Retest-Kerze.
  - Stop: Tief der Retest-Kerze − 0,1 ATR.
  - Ziel: P + H.
- **C · Früher Einstieg am zweiten Boden:**
  - Voraussetzung Reifegrad 1.
  - Auslöser: Eine Kerze erreicht die Bodenlinie (Docht höchstens 0,15 ATR entfernt) und schließt mindestens 0,25 ATR darüber.
  - Stop: tieferer Boden − 0,3 ATR.
  - Ziel: P − 0,15 ATR.
  - Nur wenn das Ziel mindestens 1 R entfernt ist.
- **D · Fehlschlag (short):**
  - Voraussetzung Reifegrad 2.
  - Auslöser: Schluss mindestens 0,1 ATR unter dem tieferen Boden vor der Bestätigung.
  - Stop: höchstes Hoch seit B2 + 0,1 ATR.
  - Ziel: tieferer Boden − H.

**Kosten:** wie Werkbank Rechteck v1.
- Je Trade der höhere Wert aus 0,03 R (long) bzw. 0,05 R (short) und der Slippage.
- Slippage = 2 × max(0,01 $; 0,02 %) / Stop-Abstand.
- Kostenstress + 0,03 R.
- Leihgebühren für short sind nicht modelliert; das gehört in die Vorbehalte.

## 5. Daten und Zeiträume

- **Tag, breit (Wunsch des Inhabers: viele Märkte, um zu lernen, wo es geht und wo nicht):**
  - Tageskerzen aus SIP, split- und dividendenbereinigt.
  - **Universum:**
    - die Liste mit 1.500 US-Werten (`universe_us_1500.csv`);
    - dazu US-gelistete **Länder-ETFs**, als Gruppe „Länder“. Vorschlag: EWA, EWC, EWG, EWU, EWQ, EWI, EWP, EWL, EWN,
      EWD, EWJ, EWY, EWT, EWH, EWS, FXI, INDA, EWZ, EWW, EZA, EPOL, TUR. VS Code prüft, welche es seit 2016 mit genug
      Umsatz gibt.
  - **Filter je Tag**, nur aus Vortagen:
    - Kurs über 5 $;
    - mittlerer Tagesumsatz der letzten 20 Tage mindestens 10 Mio. $.
  - **Aktien direkt an ausländischen Börsen** liefert unsere Datenquelle (Alpaca) nicht, und der Bot könnte sie dort
    auch nicht handeln. Sie kommen erst in Frage, wenn sich ein Muster hier bewährt, mit einer eigenen Datenquelle.
  - Entwicklung 01.10.2016–30.09.2023 (7 Jahre), dazu ein Vorlauf ab 01.01.2016 für ATR und Vortrend.
- **Intraday:** die 50 der Werkbank, 5 und 15 Min, 01.10.2021–30.09.2023, Vorlauf wie beim Rechteck.
- **Prüftopf ab 01.10.2023 bleibt zu.** `daten.py` sperrt jeden Tag ab dann, auch für Tageskerzen.
- **Downloads:** nur außerhalb 15:30–22:00 deutscher Zeit, gedrosselt, nur Marktdaten.
- **Vorbehalt:** Die Überlebensverzerrung wiegt bei 7 Jahren und der Liste von heute schwerer als beim Rechteck. Sie steht
  im Bericht an erster Stelle.

## 6. Sichtprüfung und Seite

- **Runde 1 (Präzision):** 30 Bilder, je 10 Tag (aus allen Werten nach Filter), 15 Min und 5 Min, fester Startwert.
  - Frage: „Ist das ein sauberer Doppelboden?“
  - Blind, ohne Note und Punkte. Das Bild endet an der Signalkerze.
  - Tag: etwa 120 Kerzen vor der Entscheidung zeigen.
- **Datenvertrag wie beim Rechteck, mit diesen Zusätzen:**
  - `muster: "Doppelboden"` je Bild;
  - `zeitebene`: 5, 15 oder **1440** (Tag);
  - bei 1440 ist das erste Feld jeder Kerze das Datum `"YYYY-MM-DD"`;
  - `oben` = P (Nackenlinie), `unten` = Bodenlinie, `box_von` = Index von B1, `box_bis` = Index von B2, `toleranz` =
    Bodentoleranz;
  - `beruehrungen` = B1 und B2 mit `seite: "unten"`, P mit `seite: "oben"`.
- Die Lernhub-Seite zeichnet bei `muster: "Doppelboden"` das W, die Nackenlinie und die Bodenzone statt eines Kastens und
  zeigt bei 1440 Daten statt Uhrzeiten. Das baut Claude. **Runde 1 geht erst online, wenn diese Seite auf main ist.**

## 7. Bewertung (Vorschlag; endgültig in der Vorab-Datei, bevor ein Ergebnis da ist)

- **Tag:**
  - über 7 Jahre nach Kosten positiv;
  - in mindestens 5 von 7 Jahren positiv;
  - mindestens 300 Trades;
  - mit Kostenstress positiv;
  - Zufallstest mindestens 95 von 100;
  - Note A besser als Note C.
- **Intraday:** wie Werkbank Rechteck v1 (beide Jahre positiv mit je mindestens 50 Trades, Kostenstress, Zufall 95, A besser als C).
- **Prüftopf:** nur für Varianten, die überzeugen, mit eigener Vorab-Datei und der Zufallslatte „Bester von N“.
- **Wo es geht und wo nicht:** Die Entscheidung fällt immer auf **allen** Werten zusammen, mit einer Regel für alle.
  - Aufteilungen nach Land, Branche, Größe, Kursniveau oder Volumen werden nur als Information ausgewiesen.
  - Bei 1.500 Werten sieht ein Teil immer zufällig gut aus.
  - Eine auffällige Gruppe ist deshalb eine **neue Hypothese**. Sie braucht eine eigene Vorab-Datei und frische Daten, bevor
    sie zählt.
  - Nie Märkte nach dem Ergebnis auswählen.
- **Das Lernen, die „eigene KI“:** Gelernt wird auf zwei Wegen, beide mit Trennung in Lernen und Prüfen.
  - **Erkennung:** Die Sichtprüfungs-Antworten sind die Lehrbeispiele für ein späteres Bild-Modell.
  - **Erfolg:** Die Merkmale je Trade dienen dazu, Bedingungen zu finden. Gefunden wird auf Jahr 1–4 der Entwicklung,
    bestätigt auf Jahr 5–7, erst dann geht es in den Prüftopf.

## 8. AUFTRAG HEUTE · Schritt 1 (keine Trades, kein R)

1. **Daten:**
   - Tageskerzen der 1.500 und der Länder-ETFs von 01.01.2016 bis 30.09.2023 laden, außerhalb 15:30–22:00 deutscher Zeit.
   - Intraday ist schon im Cache.
   - Melden: je Aktie, ob die Daten vollständig sind.
2. **Erkennung** nach Abschnitt 3 für Tag, 15 Min und 5 Min, mit eigenem Code-Hash. Pflichttests auf künstlichen Kursen:
   - ein lehrbuchreines W wird A;
   - ohne Vortrend gibt es keinen Doppelboden;
   - Böden 0,8 ATR auseinander ergeben höchstens C;
   - ein W über zwei Tage wird intraday nicht erkannt;
   - die Bestätigung erst nach der Frist zählt nicht;
   - der Abschneide-Test: Mit Daten nur bis zur Entscheidung entstehen dieselben Muster.
3. **Diagnose:**
   - Trichter je Zeitebene;
   - Muster je Note und Jahr;
   - wie viele bestätigt, wie viele gescheitert;
   - intraday: wie viele Bestätigungen zu spät für einen Einstieg kommen.
4. **Sichtprüfung 1** nach Abschnitt 6 vorbereiten (`doppelboden-1`). Nur lokal und als Datei auf backtest, **noch nicht als
   `sichtpruefung.json` veröffentlichen**, bis die Seite angepasst ist.
5. **Logbuch** mit Code-Hash und Zahlen, kurzer Bericht an den Inhaber, dann **Stopp**.

**Immer:**
- Nur Paper, keine Live-Freigabe.
- Pi, Live-Bot und main bleiben unberührt (main nur für die Seite und nur nach Freigabe).
- Bot-Code nicht auf GitHub.
- Keine Läufe über Nacht auf dem Hauptrechner.
- Keine Regel ändern, nachdem ein Ergebnis gelesen wurde.
