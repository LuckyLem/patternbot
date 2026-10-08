# Fahrplan

Der eine Ort für alles, was ansteht, läuft oder erledigt ist: Live-Bot, Backtest-Runden, ORB-Studie und Lern-Labor.
Angelegt am 08.10.2026. Das Raster „Fahrplan“ auf der Webseite wird aus dieser Datei erzeugt.

**Status:** ✅ erledigt (mit Datum) · ⏳ läuft oder gebaut · ⬜ offen · 🔬 nur per Test · ❌ verworfen.
Nichts wird gelöscht, nur abgehakt.

**Wer:**
- **VS Code:** Claude Code im Editor; baut, rechnet und lädt hoch.
- **Chat:** Claude im Chat; prüft Vorab-Dateien und Berichte.
- **Inhaber:** gibt frei, schaltet um und legt Konten und Schlüssel an.

**Zeiten:** in deutscher Zeit, New York in Klammern. Der Code rechnet ausschließlich in New-York-Zeit.

**Fortschritt** je Bereich: erledigte Punkte geteilt durch alle Punkte ohne die verworfenen.

Ältere Listen (Stand 02.10.2026, unverändert übernommen):
- [Checkliste Trading](docs/checkliste-trading.md)
- [Fehler und Verbesserungen](docs/fehler-und-verbesserungen.md)
- [Break-even-Vergleich](docs/break-even-vergleich.md)

Die aktuellen Stati stehen hier.

<a id="kriterien"></a>
## Erfolgskriterien (unveränderlich)

<!-- KRITERIEN:ANFANG -->
Quelle: festgehalten am 03.10. um 12:02 im Commit be9ca33 auf backtest, vor dem ersten Ergebnis.

- K1 Trades: mindestens 200 im Prüfzeitraum.
- K2 Erwartungswert nach Kosten: mindestens +0,10R je Trade.
- K3 Profitfaktor nach Kosten: mindestens 1,3.
- K4 Max. Drawdown: höchstens 15R. Gemessen Trade für Trade in R über den ganzen Prüfzeitraum, wie live mit 5 Plätzen und 0,5 % Risiko.
- K5 Zufallsvergleich: besser als mindestens 95 von 100 Zufallsläufen. Aufbau wie im bestehenden Zufallsvergleich, fester Startwert. Bei mehreren Kandidaten gilt die Latte „Bester von N“.

Kosten:

- Jahresrunden: 0,03R je Long, 0,05R je Short.
- Lern-Labor, Kandidaten und ORB: der höhere Wert aus diesen festen Kosten und der Slippage. Slippage = je Seite max(0,01 $; 0,02 % vom Kurs) je Aktie, geteilt durch den Stop-Abstand.

Daten: Quelle, Zeitraum und Datenstand stehen in jeder Vorab-Datei.

Lern-Labor zusätzlich: jedes Jahr im Prüftopf einzeln positiv.

Ein Vorteil unter +0,10R zählt nur als „echter kleiner Vorteil“, wenn er bei +0,03R Kostenstress noch positiv ist. Er wird dokumentiert und beobachtet, kommt aber nicht ins Paper.

Eine spätere Änderung der Kriterien gilt nur als neue Fassung mit Begründung und neuer Commit-ID, und nur für Prüfungen, die danach festgelegt werden.
<!-- KRITERIEN:ENDE -->

Commit-ID dieses Abschnitts: [4c580ae](../../commit/4c580ae51667568a4d3c0d0be90d4f62ba1964c1), der erste Commit
dieser Datei am 08.10.2026 um 19:19.

SHA-256 des Abschnitts zwischen den Markierungen:
`e5c7ba37755a34936d1c2101c550598a50c8ec493f8a63a7e46e615f7f70cd75`.

Der Generator der Webseite prüft diesen Wert bei jedem Lauf. Weicht der Abschnitt ab, bricht er ab, und nichts wird
hochgeladen.

## Feste Regeln (gelten immer)

- Nur Paper, keine Live-Freigabe.
- Risiko 0,5 % je Trade, max. 5 Positionen, 20-%-Wertgrenze unverändert. Keine gelockerten Filter.
- Nie zwei Instanzen auf einem Konto. Schlüssel nie ausgeben.
- Der Live-Bot ist nach dem Technik-Paket eingefroren.
  - Änderungen nur nach bestandener Prüfung und mit OK des Inhabers.
  - Ausnahme: reine Technik- und Sicherheits-Fixes wie die Halbtage, ebenfalls nur mit OK.
- Deploy nur:
  - mit grünen Tests auf dem Pi;
  - ohne offene Positionen;
  - mit Backup;
  - außerhalb von 15:30–22:00 (09:30–16:00 New York);
  - nie in der Tagesend-Phase.
- Bot-Code nie auf GitHub, das Repo ist öffentlich.
- Backtest- und Lern-Ergebnisse nur auf dem Branch backtest. Fahrplan, Raster und Webseiten auf main.
- Keine Buchinhalte, keine Schlüssel, keine Kontodaten im Repo oder auf der Webseite.
- Öffentliche Dateien enthalten auch keine IP-Adressen, Hostnamen, Benutzernamen oder Pfade. Ein Prüfer läuft vor
  jedem Upload.
