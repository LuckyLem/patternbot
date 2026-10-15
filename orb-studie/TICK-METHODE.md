# ORB-Studie · Tick-Methode für die Neuberechnung von Jahr 1

Festgelegt am 15.10.2026, **bevor** neu gerechnet wird. Freigabe des Inhabers vom 09.10. und 15.10.

## Warum

In der ersten Rechnung (Commit 98def9a7) wurden 594 von 973 Trades schon in ihrer Einstiegsminute gestoppt. Grund ist
Vorab-Regel 7: „Erreicht die Einstiegsminute auch den Stop, zählt der Stop (vorsichtig gerechnet).“

Bei einem Ausbruch liegt das Tief (long) bzw. das Hoch (short) der Einstiegsminute aber meist **vor** dem Fill. Ob
der Stop nach dem Fill erreicht wurde, entscheiden nur die einzelnen Abschlüsse (Ticks). Das ist eine Frage des
Simulators.

**Die Handelsregeln aus `VORAB-REGELN.md` (Commit d48250c2) bleiben unverändert**: Auswahl, Richtung, Kante, Stop von
10 % ATR, Ausstieg um 15:50, Kosten, Varianten und Zufallsvergleich. Beide Ergebnisse kommen ins Protokoll. Es gibt
kein Jahr 2.

## Daten und Filter

- SIP-Abschlüsse (Ticks) je ausgewählter Aktie und Tag, von 09:30 bis 12:00 New York.
  - Damit sind die Einstiege vor 12:00 abgedeckt (erste Rechnung: 931 von 973) und die meisten Stopps, die bei 10 %
    ATR meist kurz nach dem Einstieg kommen.
  - Für Einstiege ab 12:00 werden die Ticks der Einstiegsstunde und der Stunde danach geladen.
- **Filter wie beim Simulatorfix vom 05.10.:** Es zählen nur Abschlüsse, deren Kurs innerhalb der offiziellen
  SIP-Minutenkerze ihrer Minute liegt (zwischen Tief und Hoch). Minuten ohne offizielle Kerze fallen weg. So zählen
  keine Fehlkurse, wie ELV am 20.10.2025 (1 Aktie zu 310 bei Markt 352).
- Die Reihenfolge ist die Zeitreihenfolge der Abschlüsse. Bei gleicher Zeit gilt die Reihenfolge der Lieferung.

## Ablauf eines Trades

1. **Einstieg:**
   - Die Stop-Order an der Kante gilt ab 09:35 bis 15:30, wie in den Vorab-Regeln.
   - Gefüllt wird beim ersten gefilterten Abschluss mit Kurs ≥ Kante (long) bzw. ≤ Kante (short).
   - **Füllkurs = Kurs dieses Abschlusses.** Öffnet eine Minute schon jenseits der Kante, ist das ihr erster
     Abschluss.
2. **Stop:**
   - Der Stop liegt 10 % ATR vom Füllkurs entfernt, wie bisher.
   - Er löst beim ersten gefilterten Abschluss **nach** dem Fill aus, mit Kurs ≤ Stop (long) bzw. ≥ Stop (short).
   - **Er füllt zum Kurs dieses auslösenden Abschlusses, nicht zum Stopkurs.** Eine Kurslücke kostet also echt.
3. **Ausstieg um 15:50:** zum Eröffnungskurs der Minute 15:50 (offizielle Minutenkerze), wie bisher.
4. **Außerhalb der geladenen Ticks:** Ist bis zum Ende der Tick-Daten kein Stop gefallen, geht es auf Minutenkerzen
   weiter.
   - Eine Minute, die den Stop erreicht, beendet den Trade zum Stopkurs, oder zur Eröffnung der Minute, wenn sie
     schon jenseits davon öffnet.
   - Der Bericht nennt, wie viele Trades und Zufallstrades das betrifft.
5. **Kosten:** dasselbe Kostenmodell, je Trade der höhere Wert aus 0,03R long bzw. 0,05R short und der Slippage.
   Slippage = 2 × max(0,01 $; 0,02 % vom Kurs) je Aktie, geteilt durch den Stop-Abstand.

## Zufallsvergleich

- Dieselben 100 Läufe mit demselben Startwert 20261005 und denselben Ziehungen wie in der ersten Rechnung:
  - gleiche Aktie, gleicher Tag und gleiche Stunde wie der echte Einstieg;
  - gleiche geloste Minute und Richtung;
  - gleicher Stop-Abstand in Prozent.
- Einstieg beim ersten gefilterten Abschluss der gelosten Minute.
- Stop, Ausstieg, Ausweichen auf Minutenkerzen und Kosten genau wie oben, **mit demselben Tick-Filter**.

## Bericht

- Die fünf Kriterien der Hauptvariante, wie in der ersten Rechnung.
- Zusätzlich:
  - Trefferquote;
  - längste Verlustserie;
  - Ergebnis geteilt durch Drawdown;
  - Anzahl der Stopps in der Einstiegsminute;
  - Anteil der Trades auf Minutenkerzen-Ersatz.
- Die Nachbarwerte (OR 15/30, Stop 5/20 %, Top 10/20) laufen nach derselben Methode, nur als Information.
- Simulator- und ORB-Code-Hash, Datenstand, Überlebensverzerrung wie gehabt.
- Danach Stopp bis zum OK des Inhabers. **Kein Jahr 2.**
