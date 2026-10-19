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

Stand 19.10. Ziel dieser Woche: Das Labor findet und bewertet die ersten Trades; die erste Rangliste kommt am Sa/So 24./25.10.

**Mo 19.10.:**
- Offenes vom Wochenende: Berichte Runde 2 und ORB mit Ticks auf backtest, Änderungsprotokoll berichtigt, Fahrplan und Tageslog.
- Vorab-Datei „Lerntopf-Lauf 1“ an den Inhaber, bevor irgendetwas gerechnet wird.
- Ab 22:00 (16:00 New York): Downloads für den Lerntopf in die Warteschlange des PCs, gedrosselt.
- Abends: erster Handelstag mit dem Technik-Paket prüfen (Version bei Trades und Setups, Stop-Protokoll, skip-maxopen, Review nach Kosten).

**Di–Mi 20.–21.10.:**
- Labor-Simulator aus dem schnellen Simulator von bt/, mit Pflichttests auf künstlichen Kursen und der Gegenprobe gegen das Replay.
- Chart-Leser Teil 2 als Signalquelle für M008–M010.

**Do–Fr 22.–23.10.:**
- Läufe Jahr für Jahr, nachts auf dem PC oder im Labor-Slice auf dem Pi, mit Zwischenständen.

**Sa/So 24.–25.10.:**
- Rangliste mit Stufen, Bericht auf backtest, Telegram über den Labor-Bot.
- Die Labor-Seite zeigt die Rangliste erst nach dem OK des Inhabers zum Diff.

Wird die Zeit knapp, gilt die Reihenfolge: Vorab-Datei, Downloads, Simulator, Läufe, Rangliste. Der Prüftopf (Okt. 2023–Sep. 2026) bleibt zu.

<a id="b1"></a>
## 1. Betrieb und diese Woche

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 1.1 | Halbtage 27.11. und 24.12. (Schluss 19:00, 13:00 New York): kennt der Live-Bot sie? | ✅ 08.10. | VS Code | 08.10. | – | Kein Fix nötig, Befund im Tageslog 08.10. |
| 1.2 | Halbtag-Test: Einstiege bis 12:30, Glattstellung 12:50 New York, danach keine Order | ✅ 18.10. | VS Code | So 18.10. | mit dem Technik-Paket live | Tagestest Abschnitt 4 (27.11.) grün, auch in der Bereitstellung auf dem Pi (Bedingungsbericht 18.10.) |
| 1.3 | Technik-Paket aufspielen: Bot-Version, Änderungsprotokoll, Stop-Protokoll, skip-maxopen, Universum ohne BK/MMC/FI, Review nach Kosten, Halbtag-Test, Speicherschutz, Seiten-Dateien | ✅ 18.10. | VS Code + Inhaber | So 18.10. 17:49 | Die Termine 09.10. und 15.10. fielen aus (keine Sitzung bzw. abgebrochen) | Bedingungen grün: Exporte vom 16.10. auf main, Broker flach, Code bfe06cff, 9 von 9 Suiten und Selbsttest, Backup mit 96 Trades. Startzeile `version=2026-10-04+cbfe06cff.s5416c914 chase_anchor=close universe_exclude=BK,MMC,FI`; Änderungsprotokoll in data.json mit echter Uhrzeit (18.10. 17:48; Text am 19.10. berichtigt, als Korrektur kenntlich) |
| 1.4 | Speicherschutz für den Bot-Dienst: MemoryLow und negatives OOMScoreAdjust (Drop-in) | ✅ 18.10. | VS Code + Inhaber | So 18.10. | Technik-Paket; die Startzeilen-Anzeige kommt ins Ausgabe-Paket (4.8.11) | `systemctl show`: MemoryLow 512 MB, OOMScoreAdjust −500, Drop-in aktiv; `oom_score_adj` des Bots −500. Seit dem Neustart mit Speichersteuerung (4.0.24) wirkt auch memory.low = 512 MB |
| 1.5 | Live einfrieren: danach nur Technik- und Sicherheits-Fixes mit OK | ✅ 18.10. | Inhaber | So 18.10. | 1.3 | Eingefroren seit dem Umschalten am 18.10. um 17:49. Der Split-Fix (1.13) wartet auf einen eigenen Termin |
| 1.6 | Wochenreview | ✅ 17.10. | VS Code | Sa 17.10. | am Freitag ausgefallen (Sitzung beendet), am Samstag nachgeholt | Woche 12.–16.10.: 16 Trades, −2,43R nach Kosten, PF 0,30, −57,50 $; Vorwoche −0,85R. Tageslog 17.10. |
| 1.7 | V1-Woche 05.–09.10. im Replay nachrechnen und mit Paper vergleichen (gleiche Kriterien wie die Kalibrierung) | ✅ 18.10. | VS Code + Inhaber | Sa 17.10. | – | 19 von 19 Orders, keine zusätzliche; 722 von 723 Entscheidungen gleich; 18 von 19 Ausstiegen ≤ 0,1R. Die 2 offenen Fälle (KLAC: Split, siehe 1.13; TT t68: Verwaltungstakt) hat der Inhaber am 18.10. als erklärt angenommen: Die Kalibrierung gilt auch für V1. `kalibrierung-v1/erklaerung.md`, Protokoll [Commit d0b4ea1](../../commit/d0b4ea1a) |
| 1.8 | Notfallplan schriftlich: Strom, Internet oder API fallen aus, während Positionen offen sind | ✅ 08.10. | VS Code | 08.10. | – | [docs/notfallplan.md](docs/notfallplan.md), [Commit 7e8a063](../../commit/7e8a063135) |
| 1.9 | Bot-Version je Trade und Änderungsprotokoll | ✅ 19.10. | VS Code | Mo 19.10. | Technik-Paket | Erster Handelstag: 6 von 6 Trades und 131 von 131 Setups mit Version `2026-10-04+cbfe06cff.s5416c914`, ebenso der Setup-Export vom 19.10. auf main; Änderungsprotokoll in data.json |
| 1.10 | Kalibrierung auf dem Pi wiederholen, bevor dort gerechnet wird | ⬜ | VS Code | vor dem ersten Lauf auf dem Pi | nur falls auf dem Pi gerechnet wird; bisher rechnet der PC (dort bestanden 06.10.) | – |
| 1.11 | 1-Min-Export vom 13.10. nachholen | ✅ 16.10. | VS Code | 16.10. | Ursache: einmaliger Fehler beim Hochladen; der Bot versucht es nur einmal am Tag (Größe war nicht der Grund) | Nur die fehlende Datei, 920 KB, 67 Werte; `setups/2026-10-13.json` blieb unverändert. [Commit 9258adb](../../commit/9258adbf69) |
| 1.12 | Setup-Export: Wiederholversuch, wenn das Hochladen scheitert | ⬜ | VS Code | mit dem Ausgabe-Paket | nur Ausgabe, nur mit OK (4.8.11) | – |
| 1.13 | Befund: Der Tagestrend des Live-Bots ist nach einem Split monatelang verfälscht, weil er die Tageskerzen unbereinigt holt. Seit Okt. 2025 betraf das NFLX, NOW, BKNG und KLAC an 186 Symbol-Tagen, fast immer „down“ statt „flat“ oder „up“. Seit 13.10. ist kein Wert betroffen | ⏳ vorbereiten | VS Code + Inhaber | eigener Termin nach dem Technik-Paket | Inhaber 18.10.: Tageskerzen bereinigt wie im Replay; Test: an den 186 Tagen gilt der bereinigte Trend, sonst bleibt jede Entscheidung gleich; danach Kalibrierung 21.09.–09.10. neu (KLAC 06.10. gleich, sonst alles identisch). Nicht aufspielen ohne OK | Gefunden in der V1-Woche (1.7), `kalibrierung-v1/erklaerung.md` auf backtest |

