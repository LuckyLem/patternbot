# Große Umstellung · Prompt Version 2 · Zielsetzung

Stand: Fr 23.10.2026. Geschrieben von Claude im Chat für VS Code, im Auftrag des Inhabers.
Ort: Branch `claude/epic-gates-iz9swg`, Ordner `lernhub/`. Vorlage der Seite: `lernhub/vorlage/lernhub.html`.

Diese Datei ist der Auftrag. Sie ersetzt den großen Auftrag vom 20.10. (Lerntopf-Lauf 1 mit 230 Kandidaten).
Lauf 1 wird nicht weiter gerechnet. Seine Berichte bleiben als Archiv auf backtest.

---

## 1. Zielsetzung

Der Bot soll handeln wie ein Profi, der **ein Muster in- und auswendig kennt** und keine Gefühle hat:
- Er zieht seine Linien selbst, und die Linien **berühren wirklich**. Kein Spielraum von Prozenten.
- Er beobachtet ein Muster, während es entsteht, gibt ihm eine Note und steigt **nur beim sauberen Lehrbuch-Muster** ein.
  Ungefähre Muster werden nie gehandelt.
- Jedes Bild zeigt **genau das, was der Bot im Moment der Entscheidung gesehen hat**, mit seinen eigenen Linien.
  Es wird nie nachträglich neu gezeichnet.
- Wir sehen jeden Trade und jede Linie auf der Webseite und prüfen mit eigenen Augen, ob die Erkennung stimmt.

Dafür bauen wir eine **Werkbank für ein einziges Muster: das Rechteck**.
- 50 Aktien mit dem meisten Handel.
- 5- und 15-Minuten-Kerzen.
- Vier Einstiege im Vergleich.

Erst wenn das Rechteck sauber erkannt wird und ein Einstieg nachweislich trägt, kommt das nächste Muster.

## 2. Warum die Umstellung (Befund Lerntopf-Lauf 1, 15 Min)

- **Kein Kandidat hat Stufe 1 erreicht.** Vor Kosten liegt fast alles bei ±0,02R, nach Kosten bei minus den Kosten.
  Die Signale tragen keine Information.
- **Die Bot-Muster M001–M007 sind zu locker erkannt.**
  - Die Toleranzen sind in Prozent angegeben (Rechteck und Doppeltop 2 %, Dreieck 1,5 %, SKS 4 %). Auf 15 Min sind das 5–10 Kerzenspannen.
  - Die Wendepunkte sind 3-Kerzen-Fraktale, also jedes kleine Zucken.
  - Nachgemessen an den 40 Live-Rechtecken: nur 6 haben an beiden Kanten mindestens 2 echte Berührungen (±0,25 ATR). Die Höhe liegt im Median bei 7,75 ATR.
    Das „Rechteck“ ist meist nur das höchste Hoch und das tiefste Tief der letzten 50 Kerzen.
- **Auch exakt erkannte Kerzenmuster** (Hammer, Umarmung, Sterne) liegen vor Kosten bei etwa 0.
  Darum testen wir neben der Erkennung auch **die Art des Einstiegs**.
- **M015 (+0,135R vor Kosten) war ein Artefakt** winziger Stops unter 0,15 %. Ab 0,3 % Stop liegt es bei 0,00R.
  Darum gilt jetzt ein Mindest-Stop.
- **Der Zufallstest „gleiche Richtung“ war unfair.** Die Zufallsminute konnte vor dem echten Ausbruch liegen und kannte dessen Richtung.
  Er wird ersetzt (Abschnitt 7).
- **Muster über mehrere Tage:** Auf 5 und 15 Min darf ein Muster nicht über Nacht reichen. Ab jetzt entsteht und endet alles an einem Handelstag.

## 3. Recherche (Kurzfassung, nur in eigenen Worten)

- **Rechtecke auf Tageskerzen** (Bulkowski): Nach dem Ausbruch kommt der Kurs in etwa zwei von drei Fällen noch einmal zur Kante zurück.
  Diese Rücksetzer schwächen das Ergebnis.
  Quellen: https://thepatternsite.com/recttops.html und https://thepatternsite.com/rectbots.html
- **Seitwärtsphasen intraday** (Al Brooks, Faustregel): Die meisten Ausbruchsversuche scheitern, oft innerhalb von 1–5 Kerzen.
  Profis warten auf den zweiten Einstieg oder handeln den Fehlausbruch zurück in die Spanne.
  Quelle: https://www.brookstradingcourse.com/support-forum/12-market-cycle/breakout-fail/
