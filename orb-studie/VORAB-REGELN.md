# ORB-Studie: Opening-Range-Breakout auf „Aktien im Spiel“ – vorab festgelegte Regeln

Festgelegt am 05.10.2026, **bevor ein einziger Test gerechnet wurde**. Nach dem Blick auf Ergebnisse wird an diesen
Regeln nichts mehr geändert. Neue Ideen sind neue Hypothesen und brauchen ein frisches Jahr.

## Hypothese und Quelle

Zarattini, Barbon, Aziz (2024): *A Profitable Day Trading Strategy For The U.S. Equity Market* (SSRN 4729284).
Die Studie umfasst 2016–2023 und rund 7.000 US-Aktien. Die Regeln unten folgen ihren Abschnitten 2.1 und 4.
Ergebnisse der Studie:

| Variante | Ergebnis |
|---|---|
| ORB auf allen Aktien | schwach: 29 % in 8 Jahren, Sharpe 0,48 |
| Relatives Volumen ≥ 100 % | +0,08R je Trade nach Provision, **ohne Slippage** |
| Top 20 nach relativem Volumen | +1.637 %, Sharpe 2,81 |

Unser Test liegt komplett **nach der Veröffentlichung** (Feb. 2024). Er ist damit eine echte Prüfung außerhalb der
Stichprobe.

## Die Regeln (Hauptvariante – nur sie zählt)

1. **Universum:** die 1.500 Werte der bestehenden Liste (`universe_us_1500.csv`). Davon kommen an jedem Tag nur
   Werte in Frage, die diese Bedingungen erfüllen (alles aus Vortagen, ohne Rückschau):
   - Eröffnungskurs über 5 $,
   - Durchschnittsvolumen der letzten 14 Tage mindestens 1.000.000 Aktien,
   - ATR der letzten 14 Tage über 0,50 $. Die ATR ist der Mittelwert der „True Range“ der 14 Vortage.
2. **Relatives Volumen (RV):** Volumen der ersten 5 Minuten (09:30–09:35 New York) geteilt durch den Durchschnitt
   der ersten 5 Minuten der 14 Vortage. In Frage kommt nur, wer **RV ≥ 1,0** hat.
3. **Auswahl:** Die **5 Werte mit dem höchsten RV** werden gehandelt. Das entspricht unserer Live-Grenze von
   höchstens 5 Positionen. Die Studie nahm 20; das rechnen wir nur als Information mit.
4. **Richtung:** Schließt die erste 5-Minuten-Kerze über ihrer Eröffnung, wird nur long gehandelt, schließt sie
   darunter, nur short. Bei gleichem Eröffnungs- und Schlusskurs (Doji) gibt es keinen Trade.
5. **Einstieg:** Stop-Order am Hoch (long) bzw. Tief (short) der ersten 5 Minuten. Sie gilt ab 09:35 und bis
   15:30, unserer Live-Grenze für neue Einstiege. Gefüllt wird in der ersten Minute, die die Marke erreicht. Öffnet
   die Minute schon jenseits der Marke, wird zu ihrem Eröffnungskurs gefüllt.
6. **Stop:** 10 % der 14-Tage-ATR vom tatsächlichen Einstiegskurs entfernt. Das ist 1R.
7. **Ausstieg:** am Stop. Wird er nicht erreicht, um 15:50 zum Eröffnungskurs der Minute 15:50. Das entspricht
   unserer Live-Glattstellung, die Studie stellte erst um 16:00 glatt.
   - Erreicht die Einstiegsminute auch den Stop, zählt der Stop (vorsichtig gerechnet).
   - Öffnet eine Minute jenseits des Stops, wird zum Eröffnungskurs gefüllt (Kurslücke).
8. **Kosten je Trade:** der höhere von zwei Werten:
   - unsere festen Kosten (0,03R long, 0,05R short),
   - die Slippage in R: je Seite max(0,01 $; 0,02 % vom Kurs) je Aktie, Ein- und Ausstieg zusammen, geteilt durch
     den Stop-Abstand je Aktie.

   Bei so engen Stops kann das deutlich über 0,05R liegen. Das ist Absicht: Die Studie rechnete ohne Slippage.
9. **Positionsgröße** (nur für die $-Angaben): 0,5 % Risiko je Trade und höchstens 20 % des Kapitals je Position,
   wie live. Die Kriterien selbst werden in R gemessen.

## Erfolgskriterien (dieselben wie bisher, fest)

- mindestens 200 Trades,
- Erwartungswert nach Kosten mindestens +0,10R,
- Profitfaktor mindestens 1,3,
- maximaler Drawdown höchstens 15R,
- besser als mindestens 95 von 100 Zufallsläufen.

**Zufallsvergleich:** Jeder Zufallstrade nimmt dieselbe Aktie am selben Tag. Er steigt in einer zufälligen Minute
derselben Stunde zum Minuten-Eröffnungskurs ein, die Richtung wird gelost. Stop-Abstand in Prozent, Ausstieg und
Kosten sind dieselben wie beim echten Trade. Gerechnet werden 100 Läufe mit festem Startwert 20261005.

## Nachbarwerte (nur Information, keine Auswahl)

Nach unserer Spielregel ist ein Wert nur gut, wenn auch die Nachbarwerte gut sind. Ausgewiesen, aber nicht
ausgewählt, werden deshalb:
- Opening Range 15 und 30 Minuten (Richtung und Marke aus diesem Zeitraum),
- Stop bei 5 % und 20 % der ATR,
- Top 10 und Top 20.

Es zählt nur die Hauptvariante: 5 Minuten, 10 % ATR, Top 5.

## Ablauf

1. **Jahr 1:** 01.10.2025–30.09.2026. Danach Bericht und **Stopp bis zum OK** des Nutzers.
2. **Jahr 2, frisch:** 01.10.2024–30.09.2025, mit **unveränderten** Regeln.
3. Live kommt erst in Frage, wenn beide Jahre alle Kriterien erfüllen. Dann folgen der Einbau in den Bot, eine
   Kalibrierung gegen Paper und die Entscheidung des Nutzers. Die heutige Sperre in den ersten 20 Minuten nach der
   Eröffnung müsste für diese Strategie fallen.

## Daten und was nicht nachstellbar ist

- **Daten:** SIP-Kerzen (alle Börsen) zu 5 Minuten, 1 Minute und Tagen, split-bereinigt. Börsenkalender NYSE.
  Downloads laufen nur außerhalb der Handelszeit, gedrosselt und mit derselben harten Sperre (nur Marktdaten, kein
  Trading).
- **Nicht nachstellbar oder vereinfacht:**
  - Das Universum ist die heutige Liste mit 1.500 Werten. Das bringt eine Überlebensverzerrung; die Studie nutzte
    rund 7.000 Werte ohne diese Verzerrung.
  - Es gibt keine Nachrichtendaten. Das relative Volumen dient als Ersatz, wie in der Studie.
  - Ob eine Aktie leerverkauft werden kann (schwer leihbare Werte), ist nicht modelliert.
  - Fills auf Minutenkerzen statt Ticks.
  - Live würde der Bot heute IEX-Daten sehen. Das klärt eine spätere Kalibrierung.
