# Chart-Leser · Festlegung v1.1 · 16.10.2026

Fassungen: **v1** vom 15.10.2026 (Teil 1, SHA-256 93efee36…, im Logbuch); **v1.1** vom 16.10.2026 legt Teil 2 fest,
Teil 1 ist Wort für Wort unverändert.

Der Chart-Leser zeichnet die Linien eines Musters selbst, prüft sie auf Fehler und bewertet das Muster. Er ist vom
Bot getrennt: Er liest nur Kerzen und ändert am Bot nichts.

**Feste Regeln:**
- Er benutzt nur Daten, die zum Entscheidungszeitpunkt vorlagen.
- Diese Datei wird **vor** jedem Lauf auf echten Daten festgelegt.
- Jede Änderung ergibt eine neue Fassung mit neuem Hash im Logbuch.
- Der Chart-Leser wird nicht auf einzelne Beispiele eingestellt, auch nicht auf t70.

## Teil 1 · Signalprüfung (fertig, Tests grün)

Teil 1 prüft ein Signal des Live-Bots: Hängen seine Linien an echten Kursen?

1. **Eingabe**
   - IEX-15-Min-Kerzen wie live: roh, mit vor- und nachbörslichen Kerzen, bis einschließlich der Signalkerze.
   - Der Detektor sieht wie live die letzten 200 Kerzen.
   - Für die Maßstäbe braucht es mindestens 20 Handelstage Vorlauf.
2. **Ankerpunkte**
   - Das sind die Punkte, aus denen der Bot-Detektor Kante, Gegenkante, Stop und Ziel bildet. Beim Rechteck zählen
     zusätzlich alle Berührungen dazu.
   - Sie werden mit der Wendepunkt-Funktion des Bots (k = 3) nachgebaut und gegen den echten Detektor geprüft:
     Kante und Ziel müssen exakt übereinstimmen. Sonst lautet das Ergebnis „nicht prüfbar“.
3. **Prüfung je Ankerpunkt** (das Hoch bzw. Tief der Kerze)
   - **Gibt es eine SIP-Kerze** (Kerzenende + 15 Minuten ≤ Entscheidung, Verzögerung des Gratis-Tarifs), entscheidet
     SIP.
     - Verglichen wird mit der SIP-Spanne derselben 15 Minuten aus SIP-1-Min-Kerzen (roh).
     - Liegt das IEX-Tief um mindestens 1 Cent unter dem SIP-Tief bzw. das IEX-Hoch über dem SIP-Hoch, ist der Punkt
       **nicht bestätigt**. Er wird verworfen und durch den SIP-Wert ersetzt.
     - Sonst ist der Docht **echt**, auch ein langer (z. B. ein Stop-Lauf), und bleibt Ankerpunkt.
   - **Gibt es keine SIP-Kerze**, wird ein Docht verworfen, der länger als **3 × die mittlere Spanne** ist. Er wird
     auf den Kerzenkörper gekürzt. Die 3×-Regel stammt aus dem Live-Trade t70.
   - **Maßstab für die mittlere Spanne** (Hoch − Tief):

     | Kerze | gemessen an |
     |---|---|
     | Eröffnungskerze (09:30 NY) | den Eröffnungskerzen der letzten 20 Handelstage |
     | andere Kerze der Handelszeit | den 20 Kerzen der Handelszeit davor |
     | vor- oder nachbörsliche Kerze | den 20 Kerzen davor |

     Bei weniger als 10 Vergleichskerzen gibt es kein Urteil („Maßstab fehlt“). Der Punkt bleibt dann und wird als
     ungeprüft gezählt.
4. **Neu ziehen**
   - Derselbe Detektor läuft auf den korrigierten Kerzen, höchstens 3 Runden. Neue Ankerpunkte werden ebenfalls
     geprüft.
   - Kante, Gegenkante, Stop und Ziel kommen **nur** aus diesem Ergebnis. Wie live gelten der Mindest-Stop von 0,3 %
     und ein Chance-Risiko von mindestens 0,8.
   - Findet der Detektor auf den korrigierten Kerzen kein Muster mehr, lautet das Ergebnis „ungültig“, mit Grund.
5. **Signalkerze**
   - Zuerst wird ihr eigener Docht geprüft. Zur Entscheidung gibt es nie eine SIP-Kerze, also gilt die 3×-Regel.
   - **Abzug** gibt es, wenn sie mehr als 1 ATR jenseits der Kante eröffnet und in derselben Kerze mehr als 0,5 ATR
     zurück hinter die Kante fällt.
   - Für Short gilt das gespiegelt.
   - ATR ist Wilder 14 auf 15-Min-Kerzen, bis zur Kerze vor dem Signal.
