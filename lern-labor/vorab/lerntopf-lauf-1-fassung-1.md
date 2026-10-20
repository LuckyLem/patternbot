# Vorab-Datei · Lerntopf-Lauf 1 (großes Paket) · Fassung 1

**Festgelegt am 20.10.2026.** Grundlage ist der Entwurf vom 20.10. (Commit 8d7a7fd auf backtest), geprüft von Claude
im Chat, mit den Antworten und Ergänzungen des Inhabers vom selben Tag (Abschnitt 13). Commit und SHA-256 dieser Datei
stehen im Logbuch.

Vor dieser Festlegung lief nichts auf echten Daten. Ab jetzt ändern sich die Regeln nicht mehr:
- Eine Änderung ergibt eine neue Fassung mit neuer Nummer, und das nur, bevor Ergebnisse da sind.
- Claude im Chat prüft diese festgelegte Datei, während Abschneide-Test und Gegenprobe laufen. Findet er noch einen
  Fehler, gibt es vor dem ersten Ergebnis eine Fassung 2.
- Muster, die der Inhaber ab jetzt per Bild bringt, gehen in Lauf 2.

## 1. Ziel

Eine große Rangliste: welche Muster auf welcher Zeitebene mit welchem Ausstieg über 3 Jahre nach Kosten funktionieren
und welche nicht. Die Besten werden danach im Prüftopf bestätigt (eigene Vorab-Datei) und erst dann auf dem zweiten
Paper-Konto gehandelt.

Befund aus Runde 1, der zur Frage nach Ziel und Haltedauer führt (nur Zählung):
- 86 % der Trades enden durch Zeit-Stop oder Tagesende;
- 3,8 % erreichen das Ziel;
- die Ziele liegen im Median 1,49R entfernt.

## 2. Daten

| Teil | Zeitraum | Wofür |
|---|---|---|
| IEX 15 Min, split-bereinigt | 01.10.2020–29.09.2023, Vorlauf ab 01.09.2020 | Zeitebene 15 Min wie live |
| SIP 1 Min, split-bereinigt | jeder Handelstag, alle Werte und SPY | Zeitebenen 1 und 5 Min (daraus zusammengesetzt), Einstieg, Stop, Ziel, Zeit-Stop, Tagesende, Kurslücken, Zufallsläufe |
| IEX 1 Min, nur SPY | jeder Handelstag | „SPY heute“ auf 15 Min, wie im Replay |
| IEX-Tageskerzen, split-bereinigt | ab 27.07.2020 | Tagestrend (M001–M007) |
| SIP-Tageskerzen, split-bereinigt | 2020 als Vorlauf | Tagestrend am Anfang. Gemessen am 08.10. (Fahrplan 4.0.26): 0,46 % Abweichung, also beginnt der Lerntopf am 01.10.2020 |

- **Stand der Daten:** alles geladen am 19./20.10.2026 (9.947 Abrufe, keine Wiederholung nach 429). Für die
  Zeitebenen 1 und 5 Min ist kein weiterer Download nötig.
- **Werte:** die 150 Werte der heutigen Liste wie in den Jahresrunden, dazu SPY. Werte ohne Kerzen werden gezählt und
  genannt.
- **Keine Quotes und keine einzelnen Abschlüsse im Lauf.** Spread und Schlupf laufen über das Kostenmodell
  (Abschnitt 7). Für die Gegenprobe (Abschnitt 9) holt das Replay IEX-Abschlüsse und -Quotes, nur für Setups nach dem
  Volumenfilter, mit derselben Drosselung.
- **Split-bereinigt:** Unbereinigte Kerzen ergäben über drei Jahre an jedem Split falsche Kanten und einen falschen
  Tagestrend (Befund 1.13). Das kalibrierte Replay rechnet ebenfalls bereinigt.