<a id="b2"></a>
## 2. Backtest-Runden und ORB

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 2.1 | Replay kalibrieren: 659/659 Entscheidungen, 11/11 Orders | ✅ 03.10. | VS Code | 03.10. | – | Neu bestanden 06.10., [Commit 91526e9](../../commit/91526e9ce2), `kalibrierung/bericht.md` auf backtest |
| 2.2 | Runde 1 (Okt 2025–Sep 2026) | ✅ 06.10. | VS Code | 06.10. | – | 1.009 Trades, −0,056R, PF 0,76, max. DD 65R, Zufall 25/100: 1 von 5 Kriterien, Ziel nicht erreicht. [Commit 91526e9](../../commit/91526e9ce2), `runde-1/zusammenfassung.md` |
| 2.3 | Runde 2 (Okt 2024–Sep 2025), einzige Änderung: Rechtecke gestrichen. Bericht | ✅ 17.10. | VS Code | 17.10. | nur im Replay, kein Bot-Code; Kalibrierung gültig | Hauptlauf ohne Rechteck (zählt): 511 Trades, −0,083R, PF 0,66, max. DD 43R, Zufall 27/100: 1 von 5 Kriterien, Ziel nicht erreicht. Nebenrechnung wie live (zählt nicht): 1.085 Trades, −0,070R, PF 0,68, Zufall 33/100. [Commit d0b4ea1](../../commit/d0b4ea1a), `runde-2/zusammenfassung.md` |
| 2.4 | Entscheidung nach Runde 2: liegt sie bei null oder darunter, enden die Jahresrunden des jetzigen Bots, dann Fokus auf ORB und Lern-Labor | ✅ 19.10. | Inhaber | Mo 19.10. | 2.3 | Bestätigt vom Inhaber: Runde 2 −0,083R, die Jahresrunden des jetzigen Bots enden; ORB hat auch mit Ticks nicht bestanden (2.10). Fokus auf dem Labor. Der Live-Bot läuft unverändert weiter (Paper, eingefroren) als Messgerät für Setups, Fills und Technik |
| 2.5 | ORB-Studie: Regeln vorab festgelegt | ✅ 05.10. | VS Code | 05.10. | – | [Commit d48250c](../../commit/d48250c2), `orb-studie/VORAB-REGELN.md` |
| 2.6 | ORB Jahr 1 (Okt 2025–Sep 2026) nach den Vorab-Regeln. Bericht zusätzlich mit Trefferquote, längster Verlustserie, Ergebnis geteilt durch Drawdown. Dann Stopp bis zum OK | ✅ 08.10. | VS Code | 08.10. | – | 973 Trades, −0,465R, PF 0,57, Zufall 0/100: 1 von 5 Kriterien. Trefferquote 7,3 %, längste Verlustserie 46, Ergebnis/Drawdown −0,96. [Commit 98def9a](../../commit/98def9a7), `orb-jahr-1/zusammenfassung.md` auf backtest |
| 2.7 | ORB Jahr 2 (Okt 2024–Sep 2025) | ⬜ | VS Code | – | Inhaber 15.10.: vorerst kein Jahr 2 | – |
| 2.8 | Rechtecke im Live-Bot streichen | ❌ 19.10. | Inhaber | Mo 19.10. | – | Verworfen vom Inhaber: In Runde 2 hilft das Streichen nicht (ohne Rechteck −0,083R, mit −0,070R). Live bleibt unverändert |
| 2.9 | Replay-Seite (claude.ai) nach jeder Runde aktualisieren | ✅ bis 07.10. | Chat | nach jeder Runde | – | Runde 1 mit echten Zahlen |
| 2.10 | ORB Jahr 1 mit Ticks für die Einstiegsminute neu rechnen. 594 von 973 Trades wurden schon in ihrer Einstiegsminute gestoppt (Vorab-Regel 7, vorsichtig). Tick-Methode vorher festgelegt, Zufallsläufe ebenfalls auf Ticks, Handelsregeln unverändert, kein Jahr 2 | ✅ 18.10. | VS Code | 18.10. | Freigabe des Inhabers 09.10./15.10. | 973 Trades, −0,404R, PF 0,69, Zufall 0/100: 1 von 5 Kriterien, Ziel nicht erreicht. In der Einstiegsminute gestoppt: 425 statt 594. [Commit d0b4ea1](../../commit/d0b4ea1a), `orb-jahr-1-ticks/zusammenfassung.md` |

<a id="b3"></a>
## 3. Offene Punkte aus den alten Listen

