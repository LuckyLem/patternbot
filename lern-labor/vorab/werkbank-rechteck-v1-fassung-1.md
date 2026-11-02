# Vorab-Datei · Werkbank Rechteck v1 · Fassung 1

**Stand 28.10.2026.** Grundlage: Auftrag „Große Umstellung v2“ (Fassung 2.1), Abschnitte 5 bis 9, mit der
Erkennung Fassung 2.2. SHA-256 und Commit dieser Datei stehen im Logbuch. **Kein Lauf vor dem OK des Inhabers.**

Vor dieser Datei wurde kein Ergebnis gelesen. Auf echten Daten liefen bis jetzt nur:
- die Erkennung (nur Geometrie);
- die Abschneide-Tests;
- die Diagnose „warum so wenige A“ (nur Geometrie, Zählungen von Tagen);
- die vier Sichtprüfungen.

Keines davon rechnet Trades oder R. Nach Ergebnissen ändert sich nichts mehr. Eine Änderung ergibt eine neue Fassung,
und das nur, bevor Ergebnisse da sind.

## 1. Was festgelegt ist

| Punkt | Wert |
|---|---|
| Erkennung | Fassung 2.2, Code-Hash `2489765016f5` (`lern_labor/werkbank/daten.py` + `rechteck.py`), festgelegt nach Sichtprüfung 4 (24 von 30 ja) |
| Vergleichsstand | `8454cdc07786`, eingefroren als `rechteck_8454cdc07786.py`, nur für die Merkmale in Abschnitt 8 |
| Aktien | die 50 aus `lernhub/aktien.json`, SHA-256 `541d9b83529d68b26ff7681964321c19acd4dee15f5ed4f9136dd7f89843a663` (höchster mittlerer Tagesumsatz in Dollar im September 2021 aus unserer Liste von 150) |
| Zeitraum | nur 01.10.2021 – 30.09.2023 (502 Handelstage). Jahr 1 = 01.10.2021 – 30.09.2022 (252 Tage), Jahr 2 = 01.10.2022 – 29.09.2023 (250 Tage) |
| Vorlauf | SIP 1 Min ab 02.08.2021 nur für das ATR je Tageszeit und den Vortagesschluss; keine Signale davor |
| Prüftopf | bleibt zu; `daten.py` sperrt jeden Tag ab 01.10.2023 |
| Daten | SIP 1 Min, split-bereinigt, nur 09:30 – 16:00 New York, nur aus dem Cache (kein Abruf); 5 und 15 Min daraus zusammengesetzt |
| Zeit | im Code nur New York |
| Zufall | Startwert `20261028` |

**Note in Fassung 2.2** (je Kasten im Moment der Entscheidung):
- **A:** nur aus dem strengen Durchgang (Toleranz 0,15 ATR, höchstens 10 % der Höhe). Dazu:
  - mindestens 2 + 2 Berührungen;
  - Passgüte höchstens 0,08 ATR;
  - kein Docht außerhalb des strengen Bands;
  - kein unruhiges Bein (gemessen mit Band ± 10 % der Höhe).
- **B:** streng gültig, aber nicht A.
- **C:** nur mit der gelockerten Toleranz gültig (Berührung und Schluss bis 0,3 ATR, höchstens 10 % der Höhe; ein
  Docht bis 0,6 ATR).

Die Punktzahl ordnet nur, sie entscheidet keine Note.

## 2. Die Kästen

Alle Kästen der Erkennung 2.2 an den 50 Aktien im Zeitraum, aller Noten. Erkennung Kerze für Kerze, nur mit dem Wissen
bis zur jeweiligen Kerze.

Stand der Erkennung (nur Geometrie, aus `zusammenfassung.json`):
- **15 Min:** 1.036 Kästen (A 301, B 228, C 507);
- **5 Min:** 10.108 Kästen (A 1.964, B 2.000, C 6.144).

Gemessen werden alle Noten. Als „gehandelt“ zählt nur Note A.

## 3. Vier Einstiege (Abschnitt 5)

Für alle vier gilt:
- **Kasten:** der Kasten, der an der Kerze vor dem Auslöser gültig war (Linien, Toleranz, Note eingefroren). Bei B und
  D ist es der Kasten an der Kerze vor dem Ausbruch.
