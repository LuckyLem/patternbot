# Checkliste: Der Weg zum erfolgreichen Trading

Bewertung aus der Sicht eines erfahrenen, unabhängigen Traders, der vom Trading lebt. Stand: 01.10.2026.

Die Fehler und Verbesserungen im Einzelnen, sortiert nach Geld-Wirkung, stehen in [fehler-und-verbesserungen.md](fehler-und-verbesserungen.md).

## Lage in Kürze

- **Konto:** 10.011,11 $, zum ersten Mal über dem Start (+11,11 $).
- **Alle 56 Trades seit 10.09.:** +31,48 $, Profitfaktor 1,11. Das ist gute Technik bei einem Ergebnis um null. Ein Vorteil ist noch nicht nachgewiesen, in diesem Stadium ist das normal.
- **Neue Version seit 28.09.:** 6 Trades, +1,55R bzw. +25,09 $, 5 davon im Plus.
- **30.09.:** 3 von 3 Trades im Plus, +1,12R. Keiner erreichte sein Ziel. Das Geld kam vom Zeit-Stop und vom Tagesende. Mit V1 wären es laut Simulation 6 Trades mehr gewesen, zusammen +1,59R.

## Was schon richtig gut läuft

- **Mechanische Regeln, kein Bauchgefühl.** Die meisten privaten Trader scheitern an der eigenen Disziplin. Der Bot hat dieses Problem nicht.
- **Risikomanagement auf Profi-Niveau:** festes Risiko pro Trade, höchstens 5 Positionen, abends flach, nur Paper.
- **Messkultur.** Jedes Setup, jede Ablehnung und jede Order wird protokolliert. Hypothesen werden geprüft und auch verworfen, wie beim Volumenfilter. Das ist seltener und wertvoller als jede Mustererkennung.
- **Ausführung.** Order in Sekunden, Broker-Abgleich jede Minute, verifizierte Glattstellungen. Gute Ausführung schafft keinen Vorteil, schlechte zerstört ihn aber. Diese Baustelle ist zu.
- **Statistische Ehrlichkeit.** „Unter 60 Trades kein Urteil“ und „Backtest vor Umstellung“: Genau so denkt man, wenn man davon leben muss.

## Was ich verbessern würde, nach Wichtigkeit

1. **Erst den Vorteil beweisen, dann optimieren.** Der Backtest über 8 bis 12 Wochen ist der wichtigste offene Punkt. Dazu gehört der Vergleich mit zufälligen Einstiegen in derselben Aktie zur selben Tageszeit, mit denselben Stops und derselben Haltedauer. Schlagen die Muster den Zufall nicht, steckt der Vorteil nicht in den Mustern.
2. **Das Problem „Ausbrüche laufen nicht weiter“ angehen.** Im Median kamen die Trades nur auf +0,19R, von 42 Zielen wurden 2 erreicht. Ausbrüche funktionieren vor allem in Trendmärkten, nach einer engen Seitwärtsphase und in Richtung des Gesamtmarkts. Das als Filter testen, statt an bestehenden Schwellen zu drehen.
3. **Ziele an die tatsächliche Bewegung anpassen.** Endet die typische Bewegung bei 0,5 bis 0,7R, sind Ziele bei 1,5R Wunschdenken. Im Backtest testen: Teilgewinn bei etwa 0,7 bis 1R, den Rest mit Trailing-Stop laufen lassen. Profis verdienen meist an wenigen großen Gewinnern. Das System lässt heute keinen zu.
4. **Gleiches echtes Risiko pro Trade.** Durch die Wertgrenze riskiert ein Trade mal 16 $, mal 50 $. Dann laufen R und Dollar auseinander.
5. **Risiko auf Portfolioebene.** Fünf Bank-Shorts gleichzeitig sind keine fünf Trades, sondern eine Wette. Positionen in dieselbe Richtung und Branche begrenzen, dazu ein Verlustlimit pro Woche.
6. **Datenqualität vor Echtgeld.** IEX-only bedeutet veraltete Kurse, ein unbrauchbares Orderbuch und Symbole ohne Kerzen. Für Paper reicht das, für echtes Geld gehören Echtzeit-SIP-Daten (etwa 99 $ im Monat) dazu.
7. **Kosten realistisch einrechnen.** Paper-Ausführungen sind zu freundlich. In jeder Auswertung pauschal 0,03R bis 0,05R pro Trade abziehen, bei Shorts eher mehr.
8. **Pro Zyklus nur eine Änderung.** Jede Regeländerung bekommt Datum und Versionsnummer, und jeder Trade speichert die Version mit. Sonst weiß niemand, was gewirkt hat.

## Die Checkliste

### 1. Fundament: Technik und Betrieb

- [x] Nur Paper, festes Risiko von 0,5 %, höchstens 5 Positionen, Tagesverlust-Stopp
- [x] Mechanische Regeln, keine Handeingriffe im laufenden Handel
- [x] Abends immer flach, Übernacht-Fehler behoben, Abgleich mit dem Broker jede Minute
- [x] Order in Sekunden nach Kerzenschluss (seit 28.09.)
- [x] Jeder Trade und jedes Setup wird protokolliert und exportiert (seit 30.09.)
- [x] Täglicher Abgleich DB gegen Broker auf 0,10 $ genau
- [ ] Bot-Version bei jedem Trade mitspeichern, Änderungsprotokoll mit Datum führen
- [ ] Notfallplan schriftlich: Was passiert bei Ausfall von Strom, Internet oder API mit offenen Positionen?