- **Prüftopf:** Er bleibt zu. Aus der Zeit ab dem 01.10.2023 wird nichts geladen und nichts gelesen.
- **Überlebensverzerrung:** Die Liste stammt von heute. Werte, die 2020–2023 groß waren und heute fehlen, sind nicht
  dabei. Das macht die Ergebnisse eher zu gut. Der Bericht nennt das an erster Stelle.

## 3. Kandidaten: 23 Muster × 3 Zeitebenen × 5 Varianten = 345

Ein Kandidat heißt z. B. **M003-15m-H0**: Muster M003, Zeitebene 15 Min, Variante H0. Die Muster sind die Steckbriefe
M001–M023 in der Fassung vom 20.10.2026, mit SHA-256 je Datei in Anhang A.

| Muster | Erkennung | Steckbriefe |
|---|---|---|
| M001–M007 | Code des Live-Bots (Stand cbfe06cff), auf 15 Min genau wie im Replay | Aufsteigendes und absteigendes Dreieck, Rechteck, Doppeltop, Doppelboden, Schulter-Kopf-Schulter und inverse |
| M008–M010 | Chart-Leser Teil 2 (v1.1, unverändert) plus Vortrend und Kaufkraft aus den Steckbriefen | Keil steigend, Keil fallend, Doppelboden mit Kaufkraft |
| M011–M023 | neue Erkennung des Labors, genau nach den Steckbriefen | Hammer, Shooting Star, bullische und bärische Umarmung, Bullen- und Bären-Flagge, symmetrisches Dreieck, Inside-Bar, Morgen- und Abendstern, Dreifachboden und -top, Tasse mit Henkel |

**Je Muster und Zeitebene handeln alle 5 Varianten dieselben Signale zum selben Einstieg.** Auch Auswahl und Filter
rechnen bei allen mit dem Ziel aus dem Steckbrief. Anders ist nur der Ausstieg.

**Andere Zeitebene, gleiche Regeln:** Ein Muster auf 1 oder 5 Min ist ein eigener Kandidat. Die Regeln des Steckbriefs
gelten unverändert, alle Längen (Fenster, Zickzack, Kerzenzahlen) und das ATR in Kerzen der jeweiligen Zeitebene. Feste
Prozentgrenzen im Code des Bots (z. B. Höhe eines Rechtecks 1,5–12 %) bleiben, wie sie sind.

## 4. Zeitebenen

| | 15 Min | 5 Min | 1 Min |
|---|---|---|---|
| Kerzen | IEX wie live, mit Vor- und Nachbörse wie im Abruf des Bots | aus SIP-1-Min, nur reguläre Handelszeit 09:30–16:00 | SIP-1-Min, nur reguläre Handelszeit |
| Entscheidung | Kerzenschluss + 33 s; die Eröffnungskerze im Nachholdurchgang um 09:50:18 (wie live) | Kerzenschluss + 33 s | Kerzenschluss + 33 s |
| Erste und letzte Entscheidung | mindestens 20 Minuten nach der Eröffnung, mehr als 30 Minuten vor Schluss | ebenso; kein Nachholdurchgang | ebenso; kein Nachholdurchgang |
| Fenster | 200 Kerzen aus 14 Tagen (Bot), Chart-Leser 14 Tage | die letzten 200 Kerzen; Chart-Leser die Kerzen der letzten 14 Tage | ebenso |
| SPY (relative Stärke, „SPY heute“) | IEX 15 Min und IEX 1 Min wie im Replay | SPY aus SIP auf derselben Zeitebene, „SPY heute“ aus SIP 1 Min | ebenso |

- **Einstieg auf allen Zeitebenen:** zum Eröffnungskurs der SIP-Minute nach dem Entscheidungszeitpunkt.
- **Im Bericht vermerkt:** Ein Gewinner auf 1 oder 5 Min bräuchte live Echtzeitdaten von SIP (der Gratis-Tarif liefert
  SIP erst nach 15 Minuten) oder einen Zusatztest auf IEX-Kerzen.

## 5. Varianten H0–H4: gleiche Signale, nur der Ausstieg ist anders