- **Ausbruch gegen Retest:** Der Retest bringt den besseren Preis, kommt aber nur bei etwa der Hälfte der Ausbrüche.
  In einer offenen Testreihe war der Erwartungswert je Ausbruch am Ende ähnlich.
  Quelle: https://www.tradingview.com/script/SA4YoyNF-Breakout-Retest-Entry-Signals-the-Break-vs-Retest/
- **Folgerung:** Kein Einstieg ist von vornherein der richtige. Wir testen vier, auf unseren Aktien, nach Kosten, und die Daten entscheiden.
  Erwartung, nur als Vermutung: Auf 5 und 15 Min schneiden C (Abpraller) und D (Fehlausbruch) besser ab als A (Ausbruch).
- Hinweis: Bulkowskis Seite untersagt die Nutzung zum Training von KI. Wir übernehmen nur einzelne Zahlen in eigenen Worten als Quelle, nichts wird kopiert oder trainiert.

## 4. Das Rechteck: Erkennung

**Kerzen**
- 5 und 15 Min, nur reguläre Handelszeit 09:30–16:00 New York.
- Zusammengesetzt aus SIP-1-Min (alle Börsen, split-bereinigt). Keine Vor- und Nachbörse.

**Ein Handelstag**
- Alle Kerzen eines Rechtecks stammen vom selben Handelstag.
- Einstieg und Ausstieg am selben Tag, Glattstellung spätestens 15:50 New York.
- Keine Linie und kein Trade über Nacht.

**ATR**
- Wilder 14 auf den Kerzen der Zeitebene, nur reguläre Handelszeit.
- Vortage dürfen dafür mitzählen; das ATR misst nur die Schwankung, es ist kein Teil des Musters.
- Wert der Kerze vor der Entscheidung.

**Wendepunkte**
- Ein Hoch ist Wendepunkt, wenn es höher ist als die 2 Kerzen davor und danach. Tief entsprechend.
- Bekannt ist ein Wendepunkt erst 2 Kerzen später, nie früher.

**Linien**
- Obere Linie = Mittelwert der Hochs ihrer Berührungen, untere Linie = Mittelwert der Tiefs ihrer Berührungen.
- Die Linien sind waagerecht.

**Berührung** (der Kern)
- Der Docht eines Wendepunkts liegt höchstens **0,15 ATR** von der Linie entfernt.
- Zwischen zwei Berührungen derselben Linie läuft der Kurs mindestens **40 % der Kastenhöhe** weg und kommt zurück.
  Nebeneinander liegende Kerzen am selben Hoch sind EINE Berührung.
- Berührungen wechseln sich ab: Zwischen zwei Berührungen oben liegt mindestens eine unten, und umgekehrt.

**Kasten gilt nur, wenn**
- mindestens 2 Berührungen oben und 2 unten;
- kein Schluss außerhalb der Linien ± 0,15 ATR;
- höchstens ein Docht ragt bis 0,3 ATR hinaus;
- Höhe zwischen 1,5 und 6 ATR;
- Breite mindestens 10 Kerzen (15 Min) bzw. 12 Kerzen (5 Min).

**Note**, im Moment der Entscheidung berechnet:
- **A, lehrbuchreif:**
  - mindestens 3 Berührungen an einer Linie und 2 an der anderen;
  - mittlere Abweichung der Berührungen höchstens 0,08 ATR;
  - kein Docht außerhalb des Bands.
- **B, brauchbar:**
  - 2 + 2 Berührungen;
  - mittlere Abweichung höchstens 0,15 ATR;
  - höchstens ein Docht bis 0,3 ATR hinaus.
- **C, ungefähr:**
  - Kasten nur mit gelockerter Toleranz (bis 0,3 ATR statt 0,15) erkennbar.
  - Wird **nur gemessen, nie gehandelt.** C wird gebraucht, um zu beweisen, dass Sauberkeit zählt (Abschnitt 6).
- Diese Grenzen stehen vorab fest. Sie kommen aus dem Lehrbuch und der Sichtprüfung, **nie aus Ergebnissen**.

**Reifegrad (der „Indikator“ je Aktie)**

