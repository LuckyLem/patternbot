# Auftrag: Lernhub mit Muster-Mappen online stellen

Kurz: Die Seite ordnet jetzt alles nach Mustern. Jedes Muster hat eine Mappe zum Auf- und Zuklappen. Darin stehen:

- Läufe;
- Prüfungen;
- was das Muster ist;
- wie der Bot es liest;
- Einstiege long und short.

Die Trades sind erst zu sehen, wenn man einen Lauf auswählt. Dafür kommen zwei neue Datendateien dazu. An Erkennung, Regeln und Bot änderst du nichts.

## Feste Regeln (unverändert)

- Nur Paper. Keine Live-Freigabe.
- Bot-Code kommt nicht auf GitHub.
- Öffentliche Dateien enthalten keine IP-Adressen, Hostnamen, Benutzernamen, Pfade, Schlüssel oder Kontonummern.
- Niemals force-push. Der Prüftopf ab 01.10.2023 bleibt zu.
- Der Nutzer hat diesen Auftrag freigegeben, auch die Änderung auf main in Schritt 1.

## Schritt 1: Seite auf main

1. Hole den Branch `claude/epic-gates-iz9swg` (neuester Commit).
2. Kopiere `lernhub/vorlage/lernhub.html` nach main als `labor.html`. Die Zeile `<script src="labor-name.js"></script>` bleibt drin.
3. Commit auf main ("Lernhub: Muster-Mappen"), dann push.
4. Die laufende Runde doppelboden-1 geht dabei nicht verloren. Die Antworten liegen im Browser unter demselben Schlüssel wie vorher.

## Schritt 2: Daten auf dem Branch backtest

1. Kopiere vom Branch `claude/epic-gates-iz9swg` nach `lernhub/daten/`:
   - `lernhub/vorlage/daten/laeufe.json`;
   - `lernhub/vorlage/daten/pruefungen.json`.
2. Prüfe `pruefungen.json` gegen dein Logbuch:
   - Bei Rechteck Runde 1 und Runde 4 kenne ich nur die Zahl der Ja-Antworten. Der Rest steht als `"andere"` (nicht ja).
   - Steht die Aufteilung in nein und unsicher im Logbuch, ersetze `"andere"` durch `"nein"` und `"unsicher"`.
   - Sonst bleibt es so. Nichts schätzen.
3. `analysen.json` wird nicht mehr gebraucht. Sie darf liegen bleiben.
4. Commit auf backtest, dann push.

## Ab jetzt bei jeder Runde und jedem Lauf

- **Nach jeder Sichtprüfung:**
  - Trage das Ergebnis in `pruefungen.json` ein: `ja`, `nein`, `unsicher`, `status` und `ergebnis` (ein Satz).
  - Werte für `status`: `bestanden`, `nicht bestanden`, `ausgewertet`, `bereit` oder `läuft`.
  - Eine neue Runde bekommt einen eigenen Eintrag mit `muster`, `art`, `datum`, `bilder` und `status: "bereit"` oder `"läuft"`.
- **Nach jedem Lauf:**
  - Neuer Eintrag in `laeufe.json`:
    - `id`, `muster`, `name`, `register` (Kennung im Ideen-Register), `datum`, `daten`, `zeitebenen`;
    - `trades`, `status`, `ergebnis`;
    - `dateien` mit `ergebnisse`, `trades` und `analyse`.
  - **Eigene Dateien je Lauf**, zum Beispiel:
    - `ergebnisse-doppelboden-v1.json`;
    - `trades-doppelboden-v1/index.json` mit den Teilen darunter;
    - `analyse-doppelboden-v1.json`.
  - Alte Lauf-Dateien bleiben unverändert stehen, damit man jeden Lauf später noch ansehen kann.
- **Trade-Index:**
  - Jede Gruppe braucht `zeitebene` (5, 15 oder 1440 für Tag) und `einstieg` (A–D).
  - Die Seite baut die Filter-Knöpfe daraus. Tageskerzen funktionieren damit ohne Änderung an der Seite.
- **Trades:**
  - Beim Doppelboden trägt jeder Trade `muster` ("Doppelboden" oder "Doppeltop") und `linien` wie in `doppelboden-1.json`.
  - `oben` ist die Nackenlinie, `unten` die Bodenlinie.

## Schritt 3: Prüfen und melden

Öffne `labor.html` auf GitHub Pages, nachdem die Seite neu gebaut ist. Melde kurz:

- **Abschnitt Muster:** Mappe Doppelboden ist offen, Mappe Rechteck zu.
- **Mappe Rechteck:**
  - Unter Läufe steht "Werkbank Rechteck v1" mit Knopf "Ansehen".
  - Ein Klick zeigt Ergebnis, „Warum?“ und Trades.
  - Vorher sind keine Trades zu sehen.
- **Prüfungen deines Auges:**
  - Rechteck zeigt 5 fertige und 2 bereite Runden.
  - Doppelboden zeigt Runde 1 als laufend.
- **Browser-Konsole:** keine Fehler.

Danach STOPP.