| Variante | Ziel | Ausstieg |
|---|---|---|
| **H0** | aus dem Steckbrief | Zeit-Stop in Kerzen: nach 8 Kerzen raus, wenn R ≤ 0 oder unter 80 % des besten R; nach 16 Kerzen raus. Auf 15 Min ist das genau wie live (120/240 Minuten). Tagesende 10 Minuten vor Schluss |
| **H1** | aus dem Steckbrief | ohne Zeit-Stop: bis Ziel, Stop oder Tagesende |
| **H2** | Kante + ½ × (Ziel aus dem Steckbrief − Kante) | sonst wie H0 |
| **H3** | aus dem Steckbrief | über Nacht bis Ziel oder Stop, höchstens 3 Handelstage (der Einstiegstag zählt als Tag 1), Ausstieg 10 Minuten vor Schluss des 3. Tages; spätestens am 29.09.2023 zehn Minuten vor Schluss. Kurslücken zählen voll. Nur Simulation |
| **H4** | aus dem Steckbrief | wie H0, nur mit eigener Länge: ab L Kerzen raus, wenn R ≤ 0 oder unter 80 % des besten R; nach 2 L Kerzen raus; höchstens bis Tagesende. L = Entstehungsdauer des Musters vom Beginn bis zur Signalkerze (Tabelle unten), mindestens 1 Kerze |

- **In allen Varianten wie live:** Break-even ab einem Minutenschluss bei +0,6R (Stop auf Einstieg ± 0,05 %);
  Trailing ab +1,5R im Abstand von 1R hinter dem besten Minutenschluss.
- **Prüfungen:** Sie laufen am Minutenschluss; Ausstiege danach zum Eröffnungskurs der nächsten Minute.

**Beginn des Musters für H4:**

| Muster | Beginn |
|---|---|
| M001–M007 | der erste Wendepunkt, den der Detektor für dieses Signal benutzt (nachgerechnet wie bei den rekonstruierten Bildern der Live-Trades) |
| M008–M010 | erste Berührung bzw. erster Boden laut Chart-Leser |
| M011–M014, M019, M020 | das Zickzack-Hoch bzw. -Tief, an dem der Vortrend beginnt (das Ziel) |
| M015, M016 | das Tief bzw. Hoch, an dem die Fahnenstange beginnt |
| M017 | die erste Berührung |
| M018 | die Mutterkerze |
| M021, M022 | der erste Boden bzw. das erste Top |
| M023 | der linke Rand |

## 6. Signale und Filter

- **Point-in-time:** Jede Kerze wird nach ihrem Schluss bewertet, nur mit den Kerzen bis dahin.
- **Abschneide-Test:** Er ist Pflicht und läuft auf echten Daten als erster Schritt nach der Festlegung, mit einer
  Stichprobe von 300 Entscheidungen je Zeitebene. Signale mit allen Daten müssen gleich den Signalen mit Daten nur bis
  zum Zeitpunkt sein. Das Ergebnis kommt ins Logbuch; schlägt der Test fehl, bricht der Lauf ab.
- **Höchstens 1 Signal je Muster, Zeitebene, Aktie und Tag:** Es zählt das erste, das alle Filter besteht.
- **Jedes Signal wird einzeln gewertet:** keine 5-Plätze-Grenze, keine Reihenfolge der Aktienliste.

**Filter (wie im jeweiligen Steckbrief):**