| Stufe | Name | Bedingung | Bot tut |
|---|---|---|---|
| 0 | nichts | keine zwei Berührungen auf gleicher Höhe | nichts |
| 1 | entsteht | 2 Berührungen an einer Linie | beobachten |
| 2 | reif | 2 + 2 Berührungen, Kasten gültig, Note vergeben | Prioritätsliste, beste Note zuerst |
| 3 | Auslöser | Regel des Einstiegs erfüllt (Abschnitt 5) | Einstieg nur bei Note A |
| 4 | im Trade | Stop und Ziel aus den eigenen Linien | verwalten |

Die Stufen werden je Kerze mitgeschrieben. So kann die Seite zeigen, wie ein Muster reift, und später der Scanner live.

## 5. Vier Einstiege (dieselben Kästen, nur der Einstieg ist anders)

**Für alle gilt**
- Entscheidung am Kerzenschluss + 33 s, Einstieg zum Eröffnungskurs der SIP-Minute danach (wie live).
- Keine Einstiege in den ersten 20 und den letzten 30 Minuten.
- Ausstieg: Ziel, Stop oder Tagesende (15:50 New York). Kein Break-even und kein Trailing in diesem Lauf, bewusst einfach.
- **Mindest-Stop:** Abstand Einstieg–Stop mindestens max(0,5 ATR; 0,15 % vom Kurs). Ein engerer Stop wird auf dieses Minimum aufgeweitet, das Ziel bleibt.
- Höchstens 1 Trade je Einstieg, Aktie und Tag (der erste).
- Long und short.

**A · Ausbruch**
- Auslöser: Eine Kerze schließt mindestens 0,1 ATR jenseits einer Linie.
- Stop: Mitte des Kastens. Ziel: gebrochene Linie ± Kastenhöhe.

**B · Retest**
- Zuerst ein Ausbruch wie bei A, ohne Einstieg.
- Innerhalb von 6 Kerzen (15 Min) bzw. 12 Kerzen (5 Min) kommt ein Docht bis auf 0,15 ATR an die gebrochene Linie zurück, ohne Schluss zurück im Kasten.
- Auslöser: Die nächste Kerze schließt in Ausbruchsrichtung über dem Hoch (long) bzw. unter dem Tief (short) der Retest-Kerze.
- Stop: Extrem der Retest-Kerze ∓ 0,1 ATR. Ziel: gebrochene Linie ± Kastenhöhe.
- Schließt vorher eine Kerze zurück im Kasten: kein B-Trade.

**C · Abpraller**
- Der Kasten ist reif (Stufe 2).
- Eine neue Berührung an einer Linie (Docht innerhalb 0,15 ATR), und die Kerze schließt mindestens 0,25 ATR innerhalb des Kastens.
- Auslöser: Schluss dieser Kerze. Einstieg Richtung andere Seite (an der unteren Linie long, an der oberen short).
- Stop: Linie ∓ 0,3 ATR. Ziel: gegenüberliegende Linie ∓ 0,15 ATR.
- Nur wenn das Ziel mindestens 1 R entfernt ist.

**D · Fehlausbruch**
- Zuerst ein Ausbruch wie bei A, ohne Einstieg.
- Innerhalb von 3 Kerzen schließt eine Kerze wieder mindestens 0,1 ATR innerhalb des Kastens.
- Auslöser: Schluss dieser Kerze. Einstieg gegen den Ausbruch.
- Stop: Extrem des Ausbruchs ± 0,1 ATR. Ziel: gegenüberliegende Linie.

**Simulation**
- Auf SIP-1-Min-Kerzen.
- Berühren Stop und Ziel dieselbe Minute, zählt der Stop.
- Öffnet eine Minute jenseits des Stops, zählt ihr Eröffnungskurs.
- Das Ziel füllt nur, wenn der Kurs durch das Ziel handelt.

**Varianten**
- 4 Einstiege × 2 Zeitebenen = **8 Varianten**.
- In jeder Variante werden die Noten A, B und C getrennt gemessen. Als „gehandelt“ zählt nur Note A.

## 6. Daten, Aktien, Zeiträume, Bewertung

**Aktien**
- Die 50 mit dem höchsten mittleren Tagesumsatz in Dollar aus unserer Liste von 150.
- Gemessen im September 2021, also vor dem Entwicklungszeitraum. Die Liste wird vorab festgelegt.
- Die Überlebensverzerrung (Liste von heute) steht im Bericht an erster Stelle.

**Entwicklung**
- 01.10.2021–30.09.2023, also zwei Jahre im Lerntopf.
- Die Daten (SIP 1 Min) liegen schon auf dem PC, es ist kein Download nötig.