- **ATR:** das Kasten-ATR dieses Kastens, also das Mittel der ATR je Tageszeit über die Kasten-Kerzen. Es ist dasselbe
  ATR wie für Toleranz, Höhe und Passgüte.
- **Entscheidung:** am Schluss der Auslöserkerze + 33 s.
- **Einstieg:** zum Eröffnungskurs der SIP-Minute, die eine Minute nach dem Kerzenschluss beginnt (Kerze bis 10:30 →
  Minute 10:31). Fehlt diese Minute, gilt die nächste vorhandene Minute, solange sie im Einstiegsfenster liegt;
  sonst kein Trade.
- **Einstiegsfenster:** Die Einstiegsminute beginnt frühestens 09:50 und vor den letzten 30 Minuten (sonst 15:30, an
  Halbtagen 12:30). Halbtage im Zeitraum: 26.11.2021, 25.11.2022, 03.07.2023.
- **Ausstieg:** Ziel, Stop oder Tagesende.
  - Das Tagesende ist der Eröffnungskurs der Minute 15:50, an Halbtagen 12:50.
  - Kein Break-even, kein Trailing, nichts über Nacht.
- **Mindest-Stop:**
  - Der Abstand Einstieg–Stop beträgt mindestens max(0,5 × Kasten-ATR; 0,15 % vom Einstiegskurs).
  - Gemessen wird vom tatsächlichen Einstiegskurs.
  - Ein engerer Stop wird auf dieses Minimum aufgeweitet, das Ziel bleibt.
  - Funktion: `mindest_stop` in `rechteck.py`, mit Pflichttest.
- **Kein Trade, wenn:**
  - der Einstiegskurs schon auf oder jenseits des Stops bzw. des Ziels liegt;
  - das Ziel nicht in Richtung des Trades liegt.

  Gezählt wird das als „verworfen“, mit Grund.
- **Höchstens 1 Trade:** je Einstieg, Zeitebene, Note, Aktie und Tag, und zwar der erste. Die Noten werden getrennt
  gezählt, damit ein früher C-Auslöser keinen späteren A-Trade verdrängt.
- **Richtung:** long und short.
- **Rechnung:** Jeder Trade zählt für sich in R. Es gibt kein Kapital und keine Positionsgrenze; live wären es
  höchstens 5 Positionen mit 0,5 % Risiko.

**A · Ausbruch**
- **Auslöser:** Die Kerze schließt mindestens 0,1 ATR über der oberen Linie (long) bzw. unter der unteren (short).
- **Stop:** Mitte des Kastens.
- **Ziel:** gebrochene Linie ± Kastenhöhe.

**B · Retest**
- **Zuerst:** ein Ausbruch wie bei A, ohne Einstieg.
- **Retest-Kerze:** Innerhalb der 6 Kerzen (15 Min) bzw. 12 Kerzen (5 Min) nach der Ausbruchskerze kommt ein Docht auf
  höchstens 0,15 ATR an die gebrochene Linie heran. Bei long reicht das Tief bis Linie + 0,15 ATR. Die Kerze darf dabei
  nicht zurück im Kasten schließen: long Schluss über der oberen Linie, short unter der unteren.
- **Auslöser:** Die nächste Kerze schließt über dem Hoch (long) bzw. unter dem Tief (short) der Retest-Kerze.
  - Erfüllt die nächste Kerze das nicht, kann eine spätere Kerze im Fenster eine neue Retest-Kerze sein.
  - Der Auslöser darf die Kerze direkt nach dem Fenster sein.
- **Stop:** Tief der Retest-Kerze − 0,1 ATR (long) bzw. Hoch + 0,1 ATR (short).
- **Ziel:** gebrochene Linie ± Kastenhöhe.
- **Kein B-Trade:** wenn vorher eine Kerze zurück im Kasten schließt.

**C · Abpraller**
- **Voraussetzung:** Der Kasten ist reif (Stufe 2).
- **Auslöser:** Eine Kerze berührt eine Linie (Docht höchstens 0,15 ATR von der Linie entfernt) und schließt mindestens
  0,25 ATR innerhalb des Kastens. Entschieden wird am Schluss dieser Kerze.
