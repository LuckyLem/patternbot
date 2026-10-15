# Chart-Leser · Festlegung v1 · 15.10.2026

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

## Teil 2 · Lesen ohne Bot (im Bau, Freitag und Samstag)

Teil 2 liest den Chart ohne den Bot. Seine Bausteine stehen schon im Code und im Abschneide-Test:

- **Wendepunkte:** Zickzack in 3 Größen, 1, 2 und 4 ATR (Wilder 14).
  - Ein Hoch ist bestätigt, sobald der Kurs um Größe × ATR der bestätigenden Kerze darunter fällt. Für ein Tief gilt
    das gespiegelt.
  - Hochs und Tiefs wechseln sich ab. Bekannt ist ein Punkt erst ab der bestätigenden Kerze.
- **Zoom:** 50, 100 und 200 Kerzen.
- **Waagerechte Zonen:** Gruppen von Hochs bzw. Tiefs innerhalb der Toleranz. Die Linie geht durch den äußersten
  Docht.
- **Trend- und Nackenlinien:** Geraden durch Wendepunkte, durch die Dochte, mit Berührungen innerhalb der Toleranz.
- **Passgüte:** Streuung der Berührungen gemessen an der Toleranz.
- **Selbstkontrolle:** wie in Teil 1.

**Noch nicht festgelegt:**
- die Toleranz;
- die Bedingungen für Rechteck, Keil und Doppelboden;
- die Berührungsregeln je Linie.

Sie werden vor dem ersten Lauf auf echten Daten als Fassung v1.1 festgelegt, mit Hash und den Pflichttests:
künstlicher Keil, künstliches Rechteck und künstlicher Doppelboden werden erkannt, Rauschen nicht.

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
