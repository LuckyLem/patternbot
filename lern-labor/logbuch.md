# Logbuch Lern-Labor

Hier steht jeder Zugriffstest, jeder Abschneide-Test, jede Vorab-Datei (mit Commit und SHA-256) und jede Öffnung
des Prüftopfs. Zeiten in New-York-Zeit, der neueste Eintrag steht unten. Einträge werden nie geändert oder gelöscht.

| Zeit (New York) | Art | Eintrag | Ergebnis |
|---|---|---|---|
| 2026-10-08 13:04 | Einrichtung | Logbuch und Prüftopf-Logbuch angelegt. Prüftopf 01.10.2023–30.09.2026: 0 von 3 Öffnungen. | – |
| 2026-10-08 13:04 | Abschneide-Test | Feste Funktion angelegt (Code-Hash Labor e52378c6f0cd). Selbsttest auf künstlichen 15-Min-Kerzen, 80 Zeitpunkte: 4 Merkmale ohne Zukunftsdaten identisch; 4 absichtlich undichte Merkmale (zentrierter Durchschnitt, Normierung über alle Daten, Kurs der nächsten Kerze, Rückwärts-Auffüllen) alle als Leck erkannt. | bestanden |
| 2026-10-08 13:04 | Lernzeit-Wächter | Rechnet in New-York-Zeit mit dem NYSE-Kalender: Handelstage 16:30–09:00, Wochenende und Feiertage durchgehend. 17 Prüfungen grün, darunter Halbtage 27.11. und 24.12., Thanksgiving, Weihnachten und die Zeitumstellung 25.10.–01.11. (Start dann 21:30 deutscher Zeit). | bestanden |
| 2026-10-08 16:57 | Messung | Tagestrend SIP gegen IEX (147 Werte, 03.08.2020–29.09.2023, Funktion des Bots, unbereinigte Tageskerzen): bei vollen 120 Kerzen weichen 459 von 100.107 Entscheidungen ab (0,46 %; 2021 0,55 %, 2022 0,53 %, 2023 0,24 %). Unter 1 %: SIP-Vorlauf, der Suchtopf bleibt ab 01.10.2020. Aufwärmphase mit Vorlauf 0,28 % gegen das volle SIP-Fenster, ohne Vorlauf 3,32 %. Bericht: messungen/trend_sip_iex.md | – |
