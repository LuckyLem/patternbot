# Messung: Tagestrend mit SIP- statt IEX-Tageskerzen

Stand 08.10.2026, 22:57. Grundlage für die Vorab-Datei von Etappe 1, Entscheidung des Inhabers vom 08.10. (Punkt 2).
Rohdaten: `trend_sip_iex.json`.

## Frage

IEX-Tageskerzen gibt es erst ab dem 27.07.2020. Der Tagestrend des Bots braucht aber mindestens 55 Tageskerzen,
live lädt er 120. Kann SIP als Vorlauf einspringen?

Regel des Inhabers:
- Weichen unter 1 % der Trendentscheidungen ab, gilt der SIP-Vorlauf, und der Suchtopf bleibt ab Okt. 2020.
- Sonst dient Okt. 2020 bis Jan. 2021 nur zum Aufwärmen.

## Aufbau

- **Entscheidung:** die Funktion des Bots selbst (EMA20/EMA50 aus den letzten 120 abgeschlossenen Sitzungen, unter
  55 Kerzen „flat“).
- **Kerzen:** unbereinigte Tageskerzen wie live. Verglichen wurde nur der Feed, IEX gegen SIP.
- **Universum:** die 150 Werte wie live, ohne BK, MMC und FI, also 147 Werte.
- **Zeitraum:** 796 Handelstage vom 03.08.2020 bis 29.09.2023, nur der Suchtopf. Der Prüftopf blieb zu.
- **Abrufe:** 176.

## Ergebnis

| Phase | Entscheidungen | abweichend | Anteil |
|---|---|---|---|
| **Volle Fenster** (beide Feeds mit 120 Kerzen, 15.01.2021–29.09.2023) | 100.107 | 459 | **0,46 %** |
| davon 2021 | 35.721 | 195 | 0,55 % |
| davon 2022 | 36.897 | 197 | 0,53 % |
| davon 2023 | 27.489 | 67 | 0,24 % |

**Art der Abweichungen bei vollen Fenstern:**
- flat→up 133, up→flat 130, flat→down 108, down→flat 87;
- nur ein einziges Mal up↔down.

**Aufwärmphase** (13.10.2020–14.01.2021, IEX hat 55–119 Kerzen, 9.555 Entscheidungen):

| Vergleich | abweichend |
|---|---|
| IEX gegen SIP mit gleich kurzem Fenster | 0,19 % |
| IEX mit kurzem Fenster gegen SIP mit vollem Fenster (so wäre es ohne Vorlauf) | 3,32 % |
| SIP-Vorlauf plus IEX gegen SIP mit vollem Fenster | 0,28 % |

**Zu kurz** (03.08.–12.10.2020, IEX unter 55 Kerzen, 7.276 Entscheidungen):
- Ohne Vorlauf sagt der Trend dort immer „flat“, damit fielen alle Signale weg.
- SIP sagt in dieser Zeit 4.736 × up, 1.109 × flat, 1.431 × down.
- Mit Vorlauf weicht die Entscheidung 0,34 % vom vollen SIP-Fenster ab.

## Urteil nach der Regel des Inhabers

**0,46 % liegt unter 1 %. Es gilt der SIP-Vorlauf, der Suchtopf bleibt ab dem 01.10.2020.**

Für die Vorab-Datei:
- Der Tagestrend nutzt bis zum Vorliegen von 120 IEX-Kerzen SIP-Tageskerzen vor dem 27.07.2020 als Vorlauf.
- Ab dem 15.01.2021 gilt wie live nur IEX.
- Der Vorlauf ist je Entscheidung gekennzeichnet.