Nummern in Klammern = Nummer in [Fehler und Verbesserungen](docs/fehler-und-verbesserungen.md).

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 3.1 | (#1) Einstieg erst Minuten nach Kerzenschluss | ✅ 28.09. | VS Code | 28.09. | – | Order 32–38 s nach Kerzenschluss |
| 3.2 | (#2) Blinde Fenster bei 5 offenen Positionen | ⏳ live | VS Code | seit So 18.10. | Technik-Paket (skip-maxopen) | Live seit 18.10.; am 19.10. ohne Anlass (höchstens 3 Positionen gleichzeitig offen). Abgehakt beim ersten Tag mit 5 offenen |
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
| 4.0.3 | Labor-Ordner außerhalb des Home-Bereichs, eigener Linux-Nutzer ohne Zugriff auf den Bot | ✅ 18.10. | VS Code + Inhaber | So 18.10. | Obergrenze 12 GB (OK 08.10.) | Labor-Nutzer ohne Anmeldung; Labor-Ordner als eigenes Dateisystem mit 12 GB, nach dem Neustart wieder eingehängt. Logbuch 18.10. |
| 4.0.4 | Eigene systemd-Slice: MemoryMax 40 %, MemorySwapMax=0, CPUWeight=10, CPUQuota=200 %, IOWeight=10, Nice=19, IOSchedulingClass=idle, OOMScoreAdjust=1000 | ✅ 18.10. | VS Code + Inhaber | So 18.10. | 4.0.3 | Labor-Scheibe mit diesen Grenzen; Nice, IO und OOMScoreAdjust gelten für jeden Labor-Dienst. MemoryMax = 1.518 MB (40 %). Logbuch 18.10. |
| 4.0.5 | Bot-Schutz: MemoryLow und negatives OOMScoreAdjust | ✅ 18.10. | VS Code + Inhaber | So 18.10. | Technik-Paket, siehe 1.4 | OOMScoreAdjust −500, memory.low 512 MB wirksam |
| 4.0.6 | Zugriff: InaccessiblePaths für Bot-Verzeichnis und Schlüssel, ProtectHome, ProtectSystem=strict, ReadWritePaths nur Labor-Ordner, NoNewPrivileges, PrivateTmp | ✅ 18.10. | VS Code + Inhaber | So 18.10. | 4.0.3 | Bot-Verzeichnis und Schlüssel liegen im Home-Bereich und sind über ProtectHome unsichtbar (statt einzelner InaccessiblePaths); dazu ProtectSystem=strict, schreiben nur im Labor-Ordner, PrivateTmp, NoNewPrivileges, fremde Prozesse unsichtbar, keine Capabilities. Sicherheitsbewertung von systemd 2,9 (OK) |
| 4.0.7 | Zugriffstest: als Labor-Nutzer Bot-Verzeichnis und Schlüssel lesen, muss scheitern; Ergebnis ins Logbuch | ✅ 18.10. | VS Code | So 18.10. | 4.0.6 | Bestanden: 9 von 9 verbotenen Zugriffen scheitern, 5 von 5 erlaubten gehen; auch ohne Sperren ist die Schlüsseldatei des Bots nicht lesbar. Vor und nach dem Neustart gleich. Logbuch 18.10. |
| 4.0.8 | Timer in New-York-Zeit: Start 16:30, harter Stopp 09:00 mit Alarm; den Börsenkalender prüft der Job selbst; bei jedem Deploy pausiert alles | ⬜ | VS Code | ab So 18.10. | 4.0.2 | – |
| 4.0.9 | Immer nur ein schwerer Job. Vorrang: Live-Bot, Runde 2, ORB, Lern-Labor | ⬜ | VS Code | ab So 18.10. | – | – |
| 4.0.10 | Zwischenstände, damit ein gestoppter Job weitermachen kann | ⬜ | VS Code | ab So 18.10. | – | Replay kann es schon |
| 4.0.11 | Speicherwächter: Stopp unter 5 GB frei auf dem System, zusätzlich zur festen Obergrenze von 12 GB für den Labor-Ordner; Alarm per Telegram | ⬜ | VS Code | ab So 18.10. | 4.0.3, 6.1 | – |
| 4.0.12 | Harte Sperre wie im Replay: nur Marktdaten, kein Trading. Eigene Sperrliste mit SEC-EDGAR (höchstens 10 Abrufe/s, Kontakt im User-Agent nur aus der .env, nie im Repo) | ⏳ teils | VS Code | – | – | Datencode des Labors: nur der Marktdaten-Host erlaubt, Handels-API und GitHub gesperrt (geprüft 17.10.). Die SEC-EDGAR-Sperrliste fehlt noch |
| 4.0.13 | Eigene Alpaca-Schlüssel (z. B. zweites Paper-Konto) in eigener .env im Labor-Ordner. Nie die Schlüssel des Bots: eigenes Abruflimit, keine Leserechte auf dessen .env. Ohne eigene Schlüssel holt das Labor auf dem Pi keine Daten | ✅ 18.10. | Inhaber | So 18.10. | – | Schlüssel des zweiten Paper-Kontos in der .env des Labors, vom Inhaber selbst eingetragen; vorerst nur für Daten, die Handelssperre bleibt (Inhaber 17.10.). Logbuch 18.10. |
| 4.0.14 | Eigener GitHub-Token mit minimalen Rechten, nur für Ergebnisse: fein abgestuft, nur dieses Repo, nur Contents lesen und schreiben, mit Ablaufdatum. Weil der Token technisch auch auf main schreiben kann: harte Sperre im Code, nur der Branch backtest (Inhaber 17.10.) | ✅ 18.10. | Inhaber + VS Code | So 18.10. | – | Token in der .env des Labors. `lern_labor/push_backtest.py`: nur ein Commit auf refs/heads/backtest, kein main, kein Contents-API, kein Force-Push; 20 Prüfungen grün (17.10.) |
| 4.0.15 | Downloads nur außerhalb der Handelszeit und gedrosselt | ⬜ | VS Code | ab So 18.10. | – | Replay-Sperre als Vorlage |
| 4.0.16 | Datenplan mit Größe je Teil | ✅ 08.10. | VS Code | 08.10. | – | `lern-labor/datenplan.md` auf backtest |
| 4.0.17 | Daten 2020–2023 laden: IEX 15 Min und Tageskerzen, IEX-Kurse und -Quotes für die Filter, SIP 1 Min; 150 Werte und SPY | ⏳ läuft seit 19.10. 22:30 | VS Code | ab Mo 19.10. 22:30 | 4.0.16; auf dem PC, gedrosselt auf 100 Abrufe je Minute, nur außerhalb 15:30–22:00 | Lerntopf-Lauf 1 ohne Quotes, die Kosten laufen über das Kostenmodell (Inhaber 19.10.). Auftrag `lerntopf-daten` in der Warteschlange des PCs, verweigert jeden Abruf ab 01.10.2023 |
| 4.0.18 | Situation zur Form point-in-time: Kurslücke, relatives Volumen, Quartalszahlen, Nachrichten. Quellen klären, nichts Kostenpflichtiges ohne OK | ⬜ | VS Code | ab Mo 12.10. | – | – |
| 4.0.19 | Universum zum Stichtag inklusive gestrichener Werte (Überlebensverzerrung). Quelle klären | ⬜ | VS Code | ab Mo 12.10. | – | – |
| 4.0.20 | Jeder Trade wird bewertet wie der Bot handelt: Stop, Ziel, Zeitstopp, Tagesende. Kosten wie unter Erfolgskriterien | ⬜ | VS Code | ab Mo 12.10. | schneller Simulator | – |
| 4.0.21 | Nächtliche Schattenbilanz (Grundgerüst) | ⬜ | VS Code | – | 4.0.8 | – |
| 4.0.22 | Logbuch und Prüftopf-Logbuch | ✅ 08.10. | VS Code | 08.10. | – | `lern-labor/logbuch.md`, `lern-labor/prueftopf-logbuch.md` auf backtest |
| 4.0.23 | Abschneide-Test als feste Funktion: jedes Merkmal mit allen Daten und mit Daten nur bis zum Signal, beides muss gleich sein | ✅ 08.10. | VS Code | 08.10. | – | Selbsttest: 4 eingebaute Datenlecks erkannt (Logbuch 08.10.) |
| 4.0.24 | Speicher-Controller im Kernel des Pi einschalten. Der Pi startet mit abgeschalteter Speichersteuerung; ohne sie wirken MemoryMax (Labor) und MemoryLow (Bot) nicht, OOMScoreAdjust und die CPU-Grenzen schon | ✅ 18.10. | Inhaber + VS Code | So 18.10. 19:13 | Startdatei vorher gesichert, Zeile vorher und nachher gezeigt, nur cgroup_enable=memory angehängt; Neustart bei flachem Broker | Kernel meldet die Speichersteuerung; der Bot läuft wieder mit memory.low 512 MB; MemoryMax im Labor greift (4.0.25). Logbuch 18.10. |
| 4.0.25 | Schwere Labor-Jobs auf dem Pi erst, wenn MemoryMax nachweislich wirkt (Test im Labor-Slice) | ✅ 18.10. | VS Code | So 18.10. | 4.0.24 | Speichertest: Grenze 200 MB, der Test will 400 MB, bei 200 MB vom Kernel beendet (oom-kill); der Bot lief weiter |
| 4.0.26 | Tagestrend 2020: SIP- gegen IEX-Tageskerzen messen. Unter 1 % abweichend: SIP-Vorlauf, der Suchtopf bleibt ab Okt 2020; sonst Okt 2020 bis Jan 2021 nur zum Aufwärmen | ✅ 08.10. | VS Code | 08.10. | – | 459 von 100.107 Entscheidungen abweichend (0,46 %): SIP-Vorlauf. `lern-labor/messungen/trend_sip_iex.md` auf backtest, Logbuch 08.10. |
| 4.0.27 | .env-Vorlage des Labors: leere Zeilen, Rechte 600, gehört dem Labor-Nutzer | ✅ 18.10. | VS Code + Inhaber | So 18.10. | 4.0.3 | Angelegt mit Rechten 600, gehört nur dem Labor-Nutzer; 8 von 9 Feldern gefüllt, der SEC-Kontakt folgt |

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
| 4.1.9 | „Bester zuerst“ statt „wer zuerst kommt“, wenn alle 5 Plätze belegt sind: im Lerntopf testen, nicht in Runde 2 | ⬜ | VS Code | – | Etappe 1 | – |

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
| 4.2.8 | Start von Etappe 2 direkt nach der ersten Rangliste, mit denselben Daten und demselben Simulator wie Lerntopf-Lauf 1 (Inhaber 19.10.) | ⬜ | VS Code | nach der ersten Rangliste (24./25.10.) | 4.8.13 | – |
| 4.2.9 | Formen-Gruppen aus normierten Ausschnitten, gesucht nur im Lerntopf. Eine Gruppe zählt nur, wenn sie bei vielen Aktien und in jedem Jahr wiederkehrt | ⬜ | VS Code | nach 4.2.8 | 4.2.1, 4.2.2 | – |
| 4.2.10 | Zufallslatte nach der Zahl der getesteten Gruppen („Bester von N“) | ⬜ | VS Code | nach 4.2.8 | 4.2.9 | – |
| 4.2.11 | Je Gruppe ein Bild der typischen Form mit Beispielen für den Inhaber | ⬜ | VS Code | nach 4.2.8 | 4.2.9 | – |
| 4.2.12 | Fallende Gruppen werden mit ausgewertet: als Short-Kandidat oder als „Finger weg“-Filter für andere Muster | ⬜ | VS Code | nach 4.2.8 | 4.2.9 | – |

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

### Chart-Leser, Steckbriefe, Bilder, Rangliste (Auftrag vom 15.10.)

Ziel: Der Bot liest Charts wie ein erfahrener Trader. Er zeichnet die Linien eines Musters selbst, prüft sie auf
Fehler, bewertet das Muster und zeigt bei jedem Signal das Bild, so wie er es sieht.

Spielregeln:
- Jeder Steckbrief ist eine feste Regel. Eine Änderung ergibt ein neues Muster mit neuer Nummer.
- Neue Ideen schickt der Inhaber als Bild oder Idee an Claude im Chat. Daraus wird ein Steckbrief in
  `lern-labor/kandidaten.md`. Getestet wird einmal pro Woche als Paket.
- Die Zeitebene gibt das Muster vor. Muster auf Tageskerzen werden über mehrere Tage gehalten, auch über Nacht. Sie
  laufen nur in Simulation und Schatten, ins Paper nur mit OK des Inhabers.
- Regeln werden nie nach Ergebnissen geändert.

Die 7 heutigen Muster des Bots sind:
1. Aufsteigendes Dreieck
2. Absteigendes Dreieck
3. Rechteck
4. Doppeltop
5. Doppelboden
6. Schulter-Kopf-Schulter
7. Inverse Schulter-Kopf-Schulter

| Nr | Punkt | Status | Wer | Datum | Abhängigkeit | Beleg |
|---|---|---|---|---|---|---|
| 4.8.1 | Chart-Leser v1 im Lern-Labor, getrennt vom Bot: Wendepunkte in drei Größen (1, 2, 4 ATR) und auf drei Zoomstufen (50, 100, 200 Kerzen); waagerechte Zonen, Trend- und Nackenlinien durch die Dochte; Berührungen mit Toleranz und Passgüte | ✅ 16.10. | VS Code | 16.10. | – | Teil 1 (Signalprüfung) Festlegung v1 vor dem ersten Lauf ([Commit fb824c2](../../commit/fb824c21)); Teil 2 (Lesen ohne Bot) Festlegung v1.1 ([Commit 778f395](../../commit/778f395e)), `lern-labor/chartleser/CHARTLESER.md` auf backtest |
| 4.8.2 | Selbstkontrolle vor jeder Bewertung: Mindestberührungen laut Steckbrief; Ziel und Stop nur aus geprüften Linien; Signalkerze mit großer Kurslücke und tiefem Durchfall senkt die Bewertung | ✅ 16.10. | VS Code | 16.10. | 4.8.1 | Ziel und Stop nur aus geprüften Linien, Prüfung der Signalkerze, Mindestberührungen je Muster festgelegt in `CHARTLESER.md` v1.1 ([Commit 778f395](../../commit/778f395e)); die Steckbriefe übernehmen sie |
| 4.8.3 | Ausreißer-Docht: SIP entscheidet. Bestätigt SIP den Kurs, bleibt er Ankerpunkt. Verworfen wird er nur, wenn SIP ihn nicht bestätigt, oder ohne SIP-Kerze (jünger als 15 Min), wenn er länger als das Dreifache der mittleren Spanne ist. Eröffnungskerzen werden an den Eröffnungskerzen der letzten 20 Tage gemessen. Die 3×-Regel stammt aus Live-Trade t70 | ✅ 15.10. | VS Code | 15.10. | 4.8.1 | Festgelegt in `CHARTLESER.md` Teil 1, [Commit fb824c2](../../commit/fb824c21); Pflichttest grün und Herkunft der 3×-Regel im `lern-labor/logbuch.md` |
| 4.8.4 | Ausgabe je Signal als JSON: Wendepunkte, Linien mit Anfang, Ende und Preis, Fenster, Zoom, Berührungen, Prüfergebnisse, verworfene Punkte mit Grund, Bewertung | ✅ 16.10. | VS Code | 16.10. | 4.8.1 | Teil 1 und Teil 2 schreiben je Signal Linien mit Anfang, Ende und Preis, Fenster, Zoom, Berührungen, Prüfungen, verworfene Punkte und Bewertung; erstes Beispiel t70 ([Commit 7172713](../../commit/7172713f)) |
| 4.8.5 | Pflichttests: Abschneide-Test; künstlicher Keil, Rechteck und Doppelboden werden erkannt, Rauschen nicht; ein eingebauter Ausreißer-Docht wird verworfen | ✅ 16.10. | VS Code | 16.10. | 4.8.1 | Abschneide-Test und Ausreißer-Test grün (15.10., `lern-labor/logbuch.md`). Künstlicher Keil steigend 48/50, fallend 50/50, Doppelboden 45/50, Rechteck 50/50 erkannt; Rauschen: Zufallspfade 15/300, stationär 9/300 (Grenze 15). Festgelegt in `CHARTLESER.md` v1.1, [Commit 778f395](../../commit/778f395e) |
| 4.8.6 | Steckbrief-Vorlage `lern-labor/steckbriefe/VORLAGE.md` | ✅ 15.10. | VS Code | 15.10. | – | [Commit fb824c2](../../commit/fb824c21), `lern-labor/steckbriefe/VORLAGE.md` auf backtest |
| 4.8.7 | Steckbriefe der 7 heutigen Muster, genau wie der Code sie erkennt | ✅ 15.10. | VS Code | 15.10. | 4.8.6 | M001–M007 auf Stufe 0, [Commit fb824c2](../../commit/fb824c21), `lern-labor/steckbriefe/` auf backtest |
| 4.8.8 | Neue Steckbriefe: Keil steigend und fallend (nur nach klarem Trend); Doppelboden mit Kaufkraft (Volumen am ersten gegen das am zweiten Tief, Dochte, Stärke des Abpralls) | ✅ 16.10. | VS Code + Chat | 16.10. | 4.8.6 | M008 Keil steigend, M009 Keil fallend, M010 Doppelboden mit Kaufkraft auf Stufe 0, Regeln fest vor jedem Ergebnis: [Commit d100a85](../../commit/d100a85b), `lern-labor/steckbriefe/` |
| 4.8.9 | Bild-Renderer im Stil der Vorlage `musterbild-t70.html`: Kerzen, Linien mit Berührungen, verworfene Punkte sichtbar, Einstieg, Stop, Ziel, Ausstieg, Volumen, Infofeld beim Überfahren; hell und dunkel, auch am Handy | ✅ 16.10. | VS Code | 16.10. | – | Erstes Bild t70, hell und dunkel, Handy und Desktop geprüft: [Commit 7172713](../../commit/7172713f), `lern-labor/bilder/` auf backtest |
| 4.8.10 | Rekonstruierte Bilder für alle bisherigen Live-Trades, deutlich als „rekonstruiert“ markiert, mit der Tabelle „exakt / zurückgerechnet / angenommen“ | ✅ 16.10. | VS Code | 16.10. | 4.8.9 | Alle 94 Live-Trades (t1–t96 ohne die 2 stornierten), Kante, Stop und Ziel bei allen 94 exakt nachgebaut, mit SIP geprüft: 0 Ankerpunkte verworfen, 3 Abzüge für die Signalkerze (t17, t70, t92). [Commit 923c3a4](../../commit/923c3a41), `lern-labor/bilder/live/` |
| 4.8.11 | Ausgabe-Paket für den Live-Bot: Geometrie des Detektors beim Signal speichern (Wendepunkte, Kante, Gegenkante, Fenster, Berührungen); dazu Startzeilen-Anzeige Speicherschutz und Export-Wiederholversuch. Nur Ausgabe, Test: alle Entscheidungen von entry_scan unverändert | ⬜ | VS Code + Inhaber | nach dem Technik-Paket | nur mit OK, nach den Deploy-Regeln | – |
| 4.8.12 | Diagnose des Chart-Lesers auf Runde 1, nur Geometrie (das Jahr gehört zum Prüftopf): Wie viele Linien hängen an Ausreißern, wie würden sich Kante, Ziel und Stop ändern? Kein Vorher/Nachher in R, keine Auswahl nach Ergebnis. Bilder für 40 zufällig gezogene Trades (fester Seed). Dazu (Inhaber 17.10.): wie oft das Ziel erreicht wird und wie die Trades enden | ✅ 17.10. | VS Code | Sa 17.10. | 4.8.1–4.8.5 | Mit SIP: 1.009 von 1.009 Signalen exakt nachgebaut; 6.639 Ankerpunkte geprüft, 1 verworfen (WMT, 2 Cent), dadurch keine Kante, kein Stop und kein Ziel geändert. Ausgänge: Ziel 38 (3,8 %), Zeit-Stop 616, Tagesende 250, Stop 105 (davon 31 auf dem Einstieg). 40 Bilder. [Commit e77d2ca](../../commit/e77d2cad), `lern-labor/diagnose-runde-1/` auf backtest |
| 4.8.13 | Lerntopf (Okt. 2020–Sep. 2023): alle Steckbriefe, jedes Jahr einzeln, mit Selbstkontrolle, Zufallslatte und Kostenstress. Daraus entsteht die erste Rangliste. Vorher/Nachher in R gibt es nur hier | ⏳ Vorab-Datei | VS Code | erste Rangliste Sa/So 24./25.10. | 4.0.17, 4.8.22–4.8.24 | – |
| 4.8.14 | Stufen: 0 Idee (Steckbrief liegt vor); 1 Lerntopf bestanden (jedes Lernjahr positiv, über der Zufallslatte, hält dem Kostenstress stand); 2 Prüfung bestanden (bei einer der 3 Öffnungen); 3 Schatten bestanden (200 Trades, 3 Monate, alle 5 Kriterien); 4 Paper, nur mit OK | ⬜ | VS Code | mit 4.8.13 | – | – |
| 4.8.15 | Wochenroutine: neue Steckbriefe als Paket im Lerntopf; alle Muster bekommen die neue Handelswoche im Schatten; Rangliste und Bericht auf GitHub, per Telegram und auf der Webseite | ⬜ | VS Code | jedes Wochenende | 4.8.13, 6.1 | – |
| 4.8.16 | Prüfung der Eröffnungskerzen (nur lesen): a) AMD 05.10./06.10. gegen SIP; b) alle 147 Werte seit 21.09.: IEX außerhalb der SIP-Spanne; c) Setups seit 28.09. mit einer Linie an so einem Ausreißer, mit der Wirkung auf Ziel und Stop | ✅ 16.10. | VS Code | 16.10. | Downloads außerhalb 15:30–22:00 | Keine Ausreißer: an 2.788 Symbol-Tagen lag IEX nie außerhalb der SIP-Spanne; 0 von 1.912 Setups mit einer Linie an einem Ausreißer. AMD 05.10.: 620,05 ist echt (SIP-Tief 619,99). [Commit 7172713](../../commit/7172713f), `lern-labor/messungen/eroeffnungskerzen.md` |
| 4.8.17 | Später: Bewertung, die mit dem Muster wächst, Einstieg erst am Auslöser. Die Gewichte lernt Etappe 1. Nachweis: Setups in 5 Gruppen nach Bewertung, die beste klar besser als die schlechteste, die Gruppen steigen sauber an | ⬜ | VS Code | später | Etappe 1 | – |
| 4.8.18 | Später: Recherche-Bot, liest Bücher und Webseiten und schreibt Steckbriefe mit Quelle und Einschätzung der Belastbarkeit; abgeschottet, ohne Zugriff auf Bot oder Schlüssel; höchstens 5 Muster pro Woche; der Inhaber gibt frei, was getestet wird | ⬜ | VS Code | später | – | – |
| 4.8.19 | Später: Bild-Netz (Etappe 3) | ⬜ | VS Code | später | Etappe 3 | – |
| 4.8.20 | 3×-Regel prüfen: Ihre Begründung (t70) ist weggefallen, der Docht dort war echt. Im Lerntopf zählen, wie oft sie einen von SIP bestätigten Docht verworfen hätte und wie oft einen nicht bestätigten; danach Entscheidung über Chart-Leser v1.2 | ⬜ | VS Code + Inhaber | mit dem Lerntopf | 4.8.13 | Logbuch 17.10. |
| 4.8.21 | Erste Lerntopf-Frage: Ziel-Abstand und Haltedauer passend zur Zeitebene. Befund aus Runde 1: 86 % der Trades enden durch Zeit-Stop (61 %) oder Tagesende (25 %), nur 3,8 % erreichen das Ziel, die Ziele liegen im Median 1,49R entfernt. Varianten nur als neue Steckbriefe mit eigener Nummer, vorab festgelegt; live bleibt unverändert | ⬜ | VS Code + Inhaber | mit dem Lerntopf | 4.8.13 | Diagnose Runde 1 (17.10.) |
| 4.8.22 | Vorab-Datei „Lerntopf-Lauf 1“: Daten Okt. 2020–Sep. 2023, Muster M001–M010 mit je 4 Varianten zu Ziel und Haltedauer (H0 wie live, H1 ohne Zeit-Stop, H2 halbe Musterhöhe als Ziel, H3 bis 3 Handelstage über Nacht), 40 Kandidaten, Zufallslatte „Bester von 40“, Kostenstress +0,03R. Festlegen mit Commit und SHA-256 im Logbuch, vor jedem Lauf auf echten Daten | ⏳ Entwurf zur Prüfung | VS Code + Chat + Inhaber | Mo 19.10. | 4.8.21 | Entwurf mit den Entscheidungen des Inhabers vom 19.10. (Latte über alle 3 Jahre, mindestens 30 Trades je Jahr, H3-Ende 29.09.2023), `lern-labor/vorab/lerntopf-lauf-1-ENTWURF.md` auf backtest; Prüfung durch Claude im Chat, dann Festlegung |
| 4.8.23 | Labor-Simulator aus dem schnellen Simulator von bt/ abgeleitet. Pflichttests: Abschneide-Test; künstliche Kurse mit bekanntem Ergebnis (Ziel, Stop, Zeit-Stop, Tagesende, über Nacht mit Lücke); Gegenprobe M003-H0 und M001-H0 auf einem Lerntopf-Jahr gegen das Replay | ⏳ gebaut | VS Code | Mo 19.10. | 4.8.22 | Pflichttests auf künstlichen Kursen grün: H0 gleich dem Simulator des Replays auf 400 Zufallsverläufen, dazu Ziel, Stop, Lücke, Break-even, Trailing, Zeit-Stop, Tagesende, Halbtag, H3 über Nacht. Lauf und Gegenprobe gesperrt, bis die Vorab-Datei festgelegt ist; die Gegenprobe läuft danach auf J3 |
| 4.8.24 | Chart-Leser Teil 2 als Signalquelle für M008–M010 | ⏳ gebaut | VS Code | Mo 19.10. | 4.8.23 | Chart-Leser v1.1 unverändert (Hash c5ca9efa1343 nachgerechnet); Vortrend und Kaufkraft prüft die Signalquelle nach dem Wortlaut der Steckbriefe; Abschneide-Test grün auf künstlichen Keilen und einem Doppelboden mit und ohne Kaufkraft |
| 4.8.25 | Einreichung neuer Muster: Der Inhaber schickt Bild und Erklärung an Claude im Chat. Daraus wird ein Steckbrief mit Nummer, der in `kandidaten.md` kommt; getestet wird am Wochenende im Paket (4.8.15) | ⬜ | Inhaber + Chat + VS Code | ab der ersten Rangliste (Sa/So 24./25.10.) | 4.8.13 | – |

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
| 6.1 | Eigener Telegram-Bot oder Kanal fürs Lern-Labor, getrennt vom Handels-Bot. Zugang nur in die .env des Labors, nie in den Chat | ✅ 18.10. | Inhaber | So 18.10. | – | Token und Chat-ID in der .env des Labors, vom Inhaber selbst eingetragen |
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
| 7.5 | Seiten-Dateien mit gleicher Prüfsumme ins Technik-Paket, damit ein späteres Hochladen der Dashboard-Seite nichts überschreibt | ✅ 18.10. | VS Code | So 18.10. | 1.3 | Prüfsummen von index.html, labor.html und labor-name.js gleich main (Bedingungsbericht 18.10.) |
| 7.6 | Lern-Labor-Seite, neue Bereiche: Rangliste aller Muster mit Stufe und Kennzahlen; Galerie der Musterbilder mit Großansicht; Steckbriefe mit Beispielbild; Beobachtungsliste „Muster im Aufbau“ (vorerst Leerzustand, gefüllt erst, wenn die Bewertung nachweislich sortiert) | ⏳ gebaut, Diff gezeigt | VS Code + Inhaber | 16.10. | 4.8.9; Diff vor dem Push gezeigt (16.10.), Upload nach OK | Rangliste (10 Steckbriefe, Kennzahlen nach dem Lerntopf), Galerie mit 94 Bildern und Großansicht, Steckbriefe mit Beispielbild, „Muster im Aufbau“ leer; hell, dunkel, Handy geprüft |
| 7.7 | Dashboard: in der Trade-Detailansicht das Musterbild mit den Linien des Bots, als „rekonstruiert“ markiert, bis das Ausgabe-Paket live ist. Das Fahrplan-Raster bleibt, wie es ist | ⏳ gebaut, Diff gezeigt | VS Code + Inhaber | 16.10. | 4.8.10; Diff vor dem Push gezeigt (16.10.), Upload nach OK; Seiten-Dateien ins nächste Paket | Musterbild im Trade-Detail nur, wenn eines da ist; Raster unverändert |

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

