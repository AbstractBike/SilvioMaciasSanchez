🌐 [Español](https://github.com/AbstractBike/SilvioMaciasSanchez/tree/es) · [English](https://github.com/AbstractBike/SilvioMaciasSanchez/tree/en) · **Deutsch**

# Silvio Macías Sánchez

Muster, um mit künstlicher Intelligenz zu arbeiten, ohne zu verlieren, was zählt: deine Handlungsfähigkeit und die Kontrolle über deine Systeme. Außerdem einige Entwürfe für Speichersysteme.

Jedes Muster liest sich in wenigen Minuten und beginnt mit einer Zusammenfassung in einem Satz und einem Kurzsteckbrief. Wenn du nur einen Moment hast, lies das.

## Die Muster

| Muster | In einem Satz | Lesezeit |
| --- | --- | --- |
| [**Motivationsumkehr**](motivacion/inversion-de-motivacion.md) | Eine KI, die die Arbeit nicht für dich erledigt, sondern dir hilft, sie selbst zu machen. | 5 Min. |
| [**Kristallisation**](abstract-architectures/cristalizacion.md) | Bitte die KI um das Programm, das das Problem löst, nicht um die Antwort auf jeden Einzelfall. | 6 Min. |
| [**Schmiede**](abstract-architectures/forja.md) | Ein Proxy vor dem LLM, der entdeckt, welche Aufgaben sich wiederholen, und dir sagt, wann du sie kristallisieren solltest. | 7 Min. |

### Wie sie zusammenhängen

Die drei teilen dieselbe Idee: **Das Ziel ist nicht die Antwort, sondern die Fähigkeit, die bleibt, wenn sich die KI zurückzieht.**

```mermaid
flowchart LR
    IM["🧠 Motivationsumkehr<br/><i>für Menschen</i>"] -. "gleiche Idee" .- CR["💎 Kristallisation<br/><i>für Systeme</i>"]
    CR -->|"ohne zu wissen, welche Stufen es gibt"| FO["⚒️ Schmiede<br/><i>für LLM-Traffic</i>"]
```

- **Nutzt du KI, um zu lernen oder etwas zu erschaffen?** Beginne mit der [Motivationsumkehr](motivacion/inversion-de-motivacion.md).
- **Hast du eine Pipeline, die in jedem Schritt ein LLM aufruft?** Beginne mit der [Kristallisation](abstract-architectures/cristalizacion.md).
- **Hast du viel LLM-Traffic und weißt nicht, was darin steckt?** Beginne mit der [Schmiede](abstract-architectures/forja.md).

### Wie jedes Muster aufgebaut ist

Alle folgen derselben Struktur, damit du weißt, wo du suchen musst:

1. **In einem Satz** und ein **Steckbrief**: Problem, Lösung, wann du es einsetzt und wie man es misst.
2. **Die Idee** und **ein schnelles Beispiel**.
3. **Wann du es anwendest (und wann nicht).**
4. **Wie es funktioniert** und **wie du es umsetzt**.
5. **Risiken und Schutzmaßnahmen.**
6. **Siehe auch**.

## Dateisysteme

| Entwurf | In einem Satz |
| --- | --- |
| [**gefs + FDP**](sistemas-de-ficheros/gefs-fdp.md) | Das Dateisystem von 9front sagt der SSD, welche Blöcke gemeinsam sterben, damit die Schreibverstärkung auf ≈1 sinkt, ohne das Format auf der Platte zu ändern. |

## Sprachen

Der Inhalt liegt in drei Sprachen vor, jede in ihrem eigenen Branch, mit denselben Dateien unter denselben Pfaden:

| Branch | Sprache |
| --- | --- |
| [`es`](https://github.com/AbstractBike/SilvioMaciasSanchez/tree/es) | Español (Original) |
| [`en`](https://github.com/AbstractBike/SilvioMaciasSanchez/tree/en) | English |
| [`de`](https://github.com/AbstractBike/SilvioMaciasSanchez/tree/de) | Deutsch |

Spanisch ist die Originalfassung; wenn eine Übersetzung und das Original voneinander abweichen, gilt das Original.

## Nutzung und Rechte

Frei für Forschung und Lehre ohne Gewinnabsicht, unter Nennung des Autors. Für kommerzielle Nutzung schreib mir –ich bin sehr freundlich–: silvio.macias.sanchez@abstract.bike oder info@abstractarchitectures.ltd. Details in [COPYRIGHT.md](COPYRIGHT.md).

---

© 2026 Silvio Macías Sánchez. Alle Rechte vorbehalten.