- GitHub-Push:
  - Nie data.json oder andere Dateien anfassen, die der Pi schreibt (er pusht alle 10 Minuten auf main).
  - Nur die gewünschte Datei schreiben, über die Contents-API mit aktuellem SHA.
  - Bei Konflikt: neu lesen und höchstens dreimal versuchen, dann Stopp und Meldung an den Inhaber.
  - Nie force-push, kein automatisches Mergen fremder Änderungen.

## Zeitplan

**Do 08.10.:**
- Fahrplan und Erfolgskriterien.
- Raster „Fahrplan“ im Dashboard.
- Lern-Labor-Seite mit Knopf, vorgezogen von Mo 12.10.
- Halbtage geprüft.
- Notfallplan.
- Entwürfe: Lernzeit-Wächter, Telegram-Texte, Datenplan.
- Logbücher und Abschneide-Test.

**Fr 09.10.:**
- Wochenreview.
- Technik-Paket ab 22:30 (16:30 New York). Bedingung: `setups/2026-10-09.json` liegt auf main. Review und Export
  laufen vorher ungestört durch.
- Danach ist live eingefroren.

**Sa/So 10.–11.10.:**
- V1-Woche im Replay nachrechnen.
- Runde 2 (ohne Rechtecke).
- Downloads 2020–2023.
- Isolation auf dem Pi einrichten und testen.
- Entwurf der Vorab-Datei für Etappe 1, vor dem finalen Commit an den Inhaber.

**Ab Mo 12.10.:**
- Point-in-time-Quellen für Quartalszahlen, Nachrichten und das Universum zum Stichtag klären.
- Setups 2020–2023 erzeugen.

<a id="b1"></a>
## 1. Betrieb und diese Woche

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 1.1 | Halbtage 27.11. und 24.12. (Schluss 19:00, 13:00 New York): kennt der Live-Bot sie? | ✅ 08.10. | VS Code | 08.10. | – | Kein Fix nötig, Befund im Tageslog 08.10. |
| 1.2 | Halbtag-Test: Einstiege bis 12:30, Glattstellung 12:50 New York, danach keine Order | ⏳ | VS Code | Fr 09.10. | geht ins Technik-Paket | – |
| 1.3 | Technik-Paket aufspielen: Bot-Version, Änderungsprotokoll, Stop-Protokoll, skip-maxopen, Universum ohne BK/MMC/FI, Review nach Kosten, Halbtag-Test, Speicherschutz, Seiten-Dateien | ⏳ gebaut | VS Code + Inhaber | Fr 09.10. ab 22:30 | `setups/2026-10-09.json` auf main; Review (22:05) und Export (22:20) durch; Broker flach; Backup; Suiten grün auf dem Pi | Änderungsprotokoll mit echter Uhrzeit |
| 1.4 | Speicherschutz für den Bot-Dienst: MemoryLow und negatives OOMScoreAdjust (Drop-in) | ⏳ | VS Code + Inhaber | Fr 09.10. | Technik-Paket; danach Startzeile und Dienst-Einstellungen prüfen | – |
| 1.5 | Live einfrieren: danach nur Technik- und Sicherheits-Fixes mit OK | ⬜ | Inhaber | Fr 09.10. | 1.3 | – |
| 1.6 | Wochenreview | ⬜ | VS Code | Fr 09.10. | Handelsschluss | – |
| 1.7 | V1-Woche 05.–09.10. im Replay nachrechnen und mit Paper vergleichen (gleiche Kriterien wie die Kalibrierung) | ⬜ | VS Code | Sa 10.10. | frische Kopie der Live-Datenbank nach dem 09.10. | – |
| 1.8 | Notfallplan schriftlich: Strom, Internet oder API fallen aus, während Positionen offen sind | ✅ 08.10. | VS Code | 08.10. | – | [docs/notfallplan.md](docs/notfallplan.md), [Commit 7e8a063](../../commit/7e8a063135) |
| 1.9 | Bot-Version je Trade und Änderungsprotokoll | ⏳ gebaut | VS Code | Fr 09.10. | Technik-Paket | Prüfung nach dem Aufspielen |
| 1.10 | Kalibrierung auf dem Pi wiederholen, bevor dort gerechnet wird | ⬜ | VS Code | vor dem ersten Lauf auf dem Pi | nur falls auf dem Pi gerechnet wird; bisher rechnet der PC (dort bestanden 06.10.) | – |

