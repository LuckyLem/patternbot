# V1-Woche 05.–09.10.2026 · Erklärung der zwei Abweichungen

Rechnung vom 17.10.2026 (Fahrplan 1.7). Gleiche Kriterien wie die Kalibrierung, Live-Datenbank als Kopie vom 17.10.
Der Bericht `bericht.md` bleibt unverändert: nach den festen Kriterien **nicht bestanden**, wegen genau zwei Fällen.
Am Simulator und an den Kriterien wurde nichts geändert. Ob die beiden Fälle als erklärt gelten, entscheidet der
Inhaber (wie am 03.10.).

| Kriterium | Ergebnis |
|---|---|
| echte Orders auch im Replay | 19 von 19 |
| zusätzliche Orders im Replay | 0 |
| gleiche Entscheidungen | 722 von 723 (99,9 %), 1 offen: KLAC |
| Ausstiege ≤ 0,1R | 18 von 19, 1 offen: TT t68 (−0,15R) |
| Fill-Preis der Einstiege | −0,036R bis +0,035R, Mittel −0,0035R |

## 1. KLAC 06.10. 10:30, Rechteck short: live geprüft (skip-spread), im Replay kein Setup

- Die 15-Min-Kerze ist in beiden Quellen gleich (O 199,965 · H 199,985 · L 197,44 · C 197,51 · V 40.752).
- Der Unterschied ist der **Tagestrend**. KLAC hatte am 12.06.2026 einen Split 1:10.
  - Der Live-Bot holt die Tageskerzen **unbereinigt** (`adjustment=raw`, 120 Tage).
  - Das Replay rechnet auf split-bereinigten Kerzen.
- Mit der Trendfunktion des Bots (`indicators.daily_trend`) und den Tageskerzen bis 05.10.:
  - unbereinigt: **down**;
  - bereinigt: **flat**.

  Der EMA50 enthält auf den unbereinigten Kerzen noch Kurse von vor dem Split (zehnfach höher). Darum liegt der
  Schlusskurs darunter.
- Ein Rechteck short braucht den Tagestrend „down“. Live wurde das Setup deshalb geprüft, im Replay nicht.
- Die Entscheidung blieb ohne Folgen: Live lehnte das Setup wegen des Spreads ab (skip-spread), es gab keine Order.

**Das ist ein Befund am Live-Bot, nicht am Simulator.** Nach einem Split ist der Tagestrend des Bots monatelang
verfälscht. Gezählt mit der Funktion und dem Fenster des Bots für alle 150 Werte, Okt. 2025 bis 16.10.2026:

| Wert | Split | Tage mit anderem Trend als bereinigt | Zeitraum | live / bereinigt |
|---|---|---|---|---|
| NFLX | 17.11.2025, 1:10 | 47 | 02.03.–05.05.2026 | down/up 29, down/flat 18 |
| NOW | 18.12.2025, 1:5 | 17 | 09.03.–11.06.2026 | down/flat 9, flat/up 6, down/up 2 |
| BKNG | 06.04.2026, 1:25 | 77 | 09.04.–14.09.2026 | down/up 51, down/flat 26 |
| KLAC | 12.06.2026, 1:10 | 45 | 15.06.–12.10.2026 | down/up 24, down/flat 20, flat/up 1 |

- Zusammen sind es 186 Symbol-Tage. Der Fehler zeigt fast immer „down“, das öffnet Shorts und sperrt Longs bei
  Fortsetzungsmustern.
- Seit dem 13.10. ist kein Wert mehr betroffen. Mit dem nächsten Split im Universum kommt der Fehler wieder.
- Die Jahresrunden rechnen bereinigt, also ohne diesen Fehler. An diesen Tagen weicht das Replay vom Live-Bot ab.
- Eine Korrektur ist Entscheidungslogik. Sie gehört nicht ins Ausgabe-Paket und kommt nur nach Test und mit dem OK
  des Inhabers. Live ist eingefroren.

## 2. TT t68 05.10., Long, Glattstellung zum Tagesende: −0,15R daneben

- **Zeitpunkt:**
  - Live hat um 15:50:43 New York glattgestellt (Fill 471,42). Der Verwaltungstakt läuft live alle 60 s ab dem
    Prozessstart.
  - Das Replay stellt um 15:50:02 glatt (Takt ab :00 + 2 s, Fill 471,00).

  Der Takt ist nicht nachstellbar; das steht schon in den Hinweisen des Berichts.
- **SIP-Geldkurs zum echten Zeitpunkt:**
  - 15:50:43,50 bis 15:50:43,94: 471,42, genau der echte Fill. Die Regel des Simulators „Glattstellung zum Geldkurs
    bei Ankunft“ trifft also exakt.
  - Um 15:50:01,5 fiel der Geldkurs kurz auf 470,26 und erholte sich bis 15:50:04 auf 471,01. Das Replay stellte in
    diesem Loch glatt.
- **Warum die automatische Erklärung „unerklärt“ schreibt:**
  - Sie liest den Geldkurs 2 s vor dem gemeldeten Fill. Das war 471,15, also −0,19R; die Grenze liegt bei 0,03R.
  - In diesen 2 s stieg der Geldkurs um 27 Cent.
  - Die Prüfung ist eine Näherung für den Moment der Ankunft. Geändert wird sie nicht, um den Fall nicht nachträglich
    passend zu machen.

## Einordnung

- Alle 19 Orders der Woche entstehen genau so im Replay. Keine Order kommt dazu, keine fehlt.
- Die beiden offenen Fälle haben eine benannte Ursache:
  - Datenbereinigung: Das ist ein Fehler des Live-Bots, das Replay rechnet richtig.
  - Verwaltungstakt: nicht nachstellbar.
- **Vorschlag:** beide Fälle als erklärt annehmen. Dann gilt die Kalibrierung auch für V1 (Anker am Schlusskurs).