**Prüfung**
- Kalenderjahre **2024 und 2025**, genau **einmal**, nur für die Variante(n), die in der Entwicklung überzeugen.
- Nur nach eigener Vorab-Datei und OK des Inhabers. Das ist Öffnung 1 von 3 des Prüftopfs.
- Fehlende SIP-1-Min für die 50 Werte werden erst dann geladen, außerhalb 15:30–22:00.

**„Überzeugt“ in der Entwicklung**, vorab festgelegt, alles nach Kosten, nur Note A:
1. beide Jahre positiv, je mindestens 50 Trades (darunter heißt es „zu wenig Daten“);
2. über beide Jahre mit Kostenstress (+0,03R) noch positiv;
3. schlägt den neuen Zufallstest (Abschnitt 7) in mindestens 95 von 100 Läufen;
4. **Note A besser als Note C** (Ø R nach Kosten). Sonst bringt die saubere Erkennung nichts, und das Muster fliegt raus.

**Prüfung 2024–2025:** die Erfolgskriterien K1–K5 aus FAHRPLAN.md, unverändert; dazu jedes Jahr positiv; die Zufallslatte „Bester von N“ mit N = Zahl der geprüften Varianten.

## 7. Kosten und Zufall

**Kosten**
- Je Trade der höhere Wert aus 0,03R (long) bzw. 0,05R (short) und der Slippage.
- Slippage = 2 Seiten × max(0,01 $; 0,02 % vom Kurs), geteilt durch den Stop-Abstand.
- Kostenstress: zusätzlich +0,03R.

**Zufallstest, neu**
- Je echtem Trade gleiche Aktie, gleiche Uhrzeit (dieselbe Kerze des Tages), gleiche Richtung, aber ein **zufälliger anderer Handelstag**, höchstens 20 Handelstage entfernt und im selben Zeitraum.
- Gleicher Stop-Abstand in %, gleiches Ziel in R, gleiche Ausstiegsregeln und Kosten.
- 100 Läufe, fester Startwert.
- So kennt der Zufall keinen echten Ausbruch, und ein reiner Markttrend wird trotzdem herausgerechnet.

## 8. Bilder: der Moment der Entscheidung

- Im Moment der Entscheidung schreibt die Erkennung einen **Schnappschuss**:
  - die Kerzen bis einschließlich der Entscheidungskerze;
  - die Linien, die Berührungen, Note und Stufe;
  - geplanter Einstieg, Stop und Ziel.
- Danach kommt nur noch der Ausgang dazu (spätere Kerzen, Ausstieg), in eigenen Feldern.
  Linien und Berührungen werden **nie neu berechnet**.
- Pflichttest: Der Hash des Schnappschusses ist vor und nach dem Anhängen des Ausgangs gleich.
- Dieselbe Funktion schreibt später live den Schnappschuss beim Signal (Paper auf Konto 2).
- Pflichttests auf künstlichen Kursen:
  - Ein Lehrbuch-Rechteck wird erkannt, ein Kasten mit nur einer Berührung oben nicht.
  - Ein Kasten über zwei Tage wird nicht erkannt.
  - Ein Docht 0,2 ATR neben der Linie zählt nicht als Berührung.
  - Abschneide-Test: Mit Daten nur bis zur Entscheidung entstehen dieselben Signale.

## 9. Die Lernhub-Seite und der Datenvertrag

**Seite**
- `lernhub/vorlage/lernhub.html` ist fertig gebaut: Design wie das Dashboard, hell und dunkel, Handy.
- Der Inhaber hat sie als Vorschau mit Beispielbildern gesehen und freigegeben.
- Abschnitte:
  - Plan;
  - so liest der Bot ein Rechteck;
  - vier Einstiege;
  - Ergebnisse;
  - alle Trades mit großem Bild (Moment der Entscheidung oder mit Ausgang);
  - Sichtprüfung;
  - Scanner;
  - Dokumentation.
- Die Seite liest alle Daten vom Branch **backtest**, Ordner `lernhub/daten/`, über raw.githubusercontent.com, wie die alte Labor-Seite.
- Ergebnisse gehen also NICHT auf main, sondern nur nach backtest. Auf main liegt nur die Seite.
- Fehlt eine Datei, zeigt der Abschnitt einen Leerzustand.