### 2. Datenqualität

- [ ] V4: Spread-Prüfung nur mit plausiblem Orderbuch
- [ ] Universum bereinigen: BK, MMC und FI liefern keine Kerzen
- [ ] In jeder Auswertung pauschal 0,03R bis 0,05R Kosten pro Trade abziehen
- [ ] Vor Echtgeld: Echtzeit-SIP-Daten

### 3. Vorteil nachweisen (Backtest)

- [ ] Backtest auf 1-Minuten-Kerzen über 8 bis 12 Wochen. Die heutige Variante muss die echte Woche auf höchstens 0,1R pro Trade genau treffen.
- [ ] Erfolgskriterien vorher festlegen, bevor die Ergebnisse da sind:
  - mindestens 200 Trades
  - Erwartungswert nach Kosten mindestens +0,10R pro Trade
  - Profitfaktor mindestens 1,3
  - maximaler Drawdown höchstens 15R
- [ ] Vergleich mit zufälligen Einstiegen bei gleichen Regeln
- [ ] Prüfung auf Daten, die nicht zum Entwerfen benutzt wurden: erste Hälfte entwerfen, zweite Hälfte prüfen
- [ ] Auswertung nach Muster, Richtung, Tageszeit und Marktlage

### 4. Strategie schärfen (nur mit Backtest, eine Änderung pro Zyklus)

- [ ] V1 einschalten: Auswahl wie in der alten Version, mit schneller Ausführung
- [ ] V2: Zonengrenzen auf den Cent runden
- [ ] Marktfilter testen: nur in Richtung des Gesamtmarkts (SPY) handeln
- [ ] Enge Seitwärtsphase vor dem Ausbruch als Bedingung testen
- [ ] Tageszeit prüfen: Eröffnung bis 10:00 und Mittagsflaute getrennt auswerten
- [ ] Ausstieg testen: Teilgewinn plus Trailing-Stop statt festem Ziel
- [ ] Muster mit dauerhaft negativem Ergebnis streichen, zum Beispiel Rechtecke, falls sich ihr Minus bestätigt

### 5. Risiko auf Portfolioebene

- [x] Festes Risiko pro Trade
- [ ] Gleiches tatsächliches Risiko pro Trade, ohne Verzerrung durch die Wertgrenze
- [ ] Höchstzahl an Positionen in derselben Richtung und Branche
- [ ] Verlustgrenze pro Woche, zum Beispiel −5R: dann Pause und Analyse
- [ ] Verlustgrenze vom Höchststand, zum Beispiel −10R: dann Stopp und Überprüfung der Strategie

### 6. Vorwärtstest auf Paper

- [ ] 4 bis 8 Wochen ohne Regeländerung, mindestens 100 Trades
- [ ] Das Paper-Ergebnis liegt im Rahmen des Backtests, höchstens 0,05R pro Trade Abweichung
- [ ] Ausführung stabil über den ganzen Zeitraum: Order unter 60 Sekunden, höchstens 0,15R hinter der Kante, keine Waisen-Positionen, keine Fehlalarme

### 7. Echtgeld (erst wenn 3 bis 6 erfüllt sind)

- [ ] Klären, ob Alpaca Live-Konten aus Deutschland annimmt
- [ ] Nur Geld einsetzen, dessen Verlust nicht wehtut. Für Leerverkäufe sind mindestens 2.000 $ nötig.
- [ ] Die ersten 100 Trades mit halbem Risiko (0,25 %)
- [ ] Echtgeld und Paper parallel vergleichen und vorher festlegen, ab welcher Abweichung gestoppt wird
- [ ] Steuer vorbereiten: Jahresaufstellung in Euro für die Anlage KAP

## Routine

**Täglich (5 Minuten):**
- Ist der Broker flach?
- Stimmt der Abgleich?
- Gab es Alarme?
- Nichts ändern.

**Wöchentlich:**
- Review mit Latenz, Slippage, Filter-Trichter und R-Verteilung
- Liste offener Fragen pflegen
- Höchstens eine Änderung beschließen

**Monatlich:**
- Gesamtstatistik und Drawdown
- Vergleich mit dem Backtest
- Entscheiden: weiterlaufen lassen, ändern oder stoppen

## Abbruchkriterium

- [ ] Liegt nach 200 Trades der Erwartungswert nach Kosten bei null oder darunter: Strategie neu denken, nicht weiter an Parametern drehen.

## Nächste Schritte

1. **Vor dem Wochenende:** V1 nach Handelsschluss einschalten, danach die Regeln bis Samstag einfrieren.
2. **Freitag:** Wochenreview. Die erste fast volle Woche der neuen Version ist die Vergleichsbasis.
3. **Samstag:** Technik ohne Strategieänderung: Version pro Trade, Änderungsprotokoll, V4, Universum bereinigen, Notfallplan. Dazu die Erfolgskriterien für den Backtest festlegen.
4. **Sonntag:** Backtest bauen und kalibrieren, erste Varianten rechnen, Zufallsvergleich. Abends das Technik-Paket aufspielen, mit Backup, grünen Tests und ohne offene Positionen.
5. **Woche danach:** Bot unverändert laufen lassen. Erst am folgenden Wochenende höchstens eine Änderung live schalten, und zwar die, die im Backtest am klarsten gewonnen hat.
