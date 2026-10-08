# Notfallplan: Ausfall bei offenen Positionen

Stand 08.10.2026. Gilt für den Paper-Bot (kein echtes Geld). Zeiten in deutscher Zeit, New York in Klammern.
Zurück zum [Fahrplan](../FAHRPLAN.md).

## Was immer schützt, auch ohne Bot

Diese Teile liegen beim Broker und arbeiten weiter, wenn der Bot ausfällt:

- **Stop und Ziel jeder Position** liegen als ruhende Orders beim Broker. Sie sind Teil der Bracket-Order und gelten
  bis auf Widerruf, also auch über Nacht.
- **Eine Einstiegs-Order, die noch nicht gefüllt ist**, gilt ebenfalls bis auf Widerruf. Normalerweise storniert der
  Bot sie nach 45 Sekunden. Fällt er genau in diesem Moment aus, kann sie später noch füllen. Stop und Ziel sind
  dann sofort aktiv.

## Was der Bot bei jedem Durchgang und nach jedem Neustart prüft

- **Abgleich Broker gegen Bot:**
  - Eine Position, die beim Broker liegt, aber keinen Trade im Bot hat (Waise), meldet der Bot. Bei offener Börse
    schließt er sie.
  - Eine bekannte Position ohne lebende Stop- und Ziel-Order bekommt neue Schutz-Orders. Das geht auch bei
    geschlossener Börse; sie warten dann auf die Eröffnung.
- **Broker nicht lesbar:** keine neuen Einstiege, bis der Abgleich wieder klappt.
- **Tagesverlust-Stopp:** Ab 3 % Verlust am Tag gibt es keine neuen Einstiege.

## Was bei einem Ausfall fehlt

- **Break-even und Nachziehen des Stops.** Der Stop bleibt auf dem ursprünglichen Niveau.
- **Zeit-Stop** nach 120 bzw. 240 Minuten.
- **Glattstellung zum Tagesende** um 21:50 (15:50 New York). Die Position bleibt über Nacht offen, mit Stop und Ziel.
- **Alarme per Telegram.**

**Achtung über Nacht:**
- Stops lösen nur in der regulären Handelszeit aus.
- Öffnet die Aktie am nächsten Morgen mit einer Kurslücke hinter dem Stop, wird zum Eröffnungskurs ausgeführt, also
  schlechter als zum Stop.

## Szenarien

**Strom weg am Pi**
- Der Pi startet nach Rückkehr des Stroms von selbst, der Bot-Dienst ebenfalls.
- Beim Start gleicht der Bot ab (siehe oben) und verwaltet danach weiter.
- Ist auch der Router ohne Strom, gilt zusätzlich „Internet weg“.

**Internet weg**
- Der Bot erreicht weder Broker noch Kursdaten.
- Stop und Ziel beim Broker arbeiten weiter.
- Der Bot versucht es weiter und gleicht nach der Rückkehr ab.
- Ist die Verbindung um 21:50 (15:50 New York) noch nicht zurück, bleiben die Positionen über Nacht offen, mit Stop.

**Broker-Schnittstelle gestört**
- Weder Bot noch App können Orders ändern.
- Was beim Broker liegt, gilt weiter, sofern der Broker selbst läuft.
- Störungen zeigt die Statusseite des Brokers.

**Bot abgestürzt oder Pi hängt**
- Nach einem Absturz startet systemd den Bot neu.
- Hängt der ganze Pi, den Strom kurz trennen, wenn möglich erst nach 22:00 (16:00 New York).

**Telegram gestört**
- Der Bot handelt normal weiter, es fehlen nur die Nachrichten.
- Ob er lebt, zeigt der Herzschlag auf der Webseite.

**GitHub gestört**
- Die Webseite zeigt alte Daten.
- Der Bot handelt normal weiter.

## Wie merke ich einen Ausfall?

- **Webseite:**
  - Oben steht „Bot läuft“ mit grünem Punkt.
  - Ist der letzte Herzschlag älter als 25 Minuten, steht dort „Bot still seit …“.
- **Telegram:**
  - Um 15:30 (09:30 New York) kommt die Start-Nachricht.
  - Um 21:50 (15:50 New York) kommt „Broker ist flach ✅“.
  - Fehlt eine davon, nachsehen.
- **Schreibtisch-Anzeige:** zeigt dieselben Daten wie die Webseite.

## Handgriffe, in dieser Reihenfolge

1. **Webseite öffnen:** Lebt der Bot? Sind Positionen offen?
2. **Broker-App öffnen** (Paper-Konto):
   - Positionen und offene Orders ansehen.
   - Hat jede Position einen Stop?
3. **Soll nichts über Nacht offen bleiben,** vor 22:00 (16:00 New York) handeln:
   - alle Positionen schließen („Close all positions“; das storniert auch ihre Orders);
   - oder nur die eine Position schließen.
4. **Kommt der Bot nicht von selbst zurück,** den Pi neu starten (Strom kurz trennen).
5. **Nach dem Neustart prüfen:**
   - Die Start-Nachricht kommt.
   - Der Abgleich zeigt keine Waise und keinen offenen Alarm.
   - Im Zweifel den Abgleich von VS Code prüfen lassen.
6. **Ausfall ins Tageslog schreiben:** was, wann, wie lange, welche Wirkung.

## Was man nicht tun sollte

- **Keinen zweiten Bot starten,** auch nicht „zur Sicherheit“ auf einem anderen Rechner. Nie zwei Instanzen auf einem
  Konto.
- **Den alten Bot-Rechner nicht einschalten,** solange sein Bot-Dienst nicht abgeschaltet ist.
- **Keine Orders von Hand anlegen, während der Bot läuft.**
  - Ausnahme: Glattstellen im Notfall.
  - Danach meldet der Bot eine Abweichung; das ist gewollt.