| Filter | M001–M007 | M008–M010 | M011–M023 |
|---|---|---|---|
| Zeitfenster (nicht in den ersten 20 und den letzten 30 Minuten) | ja | ja | ja |
| Tagestrend in Handelsrichtung (nur Fortsetzungsmuster M001–M003, wie im Code) | ja | nein, Vortrend aus dem Steckbrief | nein, Vortrend bzw. Trend aus dem Steckbrief |
| Mindest-Stop 0,3 % vom Schlusskurs | ja | ja | nein |
| Chance-Risiko am Schlusskurs mindestens 0,8 | ja | ja | nein |
| Volumen der Signalkerze mindestens 1,5 × Schnitt der letzten 20 Kerzen | ja | ja | nein |
| Relative Stärke gegen SPY über 13 Kerzen; SPY am Tag höchstens 0,5 % dagegen | ja | ja | nein |
| Anti-Chase-Zone V1, Chance-Risiko am Limit mindestens 0,8, Geometrie Stop < Limit < Ziel | ja | ja | nur die Geometrie: Einstieg zwischen Stop und Ziel |
| Kursalter, Spread | ohne Quotes nicht nachgebildet, das Kostenmodell deckt den Spread ab | ebenso | – |

- **Ausnahme Volumenfilter:** Bei M001–M010 werden Kerzen, die den Volumenfilter nicht bestehen, gar nicht erst
  gelesen. Das spart Rechenzeit und ändert keinen Trade.
- **Selbstkontrolle bei M011–M023:** Auf 15 Min (IEX) müssen die Ankerpunkte von SIP bestätigt sein, sonst ist das
  Signal ungültig (Steckbrief).
- **Nebenzählung (zählt nicht, Fahrplan 4.8.20):** Bei M008–M010 auf 15 Min wird für jeden Ankerpunkt mit SIP-Kerze
  gezählt, wie oft die 3×-Regel einen von SIP bestätigten Docht verworfen hätte und wie oft einen nicht bestätigten.

## 7. Ausführung und Kosten

- **Stop und Ziel:** auf 1-Min-SIP-Kerzen, auf allen Zeitebenen.
  - Berühren Stop und Ziel dieselbe Minute, zählt der Stop.
  - Öffnet eine Minute jenseits des Stops, zählt ihr Eröffnungskurs (Lücke voll).
  - Das Ziel füllt nur, wenn der Kurs durch das Ziel handelt.
- **Schneller Simulator:** `bt/exits.py` als Grundlage, für die Varianten erweitert. H0 auf 15 Min ist gleich
  `bt.exits.simulate`, geprüft auf 400 Zufallsverläufen.
- **Kosten nach den Erfolgskriterien** (Lern-Labor): je Trade der höhere Wert aus
  - 0,03R (long) bzw. 0,05R (short) und
  - der Slippage = 2 Seiten × max(0,01 $; 0,02 % vom Kurs) je Aktie, geteilt durch den Stop-Abstand.
- **Kostenstress:** zusätzlich +0,03R je Trade.
- **Hinweis zu den Kosten:** Auf 1 Min liegen die Stops oft eng. Dort kann die Slippage je Trade über 0,03R liegen,
  dann zählt sie.

## 8. Auswertung, Stufe 1, Prüftopf und Flop-Liste

**Je Kandidat, je Jahr und gesamt:**
- **Jahre:** J1 = 01.10.2020–30.09.2021, J2 = 01.10.2021–30.09.2022, J3 = 01.10.2022–29.09.2023. Ein Trade zählt im Jahr
  seines Einstiegs.
- **Kennzahlen:** Trades, Erwartungswert nach Kosten, Erwartungswert mit Kostenstress, Profitfaktor, Trefferquote, max.
  Drawdown (Trade für Trade in R), Ausgänge (Ziel, Anfangsstop, nachgezogener Stop, Zeit-Stop, Tagesende, Ende der
  Haltedauer, Datenende).
- **Große Rangliste aller 345 Kandidaten:** sortiert nach dem schwächsten der drei Jahre.

**Stufe 1** (Inhaber 20.10.) verlangt alle drei Bedingungen:
1. **Jedes Jahr positiv:** nach Kosten, mit mindestens 30 Trades je Jahr. Darunter heißt es „zu wenig Daten“, nicht
   „durchgefallen“.
