# Protokoll der Backtest-Runden

Wird nur ergänzt, nie geändert.

## Kalibrierung · 2026-09-21 bis 2026-10-02 · 03.10.2026 12:01
- Ergebnis: 11/11 echte Orders im Replay, 0 zusätzliche, Entscheidungen 659/659 gleich (100.0 %), Ausstiege ≤ 0,1R: neue Version 9/9, alte Version 42/46, abgefangene Fehler 0. Fill-Preis der eigenen Einstiege +0.000R bis +0.001R.
- **Bestanden** – Entscheidung des Nutzers 03.10.: als erklärt gelten t24 PLD (Glattstellung 15:50 statt 15:51 (alte Version)); t33 NSC (bekannter Fehler der alten Version (NSC-Waise)); t41 NSC (bekannter Fehler der alten Version (NSC-Mischposition)); t44 ROP (Glattstellung 15:50 statt 15:51 (alte Version)).
- Ziel-Limits wie Paper: 1 Ziel(e) wären nur nach „durchgehandelt“ gefüllt worden (+0.42R).
- Simulator-Korrekturen vor dem Bestehen:
  1. Letzter Kurs wie Alpacas /trades/latest: ohne Odd Lots (Bedingung I). Vorher: 9 skip-stale-Abweichungen und CRM 30.09. Jetzt 62 von 62 Live-Kursabfragen exakt (Preis und Alter).
  2. Moment der Kursabfrage: geloggter Prüfbeginn + 0,14 s, ältere Zeilen: Zeitstempel minus gemessene Verzögerung je Entscheidung. Vorher: Zeitstempel der Zeile (bei Orders 0,5 s zu spät).
  3. Die simulierte Uhr läuft im Suchlauf mit. Vorher stand sie: Kursalter zu klein (PCAR 44 statt 64 s), Orders zu früh gesendet.
  4. Einstieg wie Paper: Ankunft 0,26 s nach der Kursabfrage; sofort ausführbar -> Geld-/Briefkurs bei Ankunft, sonst nur wenn durchgehandelt. Vorher: erster Trade im Limit, im Mittel 0,01-0,05R zu günstig.
  5. Glattstellung wie Paper: Geld-/Briefkurs bei Ankunft. Vorher: nächster Trade.
  6. Ziel-Limit wie Paper (Vorgabe des Nutzers 03.10.): Verkauf erst, wenn das Bid das Ziel erreicht, Rückkauf erst, wenn das Ask es erreicht. Vorher: durchgehandelt (VRTX t10 +0,42R).
  7. Testaufbau: jede Rechnung mit frischer Replay-DB; Uhr in ganzen Mikrosekunden (ein Nanosekunden-Rest ließ jeden Scan still scheitern); abgefangene Ausnahmen der Live-Schleife machen ein Replay ungültig.
- Code: Simulator und Auswertung `bt/` sha256 `b5029434d8ae`; Bot-Code `cbfe06cff` (lokale Arbeitskopie inkl. Technik-Paket, Entscheidungslogik wie live); Regeln je Tag aus dem Änderungsprotokoll.