### Mo 19.10.2026

**Geschafft:**
- Berichte von Runde 2 (Haupt- und Nebenrechnung) und ORB mit Ticks auf backtest.
  - 2.4 bestätigt: Die Jahresrunden des jetzigen Bots enden, der Fokus liegt auf dem Labor. Der Live-Bot läuft als
    Messgerät weiter.
  - 2.8 verworfen: Rechtecke live zu streichen hilft nicht.
- Änderungsprotokoll berichtigt („So 18.10.“ statt „Do 15.10.“), als Korrektur kenntlich.
- Vorab-Datei „Lerntopf-Lauf 1“ als Entwurf auf backtest, mit den Entscheidungen des Inhabers.
  - Zufallslatte „Bester von 40“ über alle 3 Jahre; mindestens 30 Trades je Jahr, sonst „zu wenig Daten“.
  - H3 endet spätestens am 29.09.2023.
  - Die Steckbriefe M001–M010 sind um den Trailing-Stop ergänzt, als Korrektur der Beschreibung.
- Labor-Simulator, Signalquelle M001–M010, Auswertung, Lauf-Gerüst mit harter Sperre und Gegenprobe gebaut.
  - Geprüft nur auf künstlichen Kursen: 8 Suiten, 166 Prüfungen grün.
  - Auf echten Daten läuft nichts, bis die Vorab-Datei festgelegt ist.