**Dateien in `lernhub/daten/` auf backtest** (Felder genau so, die Seite liest sie):
- `status.json`
  ```
  {"stand": ISO, "phase": "Text", "laeuft": true|false,
   "plan": [{"titel","text","status":"fertig|laeuft|offen","datum"}],
   "log": [{"zeit": ISO, "text", "link"?}]}
  ```
- `ergebnisse.json`
  ```
  {"stand": ISO, "varianten": [{"zeitebene": 5|15, "einstieg": "A|B|C|D",
   "werte": {"entw": {"trades", "ev_vor", "ev", "pf", "jahre": [{"ev"}, {"ev"}],
     "noten": {"A": {"trades", "ev"}, "B": {...}, "C": {...}}, "zufall": 0-100},
     "pruef": {"ev"} | null},
   "urteil": "Text", "urteil_art": "good|bad|part|run"}]}
  ```
  Die Werte gelten für Note A, außer unter `noten`.
- `trades/index.json`
  ```
  {"stand", "gruppen": [{"id": "15m-A", "zeitebene", "einstieg", "zeitraum": "entw", "anzahl", "teile": ["trades/15m-A/000.json", …]}]}
  ```
- `trades/<id>/NNN.json` (höchstens 200 Trades je Datei)
  ```
  {"trades": [{"id", "symbol", "tag": "YYYY-MM-DD", "zeitebene", "einstieg", "richtung": "long|short",
   "note": "A|B|C", "r", "r_vor", "ausgang": "ziel|stop|tagesende",
   "kerzen": [["HH:MM", o, h, l, c, v], …] (ganzer Handelstag, nur reguläre Zeit),
   "entscheidung": Index, "oben", "unten", "box_von", "box_bis",
   "beruehrungen": [{"i", "p", "seite": "oben|unten"}],
   "einstieg_i", "einstieg_p", "stop", "ziel", "ausstieg_i", "ausstieg_p",
   "fakten": [["Höhe", "3,2 ATR"], …]}]}
  ```
  Alle Trades aller Noten, damit man auch C ansehen kann.
- `sichtpruefung.json`
  ```
  {"id": "rechteck-1", "muster": "Rechteck", "stand",
   "bilder": [{"id", "symbol", "tag", "zeitebene", "note", "kerzen" (nur bis zur Entscheidung), "entscheidung",
     "oben", "unten", "box_von", "box_bis", "beruehrungen"}]}
  ```
  30 zufällige Erkennungen aus der Entwicklungszeit, fester Startwert, **ohne Ausgang, ohne Stop und Ziel**.
  Der Inhaber klickt ja/nein/unsicher, kopiert das Ergebnis und schickt es zurück. Es kommt ins Logbuch.
- `scanner.json` kommt später (Paper auf Konto 2):
  ```
  {"stand", "markt_offen", "zeilen": [{"symbol", "zeitebene", "stufe": 0-4, "note", "abstand_atr", "kerzen", "oben", "unten", "box_von", "box_bis", "beruehrungen"}]}
  ```
- Beispieldaten zum Testen der Seite: `lernhub/vorlage/beispieldaten.js`. Sie werden nie veröffentlicht.

## 10. Telegram

Der Labor-Bot meldet ohne Schlüssel und ohne Pfade:
- „Sichtprüfung bereit: 30 Bilder auf der Lernhub-Seite“;
- „15 Min fertig“ bzw. „5 Min fertig“, jeweils mit der besten Variante, den Trades, Ø R nach Kosten (Note A) und dem Link zur Seite;
- jeden Abbruch mit Grund.

## 11. Was immer gilt

- **Nur Paper.** Der Live-Bot bleibt unverändert und eingefroren, er läuft als Messgerät weiter.
- **Bot-Code nie auf GitHub, keine Schlüssel.** Öffentliche Dateien enthalten keine IP-Adressen, Hostnamen, Benutzernamen oder Pfade. Der Prüfer läuft vor jedem Upload, auch über den Inhalt der JSON-Dateien.
- **Vor jedem Lauf auf echten Daten:** Vorab-Datei mit SHA-256 im Logbuch. Nach Ergebnissen ändert sich nichts mehr; Änderungen ergeben eine neue Fassung.
- **Der Prüftopf** (Okt 2023 – Sep 2026) bleibt zu bis zur freigegebenen Prüfung 2024–2025.
- **Rechenlast:** 50 Aktien, ein Muster, zwei Jahre. Das ist klein und läuft in Minuten. Keine Läufe über Nacht auf dem Hauptrechner des Inhabers.
- **Zeit im Code nur New York.** Am So 25.10. stellt Deutschland auf Winterzeit um, die USA erst am 01.11. In dieser Woche liegt New York nur 5 Stunden zurück.