- **Richtung:** zur anderen Seite, also an der unteren Linie long, an der oberen short.
- **Stop:** Linie − 0,3 ATR (long) bzw. Linie + 0,3 ATR (short).
- **Ziel:** gegenüberliegende Linie − 0,15 ATR (long) bzw. + 0,15 ATR (short).
- **Nur wenn** das Ziel mindestens 1 R vom tatsächlichen Einstieg entfernt ist, mit dem Stop nach dem Mindest-Stop.

**D · Fehlausbruch**
- **Zuerst:** ein Ausbruch wie bei A, ohne Einstieg.
- **Auslöser:** In den 3 Kerzen nach der Ausbruchskerze schließt eine Kerze wieder mindestens 0,1 ATR innerhalb des
  Kastens. Entschieden wird am Schluss dieser Kerze.
- **Richtung:** gegen den Ausbruch.
- **Stop:** Extrem des Ausbruchs von der Ausbruchskerze bis zur Auslöserkerze ± 0,1 ATR:
  - short nach einem Ausbruch nach oben: höchstes Hoch + 0,1 ATR;
  - long nach einem Ausbruch nach unten: tiefstes Tief − 0,1 ATR.
- **Ziel:** gegenüberliegende Linie (short: untere, long: obere).

**Simulation auf SIP 1 Min:**
- Ab der Einstiegsminute zählen Hoch und Tief nach ihrer Eröffnung.
- Berühren Stop und Ziel dieselbe Minute, zählt der Stop.
- Öffnet eine Minute jenseits des Stops, zählt ihr Eröffnungskurs.
- Der Stop füllt am Stop, sobald das Tief bzw. Hoch ihn erreicht.
- Das Ziel füllt nur, wenn der Kurs durch das Ziel handelt (long Hoch über dem Ziel, short Tief darunter), und dann
  zum Zielkurs.

**R:**
- r_vor = (Ausstieg − Einstieg) / (Einstieg − Stop), bei short mit umgekehrtem Vorzeichen; dabei gilt der Stop nach dem
  Mindest-Stop.
- r = r_vor − Kosten (Abschnitt 4).

## 4. Kosten, Kostenstress und Zufallstest (Abschnitt 7)

- **Kosten je Trade:** der höhere Wert aus 0,03 R (long) bzw. 0,05 R (short) und der Slippage.
  - Slippage = 2 × max(0,01 $; 0,02 % vom Einstiegskurs), geteilt durch den Stop-Abstand.
- **Kostenstress:** zusätzlich + 0,03 R je Trade.
- **Zufallstest**, je echtem Trade mit Note A in derselben Variante:
  - gleiche Aktie, gleiche Uhrzeit (dieselbe Einstiegsminute), gleiche Richtung;
  - ein zufälliger anderer Handelstag, höchstens 20 Handelstage entfernt und im Zeitraum 01.10.2021 – 30.09.2023;
  - gleicher Stop-Abstand in % vom Einstieg, gleiches Ziel in R, gleiche Ausstiegsregeln (Tagesende 15:50) und Kosten.
  - Gezogen wird nur unter Tagen mit SIP-Minuten zu dieser Zeit. Gibt es keinen, fällt der Trade aus dem Zufallstest;
    gezählt wird das.
  - 100 Läufe, Startwert `20261028`, je Lauf eine eigene feste Folge.
  - **Ergebnis „Zufall“:** die Zahl der Läufe (0 – 100), in denen das echte Ø R nach Kosten höher ist als das Ø R des
    Zufallslaufs.

## 5. Varianten und Auswertung

- **8 Varianten:** Einstieg A, B, C, D × 15 und 5 Min. Zuerst 15 Min (alle vier Einstiege), dann 5 Min.
- **In jeder Variante werden die Noten A, B und C getrennt gemessen.** Als „gehandelt“ zählt nur Note A.
- **Je Variante (Note A):**
  - Trades, Ø R vor Kosten, Ø R nach Kosten;
  - Profitfaktor nach Kosten (Summe der Gewinne / Summe der Verluste in R);
  - je Jahr Trades und Ø R;
  - Ø R mit Kostenstress;
  - Zufall 0 – 100.
- **Je Note:** Trades und Ø R nach Kosten.