2. **Kostenstress:** über alle 3 Jahre mit +0,03R noch positiv.
3. **Zufall in derselben Richtung bestanden.**
   - **Aufbau:** Je Kandidat gibt es 100 Läufe. Je echtem Trade nehmen sie dieselbe Aktie, denselben Tag, eine zufällige
     Minute in derselben Stunde (nicht in den letzten 30 Minuten) und **dieselbe Richtung wie der echte Trade**.
     Stop-Abstand in % und Ziel in R sind wie beim echten Trade, dazu dieselben Ausstiegsregeln der Variante und
     dieselben Kosten.
   - **Bedingung:** Der Erwartungswert des Kandidaten über alle 3 Jahre liegt in mindestens 95 von 100 Läufen über
     dem seines eigenen Zufalls.
   - **Startwert:** fest 20261020.
   - **Grund:** J1 war ein starkes Bullenjahr. Diese Probe rechnet den Markttrend heraus. Ein Long-Muster, das nur
     wegen des steigenden Markts gewinnt, besteht sie nicht.

**Zufallslatte „Bester von N“ (in Lauf 1 nur Information, Inhaber 20.10.):**
- **N:** Gebildet wird sie nur aus den Kandidaten mit mindestens 30 Trades in jedem Jahr. N steht im Bericht.
- **Zufallsläufe:** 100 je Kandidat, gebaut wie der bestehende Zufallsvergleich:
  - derselbe Wert und Tag, eine zufällige Minute in derselben Stunde;
  - die Richtung ausgelost;
  - Stop-Abstand in % und Ziel in R wie beim echten Trade;
  - dieselben Ausstiegsregeln und Kosten.
- **Startwert:** fest 20261019. Lauf k zieht für alle Kandidaten mit demselben Startwert.
- **Latte:** In Lauf k ist sie der beste Zufalls-Erwartungswert über alle 3 Jahre unter diesen N Kandidaten.
- **Ergebnis je Kandidat:** in wie vielen der 100 Läufe er über der Latte liegt.

**Weiter in den Prüftopf:**
- **Wer:** die Top 10 der Kandidaten mit Stufe 1, nach dem schwächsten Jahr, mit **höchstens 2 Kandidaten je
  Muster** (die 2 mit dem besten schwächsten Jahr). So prüft Öffnung 1 möglichst viele verschiedene Ideen.
- **Vorab-Datei:** eine eigene, mit der Latte „Bester von 10“ und den Kriterien K1–K5.
- **Öffnung:** Das ist Öffnung 1 von 3, nur nach dem OK des Inhabers.
- **Hinweis im Bericht:** Für M001–M007 auf 15 Min sind die Jahre 2024–2026 aus den Jahresrunden schon bekannt.

**Flop-Liste:**
- **Wer:** die 10 Kandidaten, die in jedem Jahr klar verlieren, **gemessen vor Kosten**. Das heißt: in jedem Jahr
  mindestens 30 Trades und Erwartungswert vor Kosten unter 0, über alle 3 Jahre vor Kosten höchstens −0,10R. Sortiert
  nach dem besten Jahr vor Kosten, vom schlechtesten her.
- **Wozu:** Sie sind Kandidaten für „Finger weg“-Filter oder die Gegenrichtung, als eigene neue Steckbriefe in einem
  späteren Lauf.

**Seiten für die Top 10 und die Flop 10:**
- je eine Seite wie das Rechteck-Beispiel: alle gefundenen Trades mit Linien, die Auswertung und ein Urteil;
- nur aus dem Lerntopf.

## 9. Gegenprobe vor dem Lauf (nur 15 Min)

Sie läuft vor dem eigentlichen Lauf. Sie wertet nichts und wählt nichts aus.
- **M001-15m-H0 und M003-15m-H0** werden auf J3 gegen das Replay verglichen. Das Replay ist auf diese beiden Detektoren
  beschränkt.
- **Signale:** müssen 1:1 übereinstimmen (Wert, Muster, Seite, Kerze, Kante, Stop, Ziel). Ergebnisse in R werden nicht
  gelesen.