- Erster Handelstag mit dem Technik-Paket:
  - 6 Trades und 131 Setups, alle mit Bot-Version; Export mit Version.
  - Review nach Kosten: −1,47R; Broker flach.
  - Stop-Protokoll und skip-maxopen hatten heute keinen Anlass.
- Ergänzt: Einreichung neuer Muster ab der ersten Rangliste (4.8.25); Etappe 2 startet danach (4.2.8–4.2.12).
- Downloads für den Lerntopf: läuft seit 19.10. 22:30.

**Morgen dran (Di 20.10.):**
- Fortschritt der Downloads melden.
- Prüfung des Entwurfs durch Claude im Chat, dann Festlegung mit Commit und SHA-256 im Logbuch.
- Danach: Abschneide-Stichprobe auf echten Daten und die Gegenprobe auf J3, nach dem Hauptdownload.

### So 18.10.2026

**Geschafft:**
- Technik-Paket umgeschaltet um 17:49 (Börse zu), nach einem grünen Probelauf aller Bedingungen.
  - Startzeile mit `version=2026-10-04+cbfe06cff` und `chase_anchor=close`.
  - Speicherschutz aktiv: OOMScoreAdjust −500, Drop-in geladen.
  - Änderungsprotokoll in data.json mit der echten Uhrzeit.
  - Danach eine Stunde Ruhe: Herzschlag alle 10 Minuten, 0 Neustarts, 0 Fehler.