**„Überzeugt“** (Abschnitt 6, Punkte 1 – 4 unverändert, alles nach Kosten, nur Note A):
1. Beide Jahre positiv, je mindestens 50 Trades; darunter heißt es „zu wenig Daten“.
2. Über beide Jahre mit Kostenstress (+ 0,03 R) noch positiv.
3. Schlägt den Zufallstest in mindestens 95 von 100 Läufen.
4. Note A besser als Note C (Ø R nach Kosten). Sonst bringt die saubere Erkennung nichts, und das Muster fliegt raus.

Note C heißt in Fassung 2.2: Der Kasten ist nur mit der gelockerten Toleranz gültig (Abschnitt 1). Hat eine Variante
keine C-Trades, ist Punkt 4 „nicht bewertbar“, und die Variante überzeugt nicht.

## 6. Bericht (Abschnitt 13, Schritt 6)

- **Zuerst die Vorbehalte:**
  - **Überlebensverzerrung:** Die 150 sind die Liste von heute, die 50 daraus nach dem Umsatz im September 2021.
    Firmen, die es heute nicht mehr gibt, fehlen.
  - **Präzision der Erkennung:** In Sichtprüfung 4 waren 80 % der A-Kästen für das Auge sauber, auf 5 Min nur 73 %
    (11 von 15). Etwa jeder vierte A-Kasten auf 5 Min ist also kein sauberes Rechteck.
  - **Form am selben Zeitraum geeicht:** Die Regeln der Form wurden an Bildern aus demselben Zeitraum geeicht (nur
    Sichtprüfung, nie Ergebnisse).
  - **Einzelne Trades:** ohne Kapital und ohne Positionsgrenze.
- **Dann die 8 Varianten** mit Note A, B und C.
- **Dann, welche überzeugt.**
- Für 2024 – 2025 wird nichts geöffnet; die Vorab-Datei der Prüfung kommt nur als Entwurf, erst nach OK.

## 7. Schnappschüsse und Seiten-Daten (Abschnitte 8 und 9)

**Schnappschuss je Trade im Moment der Entscheidung:**
- Er enthält die Kerzen bis zur Auslöserkerze, die Linien, die Toleranz, die Berührungen, Note, Punktzahl und Stufe 3.
- Dazu den Plan:
  - Richtung;
  - geplanter Einstieg = Schluss der Auslöserkerze;
  - Stop nach Mindest-Stop zu diesem Kurs;
  - Ziel.
- SHA-256 über den Kern.
- Der Ausgang kommt in eigene Felder: tatsächlicher Einstieg (Minute und Kurs), endgültiger Stop, Ausstieg (Minute,
  Kurs, Grund), r_vor, r.
- Linien und Berührungen werden nie neu berechnet.
- Pflichttest: Der Hash ist vor und nach dem Anhängen des Ausgangs gleich.

**Seiten-Daten** nach backtest `lernhub/daten/`, Felder wie im Datenvertrag Abschnitt 9:
- `ergebnisse.json` mit Werten für Note A, dazu `noten` und `zufall`;
- `trades/index.json` und `trades/<zeitebene>m-<einstieg>/NNN.json` mit höchstens 200 Trades je Datei. Je Trade:
  - der ganze Handelstag;
  - Entscheidung, Linien, Kasten, Toleranz, Punkte, Berührungen;
  - Einstieg, Stop, Ziel, Ausstieg;
  - Fakten (Höhe, Breite, Stop · Ziel).

**Abweichung zur Größe (bitte bestätigen):**
- Alle Trades aller Noten mit ganzem Handelstag wären auf 5 Min geschätzt rund 80 MB; die Seite lädt eine Gruppe
  komplett.
- Darum kommt **Note A vollständig** auf die Seite. Von **B und C** kommt je Variante eine feste Zufallsauswahl von
  höchstens 300 Trades (Startwert `20261028`).
- **Alle Trades aller Noten** gehen vollständig, aber ohne Tageskerzen, nach backtest als
  `lernhub/werkbank/trades-<zeitebene>m-<einstieg>.jsonl.gz`, mit Hash des Schnappschusses.

