# Gegenprobe M001-H0 und M003-H0 gegen das Replay (J3)

Nur Signale und Entscheidungen, keine Ergebnisse in R (Vorab-Datei Lerntopf-Lauf 1, Abschnitt 8).

| Zählung | Wert |
|---|---|
| Setups im Labor | 8802 |
| Setups im Replay | 8802 |
| in beiden | 8802 |
| nur im Labor | 0 |
| nur im Replay | 0 |
| Kante, Stop oder Ziel abweichend | 0 |
| **Signale 1:1 gleich** | **ja** |

## Abweichende Entscheidungen (Replay -> Labor)

- skip-spread -> order: 750
- skip-stale -> order: 221
- skip-stale -> skip-chase: 143
- skip-spread -> skip-chase: 142
- skip-spread -> skip-rr: 96
- skip-chase -> order: 82
- skip-dup -> skip-vol: 39
- order -> skip-chase: 35
- skip-stale -> skip-daten: 32
- skip-spread -> skip-tag: 27
- skip-stale -> skip-rr: 25
- skip-dup -> order: 16
- order -> skip-tag: 13
- skip-chase -> skip-rr: 10
- skip-dup -> skip-tag: 8
- skip-spread -> skip-daten: 7
- skip-dup -> skip-chase: 5
- skip-stale -> skip-tag: 3
- order -> skip-daten: 2
- skip-dup -> skip-daten: 2
- skip-rr -> skip-chase: 2
- skip-chase -> skip-daten: 2
- skip-maxopen -> skip-vol: 1

Erklärt nach Abschnitt 8:

- Wert hatte im Replay schon eine Position: im Labor jedes Signal einzeln: 70
- Kursalter: ohne Quotes nicht nachgebildet: 424
- Einstieg zur Minute statt am Live-Kurs: 131
- 1 Signal je Muster, Aktie und Tag: 13
- Spread: ohne Quotes nicht nachgebildet: 1022
- 5-Plätze-Grenze: im Labor jedes Signal einzeln: 1

Offen (einzeln zu erklären): 2