- Etappe 0 auf dem Pi mit dem Inhaber:
  - Labor-Nutzer und Labor-Ordner (12 GB); .env mit Rechten 600, Zugänge vom Inhaber selbst eingetragen.
  - Labor-Scheibe mit festen Grenzen und Sperren für jeden Labor-Dienst.
  - Zugriffstest bestanden: Das Labor kann Bot, Schlüssel und Datenbank nicht lesen.
  - Speichersteuerung im Kernel eingeschaltet; Startdatei vorher gesichert, Zeile vorher und nachher gezeigt.
  - Neustart um 19:13 bei flachem Broker. Danach: Bot läuft, memory.low 512 MB wirksam, der Speichertest im Labor wird bei
    200 MB vom Kernel beendet.
- ORB Jahr 1 mit Ticks fertig: −0,404R, PF 0,69, Zufall 0/100, 1 von 5 Kriterien.
- V1-Woche: Der Inhaber nimmt beide Abweichungen als erklärt an, die Kalibrierung gilt auch für V1.

**Morgen dran (Mo 19.10.):**
- Berichte Runde 2 und ORB mit Ticks auf backtest; Änderungsprotokoll berichtigen; Fahrplan hochladen.
- Vorab-Datei „Lerntopf-Lauf 1“; ab 22:00 Downloads für den Lerntopf.
- Erster Handelstag mit dem Technik-Paket.

