# Recherche · Wie der Bot ein Rechteck richtig erkennt

Stand: Fr 23.10.2026, Claude im Chat. Gehört zu `lernhub/prompts/grosse-umstellung-v2-zielsetzung.md` (ab Fassung 2.1).
Alles in eigenen Worten, Quellen am Ende.

## 1. Was beim alten Bot falsch war

| Punkt | Alter Bot | Folge |
|---|---|---|
| Toleranz | in Prozent (Rechteck 2 %) | Auf 15 Min sind 2 % oft 5–10 Kerzenspannen. Fast jeder Punkt „berührt“. |
| Wendepunkte | jedes Hoch über 3 Kerzen | Kleines Zucken zählt wie ein echter Umkehrpunkt. |
| Kante | höchstes Hoch der letzten 50 Kerzen | Die Kante hängt oft an einem einzigen Punkt. Nur 6 von 40 Live-Rechtecken hatten 2 echte Berührungen je Kante. |
| Zeit | 50 Kerzen, über mehrere Tage | Auf 15 Min reicht ein „Rechteck“ über Nacht, inklusive Kurslücke. |
| Seitwärts? | nicht geprüft | Ein flacher Trendkanal gilt auch als Rechteck. |

## 2. Wie es Profis und die Forschung machen

- **Forschung (Lo, Mamaysky, Wang 2000):** Muster werden aus einer Folge von Wendepunkten des geglätteten Kurses bestimmt. Hochs und Tiefs müssen jeweils innerhalb einer kleinen Toleranz um ihren Mittelwert liegen. Das ist im Kern unser Ansatz, mit zwei Unterschieden:
  - Wir glätten nicht zentriert, denn das würde in die Zukunft schauen.
  - Wir messen die Toleranz in Kerzenspannen statt in Prozent.
- **Werkzeuge für Unterstützung und Widerstand** arbeiten fast alle gleich:
  1. Wendepunkte finden;
  2. Wendepunkte mit ähnlichem Preis zu einer Zone zusammenfassen, die Toleranz in ATR;
  3. Berührungen zählen;
  4. nur Zonen mit genug Berührungen behalten.
  Wichtig dabei: Ein Wendepunkt ist erst ein paar Kerzen später sicher. Das muss auch im Test so sein.
- **Lehrbuch (Bulkowski):** Der Kurs läuft zwischen den Linien hin und her und berührt jede Linie mehrmals, beim strengen Lehrbuch-Rechteck mindestens dreimal. Das ist unsere Note A+.
- **Intraday-Schwankung:** Sie ist morgens und kurz vor Schluss hoch und mittags niedrig (die bekannte U-Form). Ein festes ATR macht die Toleranz mittags zu groß und morgens zu klein.

## 3. Die Verbesserungen

1. **ATR je Tageszeit.** Statt eines gleitenden ATR über die letzten 14 Kerzen: die mittlere Kerzenspanne **derselben Uhrzeit** an den letzten 20 Handelstagen (nur aus der Vergangenheit). Das haben wir bei den Eröffnungskerzen schon so gemacht. Toleranz, Höhe und Mindest-Stop rechnen damit.
2. **Keine Berührung in den ersten 15 Minuten.** Die Eröffnung ist zu wild. Ein Kasten beginnt frühestens mit der Kerze ab 09:45 New York.
3. **Wendepunkte zweistufig.** Ein Wendepunkt braucht 2 Kerzen rechts und links **und** einen Abstand von mindestens 0,5 ATR zum vorigen Gegen-Wendepunkt. Bekannt ist er erst 2 Kerzen später.
4. **Linie robust.** Die Linie ist der **Median** der Berührungspreise statt des Mittelwerts, so zieht ein einzelner Ausreißer sie nicht weg. Die Passgüte ist die mittlere Abweichung der Berührungen in ATR.
5. **Ist es wirklich seitwärts?**
   - Die Effizienz des Kurses im Kasten ist niedrig: |Schluss Ende − Schluss Anfang| geteilt durch die Summe aller Schlusskurs-Schritte, höchstens 0,3.
   - Die Steigung der Schlusskurse im Kasten ist fast null: höchstens 0,03 ATR je Kerze.
   - So wird ein Trendkanal nicht als Rechteck gezählt.
6. **Abprall an der Linie.** Eine Berührung ist stärker, wenn die Kerze danach von der Linie wegschließt, zum Beispiel im inneren Teil ihrer Spanne. Mindestens 2 Berührungen mit Abprall sind Teil der Note A.
7. **Note als Punktzahl 0–100**, statt nur harter Grenzen. Bestandteile:
   - Zahl und Abstand der Berührungen;
   - Passgüte;
   - Kurs bleibt im Kasten;
   - seitwärts (Effizienz und Steigung);
   - Abprall;
   - Verhältnis von Höhe zu Breite.
   Die Gewichte stehen vorab fest. A ab 80, B 60–79, C unter 60. Die Punktzahl ist der „Indikator“: Sie steigt, während der Kasten reift.
