# Auftrag: Lernhub v3 online stellen und Runde doppelboden-1 starten

Kurz: Die neue Seite kommt auf main, danach geht die Sichtprüfung Doppelboden live.
An der Erkennung und an den Regeln änderst du nichts.

## Feste Regeln (unverändert)

- Nur Paper. Keine Live-Freigabe. Risiko, Positionen und Wertgrenze bleiben, wie sie sind.
- Bot-Code kommt nicht auf GitHub. Das Repo bleibt reines Dashboard.
- Öffentliche Dateien enthalten keine IP-Adressen, Hostnamen, Benutzernamen, Pfade, Schlüssel oder Kontonummern.
- Niemals force-push.
- Der Prüftopf ab 01.10.2023 bleibt zu.
- Der Nutzer hat diesen Auftrag freigegeben. Das gilt auch für die Änderung auf main in Schritt 1.

## Schritt 1: Seite auf main

1. Hole den Branch `claude/epic-gates-iz9swg` (Commit `7ade3ab` oder neuer).
2. Kopiere `lernhub/vorlage/lernhub.html` von dort nach main als `labor.html`.
3. Prüfe vor dem Commit, dass die Zeile `<script src="labor-name.js"></script>` drin ist und `labor-name.js` auf main liegt.
4. Commit auf main mit kurzer Nachricht ("Lernhub v3"), dann push.
5. Sonst änderst du nichts auf main.

Was neu ist:

- Die Sichtprüfung kann vier Arten:
  - präzision: Linien richtig?
  - trefferquote: Muster am Tag?
  - einstieg: Einstieg nach Regel?
  - verlust: Knöpfe aus `optionen`.
- W-Form, Nackenlinie und Boden-Band werden gezeichnet. Tageskerzen haben eine Datumsachse.
- Muster-Tabs: Doppelboden und Rechteck.
- Einstiege heißen Ausbruch, Retest, Früher Einstieg und Fehlschlag.
- Ausgänge (Ziel, Stop, Tagesende) gibt es je Variante und als Filter.
- Neue Abschnitte: Analyse (`analyse-*.json`) und Ideen-Register (`ideen-register.json`).

## Schritt 2: Daten auf dem Branch backtest

1. Sichere die aktuelle `lernhub/daten/sichtpruefung.json` unter ihrer `id` als eigene Datei, falls das noch nicht passiert ist. Die Runde Trefferquote ist ausgewertet: ja 8, nein 20, unsicher 2.
2. Kopiere `lernhub/daten/doppelboden-1.json` nach `lernhub/daten/sichtpruefung.json`. Ändere den Inhalt nicht.
3. Lege `lernhub/daten/analysen.json` an:
   ```json
   {"dateien": ["analyse-rechteck-v1.json"]}
   ```
   Kommen später weitere Analysen dazu, trägst du sie dort ein.
4. Commit auf backtest, dann push.
5. `einstieg-1.json` und `verlust-1.json` bleiben liegen. Sie kommen erst nach dieser Runde dran, in dieser Reihenfolge.

## Schritt 3: Prüfen

Öffne `labor.html` auf GitHub Pages, nachdem die Seite neu gebaut ist. Melde kurz:

- Kopfzeile:
  - "Versuche im Register 132";
  - "Sichtprüfung Doppelboden 0 von 30".
- Sichtprüfung: "Bild 1 von 30: Ist das ein sauberer Doppelboden?". Ein Klick auf das Bild öffnet das Chart-Fenster mit der W-Form.
- Abschnitt Analyse: Balken je Variante sind sichtbar.
- Abschnitt Ideen-Register: Tabelle ist sichtbar.
- Browser-Konsole: keine Fehler.

Danach STOPP. Der Nutzer macht die Runde allein.

## Merkpunkte für nach der Runde (jetzt nichts ändern)

- **B1 ist nicht immer der tiefste Punkt des Rückgangs.**
  - Die Regel verlangt nur "Rückgang mindestens 3 ATR in den 30 Kerzen vor B1".
  - In einigen Bildern liegt zwischen dem Vortrend-Hoch und B1 ein tieferes Tief. Dann ist B1 nur ein Zwischenboden.
  - Vorschlag für die nächste Fassung: Zwischen dem Vortrend-Hoch und B1 liegt kein Tief unter B1 (kleine Toleranz, etwa 0,1 ATR).
  - Wir entscheiden das zusammen mit den Antworten aus doppelboden-1.
- **5 Min liefert sehr viele W (34.006).** Das spricht dafür, dass die Regeln dort zu großzügig sind. Auch das prüfen wir mit den Antworten der Runde.
- Bis dahin gibt es keinen Lauf auf den Suchdaten (Phase 4).