<a id="b2"></a>
## 2. Backtest-Runden und ORB

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 2.1 | Replay kalibrieren: 659/659 Entscheidungen, 11/11 Orders | ✅ 03.10. | VS Code | 03.10. | – | Neu bestanden 06.10., [Commit 91526e9](../../commit/91526e9ce2), `kalibrierung/bericht.md` auf backtest |
| 2.2 | Runde 1 (Okt 2025–Sep 2026) | ✅ 06.10. | VS Code | 06.10. | – | 1.009 Trades, −0,056R, PF 0,76, max. DD 65R, Zufall 25/100: 1 von 5 Kriterien, Ziel nicht erreicht. [Commit 91526e9](../../commit/91526e9ce2), `runde-1/zusammenfassung.md` |
| 2.3 | Runde 2 (Okt 2024–Sep 2025), einzige Änderung: Rechtecke gestrichen. Bericht | ⬜ | VS Code | Sa/So 10.–11.10. | nur im Replay, kein Bot-Code; Kalibrierung gültig; Downloads außerhalb der Handelszeit | – |
| 2.4 | Entscheidung nach Runde 2: liegt sie bei null oder darunter, enden die Jahresrunden des jetzigen Bots, dann Fokus auf ORB und Lern-Labor | ⬜ | Inhaber | nach 2.3 | 2.3 | – |
| 2.5 | ORB-Studie: Regeln vorab festgelegt | ✅ 05.10. | VS Code | 05.10. | – | [Commit d48250c](../../commit/d48250c2), `orb-studie/VORAB-REGELN.md` |
| 2.6 | ORB Jahr 1 (Okt 2025–Sep 2026) nach den Vorab-Regeln. Bericht zusätzlich mit Trefferquote, längster Verlustserie, Ergebnis geteilt durch Drawdown. Dann Stopp bis zum OK | ⏳ läuft | VS Code | sobald die Downloads durch sind | Downloads nur nach 22:00 | – |
| 2.7 | ORB Jahr 2 (Okt 2024–Sep 2025) | ⬜ | VS Code | nach OK zu 2.6 | OK des Inhabers | – |
| 2.8 | Rechtecke im Live-Bot streichen | 🔬 | Inhaber | nach 2.3 | nur wenn ein Test es trägt und der Inhaber zustimmt | Runde 1: 567 Rechtecke, −0,087R je Trade |
| 2.9 | Replay-Seite (claude.ai) nach jeder Runde aktualisieren | ✅ bis 07.10. | Chat | nach jeder Runde | – | Runde 1 mit echten Zahlen |

<a id="b3"></a>
## 3. Offene Punkte aus den alten Listen