6. **Bewertung v1:**

   | Ergebnis | Bedeutung |
   |---|---|
   | „sauber“ | alle Ankerpunkte bestätigt, Signalkerze ohne Abzug |
   | „mit Abzug“ | mindestens ein Abzug, die Abzüge stehen einzeln in der Liste |
   | „ungültig“ | nach der Korrektur ist kein Muster mehr da |
   | „nicht prüfbar“ | der Nachbau stimmt nicht mit dem Detektor überein |

   - Es gibt **keine Punktzahl**. Welche Merkmale wirklich zählen, zeigt erst der Lerntopf.
7. **Ausgabe:** JSON je Signal mit:
   - den Bot-Werten und den Linien des Bots (Kante, Gegenkante, Fenster);
   - jeder Prüfung (Zeit, Hoch oder Tief, Kurs, SIP-Wert, Docht, mittlere Spanne, Faktor, Maßstab, Grund, Ersatz);
   - den verworfenen Punkten;
   - den korrigierten Werten (Kante, Gegenkante, Stop, Ziel);
   - der Prüfung der Signalkerze und der Bewertung.

## Teil 2 · Lesen ohne Bot (Fassung v1.1, festgelegt 16.10.2026)

Teil 2 sucht zum Entscheidungszeitpunkt Muster, die auf der letzten geschlossenen Kerze ausbrechen. Er kennt
Rechteck, Keil steigend, Keil fallend, Doppelboden und Doppeltop.

1. **Wendepunkte:**
   - Zickzack in 3 Größen: 1, 2 und 4 ATR (Wilder 14).
   - Ein Hoch ist bestätigt, sobald der Kurs um Größe × ATR der bestätigenden Kerze darunter fällt. Für ein Tief gilt
     das gespiegelt. Hochs und Tiefs wechseln sich ab.
   - Gelesen werden nur Punkte, die spätestens mit der Kerze vor dem Signal bestätigt sind.
2. **Zoom:** 50, 100 und 200 Kerzen.
   - Je Muster und Seite zählt der beste Fund über alle Größen und Zoomstufen: die meisten Berührungen, dann die beste
     Passgüte, dann die kleineren Wendepunkte.
3. **Selbstkontrolle zuerst:**
   - Jeder Wendepunkt aller Größen im 200er-Fenster wird geprüft wie in Teil 1. Gibt es eine SIP-Kerze, entscheidet
     SIP, sonst die 3×-Regel.
   - Ein verworfener Docht wird ersetzt: durch den SIP-Wert, ohne SIP-Kerze durch den Kerzenkörper. Das geht höchstens
     3 Runden lang.
   - Danach wird auf den korrigierten Kerzen gelesen. Liegt ein verworfener Punkt in der Zeitspanne des Musters, gibt
     es einen Abzug.
4. **Toleranz:** 0,5 ATR der Kerze vor dem Signal, mindestens 0,1 % vom Kurs.
   - Berührung heißt: ein Wendepunkt liegt innerhalb der Toleranz der Linie.
   - Passgüte = 1 − (mittlere Abweichung der Berührungen ÷ Toleranz).
5. **Mindestgröße, gilt für alle Muster:** Höhe mindestens 3 ATR; von der ersten bis zur letzten Berührung
   mindestens 10 Kerzen.
6. **Rechteck:**
   - Obere Zone (Hochs) und untere Zone (Tiefs) mit je mindestens 2 Berührungen. Die Linie geht durch den äußersten
     Docht der Zone.
   - Die Berührungen wechseln mindestens 3-mal zwischen oben und unten. Die Höhe beträgt höchstens 12 % vom Kurs.
   - Ab der ersten Berührung bis zur Kerze vor dem Signal liegt kein Wendepunkt und kein Schlusskurs außerhalb der
     Zonen (± Toleranz).
   - **Ausbruch:** Schlusskurs über der oberen Zone (long) bzw. unter der unteren Zone (short), die Kerze davor
     schließt noch innerhalb.
   - Stop in der Mitte, Ziel Kante ± Höhe.