8. **Merkmale mitschreiben, nicht filtern.** Zu jedem Signal:
   - Volumen im Kasten (erste gegen zweite Hälfte), Volumen der Auslöserkerze;
   - Vortrend vor dem Kasten;
   - Lage im Tagesbereich;
   - Abstand zum VWAP;
   - Richtung des SPY, Uhrzeit, Kurslücke am Morgen.
   Gefiltert wird damit erst später (Etappe 1), wenn es die Daten zeigen.
9. **Zwei Sichtprüfungen statt einer:**
   - **Präzision:** Der Bot meldet ein Rechteck. Ist es eins? (Ziel: mindestens 80 % „ja“.)
   - **Trefferquote:** 30 zufällige Tagescharts **ohne** die Linien des Bots. Siehst du ein Rechteck? Danach wird verglichen, wie viele davon der Bot auch gefunden hat. Sonst wissen wir nicht, ob er zu streng ist.
10. **Die Sichtprüfung eicht die Note, nicht das Ergebnis.** Ob die Punktzahl stimmt, zeigt der Vergleich mit deinen Ja/Nein-Antworten: Hohe Punktzahl soll oft „ja“ heißen. Gewinne und Verluste spielen dabei keine Rolle.
11. **Später: das Bild-Netz.** Studien erreichen mit Bild-Netzen auf Kerzenbildern etwa 90 % Treffer bei der Erkennung bekannter Kerzenmuster. Dafür braucht es viele bewertete Beispiele, und genau die sammelt die Sichtprüfung.

## 4. Einstellungen des Bots für das Rechteck (Vorschlag, vorab festzulegen)

| Einstellung | Wert | Warum |
|---|---|---|
| Kerzen | 5 und 15 Min aus SIP, nur 09:30–16:00 | vollständige Kurse, keine dünnen Vor- und Nachbörsenkerzen |
| Tag | alles an einem Handelstag | kein Muster über Nacht |
| ATR | je Tageszeit, 20 Tage zurück | U-Form der Schwankung |
| Erster Kastenpunkt | ab 09:45 | wilde Eröffnung |
| Wendepunkt | 2 Kerzen je Seite, mindestens 0,5 ATR Schwung | kein Zucken |
| Berührung | Docht höchstens 0,15 ATR von der Linie | „berührt wirklich“ |
| Weg zwischen zwei Berührungen | mindestens 40 % der Kastenhöhe | echtes Hin und Her |
| Berührungen | mindestens 2 + 2, abwechselnd (A: 3 + 2, A+: 3 + 3) | Lehrbuch |
| Kurs im Kasten | kein Schluss außerhalb, höchstens 1 Docht bis 0,3 ATR | sauberer Kasten |
| Seitwärts | Effizienz höchstens 0,3, Steigung höchstens 0,03 ATR je Kerze | kein Trendkanal |
| Höhe | 1,5–6 ATR | nicht zu flach, nicht zu hoch |
| Breite | mindestens 10 Kerzen (15 Min), 12 Kerzen (5 Min) | genug Zeit zum Pendeln |
| Note | Punktzahl 0–100, gehandelt nur A (ab 80) | nur Lehrbuch |
| Mindest-Stop | max(0,5 ATR; 0,15 %) | keine Trades mit winzigem Stop |
| Ausstieg | Ziel, Stop oder 15:50 | einfach, kein Halten über Nacht |
| Einstiege | A Ausbruch, B Retest, C Abpraller, D Fehlausbruch | die Daten entscheiden |

## Quellen

- Lo, Mamaysky, Wang (2000): Foundations of Technical Analysis. https://www.nber.org/papers/w7613
- Bulkowski, Rectangle Tops und Bottoms: https://thepatternsite.com/recttops.html, https://thepatternsite.com/rectbots.html, Quiz: https://thepatternsite.com/QRectTops.html
- Al Brooks, Forum zu Ausbrüchen: https://www.brookstradingcourse.com/support-forum/12-market-cycle/breakout-fail/
- Ausbruch gegen Retest (TradingView-Studie): https://www.tradingview.com/script/SA4YoyNF-Breakout-Retest-Entry-Signals-the-Break-vs-Retest/
- Zonen aus Wendepunkten (LuxAlgo): https://www.luxalgo.com/library/concept/level-clustering-algorithms.md
- U-Form der Intraday-Schwankung (Ozenbas, Zamanian): https://digitalcommons.montclair.edu/economics-facpubs/3
- Bild-Netze für Kerzenmuster (Chen, Tsai 2020): https://jfin-swufe.springeropen.com/articles/10.1186/s40854-020-00187-0/figures/13 · Velay, Daniel (2018): https://arxiv.org/pdf/1808.00418