**Telegram** nach jeder Zeitebene (ohne Link; der Prüfer lässt den Seiten-Hostnamen nicht zu):
- „15 Min fertig: beste Variante …, … Trades mit Note A, Ø … R nach Kosten. Mehr auf der Lernhub-Seite“;
- ebenso „5 Min fertig“;
- jeder Abbruch mit Grund.

## 8. Merkmale je Trade (mitschreiben, NICHT filtern; nur für später)

| Merkmal | Messung |
|---|---|
| Volumen im Kasten | Summe der zweiten Hälfte der Kasten-Kerzen (vom ersten Kastenpunkt bis zur Kerze vor dem Auslöser) geteilt durch die der ersten Hälfte |
| Volumen der Auslöserkerze | Volumen der Auslöserkerze geteilt durch das mittlere Volumen der Kasten-Kerzen |
| Vortrend | (Schluss der Kerze vor dem ersten Kastenpunkt − Eröffnung 09:30) / Kasten-ATR, mit Vorzeichen |
| Lage im Tagesbereich | (Schluss der Auslöserkerze − Tagestief bis dahin) / (Tageshoch − Tagestief bis dahin), 0 bis 1 |
| Abstand zum VWAP | (Schluss der Auslöserkerze − VWAP des Tages bis zum Kerzenschluss) / Kasten-ATR; VWAP aus SIP 1 Min mit (Hoch + Tief + Schluss) / 3 |
| SPY-Richtung | SPY von der Eröffnung 09:30 bis zum Schluss der Auslöserkerze in %, dazu das Vorzeichen (SIP 1 Min aus dem Cache) |
| Uhrzeit | Schluss der Auslöserkerze, New York |
| Morgenlücke | (Eröffnung 09:30 − Schluss des Vortags) / Schluss des Vortags in % |
| Bewertung nach 8454cdc07786 | derselbe Kasten im selben Moment nach dem eingefrorenen Stand: Steigung der Schlusskurse über die vollen Pendel, Punktzahl alt, alte Note bzw. „ungültig wegen …“ (Steigung der Schlusskurse oder Pendel ohne Band) |

Dazu kommen die Messwerte des Kastens: Höhe in ATR, Breite, Berührungen, Passgüte, Steigung der Linien, Effizienz,
Punktzahl und Kasten-ATR.

## 9. Lauf-Code und Prüfungen vor dem Lauf

- **Eigener Lauf-Code** für Einstiege, Simulation, Kosten, Zufallstest, Schnappschüsse und Seiten-Daten in
  `lern_labor/werkbank/`, mit eigenem Code-Hash. Er setzt genau diese Datei um.
- **Vor dem Lauf, Ergebnis jeweils ins Logbuch:**
  - Pflichttests auf künstlichen Kursen:
    - jeder Einstieg A – D long und short;
    - kein B nach Schluss zurück im Kasten;
    - C nur bei mindestens 1 R;
    - Mindest-Stop;
    - Simulation: Stop vor Ziel in derselben Minute, Eröffnung jenseits des Stops, Ziel nur beim Durchhandeln,
      Tagesende 15:50 und 12:50;
    - Kosten und Kostenstress;
    - Zufallstest mit festem Startwert wiederholbar;
    - Hash des Schnappschusses vor und nach dem Ausgang gleich.
  - Abschneide-Test auf echten Daten: 300 zufällige Entscheidungen; mit Daten nur bis zur Entscheidung entstehen
    dieselben Auslöser, Pläne und Schnappschüsse.
- **Beim Start** prüft der Lauf beide Hashes: Erkennung `2489765016f5` und den Lauf-Code. Weicht einer ab, startet er
  nicht.
- **Rechenzeit:** klein, etwa 15 – 25 Minuten je Zeitebene. Gestartet wird nur, wenn der Lauf vor 23:00 deutscher Zeit
  fertig ist; keine Läufe über Nacht auf dem Hauptrechner. Der Lauf setzt je Aktie fort.

## 10. Ablauf nach dem OK

1. Lauf-Code bauen, Pflichttests und Abschneide-Test grün, Hash ins Logbuch.
2. Lauf 15 Min, dann `ergebnisse.json` und `trades/` nach backtest, dann Telegram.
3. Lauf 5 Min, ebenso.
4. Kurzbericht an den Inhaber und an Claude im Chat (Abschnitt 6).