7. **Keil steigend und fallend:**
   - Obere Linie durch 2 Hochs, untere durch 2 Tiefs, jeweils durch die Dochte.
   - Ab dem Start der Linie durchsticht kein Wendepunkt sie um mehr als die Toleranz. Kein Schlusskurs bis zur Kerze
     vor dem Signal liegt jenseits der Linie. Beste Linie: die meisten Berührungen, dann Passgüte, dann Länge.
   - **Steigend:** beide Steigungen über 0, die untere ist steiler. **Fallend:** beide unter 0, die obere ist steiler.
     In beiden Fällen wird der Keil enger.
   - Eine Linie hat mindestens 3 Berührungen, die andere mindestens 2. Zusammen also mindestens 5, wie bei
     Kirkpatrick.
   - Vom Beginn bis zum Signal wird der Keil um mindestens 30 % enger. Seine Breite am Beginn beträgt mindestens 3 ATR.
   - **Ausbruch:** Der steigende Keil bricht nach unten aus (short), der fallende nach oben (long).
   - **Ziel:** der Preis der Gegenlinie am Beginn des Keils. **Stop:** der äußerste Berührungspunkt der Gegenseite.
8. **Doppelboden und Doppeltop:**
   - Zwei Tiefs (Hochs) innerhalb 1 ATR, mindestens 10 Kerzen auseinander.
   - Die Nackenlinie ist das höchste Hoch (tiefste Tief) dazwischen, durch den Docht. Der Abprall bis dorthin beträgt
     mindestens 3 ATR.
   - Der zweite Boden ist der tiefste Punkt nach der Nackenlinie (beim Top der höchste).
   - Seit dem ersten Boden schließt keine Kerze unter dem Boden (− Toleranz). Vor der Signalkerze schließt keine über
     der Nackenlinie. Beim Top gilt alles gespiegelt.
   - **Ausbruch:** Schlusskurs über (unter) der Nackenlinie.
   - Ziel: Nackenlinie ± Höhe. Stop: Boden − 0,15 ATR (Top + 0,15 ATR). Es zählt das jüngste Paar.
9. **Signalkerze und Bewertung:** wie in Teil 1.
10. **Nicht Sache des Lesers:** Vortrend, Volumen und Kaufkraft. Das legen die Steckbriefe fest.

**Pflichttests v1.1 (alle grün am 16.10.):**

| Test | Ergebnis | Grenze |
|---|---|---|
| Keil steigend, 50 verrauschte Varianten (mittleres Rauschen) | 48 erkannt | mindestens 45 |
| Keil fallend | 50 erkannt | mindestens 45 |
| Doppelboden | 45 erkannt | mindestens 45 |
| Rechteck | 50 erkannt | mindestens 45 |
| Zufallspfade, 300 Reihen | 15 mit Muster | höchstens 15 |
| stationäres Rauschen, 300 Reihen | 9 mit Muster | höchstens 15 |
| eingebauter Ausreißer-Docht an einem echten Tiefpunkt | verworfen; Rechteck danach mit 16 und 17 statt 4 und 4 Berührungen gelesen | verworfen |
| Abschneide-Test | spätere Kerzen ändern nichts | identisch |

Die Grenzen sind nach der Messung auf künstlichen Daten gesetzt. Echte Daten hat Teil 2 bis zu dieser Festlegung
nicht gesehen. Doppelboden und Zufallspfade liegen genau an der Grenze; das wird so berichtet und nicht nachgestellt.

## Diagnose Runde 1 (Okt. 2025 – Sep. 2026, Prüftopf)

Für die Diagnose gilt:
- **Nur Geometrie.** Für jeden Trade der Runde läuft Teil 1.
- **Gezählt wird:**
  - wie viele Linien an verworfenen Punkten hängen;
  - wie sich Kante, Gegenkante, Stop und Ziel ändern;
  - wie viele Muster nach der Korrektur ungültig wären.
- **Ausdrücklich nicht:**
  - kein Vorher/Nachher in R;
  - keine Auswahl nach Ergebnis.

  Ein Vorher/Nachher in R gibt es nur im Lerntopf.
- **Bilder:** 40 Trades, zufällig gezogen mit dem festen Seed 20261015.

## Live-Trade t70 (AMD, Rechteck long, Signalkerze 06.10.2026 09:30 NY, Entscheidung 09:50:26 NY)

- Diese Fassung läuft unverändert auf t70.
- **Erwartung des Inhabers:**
  - der Docht 620,05 der Eröffnungskerze vom 05.10. wird verworfen;
  - Unterkante ca. 627,36;
  - Stop 631,61 (Mitte);
  - Ziel 644,36.
- Bestätigt SIP die 620,05, bleibt der Docht stehen, und das wird so berichtet.
- Weicht das Ergebnis ab, wird es erklärt.