### Sa 17.10.2026

**Geschafft:**
- Wochenreview 12.–16.10. nachgeholt: 16 Trades, −2,43R nach Kosten, PF 0,30, −57,50 $ (Vorwoche −0,85R).
- Steckbriefe M001–M007: Kennung des Bot-Codes auf cbfe06cff berichtigt.
- Logbuch: Befund t70 (der Docht war echt) und die 3×-Regel ohne Begründung; Prüfung im Lerntopf (4.8.20).
- Diagnose des Chart-Lesers auf Runde 1, nur Geometrie:
  - 1 von 6.639 Ankerpunkten verworfen, keine Linie geändert.
  - 3,8 % der Trades erreichen das Ziel, 86 % enden durch Zeit-Stop oder Tagesende.
  - Daraus wird die erste Lerntopf-Frage (4.8.21).
- V1-Woche 05.–09.10. im Replay:
  - 19 von 19 Orders; zwei Abweichungen erklärt.
  - Dabei gefunden: Der Tagestrend des Live-Bots ist nach Splits verfälscht (1.13).
- Upload-Sperre fürs Labor gebaut: nur der Branch backtest, 20 Prüfungen grün.
- Runde 2 fertig: −0,083R, PF 0,66, Zufall 27/100, 1 von 5 Kriterien. Mit Rechteck −0,070R.