---

## 12. AUFTRAG HEUTE · Fr 23.10. · nur die Webseite (wenig Credits)

1. `lernhub/vorlage/lernhub.html` vom Branch `claude/epic-gates-iz9swg` holen und **unverändert** als `labor.html` auf main legen.
2. Die bisherige `labor.html` vorher unverändert als `labor-archiv.html` auf main sichern. Die neue Seite verlinkt sie in der Fußzeile.
3. `labor-name.js` auf main: `window.LABOR_NAME = "Lernhub";`. Der Knopf im Dashboard heißt dann automatisch so.
4. Auf backtest `lernhub/daten/status.json` anlegen:
   - Plan mit 7 Punkten wie in der Vorlage. Punkt 1 „Lernhub-Seite neu“ auf „fertig“, die übrigen auf „offen“.
   - Dazu ein Log-Eintrag „Lernhub-Seite online, Werkbank Rechteck startet So 25.10. 14:00“.
5. `push_main.py`: `labor.html`, `labor-archiv.html` und `labor-name.js` zulassen. Der Prüfer muss grün sein.
   Kein weiterer Diff an den Inhaber, die Vorschau ist freigegeben.
6. Im Fahrplan einen Punkt „Große Umstellung v2: Werkbank Rechteck (lernhub/prompts/grosse-umstellung-v2-zielsetzung.md)“, dazu ein Tageslog.
   Lauf 1 als „archiviert, nicht weiter gerechnet“.
7. Die Seiten-Dateien kommen ins nächste Ausgabe-Paket für den Pi, damit `dashboard_sync` sie nicht überschreibt.
8. Kurze Meldung an den Inhaber mit Link. Sonst heute nichts rechnen.

## 13. AUFTRAG SONNTAG · 25.10. ab 14:00 · Ziel: abends die ersten Ergebnisse

Reihenfolge, jeder Schritt erst nach dem vorigen:

1. **Aktienliste:** die 50 nach Dollar-Umsatz im September 2021 festlegen. Liste und Messung ins Logbuch.
2. **Erkennung bauen** nach Abschnitt 4, mit Reifegrad, Note und Schnappschuss (Abschnitt 8). Alle Pflichttests auf künstlichen Kursen grün.
3. **Sichtprüfung:**
   - 30 zufällige Erkennungen (15 und 5 Min gemischt, alle Noten, fester Startwert) aus Okt. 2021 bis Sep. 2023;
   - als `sichtpruefung.json` nach backtest;
   - Telegram an den Inhaber.
   - **Ab hier wartet die Warteschlange**, bis das Ergebnis des Inhabers da ist.
   - Unter 80 % „ja“: die Nein-Bilder ansehen, die Erkennung verbessern (es gibt noch keine Ergebnisse, das ist erlaubt), neue Runde mit neuem Startwert.
4. **Vorab-Datei „Werkbank Rechteck v1“** mit allen Regeln dieser Datei:
   - Aktienliste, Zeiträume, Kriterien „überzeugt“, Zufallstest, Code-Hash;
   - als Entwurf an Claude im Chat;
   - nach OK festlegen, SHA-256 ins Logbuch.
5. **Lauf Entwicklung:** 15 Min, dann 5 Min, alle 4 Einstiege, alle Noten, Zufallstest.
   - Danach `ergebnisse.json` und `trades/` nach backtest, die Seite füllt sich von selbst.
   - Telegram je Zeitebene.
6. **Kurzbericht** an den Inhaber und an Claude im Chat:
   - zuerst die Vorbehalte (Überlebensverzerrung);
   - dann die 8 Varianten mit Note A, B und C;
   - welche „überzeugt“.
   - Für 2024–2025 wird nichts geöffnet. Die Vorab-Datei der Prüfung nur als Entwurf, erst nach OK.

## 14. Bewusst später

- Break-even und Trailing als eigene Variante.
- Scanner live mit Paper auf Konto 2. Für 5 und 15 Min live braucht es Echtzeitdaten: SIP im Bezahltarif oder ein Zusatztest auf IEX-Kerzen. Das entscheidet der Inhaber.
- Das zweite Muster (Vorschlag: aufsteigendes Dreieck), erst wenn das Rechteck fertig ist.
- Bild-Netz aus den Antworten der Sichtprüfung (Etappe 3).