- **Abweichungen:** einzeln erklärt. Erwartet sind sie nur bei den Filtern ohne Quotes, durch die fehlende
  5-Plätze-Grenze und durch den Einstieg zur Minute.

## 10. Reihenfolge und Rechenzeit

1. Festlegung (Commit und SHA-256 im Logbuch).
2. Abschneide-Test auf echten Daten, dann die Gegenprobe J3. Dabei werden keine Ergebnisse in R gelesen.
3. Läufe: zuerst 15 Min, dann 5 Min, dann 1 Min. Zwischenstände werden gesichert.
4. Rechenzeit: Die Schätzung steht vor dem Lauf im Logbuch.
   - Grundlage: die Messung auf künstlichen Kursen in Originalgröße.
   - Wenn nötig, läuft es nachts zusätzlich im Labor-Slice auf dem Pi (MemoryMax wirkt dort seit 18.10.).

## 11. Was festgehalten wird

- **Kennungen:** SHA-256 dieser Datei und der Steckbriefe M001–M023.
- **Code-Hashes:**
  - Bot cbfe06cff;
  - Chart-Leser v1.1 c5ca9efa1343 (gerechnet über `chartleser/__init__.py`, `kern.py`, `lesen.py`, `signal.py` und
    `geometrie.py`);
  - `bt/` 61750fbbc22e;
  - der Code-Hash des Labors (Simulator, Signale, neue Erkennung M011–M023, Auswertung, Lauf), den der Logbuch-Eintrag
    vor dem Lauf nennt.
- **Bericht:** `lern-labor/lerntopf-lauf-1/` auf backtest. Die Labor-Seite zeigt die Rangliste erst nach dem OK des
  Inhabers zum Diff.
- **Danach:** Nach dem Lauf wird an diesen Regeln nichts geändert. Neue Ideen werden neue Steckbriefe mit neuer Nummer.

## 12. Danach (nur vorbereiten, nichts handeln)

Für die im Prüftopf Bestätigten: Paper auf dem zweiten Alpaca-Konto (5.000 $).
- eigener Dienst, nie das Konto des Live-Bots;
- 0,5 % Risiko, höchstens 5 Positionen;
- Ziel 200 Trades bzw. 3 Monate, Kriterien K1–K5;
- Start nur mit OK des Inhabers.

## 13. Entscheidungen des Inhabers

**19.10.2026:**
- Break-even und Trailing in allen Varianten;
- die Filter rechnen mit dem Ziel aus dem Steckbrief;
- mindestens 30 Trades je Jahr, sonst „zu wenig Daten“;
- IEX-Abschlüsse und -Quotes für die Gegenprobe;
- H3 endet spätestens am 29.09.2023;
- Trailing in den Steckbriefen ergänzt.

**20.10.2026 (großes Paket):**
- M011–M023;
- die Zeitebenen 1, 5 und 15 Min;
- die Varianten H0–H4 mit dem Zeit-Stop in Kerzen;
- Stufe 1 wie in Abschnitt 8, die Latte nur aus Kandidaten mit mindestens 30 Trades je Jahr;
- Top 10 in den Prüftopf (Öffnung 1 von 3, eigene Vorab-Datei, nur mit OK);
- die Flop-Liste;
- Seiten für Top und Flop;
- Paper auf Konto 2 nur vorbereiten.

**20.10.2026, Freigabe nach der Prüfung des Entwurfs durch Claude im Chat:**
1. H4 wie H0, nur mit eigener Länge: ab L Kerzen die 80-%-Regel, nach 2 L Kerzen raus, höchstens bis Tagesende.
2. Die Latte „Bester von N“ ist in Lauf 1 nur Information.
3. M012–M023 nur mit dem Zeitfenster, ohne die Filter des Bots.
4. Die Flop-Liste wird vor Kosten gemessen (Abschnitt 8).
5. 1 und 5 Min nur reguläre Handelszeit, kein Nachholdurchgang, SPY aus SIP.
6. Stufe 1 bekommt die dritte Bedingung „Zufall in derselben Richtung“ (Startwert 20261020).
7. Top 10 für den Prüftopf mit höchstens 2 Kandidaten je Muster.