**Morgen dran (So 18.10.):**
- Technik-Paket umschalten, dann eine Stunde Ruhe, dann Etappe 0.

### Fr 16.10.2026

**Geschafft:**
- Export vom 13.10. nachgeholt: nur die fehlende 1-Min-Datei (920 KB, 67 Werte), Commit 9258adb.
- Prüfung der Eröffnungskerzen: keine Ausreißer.
  - An 2.788 Symbol-Tagen lag IEX nie außerhalb der SIP-Spanne; 0 von 1.912 Setups hängen an einem Ausreißer.
  - AMD 05.10.: Das Tief 620,05 ist echt, SIP handelte bis 619,99 (524.112 Stück in der ersten Minute).
- Chart-Leser Teil 1 auf t70, Festlegung v1 unverändert: alle 10 Ankerpunkte von SIP bestätigt, die Unterkante 620,05
  bleibt. Abzug nur für die Signalkerze (Lücke 7,0 ATR, Durchfall 4,1 ATR). Die erwartete Unterkante 627,36 trifft
  nicht zu, weil SIP den Kurs bestätigt.
- Erstes Musterbild t70, hell und dunkel, Handy und Desktop (Commit 7172713).
- Befund am Pi: Er läuft seit dem 22.09. über WLAN, nicht über das Kabel, und hat seit heute eine neue Adresse.

**Morgen dran (heute Abend und Sa 17.10.):**
- Technik-Paket ab 22:30 (16:30 New York): erst der Bedingungsbericht, dann schaltet der Inhaber um.
- Wochenreview nach Handelsschluss.
- Chart-Leser Teil 2 als Fassung v1.1 festlegen; ORB mit Ticks umsetzen und laden.
- Etappe 0 mit dem Inhaber; Diagnose des Chart-Lesers auf Runde 1 (nur Geometrie, 40 Bilder).

### Do 15.10.2026

**Geschafft:**
- Auftrag „Der Bot lernt, Charts zu lesen“ in den Fahrplan übernommen (4.8.1–4.8.19, Zeitplan).
- Chart-Leser Teil 1 (Signalprüfung) mit Pflichttests, Festlegung v1 mit Hash vor dem ersten Lauf (Commit fb824c2).
- Teil 2 (Lesen ohne Bot) gebaut, Pflichttests grün.
- Steckbrief-Vorlage und die Steckbriefe der 7 heutigen Muster (Commit fb824c2).
- Runde 2 und die ORB-Tick-Methode vorab festgelegt (Commit 21f93ab).
- Technik-Paket vorbereitet: Bereitstellung auf dem Pi mit dem kalibrierten Code cbfe06cff, Bedingungsskript mit
  Rückweg.
- Abends lief die Sitzung nicht weiter: Export-Nachtrag, Eröffnungskerzen und Bedingungsbericht fielen aus, nichts
  wurde umgeschaltet.

**Morgen dran (Fr 16.10.):**
- Export 13.10., Eröffnungskerzen und t70 vor 15:30.
- Technik-Paket, neuer Termin ab 22:30.

### Fr 09.10. – Mi 14.10.2026

**Geschafft:**
- Keine Sitzung. Der Bot lief unverändert seit dem 03.10.: 13 Trades, −19,27 $, jeden Abend flach.
- Der Setup-Export vom 13.10. scheiterte beim Hochladen der 1-Min-Datei (einmaliger Fehler).

**Morgen dran (Do 15.10.):**
- Neuer Auftrag des Inhabers vom 15.10.

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
  - Entscheidung dazu in der Vorab-Datei.
- Kopfzeile der Zusammenfassung von Runde 1 korrigiert. Dort stand „erstes Rechnen“, richtig ist die Neuberechnung
  nach dem Simulatorfehler; die Zahlen sind unverändert.
- ORB Jahr 1 fertig: 973 Trades, −0,465R, 1 von 5 Kriterien.
  - 594 Trades wurden schon in ihrer Einstiegsminute gestoppt (vorsichtige Vorab-Regel).
  - Die Neuberechnung mit Ticks ist vorgeschlagen, die Entscheidung liegt beim Inhaber.
- Tagestrend SIP gegen IEX gemessen: 0,46 % abweichend, also SIP-Vorlauf; der Suchtopf bleibt ab Okt 2020.
- Entscheidungen des Inhabers eingetragen.
  - .env-Vorlage und Einrichtungsskripte für Etappe 0 sind vorbereitet.
  - Der Fahrplan-Wächter prüft jetzt auch Belege, Feste Regeln und Prüfregeln.

**Morgen dran (Fr 09.10.):**
- Wochenreview.
- Technik-Paket ab 22:30 (16:30 New York), sobald `setups/2026-10-09.json` auf main liegt. Mit dabei: Halbtag-Test,
  Speicherschutz für den Bot-Dienst und die Seiten-Dateien mit gleicher Prüfsumme. Danach ist live eingefroren.
- ORB: Entscheidung des Inhabers zur Tick-Neuberechnung, danach Jahr 2.
