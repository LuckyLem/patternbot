# M005 · Doppelboden

Steckbrief des Live-Bots, genau so, wie der Code das Muster heute erkennt (Bot-Code cbfe06cff, Detektor
„DoubleBottom“). Angelegt am 15.10.2026 · **Stufe 0** (Steckbrief liegt vor). Eine Änderung ergibt ein neues Muster mit
neuer Nummer.

| Feld | Inhalt |
|---|---|
| Name, Quelle | Doppelboden (Umkehr, nur long). Quelle: Live-Code des Bots; Lehrbuch-Grundlage Kirkpatrick/Fidelity und Bulkowski. |
| Zeitebene und Zoom | 15-Min-Kerzen von IEX, unbereinigt, wie live. Der Bot sieht die letzten 200 abgeschlossenen Kerzen einschließlich Vor- und Nachbörse (Abruf über 14 Tage). Ein Zoom gibt es nicht. |
| Vortrend | Wird nicht geprüft (das Lehrbuch verlangt einen Abwärtstrend davor). Kein Tagestrend-Filter. |
| Linienregeln | Wendepunkte nach der Fraktal-Methode mit 3 Kerzen: Ein Hoch ist Wendepunkt, wenn es das höchste der 7 Kerzen von 3 davor bis 3 danach ist, höher als die Kerze davor und mindestens so hoch wie die danach (Tief gespiegelt). Bekannt ist er erst 3 Kerzen später. Linien laufen durch die Dochte (Hoch bzw. Tief der Kerze), nicht durch die Körper. Es gibt nur diese eine Größe von Wendepunkten. Die letzten zwei Wendepunkt-Tiefs (Böden). Nackenlinie = höchstes Wendepunkt-Hoch zwischen den Böden, waagerecht. |
| Gültig nur, wenn … | Die Böden liegen höchstens 2 % auseinander und mindestens 4 Kerzen voneinander entfernt. Dazwischen liegt mindestens ein Wendepunkt-Hoch. Volumen und Abprall an den Böden werden nicht geprüft. |
| Auslöser | Die Signalkerze schließt jenseits der Kante, die Kerze davor noch nicht (Schluss davor ≤ Kante < Schluss jetzt; short gespiegelt). Bewertet wird etwa 30 Sekunden nach Kerzenschluss. |
| Stop | Tieferer Boden × (1 − Puffer); Puffer wie bei M001. |
| Ziel | Nackenlinie + Höhe; Höhe = Nackenlinie − tieferer Boden. |
| Ungültig, wenn … | Böden mehr als 2 % auseinander oder weniger als 4 Kerzen Abstand, kein Hoch dazwischen. |
| Haltedauer | Stop und Ziel ruhen als Bracket-Order beim Broker. Ab +0,6R wird der Stop auf den Einstieg nachgezogen. Zeit-Stopp nach 120 Minuten: Liegt der Trade dann im Minus oder unter 80 % seines besten R, wird er geschlossen, sonst bleibt er bis höchstens 240 Minuten. Glattstellung 10 Minuten vor Börsenschluss (an Halbtagen 12:50 New York). Nie über Nacht. |
| Bewertungsmerkmale | Der heutige Bot bewertet nicht. Er nimmt das erste Setup, das alle Filter besteht, in der Reihenfolge der Aktienliste. |
| Darstellung im Bild | Die zwei Böden als Kreise, waagerechte Nackenlinie, Höhe als Pfeil, Ziel und Stop gestrichelt. |
| Selbstkontrolle | Keine. Weder Mindestberührungen mit enger Toleranz noch eine Prüfung auf Ausreißer-Dochte oder gegen SIP (Beispiel t70: Unterkante an einem einzelnen Docht der Eröffnungskerze). Der Chart-Leser rüstet das als neue Muster nach; M001–M007 bleiben als Vergleich unverändert. |

**Danach gelten die Filter des Bots für alle Muster:**
  - Mindest-Stop 0,3 % vom Schlusskurs; ein engerer Stop wird auf 0,3 % aufgeweitet.
  - Chance-Risiko am Schlusskurs mindestens 0,8.
  - Volumen der Signalkerze mindestens 1,5 × Schnitt der letzten 20 Kerzen (einschließlich der Signalkerze).
  - Anti-Chase-Zone: Breite max(0,4 × ATR der 15-Min-Kerzen; 0,1 %), seit 05.10. am Schlusskurs verankert (V1).
  - Kurs höchstens 60 Sekunden alt, Spread höchstens 0,25R, Chance-Risiko am Fill mindestens 0,8.
  - Relative Stärke gegen SPY über 13 Kerzen in Handelsrichtung. Kein Trade gegen den Markt, wenn SPY am Tag mehr als 0,5 % dagegen steht.
  - Keine Einstiege in den ersten 20 und in den letzten 30 Minuten der Sitzung.
  - Risiko 0,5 % je Trade, höchstens 5 Positionen, Positionswert höchstens 20 % des Kontos. Sind alle 5 Plätze belegt, entfällt das Setup.

**Bisher gerechnet:** Runde 1 (Okt. 2025–Sep. 2026) mit allen Mustern zusammen. Dieses Jahr gehört zum Prüftopf und
gilt für das Lern-Labor nicht als Beweis.
