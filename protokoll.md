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

