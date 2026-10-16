# M009 · Keil fallend

Neues Muster des Lern-Labors (Umkehr nach einem Abwärtstrend, nur long), Auftrag des Inhabers vom 15.10.2026. Angelegt am 16.10.2026 · **Stufe 0** (Steckbrief liegt vor). Diese Regeln stehen fest, bevor irgendein Ergebnis bekannt ist; eine Änderung ergibt ein neues Muster mit neuer Nummer.

| Feld | Inhalt |
|---|---|
| Name, Quelle | Keil fallend (falling wedge). Quelle: Kirkpatrick/Fidelity (mindestens 5 Berührungen, Ausbruch meist nach oben) und Bulkowski; Linien nach dem Chart-Leser. |
| Zeitebene und Zoom | 15-Min-Kerzen von IEX, unbereinigt, wie live. Gelesen vom Chart-Leser Teil 2 (Festlegung v1.1): Wendepunkte 1, 2 und 4 ATR, Zoom 50, 100 und 200 Kerzen; je Muster und Seite zählt der beste Fund. |
| Vortrend | Klarer Abwärtstrend vor dem Keil: Der Schlusskurs der ersten Keil-Kerze liegt mindestens 4 ATR unter dem Schlusskurs 50 Kerzen davor (ATR der Kerze vor dem Signal). |
| Linienregeln | Obere Linie durch 2 Wendepunkt-Hochs, untere durch 2 Wendepunkt-Tiefs, durch die Dochte. Berührung innerhalb 0,5 ATR (mindestens 0,1 % vom Kurs). Eine Linie mindestens 3, die andere mindestens 2 Berührungen. |
| Gültig nur, wenn … | Beide Linien fallen, die obere steiler (der Keil wird enger). Vom Beginn bis zum Signal wird er mindestens 30 % enger; Breite am Beginn mindestens 3 ATR; erste bis letzte Berührung mindestens 10 Kerzen. Kein Wendepunkt durchsticht eine Linie um mehr als die Toleranz, kein Schlusskurs liegt jenseits einer Linie. |
| Auslöser | Die Signalkerze schließt über der oberen Linie, die Kerze davor noch nicht. Bewertet etwa 30 Sekunden nach Kerzenschluss. |
| Stop | Der tiefste Berührungspunkt der unteren Linie (Docht). |
| Ziel | Der Preis der oberen Linie am Beginn des Keils. |
| Ungültig, wenn … | Ein Schlusskurs unter der unteren Linie vor dem Auslöser; die Linien treffen sich vor dem Signal. |
| Haltedauer | Wie der Live-Bot: Stop und Ziel ruhen beim Broker, ab +0,6R Stop auf den Einstieg, Zeit-Stopp nach 120 Minuten (im Minus oder unter 80 % des besten R: schließen, sonst bis höchstens 240 Minuten), Glattstellung 10 Minuten vor Börsenschluss. Nie über Nacht. |
| Bewertungsmerkmale | Werden für jedes Signal gespeichert, auf Stufe 0 aber nicht zum Filtern benutzt: Berührungen und Passgüte je Linie, Verengung, Höhe in ATR, Prüfung der Signalkerze, verworfene Punkte. |
| Darstellung im Bild | Beide Linien mit Berührungskreisen, Beginn des Keils markiert, Ziel und Stop gestrichelt, verworfene Dochte durchgestrichen. |
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
