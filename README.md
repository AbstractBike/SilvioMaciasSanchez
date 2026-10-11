
# Silvio Macías Sánchez

Investigación y documentación sobre patrones de inteligencia artificial, motivación y sistemas de conocimiento.

## Patrón: Inversión de Motivación

La idea central es voltear el contrato implícito del agente. Normalmente el contrato es *"tú delegas, yo ejecuto"*. La inversión lo cambia a *"yo sostengo la estructura, tú ejecutas"*. La IA deja de ser el motor que produce el resultado y se convierte en el motor que produce **tu acción**.

Suena paradójico —¿para qué un agente que no hace el trabajo?— pero resuelve un problema real: cuando la IA hace todo, te vuelves espectador de tu propia vida. Pierdes la habilidad, el criterio y, sobre todo, el impulso. Este patrón existe para los casos donde *que tú actúes* vale más que *que la tarea se complete rápido*: aprender algo, escribir lo que solo tú puedes escribir, salir de la parálisis, recuperar agencia.

### Cuándo aplicarlo (y cuándo no)

Aplícalo cuando el valor está en el proceso humano: estudiar, entrenar una habilidad, vencer procrastinación, tomar decisiones que deben ser tuyas, mantener un hábito. **No** lo apliques en trabajo puramente instrumental donde el resultado es lo único que importa (formatear un CSV, traducir un correo). Forzar esfuerzo ahí solo genera fricción inútil.

### Mecánica del patrón

El agente opera con cuatro inversiones respecto al agente clásico:

**1. Invierte la dirección de la pregunta.** En vez de pedirte el problema para resolverlo, te devuelve el problema descompuesto en el siguiente paso accionable más pequeño. No *"aquí está tu ensayo"* sino *"escribe la primera frase mala, yo espero"*.

**2. Retiene la solución a propósito.** El agente puede conocer la respuesta y aun así no darla. Su función no es informar sino provocar movimiento. Puede dar pistas, marcos, o el 80% del andamiaje, pero deja el acto final en tus manos.

**3. Convierte fricción en compromiso.** Usa micro-compromisos, temporizadores, y devoluciones inmediatas. *"Tienes 5 minutos para producir un borrador horrible. Cuando vuelvas lo critico."* La IA gestiona el ritmo; tú generas el contenido.

**4. Mide tu output, no el suyo.** El éxito del agente se define por cuánto produjiste tú, no por cuánto entregó él.

### Estructura para implementarlo como prompt/sistema

Si lo quieres construir como un agente real, su instrucción núcleo sería algo así:

> Tu objetivo no es completar la tarea del usuario. Es maximizar la cantidad y calidad de trabajo que el usuario produce por sí mismo. Nunca entregues el producto final si el usuario puede producirlo. En cada turno: (a) identifica el paso más pequeño que el usuario puede hacer ahora, (b) pídeselo con una restricción de tiempo o de alcance, (c) cuando lo entregue, reacciona —corrige, sube el listón, pide el siguiente paso. Solo resuelves tú cuando el usuario está genuinamente bloqueado, y aun así devuelves apenas lo justo para desbloquear.

### Riesgos y salvaguardas

El patrón tiene dos modos de fallo que conviene anticipar. El primero es la **condescendencia**: si el agente retiene ayuda que el usuario realmente necesita, se vuelve molesto y paternalista. La salvaguarda es una válvula de escape clara —el usuario siempre puede decir "dámelo directo" y el agente obedece sin resistencia—. El segundo es la **fricción mal
calibrada**: pedir esfuerzo en el momento equivocado mata la motivación en vez de encenderla. Por eso el agente debe leer señales de cansancio o frustración y bajar la exigencia, no subirla.

La tensión filosófica de fondo vale la pena nombrarla: este patrón usa la automatización para *reducir* el trabajo que la automatización hace. Es deliberadamente ineficiente a corto plazo para ser generativo a largo plazo. Funciona solo si ambos —tú y el agente— están de acuerdo en que el objetivo no es terminar, sino que tú crezcas terminando.

## Abstract Architectures

Patrones de arquitectura para sistemas con IA.

### [Cristalización](abstract-architectures/cristalizacion.md)

Pedirle a la IA la forma de hacerlo, no el resultado: enseñar a pescar en vez de dar pescado. Un LLM en tiempo de ejecución es *líquido* —caro, estocástico, inauditable—; el método que escribe una vez es *cristal* —código determinista, versionado y con pruebas—. Las pipelines de IA se cristalizan etapa a etapa (líquida → mixta → cristalina), y los casos que el cristal no sabe resolver se convierten en la semilla de la siguiente versión.

### [Forja](abstract-architectures/forja.md)

Cristalizar sin saber de antemano qué cristalizar. Un proxy delante del LLM ve pasar el tráfico, agrupa las peticiones en *tareas* —instrucciones fijas aplicadas a entradas que cambian— y guarda muestras, no respuestas: caña, no pescado. Cuando una tarea es estable —el modelo repite la respuesta si se le pregunta dos veces— prepara su semilla para la nucleación; una vez revisado y commiteado el cristal, el proxy la atiende sin llamar al modelo y mide el grado de cristalización de todo el tráfico.

---

© 2026 Silvio Macías Sánchez. Todos los derechos reservados. Sin licencia; prohibida la reproducción, transformación y el uso para entrenar IA sin autorización escrita. Ver [COPYRIGHT.md](COPYRIGHT.md).
