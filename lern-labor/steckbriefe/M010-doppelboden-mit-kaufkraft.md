# M010 · Doppelboden mit Kaufkraft

Neues Muster des Lern-Labors (Umkehr nach einem Abwärtstrend, nur long), Auftrag des Inhabers vom 15.10.2026. Angelegt am 16.10.2026 · **Stufe 0** (Steckbrief liegt vor). Diese Regeln stehen fest, bevor irgendein Ergebnis bekannt ist; eine Änderung ergibt ein neues Muster mit neuer Nummer.

| Feld | Inhalt |
|---|---|
| Name, Quelle | Doppelboden, nur mit Zeichen von Kaufkraft am zweiten Boden. Quelle: Idee des Inhabers (15.10.: Volumen am ersten gegen das am zweiten Tief, Dochte, Stärke des Abpralls); Lehrbuch-Grundlage Bulkowski und Kirkpatrick; Linien nach dem Chart-Leser. |
| Zeitebene und Zoom | 15-Min-Kerzen von IEX, unbereinigt, wie live. Gelesen vom Chart-Leser Teil 2 (Festlegung v1.1): Wendepunkte 1, 2 und 4 ATR, Zoom 50, 100 und 200 Kerzen; je Muster und Seite zählt der beste Fund. |
| Vortrend | Abwärtstrend vor dem ersten Boden: Der Schlusskurs 50 Kerzen vor dem ersten Boden liegt mindestens 4 ATR über dem ersten Boden. |
| Linienregeln | Zwei Wendepunkt-Tiefs innerhalb 1 ATR, mindestens 10 Kerzen auseinander. Nackenlinie = höchstes Wendepunkt-Hoch dazwischen, waagerecht durch den Docht; Abprall bis dorthin mindestens 3 ATR. Der zweite Boden ist der tiefste Punkt nach der Nackenlinie. |
| Gültig nur, wenn … | Alle drei Zeichen von Kaufkraft: (1) **Volumen:** Kerze des zweiten Bodens und ihre beiden Nachbarn zusammen mit weniger Volumen als dieselben drei Kerzen am ersten Boden. (2) **Docht:** Der untere Docht der Kerze des zweiten Bodens ist mindestens 40 % ihrer Spanne. (3) **Abprall:** Das mittlere Volumen je Kerze im Anstieg vom zweiten Boden bis zur Kerze vor dem Signal ist höher als im Abstieg von der Nackenlinie zum zweiten Boden. Dazu: seit dem ersten Boden kein Schlusskurs unter dem Boden (− Toleranz), vor der Signalkerze keiner über der Nackenlinie. |
| Auslöser | Die Signalkerze schließt über der Nackenlinie, die Kerze davor noch nicht. Bewertet etwa 30 Sekunden nach Kerzenschluss. |
| Stop | Tieferer Boden − 0,15 ATR. |
| Ziel | Nackenlinie + Höhe; Höhe = Nackenlinie − tieferer Boden. |
| Ungültig, wenn … | Ein Schlusskurs unter dem Boden (− Toleranz) oder über der Nackenlinie vor dem Auslöser; eines der drei Zeichen von Kaufkraft fehlt. |
| Haltedauer | Wie der Live-Bot: Stop und Ziel ruhen beim Broker, ab +0,6R Stop auf den Einstieg, Zeit-Stopp nach 120 Minuten (im Minus oder unter 80 % des besten R: schließen, sonst bis höchstens 240 Minuten), Glattstellung 10 Minuten vor Börsenschluss. Nie über Nacht. |
| Bewertungsmerkmale | Werden für jedes Signal gespeichert, auf Stufe 0 aber nicht zum Filtern benutzt: Berührungen und Passgüte je Linie, Verengung, Höhe in ATR, Prüfung der Signalkerze, verworfene Punkte. Dazu die drei Kaufkraft-Werte als Zahlen (Volumenverhältnis, Dochtanteil, Volumen im Anstieg gegen Abstieg). |
| Darstellung im Bild | Die zwei Böden als Kreise, waagerechte Nackenlinie, Höhe als Pfeil, Volumen am ersten und zweiten Boden hervorgehoben, Ziel und Stop gestrichelt. |
| Selbstkontrolle | Chart-Leser Teil 2 v1.1: Jeder Wendepunkt im 200er-Fenster wird geprüft (SIP entscheidet, ohne SIP-Kerze die 3×-Regel), verworfene Dochte werden ersetzt und das Muster neu gelesen; Ziel und Stop nur aus geprüften Linien; Abzug für eine Signalkerze mit großer Lücke und tiefem Durchfall. |

**Danach gelten die Filter des Live-Bots wie für M001–M007, damit der Vergleich fair bleibt:**
  - Mindest-Stop 0,3 % vom Schlusskurs; ein engerer Stop wird auf 0,3 % aufgeweitet.
  - Chance-Risiko am Schlusskurs mindestens 0,8.
  - Volumen der Signalkerze mindestens 1,5 × Schnitt der letzten 20 Kerzen (einschließlich der Signalkerze).
  - Anti-Chase-Zone: Breite max(0,4 × ATR der 15-Min-Kerzen; 0,1 %), am Schlusskurs verankert (V1).
  - Kurs höchstens 60 Sekunden alt, Spread höchstens 0,25R, Chance-Risiko am Fill mindestens 0,8.
  - Relative Stärke gegen SPY über 13 Kerzen in Handelsrichtung; kein Trade gegen den Markt, wenn SPY am Tag mehr als
    0,5 % dagegen steht.
  - Keine Einstiege in den ersten 20 und in den letzten 30 Minuten der Sitzung.
  - Risiko 0,5 % je Trade, höchstens 5 Positionen, Positionswert höchstens 20 % des Kontos.

**Bisher gerechnet:** nichts. Getestet wird im Lerntopf (Okt. 2020–Sep. 2023), Jahr für Jahr, mit Selbstkontrolle,
Zufallslatte und Kostenstress.