## 14. Offene Punkte

Keine. Alle Punkte des Entwurfs sind entschieden (Abschnitt 13).

## Anhang A · SHA-256 der Steckbriefe (Fassung 20.10.2026)

| Steckbrief | SHA-256 |
|---|---|
| M001-aufsteigendes-dreieck.md | `a556401ca3674deb6ff20b8b3ad98164d95dc990a2b60973c7d720085ac683d2` |
| M002-absteigendes-dreieck.md | `9d861687ad2e1f72f415636ab87037f8e4ae4af62fffea41d81da510519383dc` |
| M003-rechteck.md | `a600a114d8788efae29e25fde1730c9e6f1467f51a6b8b149837a896fecba8b4` |
| M004-doppeltop.md | `089d7d1e9069aec03910b291a84ddd6d26391eb8be8aca0442ea2ac4e8a43f55` |
| M005-doppelboden.md | `bf5341c3d933198d24ddc47ea0aa7cec5e54fae211b5df83f137187fe9ee115e` |
| M006-schulter-kopf-schulter.md | `4cb3b796431460f2525a02716b8d13c2ef7aebc8f4caba4512af184a818e218a` |
| M007-inverse-schulter-kopf-schulter.md | `35bf948413845a01ddfbfec0a62c739fcd9a5be2803d0ee396fd65dff05dfb49` |
| M008-keil-steigend.md | `ea04a6698e4de7ce74b3e22dfb68ffe6f47e0d1a1eb9c0b4b7fa34ac5fb9d96e` |
| M009-keil-fallend.md | `da4c8e2629354e7c5a50d5f45f8279e9fd7ab2efd215039950e1726e668b761e` |
| M010-doppelboden-mit-kaufkraft.md | `d0ab6beac91b2228773346c19f1b542ca511385859e76f6ea746f84de3186ae2` |
| M011-hammer.md | `0134383f5ee8935f55c433c342f7c75599305e1fd7220f3110ac1c74ea2d1d74` |
| M012-shooting-star.md | `8b5115472b318eea72d897e9b16480b8afd95505d5fd81dcd9cd457ac285ce16` |
| M013-bullische-umarmung.md | `13d2dc0ea22b5127f96f53710cf3bf72985a979924d3d4ec480d18eb9ffb4632` |
| M014-baerische-umarmung.md | `628bfd21941f34b59e4f890b7cff191e7b8e58f1d526fbf8ca387b96d7f305fe` |
| M015-bullen-flagge.md | `9daf150b325e3ec381a21bbfd62fc78f4fad7b1d576ca11bbaa079fdea14fc2c` |
| M016-baeren-flagge.md | `cf305ea25154b99620c10ae3e93d4c91a10e26bbb1162c901c65fca2bf5bd9b9` |
| M017-symmetrisches-dreieck.md | `af1878c6d6c01eec97e930c20eae4affb97f6bdcb676d7f31a610788eefd2adc` |
| M018-inside-bar.md | `94cec3f3d1ae33b1319c1110cf76fb843c2a1d673f161fd11f92e5de48f60c98` |
| M019-morgenstern.md | `b1e0e45027a25415310153c3985a20a3bcc76deef31da8eadbe5929fd9ebc5ad` |
| M020-abendstern.md | `37ccf2d621dfe061f5903eeec6f0517d6e9204f6be09b78d536c5d615456a09b` |
| M021-dreifachboden.md | `f20fc5ba2da010dd7917571689e4be99e1067f63b72a613f553c4d62317102e6` |
| M022-dreifachtop.md | `4af57e0c944e1e191b21707195ecf2a6b818e97982e6748b0292376e1f39aefb` |
| M023-tasse-mit-henkel.md | `9a5b53a5cbb986a87d547c4de0e87505957d1969435e7a02e240347eb63017f2` |
