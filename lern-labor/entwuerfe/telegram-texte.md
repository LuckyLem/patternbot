# Entwurf: Telegram-Texte des Lern-Labors

Stand 08.10.2026.

**Grundsätze:**
- Eigener Bot, getrennt vom Handels-Bot.
- Zeiten in deutscher Zeit, New York in Klammern.
- Platzhalter stehen in {geschweiften Klammern}. Echte Werte kommen nur aus dem Lauf, nichts wird geschätzt.
- Jede Nachricht läuft vor dem Senden durch denselben Prüfer wie die öffentlichen Dateien. Nie Schlüssel, Tokens,
  Kontodaten, IP-Adressen oder Pfade.

## Lernen startet

```
🧪 Lern-Labor startet · {Wochentag} {Datum} {Zeit} ({Zeit NY} New York)
Job: {Job} · Stand {Fortschritt} %
Stopp spätestens {Wochentag} {Zeit} ({Zeit NY} New York)
```

## Lernen stoppt (regulär)

```
🧪 Lern-Labor pausiert · {Zeit} ({Zeit NY} New York)
{Job}: Zwischenstand gesichert bei {Fortschritt} %
Weiter ab {Wochentag} {Zeit} ({Zeit NY} New York)
```

## Nachts eine kurze Bilanz (morgens vor dem Stopp)

```
🌙 Nachtbilanz Lern-Labor · Nacht auf {Wochentag} {Datum}
Gerechnet: {Dauer} · {Job}: {Fortschritt vorher} % → {Fortschritt nachher} %
Schatten: {Anzahl Modelle} Modelle, {Anzahl Muster} Muster · {Trades} Schatten-Trades, {R} nach Kosten
Logbuch: {neue Einträge oder „nichts Neues“}
```

Die Schatten-Zeile gibt es erst ab Etappe 4.

## Wochenbericht (am Wochenende)

```
📊 Wochenbericht Lern-Labor · KW {Woche}
Etappe {Nr}: {erledigt}/{gesamt} Punkte · als Nächstes: {Schritt}
Schatten je Modell: {Zeilen: Name · Trades · Erwartung · Drawdown · Markierung}
Prüftopf: {Öffnungen} von 3 geöffnet
Bericht: {Datei auf dem Branch backtest}
```

## Alarme

```
⛔ Lernjob nicht beendet: {Job} lief um 09:00 New York noch. Hart gestoppt, Zwischenstand vom {Zeit}.
⛔ Speicher knapp: nur {frei} GB frei (Grenze 5 GB). Labor gestoppt, der Bot läuft weiter.
⛔ Labor-Ordner voll: {belegt} von {Grenze} GB. Labor gestoppt.
⛔ Fehler in {Job}: {Kurzbeschreibung}. Zwischenstand gesichert, nächster Versuch {Zeit}.
⛔ Abschneide-Test nicht bestanden: Datenleck in {Merkmale}. Lauf gesperrt, Eintrag im Logbuch.
⛔ Zugriffstest fehlgeschlagen: Das Labor konnte {was} lesen. Labor gesperrt, bis die Isolation stimmt.
```

## Abends „Heute geschafft / Morgen dran“

```
🗓 {Wochentag} {Datum}
Heute geschafft:
• {Punkt}
Morgen dran:
• {Punkt}
```

Die Punkte kommen aus dem Tageslog in FAHRPLAN.md, damit Webseite, Fahrplan und Nachricht immer dasselbe sagen.
