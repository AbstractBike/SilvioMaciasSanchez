🌐 **Español** · [English](https://github.com/AbstractBike/SilvioMaciasSanchez/tree/en) · [Deutsch](https://github.com/AbstractBike/SilvioMaciasSanchez/tree/de)

# Silvio Macías Sánchez

Patrones para trabajar con inteligencia artificial sin perder lo que importa: tu capacidad de actuar y el control de tus sistemas. También algún diseño de sistemas de almacenamiento.

Cada patrón se lee en unos minutos y empieza con un resumen de una frase y una ficha rápida. Si solo tienes un momento, lee eso.

## Los patrones

| Patrón | En una frase | Lectura |
| --- | --- | --- |
| [**Inversión de Motivación**](motivacion/inversion-de-motivacion.md) | Una IA que no hace el trabajo por ti, sino que te ayuda a hacerlo tú. | 5 min |
| [**Cristalización**](abstract-architectures/cristalizacion.md) | Pídele a la IA el programa que resuelve el problema, no la respuesta a cada caso. | 6 min |
| [**Forja**](abstract-architectures/forja.md) | Un proxy delante del LLM que descubre qué tareas se repiten y te avisa cuándo cristalizarlas. | 7 min |
| [**Agencia**](abstract-architectures/agencia.md) | Agentes que aprenden, encargo a encargo, cuál es el modelo más barato que hace bien su trabajo. | 6 min |
| [**Seguimiento de costes**](abstract-architectures/seguimiento-de-costes.md) | Cada commit de una IA dice qué modelo lo escribió y cuánto costó. | 6 min |
| [**Llaves de miel**](abstract-architectures/llaves-de-miel.md) | Una clave real e inofensiva donde no debería salir nunca; si sale, te avisa quien la emitió. | 7 min |
| [**Propósito sobre personalidad**](abstract-architectures/proposito-sobre-personalidad.md) | Que el entorno de tu agente no diga quién eres, sino a qué ha venido. | 7 min |

### Cómo se relacionan

Comparten una misma idea: **el objetivo no es la respuesta, sino la capacidad que queda cuando la IA se retira.** Y se encadenan: primero el modelo más barato que sabe, luego ninguno, y la cuenta apuntada para saber si mereció la pena.

```mermaid
flowchart LR
    IM["🧠 Inversión de Motivación<br/><i>para personas</i>"] -. "misma idea" .- CR["💎 Cristalización<br/><i>para sistemas</i>"]
    CR -->|"sin saber qué etapas hay"| FO["⚒️ Forja<br/><i>para tráfico de LLM</i>"]
    AG["🤖 Agencia<br/><i>el modelo más barato</i>"] -->|"la tarea madura"| FO
    SC["🧾 Seguimiento de costes<br/><i>¿salió a cuenta?</i>"] -.-> AG
    SC -.-> FO
    LM["🍯 Llaves de miel<br/><i>¿se ha filtrado?</i>"] -. "vigila sus almacenes" .-> FO
    PP["🎯 Propósito sobre personalidad<br/><i>el entorno como contexto</i>"] -. "reduce lo que sale" .- LM
```

- **¿Usas la IA para aprender o crear?** Empieza por la [Inversión de Motivación](motivacion/inversion-de-motivacion.md).
- **¿Tienes una pipeline que llama a un LLM en cada paso?** Empieza por la [Cristalización](abstract-architectures/cristalizacion.md).
- **¿Tienes mucho tráfico de LLM y no sabes qué contiene?** Empieza por la [Forja](abstract-architectures/forja.md).
- **¿Repites el mismo prompt una y otra vez?** Empieza por la [Agencia](abstract-architectures/agencia.md).
- **¿Commitean agentes en tus repos y no sabes cuánto cuestan?** Empieza por el [Seguimiento de costes](abstract-architectures/seguimiento-de-costes.md).
- **¿Te preocupa que se filtre el contexto de tus agentes?** Empieza por las [Llaves de miel](abstract-architectures/llaves-de-miel.md).
- **¿Tus agentes trabajan en tu máquina, entre tus carpetas?** Empieza por [Propósito sobre personalidad](abstract-architectures/proposito-sobre-personalidad.md).

### Cómo está escrito cada patrón

Todos siguen la misma estructura, para que sepas dónde buscar:

1. **En una frase** y una **ficha**: problema, solución, cuándo usarlo y cómo se mide.
2. **La idea** y **un ejemplo rápido**.
3. **Cuándo aplicarlo (y cuándo no).**
4. **Cómo funciona** y **cómo implementarlo**.
5. **Riesgos y salvaguardas.**
6. **Ver también**.

## Sistemas de ficheros

| Diseño | En una frase |
| --- | --- |
| [**gefs + FDP**](sistemas-de-ficheros/gefs-fdp.md) | Que el sistema de ficheros de 9front le diga al SSD qué bloques mueren juntos, para que la amplificación de escritura baje a ≈1 sin cambiar el formato en disco. |

## Idiomas

El contenido está en tres idiomas, cada uno en su rama, con los mismos ficheros en las mismas rutas:

| Rama | Idioma |
| --- | --- |
| [`es`](https://github.com/AbstractBike/SilvioMaciasSanchez/tree/es) | Español (original) |
| [`en`](https://github.com/AbstractBike/SilvioMaciasSanchez/tree/en) | English |
| [`de`](https://github.com/AbstractBike/SilvioMaciasSanchez/tree/de) | Deutsch |

El español es la versión original; si una traducción y el original no coinciden, vale el original.

## Uso y derechos

Libre para investigación y docencia sin ánimo de lucro, citando al autor. Para uso comercial, escríbeme —soy muy amigable—: silvio.macias.sanchez@abstract.bike o info@abstractarchitectures.ltd. Detalles en [COPYRIGHT.md](COPYRIGHT.md).

---

© 2026 Silvio Macías Sánchez. Todos los derechos reservados.