Nummern in Klammern = Nummer in [Fehler und Verbesserungen](docs/fehler-und-verbesserungen.md).

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 3.1 | (#1) Einstieg erst Minuten nach Kerzenschluss | ✅ 28.09. | VS Code | 28.09. | – | Order 32–38 s nach Kerzenschluss |
| 3.2 | (#2) Blinde Fenster bei 5 offenen Positionen | ⏳ gebaut | VS Code | Fr 09.10. | Technik-Paket (skip-maxopen) | – |
| 3.3 | (#3) Orders vor Börsenöffnung | ✅ bis 02.10. | VS Code | – | – | alte Liste |
| 3.4 | (#4) Zonengrenzen auf den Cent runden (V2) | ⬜ | VS Code | – | ändert die Auswahl: erst Test, dann OK | – |
| 3.5 | (#5) Anti-Chase-Zone am Schlusskurs statt an der Kante (V1) | ✅ 05.10. | Inhaber | 05.10. | – | aktiv seit 05.10. |
| 3.6 | (#6) Rechteck-Muster schwach | 🔬 | VS Code | Sa/So 10.–11.10. | Runde 2, siehe 2.3 und 2.8 | Runde 1: 567 Trades, −49R |
| 3.7 | (#7) Ziele ab 1,5R werden nicht erreicht | 🔬 | VS Code | – | Test | – |
| 3.8 | (#8) Übernacht- und Vorbörsen-Fehler (UAL, NSC) | ✅ 28.09. | VS Code | 28.09. | – | alte Liste |
| 3.9 | (#9) Einstiege in den letzten 90 Minuten | 🔬 | VS Code | – | Test | – |
| 3.10 | (#10) Eröffnungskerze und Nachholrunde um 09:50 | 🔬 | VS Code | – | Test | – |
| 3.11 | (#11) Paper füllt Ziel-Limits erst am Geldkurs (VRTX) | ⬜ | VS Code | – | ändert Ausstiege: erst Test, dann OK | – |
| 3.12 | (#12) Zeitgrenze nur zu Rundenbeginn geprüft | ✅ 28.09. | VS Code | 28.09. | – | alte Liste |
| 3.13 | (#13) Stop-Ausführung hinter dem Stop | ✅ 28.09. | VS Code | 28.09. | – | alte Liste |
| 3.14 | (#14) Spread-Prüfung mit unbrauchbarem IEX-Orderbuch (V4) | ⬜ | VS Code | – | ändert die Auswahl: erst Test, dann OK | – |
| 3.15 | (#15) Ungleiches Risiko je Trade durch die Wertgrenze | ⬜ | VS Code | – | siehe 8.1 | – |
| 3.16 | (#16) Webseite zeigt den nachgezogenen Stop (Break-even) | ✅ 03.10. | VS Code | 03.10. | – | Dashboard, [Commit 80348db](../../commit/80348dbcf5) |
| 3.17 | (#16) BK, MMC und FI liefern keine Kerzen | ⏳ gebaut | VS Code | Fr 09.10. | Technik-Paket (Universum ohne BK/MMC/FI) | – |
| 3.18 | (#16) Bot-Version je Trade | ⏳ gebaut | VS Code | Fr 09.10. | siehe 1.9 | – |
| 3.19 | (#16) Schriftlicher Notfallplan | ✅ 08.10. | VS Code | 08.10. | – | siehe 1.8 |
| 3.20 | (#16) Kein Echtzeit-SIP | ⬜ | Inhaber | vor Echtgeld | kostet: nur mit OK, siehe 8.6 | – |
| 3.21 | (#16) Übrige Technikpunkte (zehn Stück, vom Buchungsfehler bis zur Log-Rotation) | ✅ bis 02.10. | VS Code | – | – | alte Liste |
| 3.22 | Ausbrüche laufen kaum weiter | 🔬 | VS Code | – | Test | – |
| 3.23 | Teilgewinn plus Trailing-Stop statt festem Ziel | 🔬 | VS Code | – | Test | – |
| 3.24 | Marktfilter: nur in Richtung des Gesamtmarkts (SPY) | 🔬 | VS Code | – | Test | – |
| 3.25 | Enge Seitwärtsphase vor dem Ausbruch | 🔬 | VS Code | – | Test | – |
| 3.26 | Vergleich mit zufälligen Einstiegen | ✅ 03.10. | VS Code | 03.10. | – | Teil jeder Runde; Runde 1: 25 von 100 |
| 3.27 | Kosten realistisch abziehen | ✅ 03.10. | VS Code | 03.10. | – | 0,03R Long, 0,05R Short in jeder Runde |
| 3.28 | Volumenfilter auf 1,25 lockern (V5) | ❌ | – | 30.09. | – | −2,03R in 3 Tagen |
| 3.29 | Volumen nach Tageszeit normieren (V5) | ❌ | – | 30.09. | – | −5,23R in 3 Tagen |
| 3.30 | Frische-Grenze 180 statt 60 Sekunden (V3) | ❌ | – | 30.09. | – | 0 zusätzliche Orders |
| 3.31 | Stop-Order direkt am Ausbruchsniveau | ❌ vorerst | – | 27.09. | nur per Backtest neu bewerten | über alle 150 Aktien etwa 0R je Trade |
| 3.32 | Zeit-Stop nach 60 statt 120 Minuten | ❌ | – | bis 02.10. | – | −1,2R statt +2,4R |
| 3.33 | Ohne Zeit-Stop, ohne Break-even, Ziel halb so weit | ❌ | – | bis 02.10. | – | kein Gewinn |
| 3.34 | Long und Short vertauscht | ❌ | – | bis 02.10. | – | −1,6R statt +2,4R |
| 3.35 | Alle Break-even-Strategien (46 Varianten) | ❌ | – | bis 02.10. | – | [Break-even-Vergleich](docs/break-even-vergleich.md) |
| 3.36 | Break-even früher: ab +0,5R / +0,4R / +0,3R | ❌ | – | bis 02.10. | – | alte Liste |
| 3.37 | Break-even nach Anteil des Wegs zum Ziel | 🔬 | VS Code | – | im Backtest erneut prüfen | alte Liste |
| 3.38 | Fehlausbruch-Ausstieg bei Schluss hinter der Kante | ❌ | – | bis 02.10. | – | −0,71R in 52 Trades |
| 3.39 | Teilgewinn: Hälfte bei +0,4R bis +0,8R | ❌ | – | bis 02.10. | – | −0,20R bis −1,06R |

<a id="b4"></a>
## 4. Lern-Labor – das Hauptziel

Eine eigene Spur mit eigenen Vorab-Regeln, freigegeben vom Inhaber am 07.10. Die Spielregeln der Jahresrunden (keine
eigene Mustersuche, keine automatische Optimierung) gelten weiter für die Runden.

### Etappe 0 – Fundament

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 4.0.1 | Zeit im Code nur America/New_York mit echtem NYSE-Kalender (Feiertage, Halbtage); deutsche Zeit nur in Anzeigen | ✅ 08.10. | VS Code | 08.10. | – | Lernzeit-Wächter, Logbuch 08.10. |
| 4.0.2 | Lernzeit-Wächter: an Handelstagen 22:30–15:00 (16:30–09:00 New York), am Wochenende und an Feiertagen durchgehend | ✅ 08.10. | VS Code | 08.10. | – | 17 Prüfungen grün (Logbuch 08.10.); Entwurf `lern-labor/entwuerfe/lernzeit-waechter.md` auf backtest |
| 4.0.3 | Labor-Ordner außerhalb des Home-Bereichs, eigener Linux-Nutzer ohne Zugriff auf den Bot | ⬜ | VS Code + Inhaber | Sa/So 10.–11.10. | außerhalb der Handelszeit, Inhaber führt die Befehle mit Administratorrechten aus | – |
| 4.0.4 | Eigene systemd-Slice: MemoryMax 40 %, MemorySwapMax=0, CPUWeight=10, CPUQuota=200 %, IOWeight=10, Nice=19, IOSchedulingClass=idle, OOMScoreAdjust=1000 | ⬜ | VS Code + Inhaber | Sa/So 10.–11.10. | 4.0.3 | – |
| 4.0.5 | Bot-Schutz: MemoryLow und negatives OOMScoreAdjust | ⏳ | VS Code + Inhaber | Fr 09.10. | Technik-Paket, siehe 1.4 | – |
| 4.0.6 | Zugriff: InaccessiblePaths für Bot-Verzeichnis und Schlüssel, ProtectHome, ProtectSystem=strict, ReadWritePaths nur Labor-Ordner, NoNewPrivileges, PrivateTmp | ⬜ | VS Code + Inhaber | Sa/So 10.–11.10. | 4.0.3 | – |
| 4.0.7 | Zugriffstest: als Labor-Nutzer Bot-Verzeichnis und Schlüssel lesen, muss scheitern; Ergebnis ins Logbuch | ⬜ | VS Code | Sa/So 10.–11.10. | 4.0.6 | – |
| 4.0.8 | Timer in New-York-Zeit: Start 16:30, harter Stopp 09:00 mit Alarm; den Börsenkalender prüft der Job selbst; bei jedem Deploy pausiert alles | ⬜ | VS Code | Sa/So 10.–11.10. | 4.0.2 | – |
| 4.0.9 | Immer nur ein schwerer Job. Vorrang: Live-Bot, Runde 2, ORB, Lern-Labor | ⬜ | VS Code | Sa/So 10.–11.10. | – | – |
| 4.0.10 | Zwischenstände, damit ein gestoppter Job weitermachen kann | ⬜ | VS Code | Sa/So 10.–11.10. | – | Replay kann es schon |
| 4.0.11 | Speicherwächter: Stopp unter 5 GB frei, feste Obergrenze für den Labor-Ordner, Alarm per Telegram | ⬜ | VS Code | Sa/So 10.–11.10. | 4.0.3, 6.1 | – |
| 4.0.12 | Harte Sperre wie im Replay: nur Marktdaten, kein Trading. Eigene Sperrliste mit SEC-EDGAR (höchstens 10 Abrufe/s, Kontakt im User-Agent nur aus der .env, nie im Repo) | ⬜ | VS Code | Sa/So 10.–11.10. | – | – |
| 4.0.13 | Eigene Alpaca-Schlüssel (z. B. zweites Paper-Konto) in eigener .env im Labor-Ordner. Nie die Schlüssel des Bots: eigenes Abruflimit, keine Leserechte auf dessen .env. Ohne eigene Schlüssel holt das Labor auf dem Pi keine Daten | ⬜ | Inhaber | vor dem ersten Lauf auf dem Pi | – | – |
| 4.0.14 | Eigener GitHub-Token mit minimalen Rechten, nur für Ergebnisse | ⬜ | Inhaber | vor dem ersten Lauf auf dem Pi | – | – |
| 4.0.15 | Downloads nur außerhalb der Handelszeit und gedrosselt | ⬜ | VS Code | Sa/So 10.–11.10. | – | Replay-Sperre als Vorlage |
| 4.0.16 | Datenplan mit Größe je Teil | ✅ 08.10. | VS Code | 08.10. | – | `lern-labor/datenplan.md` auf backtest |
| 4.0.17 | Daten 2020–2023 laden: IEX 15 Min und Tageskerzen, IEX-Kurse und -Quotes für die Filter, SIP 1 Min; 150 Werte und SPY | ⬜ | VS Code | Sa/So 10.–11.10. | 4.0.16; auf dem PC, außerhalb der Handelszeit | – |
| 4.0.18 | Situation zur Form point-in-time: Kurslücke, relatives Volumen, Quartalszahlen, Nachrichten. Quellen klären, nichts Kostenpflichtiges ohne OK | ⬜ | VS Code | ab Mo 12.10. | – | – |
| 4.0.19 | Universum zum Stichtag inklusive gestrichener Werte (Überlebensverzerrung). Quelle klären | ⬜ | VS Code | ab Mo 12.10. | – | – |
| 4.0.20 | Jeder Trade wird bewertet wie der Bot handelt: Stop, Ziel, Zeitstopp, Tagesende. Kosten wie unter Erfolgskriterien | ⬜ | VS Code | ab Mo 12.10. | schneller Simulator | – |
| 4.0.21 | Nächtliche Schattenbilanz (Grundgerüst) | ⬜ | VS Code | – | 4.0.8 | – |
| 4.0.22 | Logbuch und Prüftopf-Logbuch | ✅ 08.10. | VS Code | 08.10. | – | `lern-labor/logbuch.md`, `lern-labor/prueftopf-logbuch.md` auf backtest |
| 4.0.23 | Abschneide-Test als feste Funktion: jedes Merkmal mit allen Daten und mit Daten nur bis zum Signal, beides muss gleich sein | ✅ 08.10. | VS Code | 08.10. | – | Selbsttest: 4 eingebaute Datenlecks erkannt (Logbuch 08.10.) |

### Etappe 1 – Trade ja oder nein (Meta-Labeling)

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 4.1.1 | Setups 2020–2023 mit dem Replay erzeugen: alle, auch die verworfenen (rund 33.000 je Jahr), und nachrechnen, was passiert wäre | ⬜ | VS Code | ab Mo 12.10. | 4.0.17 | – |
| 4.1.2 | Vorab-Datei `ETAPPE1_V1_PREREG.md`: Entwurf an den Inhaber vor dem finalen Commit | ⬜ | VS Code | Sa/So 10.–11.10. | – | – |
| 4.1.3 | Vorab-Datei prüfen und final committen; Commit-ID und SHA-256 ins Logbuch | ⬜ | Chat + Inhaber | nach 4.1.2 | 4.1.2 | – |
| 4.1.4 | Eingaben nur aus der Vergangenheit: Muster, Richtung, Uhrzeit, Volumen, Abstand zur Kante, Spread, Marktlage, Kurslücke, relatives Volumen, Quartalszahlen | ⬜ | VS Code | – | 4.0.18, 4.0.23 | – |
| 4.1.5 | Version 1: einfaches Modell | ⬜ | VS Code | – | 4.1.3 | – |
| 4.1.6 | Version 2: kleines neuronales Netz | ⬜ | VS Code | – | 4.1.5 | – |
| 4.1.7 | Später: Größe entscheiden, nur nach unten, nie über 0,5 % Risiko | ⬜ | VS Code | – | 4.1.5 | – |
| 4.1.8 | Prüftopf öffnen (Öffnung 1 von 3) | ⬜ | VS Code | – | freigegebene Vorab-Datei | – |

### Etappe 2 – Eigene Muster aus Form und Situation

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 4.2.1 | Fenster von 8, 16 und 32 Kerzen auf denselben IEX-15-Min-Kerzen wie live, normiert (Kurs in ATR, Volumen relativ zur Uhrzeit), dazu die Situation | ⬜ | VS Code | – | 4.0.17 | – |
| 4.2.2 | Formen-Gruppen: k-means mit 128 Gruppen je Fensterlänge; Stabilität über Seeds und 64/128/256 Gruppen nur im Lerntopf | ⬜ | VS Code | – | 4.2.1 | – |
| 4.2.3 | Vorwärts zählen, höchstens 1 Signal je Muster, Aktie und Tag; Musterkriterien im Lerntopf | ⬜ | VS Code | – | 4.2.2 | – |
| 4.2.4 | Mittlere Form je Muster als Bild | ⬜ | VS Code | – | 4.2.3 | – |
| 4.2.5 | Ideen aus Büchern als feste Regeln durch dieselbe Prüfung | ⬜ | VS Code | – | Abschnitt 5 | – |
| 4.2.6 | Vorab-Datei `ETAPPE2_V1_PREREG.md` | ⬜ | VS Code + Chat | – | 4.2.3 | – |
| 4.2.7 | Prüftopf öffnen (Öffnung 2 von 3, mit allen Buch-Kandidaten, die bis dahin feststehen) | ⬜ | VS Code | – | 4.2.6 | – |

### Etappe 3 – Eigenes neuronales Netz

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 4.3.1 | Lernt Signal und Entscheidung zusammen aus den Kerzen; Linien (Unterstützung, Widerstand, Trendlinien, VWAP, Durchschnitte) als Eingaben | ⬜ | VS Code | – | Etappe 1 und 2 laufen nachweislich fehlerfrei | – |
| 4.3.2 | Walk-forward: jedes Quartal neu lernen, einfrieren, nächstes Quartal im Schatten | ⬜ | VS Code | – | 4.3.1 | – |
| 4.3.3 | Rechenleistung klären: kleine Netze auf dem Pi, große Läufe am Wochenende auf dem PC mit Grafikkarte | ⬜ | VS Code | – | – | – |
| 4.3.4 | Reserve-Öffnung des Prüftopfs (Öffnung 3 von 3), z. B. Walk-forward des Netzes | ⬜ | VS Code | – | Vorab-Datei | – |

### Etappe 4 – Schattenbetrieb

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 4.4.1 | Jede Nacht alle eingefrorenen Modelle und Muster mit den Daten des Tages nachrechnen, dazu die klassischen Muster ohne 5-Plätze-Grenze | ⬜ | VS Code | – | 4.0.21 | – |
| 4.4.2 | Wochenbericht auf GitHub, per Telegram und auf der Webseite | ⬜ | VS Code | – | 4.4.1, 6.1 | – |
| 4.4.3 | Neue Suche höchstens einmal im Quartal, als neue Version | ⬜ | VS Code | – | – | – |
| 4.4.4 | Markierung „bereit für Paper“ (mindestens 200 Schatten-Trades, 3 Monate, alle 5 Kriterien) und „raus“ (Drawdown über 15R, oder nach 200 Trades Erwartungswert bei null oder darunter) | ⬜ | VS Code | – | 4.4.1 | – |

### Etappe 5 – Paper

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 4.5.1 | Nur nach bestandener Prüfung und mit ausdrücklichem OK | ⬜ | Inhaber | – | Etappe 4 | – |
| 4.5.2 | Eigenes Paper-Konto neben dem jetzigen Bot als A/B-Vergleich; prüfen, ob Alpaca ein zweites Paper-Konto erlaubt; nie zwei Instanzen auf einem Konto | ⬜ | Inhaber + VS Code | – | – | – |
| 4.5.3 | Einbau mit Kalibrierung und nach den Deploy-Regeln | ⬜ | VS Code | – | 4.5.1 | – |

### Etappe 6 – Perfektionieren

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 4.6.1 | Risiko senken: schwache Setups auslassen, bei Unsicherheit kleiner handeln | ⬜ | VS Code | – | Etappe 5 | – |
| 4.6.2 | Gewinn steigern: Ausstiege testen (Teilgewinn, Trailing), Grenzen auf Portfolioebene | ⬜ | VS Code | – | Etappe 5 | – |
| 4.6.3 | Jede Änderung geht wieder durch Schatten und Prüfung | ⬜ | VS Code | – | – | – |

### Prüfregeln für alle Etappen

**a) Vorab-Dateien**
- Ablage: `lern-labor/vorab/ETAPPE1_V1_PREREG.md`, `ETAPPE2_V1_PREREG.md` usw. auf backtest.
- Ablauf:
  1. Entwurf.
  2. Prüfung durch Claude im Chat (über den Inhaber).
  3. Finaler Commit. Commit-ID und SHA-256 der Datei ins Logbuch.
  4. Erst dann rechnen.
- Jeder Bericht nennt:
  - Commit der Vorab-Datei;
  - Datei-Hash;
  - Code-Hash von Simulator und Lern-Labor;
  - Datenstand.
- Eine Änderung ist eine neue Datei (V2). Die alte bleibt unverändert.

**b) Drei Datentöpfe, nie vermischt**
- Such- und Lerntopf 01.10.2020–30.09.2023: darf beliebig oft benutzt werden.
- Prüftopf 01.10.2023–30.09.2026:
  - gerechnet wird wie live mit 5 Plätzen und 0,5 % Risiko;
  - bestanden heißt: alle 5 Kriterien und jedes Jahr positiv.
- Zukunft: ab dem Einfrieren im Schatten.

**c) Prüftopf-Regeln**
- Jede Öffnung steht in `lern-labor/prueftopf-logbuch.md`: Datum, Baustein, Commit der Vorab-Datei, Ergebnis.
- Je Baustein höchstens einmal, insgesamt höchstens drei Öffnungen. Vorgesehen sind:
  - Etappe 1;
  - Etappe 2 mit allen Buch-Kandidaten, die bis dahin feststehen;
  - eine Reserve.

  Danach ist der Prüftopf verbraucht.
- Erst Urteil, dann Details: zuerst nur die 5 Kriterien und das Urteil ins Logbuch committen, Aufschlüsselungen
  erst danach.
- Kein Ergebnis aus dem Prüftopf fließt in den Bau einer späteren Version ein. Was dort durchfällt, wird als
  Version B nur noch in der Zukunft geprüft.
- Ideen, die aus Runde 1 oder 2 stammen (z. B. Kopf-Schulter), werden nicht auf diesen Jahren geprüft.

**d) Point-in-time (gegen Datenlecks)**
- ATR, Durchschnitte und Normierung nie mit Zukunftsdaten.
- Nachrichten nur mit dem ersten Veröffentlichungszeitpunkt, mindestens 60 Sekunden vor dem Signal.
- Quartalszahlen: nur Termine, die vor dem Handelstag bekannt waren.
- Gibt es für ein Merkmal keine Point-in-time-Quelle, fliegt es aus der Version.
- Abschneide-Test vor jedem Lauf. Ohne bestandenen Test wird nicht gerechnet, das Ergebnis kommt ins Logbuch.
- Ein auffällig gutes Ergebnis wird zuerst auf ein Datenleck geprüft.

**e) Zufallslatte**
- Dieselbe Suche oder dasselbe Training läuft auch auf vertauschten Daten. Was dort am besten aussieht, ist die
  Latte. Ein echter Fund muss sie in 95 von 100 Läufen schlagen.
- Version 1: ganze Handelstage vertauschen.
- Ab Version 2 Pflicht: Block-Permutation und Vertauschen innerhalb gleicher Marktphase.
- Es zählt immer die strengste Latte.

**f) Kosten und Simulator**
- Jeder Bericht zusätzlich mit +0,01R, +0,03R und +0,05R Extrakosten je Trade und mit +1 Cent je Aktie und Seite.
- Der Abschlag für den schnellen Simulator ist ein Messwert. Er wird bei jeder Kalibrierung neu gemessen und
  beträgt mindestens 0,01R.
- Bei einem Simulatorfehler mit unveränderten Regeln neu rechnen; beide Ergebnisse ins Protokoll.

**g) Überlebensverzerrung**
- Bis auf Weiteres nennt jeder Bericht: Die heutige Aktienliste enthält keine Werte, die früher gelistet waren
  und heute fehlen.

<a id="b5"></a>
## 5. Ideen aus Büchern

Der Inhaber liest und gibt die Bücher an Claude im Chat. Daraus werden prüfbare Regeln, in eigenen Worten.
Buchinhalte kommen nicht ins Repo.

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 5.1 | Kandidatenliste anlegen und pflegen | ✅ 08.10. | VS Code | 08.10. | – | `lern-labor/kandidaten.md` auf backtest |
| 5.2 | López de Prado, „Advances in Financial Machine Learning“ | ⬜ | Inhaber + Chat | – | – | – |
| 5.3 | Bellafiore, „The Playbook“ | ⬜ | Inhaber + Chat | – | – | – |
| 5.4 | Schwager, „Market Wizards“ | ⬜ | Inhaber + Chat | – | – | – |
| 5.5 | Aronson, „Evidence-Based Technical Analysis“ | ⬜ | Inhaber + Chat | – | – | – |

<a id="b6"></a>
## 6. Messenger (Telegram)

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 6.1 | Eigener Telegram-Bot oder Kanal fürs Lern-Labor, getrennt vom Handels-Bot. Zugang nur in die .env des Labors, nie in den Chat | ⬜ | Inhaber | vor dem ersten Lauf auf dem Pi | – | – |
| 6.2 | Texte entwerfen: Lernen startet und stoppt, nachts eine Bilanz, Wochenbericht, Alarme, abends „Heute geschafft / Morgen dran“ | ✅ 08.10. | VS Code | 08.10. | – | Entwurf `lern-labor/entwuerfe/telegram-texte.md` auf backtest |
| 6.3 | Einbau in den Labor-Dienst; jede Nachricht läuft durch den Prüfer (nie Schlüssel, Tokens oder Kontodaten) | ⬜ | VS Code | Sa/So 10.–11.10. | 6.1 | – |

<a id="b7"></a>
## 7. Webseiten

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 7.1 | Raster „Fahrplan“ im Dashboard: eine Kachel je Bereich, darüber „Zuletzt geschafft“ und „Als Nächstes“ | ✅ 08.10. | VS Code | 08.10. | `fahrplan.json` | [Commit 1faf3c1](../../commit/1faf3c1330) |
| 7.2 | Lern-Labor-Seite mit Knopf im Dashboard; Daten als JSON vom Branch backtest | ✅ 08.10. | VS Code | 08.10. | – | `labor.html`, [Commit cbc3202](../../commit/cbc320241b) |
| 7.3 | Generator für `lern-labor/status.json`: heute vom PC, später jede Nacht vom Pi | ⏳ | VS Code | ab Sa/So 10.–11.10. | Etappe 0 auf dem Pi | vom PC seit 08.10. |
| 7.4 | Auf der Lern-Labor-Seite: gefundene Muster als Bilder, Schattenbilanz je Modell und Muster, Versionen, Wochenberichte | ⬜ | VS Code | – | Etappen 2 und 4 | Leerzustände stehen |
| 7.5 | Seiten-Dateien mit gleicher Prüfsumme ins Technik-Paket, damit ein späteres Hochladen der Dashboard-Seite nichts überschreibt | ⏳ | VS Code | Fr 09.10. | 1.3 | – |

<a id="b8"></a>
## 8. Risiko und später Echtgeld (nur nach bestandenen Tests)

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 8.1 | Gleiches echtes Risiko je Trade | ⬜ | VS Code | – | Test und OK | alte Liste #15 |
| 8.2 | Grenze für Positionen in dieselbe Richtung und Branche | ⬜ | VS Code | – | Test und OK | – |
| 8.3 | Wochenverlust-Grenze −5R, Grenze vom Höchststand −10R | ⬜ | VS Code | – | Test und OK | – |
| 8.4 | Vorwärtstest auf Paper: 4 bis 8 Wochen ohne Änderung, mindestens 100 Trades, höchstens 0,05R Abweichung je Trade zum Test | ⬜ | VS Code | – | bestandener Test | – |
| 8.5 | Klären, ob Alpaca Konten aus Deutschland annimmt | ⬜ | Inhaber | – | – | – |
| 8.6 | Echtzeit-SIP-Daten | ⬜ | Inhaber | – | kostet: nur mit OK | – |
| 8.7 | Die ersten 100 Echtgeld-Trades mit 0,25 % Risiko | ⬜ | Inhaber | – | 8.4 | – |
| 8.8 | Paper läuft parallel | ⬜ | VS Code | – | 8.7 | – |
| 8.9 | Steuer vorbereiten (Anlage KAP) | ⬜ | Inhaber | – | 8.7 | – |

<a id="b9"></a>
## 9. Routine

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 9.1 | Täglich: Broker flach, Abgleich stimmt, Alarme geprüft, Tageslog | ⏳ läuft | VS Code | täglich | – | Tageslog unten |
| 9.2 | Wöchentlich: Freitag Review, am Wochenende der Lern-Labor-Bericht, höchstens eine Änderung beschließen | ⏳ läuft | VS Code + Inhaber | freitags | – | – |
| 9.3 | Monatlich: Gesamtbilanz, Vergleich mit den Tests, dann weiter, ändern oder stoppen | ⬜ | VS Code + Inhaber | Anfang November | – | – |

<a id="tageslog"></a>
## Tageslog

Neuester Tag oben.

### Do 08.10.2026

**Geschafft:**
- Fahrplan angelegt, Erfolgskriterien wörtlich übernommen (Commit 4c580ae).
- Halbtage geprüft, kein Fix nötig.
  - Der Bot rechnet das Einstiegsende und die Glattstellung mit dem Börsenschluss aus der Broker-Uhr.
  - Der Börsenkalender des Brokers führt den 27.11. und den 24.12. mit Schluss 13:00 New York.
  - Damit gilt an beiden Tagen: letzte Einstiege 18:30 (12:30 New York), Glattstellung 18:50 (12:50 New York).
- Raster „Fahrplan“ und Lern-Labor-Seite mit Knopf sind online.
- Notfallplan geschrieben, die alten Listen liegen unter docs/.
- Lern-Labor Etappe 0:
  - Lernzeit-Wächter und Abschneide-Test gebaut, beide mit Selbsttest.
  - Logbuch, Prüftopf-Logbuch und Kandidatenliste angelegt.
  - Datenplan erstellt: Lerntopf etwa 2,7 GB.
  - Telegram-Texte entworfen.
- Befund Datenplan:
  - IEX-Tageskerzen gibt es erst ab August 2020, der Tagestrend ist am Anfang des Lerntopfs deshalb eingeschränkt.
  - Die Entscheidung dazu kommt in die Vorab-Datei.
- Kopfzeile der Zusammenfassung von Runde 1 korrigiert. Dort stand „erstes Rechnen“, richtig ist die Neuberechnung
  nach dem Simulatorfehler; die Zahlen sind unverändert.

**Morgen dran (Fr 09.10.):**
- Wochenreview.
- Technik-Paket ab 22:30 (16:30 New York), sobald `setups/2026-10-09.json` auf main liegt. Mit dabei: Halbtag-Test,
  Speicherschutz für den Bot-Dienst und die Seiten-Dateien mit gleicher Prüfsumme. Danach ist live eingefroren.
- ORB Jahr 1 weiter, Downloads ab 22:00.
