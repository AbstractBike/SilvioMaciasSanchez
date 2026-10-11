# Patrón: Cristalización

La idea central es pedirle a la IA **la forma de hacerlo**, no el resultado. Enseñar a pescar en vez de dar pescado: en lugar de *"clasifica este correo"*, *"escribe el clasificador de correos"*. Lo que vuelve no es una respuesta sino un método —un programa, una gramática, una regla, una consulta— que queda escrito y responde solo, sin volver a llamar al modelo.

Un LLM que se ejecuta en cada llamada es **líquido**: toma la forma de cada entrada, cuesta en cada uso, no repite exactamente y no se puede auditar. Lo que produce cuando le pides el método es **cristal**: una estructura fija, determinista, barata, versionada y con pruebas. La IA deja de ser el intérprete que ejecuta tu problema y se convierte en el compilador que te escribe el programa que lo ejecuta.

### Las pipelines de IA se cristalizan

Una pipeline de IA es una cadena de etapas que llaman a un modelo: clasificar, extraer, normalizar, enrutar, resumir. Casi ninguna necesita inteligencia en cada ejecución; la necesitó **una vez**, para entender el problema. Cristalizar la pipeline es sacar al LLM del camino de ejecución, etapa a etapa, pasando por tres fases:

- **Líquida.** La etapa llama al LLM en cada entrada. Así nace todo, y está bien: es la forma más rápida de saber si el problema tiene solución. Desde el primer día se registra cada llamada.
- **Mixta.** Un cristal atiende lo que sabe; lo que no sabe lo declara como *defecto*, cae al LLM y queda registrado.
- **Cristalina.** El cristal lo cubre todo. El LLM ya no se ejecuta; solo se le convoca para *recristalizar* cuando el dominio cambia.

La pipeline aprende, pero lo aprendido queda escrito como código, no como pesos ni como contexto.

### Cuándo aplicarlo (y cuándo no)

Aplícalo cuando la etapa tiene **estructura estable**: extraer campos, clasificar en un conjunto cerrado, normalizar formatos, validar, transformar entre esquemas. La regla práctica: si al pedirle el resultado a la IA dos veces esperas la misma respuesta, esa etapa debería ser un cristal.

**No** lo fuerces en lo que es abierto por naturaleza: redactar texto libre, conversar, juzgar calidad subjetiva. Aun así suele cristalizar *una parte* —la plantilla del texto, la rúbrica del juicio, el árbol de la conversación— y el líquido queda acotado al hueco que de verdad lo necesita.

### Mecánica del patrón

El ciclo tiene nombre propio en cada paso:

**1. Semilla.** Lo mínimo para que crezca un cristal: el problema en una frase, ejemplos reales de entrada y salida (incluidos los raros), las invariantes que toda salida debe cumplir y lo que debe quedar *fuera de dominio*.

**2. Nucleación.** Se le pide al LLM el método, no la respuesta. Lo que vuelve es código, pruebas y la lista explícita de casos que el método no cubre. Si no puede dar un método general, la etapa no está madura: sigue líquida y se recogen más ejemplos.

**3. Red cristalina.** Las pruebas e invariantes que definen la estructura. Un cristal sin red es solo código generado; con red, es una pieza en la que se puede confiar. La red solo crece: cada versión del cristal pasa la red entera de la anterior.

**4. Crecimiento.** Los defectos registrados en fase mixta se convierten en semilla de la siguiente nucleación. Así sube el **grado de cristalización** —la fracción de entradas resueltas sin LLM—, que es la métrica que manda.

**5. Fusión.** Si el grado cae de golpe, el dominio ha cambiado. La etapa vuelve a líquida sin dramas; la semilla y la procedencia antiguas siguen en el repositorio para la próxima nucleación.

### Estructura para implementarlo como prompt/sistema

La instrucción núcleo de la nucleación sería algo así:

> No quiero que resuelvas estos casos. Quiero el programa que los resuelve todos, para no tener que volver a preguntarte. Entrega una función pura —sin red, reloj ni aleatoriedad— que para cada entrada devuelva un resultado o un defecto con su motivo; prefiero un defecto a una respuesta inventada. Incluye pruebas que cubran todos los ejemplos y comprueben las invariantes, y la lista de casos que tu método no cubre. Si el problema no admite un método general, dilo y explica qué ejemplos faltarían; no me des un programa que en el fondo sea una tabla de los ejemplos.

Implementación de referencia (librería OCaml de etapas líquidas, mixtas y cristalinas componibles, protocolo completo y un cristal de ejemplo): [AbstractBike/cristales](https://github.com/AbstractBike/cristales).

### Riesgos y salvaguardas

El patrón tiene dos modos de fallo. El primero es la **impureza**: un cristal que trata *mal* una entrada sin darse cuenta, en lugar de declararla defecto. Es peor que el LLM, porque da una respuesta equivocada con aspecto de certeza. La salvaguarda es la red: invariantes comprobadas sobre todo el registro, no solo sobre los ejemplos, y contraste con lo que respondía el líquido antes de solidificar. El segundo es el **sobreajuste a la semilla**: un "método" que en realidad memoriza los ejemplos. Se detecta exigiendo invariantes generales y probando con entradas que no estaban en la semilla.

La tensión de fondo vale la pena nombrarla: este patrón usa la IA para *dejar de usar* la IA. Es el reflejo de la [Inversión de Motivación](../README.md#patrón-inversión-de-motivación), pero aplicado a las máquinas: allí la IA retiene la solución para que tú actúes; aquí le pides el método para que el sistema actúe solo. En ambos casos el objetivo no es la respuesta, sino la capacidad que queda cuando la IA se retira.