## Kalibrierung · 2026-09-21 bis 2026-10-02 · 03.10.2026 17:09
- Ergebnis: 11/11 echte Orders im Replay, 0 zusätzliche, Entscheidungen 659/659 gleich (100.0 %), Ausstiege ≤ 0,1R: neue Version 9/9, alte Version 42/46, abgefangene Fehler 0. Fill-Preis der eigenen Einstiege +0.000R bis +0.001R.
- **Bestanden** – Entscheidung des Nutzers 03.10.: als erklärt gelten t24 PLD (Glattstellung 15:50 statt 15:51 (alte Version)); t33 NSC (bekannter Fehler der alten Version (NSC-Waise)); t41 NSC (bekannter Fehler der alten Version (NSC-Mischposition)); t44 ROP (Glattstellung 15:50 statt 15:51 (alte Version)).
- Ziel-Limits wie Paper: 1 Ziel(e) wären nur nach „durchgehandelt“ gefüllt worden (+0.42R).
- Simulator-Korrekturen vor dem Bestehen:
  1. Letzter Kurs wie Alpacas /trades/latest: ohne Odd Lots (Bedingung I). Vorher: 9 skip-stale-Abweichungen und CRM 30.09. Jetzt 62 von 62 Live-Kursabfragen exakt (Preis und Alter).
  2. Moment der Kursabfrage: geloggter Prüfbeginn + 0,14 s, ältere Zeilen: Zeitstempel minus gemessene Verzögerung je Entscheidung. Vorher: Zeitstempel der Zeile (bei Orders 0,5 s zu spät).
  3. Die simulierte Uhr läuft im Suchlauf mit. Vorher stand sie: Kursalter zu klein (PCAR 44 statt 64 s), Orders zu früh gesendet.
  4. Einstieg wie Paper: Ankunft 0,26 s nach der Kursabfrage; sofort ausführbar -> Geld-/Briefkurs bei Ankunft, sonst nur wenn durchgehandelt. Vorher: erster Trade im Limit, im Mittel 0,01-0,05R zu günstig.
  5. Glattstellung wie Paper: Geld-/Briefkurs bei Ankunft. Vorher: nächster Trade.
  6. Ziel-Limit wie Paper (Vorgabe des Nutzers 03.10.): Verkauf erst, wenn das Bid das Ziel erreicht, Rückkauf erst, wenn das Ask es erreicht. Vorher: durchgehandelt (VRTX t10 +0,42R).
  7. Testaufbau: jede Rechnung mit frischer Replay-DB; Uhr in ganzen Mikrosekunden (ein Nanosekunden-Rest ließ jeden Scan still scheitern); abgefangene Ausnahmen der Live-Schleife machen ein Replay ungültig.
  8. Symbolschreibweise wie Alpaca (gefunden im ersten Versuch von Runde 1): BRK-B aus dem Universum heißt beim Broker BRK.B. Vorher fand der Live-Code die Position nicht, buchte den Trade als 'unresolved' (0 $) und schloss die Position als Waise (24.06.2026).
  9. Testaufbau und Auswertung (03.10., ändert keine Rechnung): Abrufpause nur an NYSE-Handelstagen 15:30-22:00 (Vorgabe des Nutzers); Zufallsläufe je Trade, Tagesverlauf, Stops mit Kurslücke.
- Code: Simulator und Auswertung `bt/` sha256 `ea1111c0fedf`; Bot-Code `cbfe06cff` (lokale Arbeitskopie inkl. Technik-Paket, Entscheidungslogik wie live); Regeln je Tag aus dem Änderungsprotokoll.

## Runde 1 · Jahr 2025-10-01..2026-09-30 · 03.10.2026 21:44
- Regel-Version: {'chase_anchor': 'close', 'universe_exclude': 'BK,MMC,FI'} (sonst wie live)
- Ergebnis beim ersten Rechnen (Hauptlauf V1 an, zählt): 1007 Trades · Erwartungswert n.K. -0.089R · PF 0.67 · max. DD 96.33R · Zufall 25/100 · Ziel nein
- 01.10.2025 bis 23.08.2026 (Information): 908 Trades · Erwartungswert n.K. -0.099R · PF 0.63 · max. DD 96.33R · Zufall 11/100 · Ziel nein
- Vergleichslauf V1 aus (Information): 547 Trades · Erwartungswert n.K. -0.089R · PF 0.64 · Zufall 5/100
- Ziel-Limits wie Paper: 2 Ziel(e) wären nur nach „durchgehandelt“ gefüllt worden (+4.33R). Stops mit Kurslücke: 10 von 112 (-28.28R).
- Code: Simulator und Auswertung `bt/` sha256 `ea1111c0fedf`; Bot-Code `cbfe06cff`.
- Hinweis: Erster Versuch (03.10., Start 12:02) endete um 14:53 ohne Ergebnis: Der Prozess wurde mit einem Neustart der Sitzung beendet, keine Kennzahlen gesehen. Dabei fiel ein Simulatorfehler auf (BRK-B/BRK.B, 1 Trade als 'unresolved' gebucht). Behoben, neu kalibriert (Simulator ea1111c0fedf), Runde mit unveränderten Regeln neu gestartet.
- Beschlossene Korrekturen: (offen – erst nach OK des Nutzers)

