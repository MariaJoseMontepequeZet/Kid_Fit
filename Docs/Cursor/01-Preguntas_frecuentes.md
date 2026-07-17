# README 01 - ¿Qué es Cursor? (Guía para Principiantes)

---

## Objetivo del capítulo

Al finalizar este documento comprenderás qué es Cursor, para qué sirve, cuáles son sus funciones estrella, cómo se compara con otros editores y responderás las dudas más comunes antes de instalarlo.

---

## ¿Qué es Cursor?

Cursor es un editor de código diseñado para programar aplicaciones, páginas web, APIs y prácticamente cualquier tipo de software.

Lo que hace especial a Cursor es que **incorpora Inteligencia Artificial directamente en el núcleo del editor**.

> **Dicho de otra manera:** Imagina que Visual Studio Code y un modelo de IA avanzado (como GPT-4 o Claude) se unieran en una sola aplicación sin necesidad de instalar extensiones externas. Eso es Cursor.

Puedes escribir código como normalmente lo harías, pero además puedes interactuar con el editor como si tuvieras a un profesor al lado. Por ejemplo, puedes pedirle:

* *"¿Qué hace esta función?"*
* *"Explícame este archivo completo."*
* *"Encuentra y corrige este error."*
* *"Crea un componente visual siguiendo el estilo actual de mi proyecto."*

Todo esto ocurre de forma fluida y sin salir de tu ventana de trabajo.

---

## ¿Qué significa que Cursor está basado en Visual Studio Code?

Cursor utiliza como base el mismo proyecto de código abierto (*Open Source*) en el que se apoya **Visual Studio Code (VS Code)**.

Esto significa que ambos programas son hermanos casi idénticos en su interfaz. Comparten:

* La apariencia visual.
* El explorador de archivos y la terminal integrada.
* Las extensiones y la configuración del usuario.
* Los atajos de teclado.

Si ya has usado Visual Studio Code antes, tu curva de aprendizaje con Cursor será de prácticamente cero minutos.

---

## ¿Cursor reemplaza a Visual Studio Code?

No. Visual Studio Code sigue siendo uno de los editores de código más populares y robustos del mundo. Cursor es simplemente una evolución alternativa que rediseña la experiencia de desarrollo integrando la IA desde sus cimientos para acelerar tu flujo de trabajo.

Podemos resumirlo de la siguiente manera:

* **Visual Studio Code:** Un editor de código excelente, rápido y altamente personalizable.
* **Cursor:** Un editor de código excelente + Un asistente de Inteligencia Artificial que comprende todo tu proyecto.

---

## ¿Cuál elegir? Tabla comparativa

Para entender mejor dónde se sitúa Cursor, veamos cómo se compara con VS Code "limpio" y con la alternativa de usar VS Code añadiéndole una extensión de pago como GitHub Copilot:

| Característica | VS Code (Limpio) | VS Code + GitHub Copilot | Cursor |
| --- | --- | --- | --- |
| **Costo** | 100% Gratis | Requiere suscripción de pago (Copilot) | **Gratis (con límites)** / Planes Pro |
| **Inteligencia Artificial** | No tiene de forma nativa | Añadida mediante una extensión | **Totalmente integrada en el núcleo** |
| **Edición Multi-archivo** | No disponible | Limitada | **Sí (Edita varios archivos a la vez)** |
| **Compatibilidad** | Estándar de la industria | Estándar de la industria | **100% compatible con extensiones de VS Code** |
| **Comprensión del proyecto** | Manual (tú buscas todo) | Media (a través de la extensión) | **Alta (Indexa todo tu código de forma nativa)** |

---

## Las tres "Herramientas Estrella" de Cursor

A diferencia de otros editores que solo añaden un chat de preguntas en una barra lateral, Cursor destaca por tres funciones diseñadas específicamente para programar:

* **Cursor Tab (Autocompletado inteligente):** Mientras escribes, Cursor predice tu siguiente movimiento. No solo completa la palabra actual, sino que puede sugerir las próximas líneas de código o incluso adivinar qué archivo necesitas editar a continuación. Solo pulsas `Tab` para aceptar.
* **El Chat (`Ctrl + L` o `Cmd + L`):** Una barra lateral donde puedes conversar con la IA. La gran ventaja es que puedes escribir `@` para etiquetar archivos específicos, carpetas o incluso la documentación oficial de una tecnología, para que la IA responda con contexto exacto.
* **Composer (`Ctrl + I` o `Cmd + I`):** Es la herramienta más avanzada de Cursor. Te permite darle instrucciones complejas para que cree o modifique **múltiples archivos al mismo tiempo**, estructurando carpetas completas por ti de forma automatizada.

---

## ¿Qué pasa con la privacidad de mi código?

Una preocupación común al usar herramientas de IA es si tu código privado se usará para entrenar futuros modelos.

Cursor soluciona esto con su **Privacy Mode (Modo Privacidad)**. Si lo activas en la configuración, Cursor garantiza que ninguno de tus archivos o líneas de código se guardará en sus servidores ni se utilizará para el entrenamiento de inteligencias artificiales. Tu propiedad intelectual se mantiene 100% segura.

---

## Preguntas Frecuentes (FAQ)

### ¿Cursor es un IDE?

No exactamente. Al igual que VS Code, **Cursor es un Editor de Código**. Un IDE (*Integrated Development Environment*, como Visual Studio, Android Studio o IntelliJ IDEA) suele ser un entorno mucho más pesado que incluye compiladores nativos, diseñadores visuales y herramientas sumamente específicas integradas para un solo ecosistema. Cursor es ligero, ágil y se adapta a cualquier tecnología mediante extensiones.

### ¿Qué puedo programar con Cursor?

Prácticamente cualquier lenguaje de programación o tecnología:

* **Desarrollo Web:** HTML, CSS, JavaScript, TypeScript, React, Vue, Angular, Svelte, Tailwind CSS.
* **Backend y APIs:** Node.js, Python, Java, PHP, Laravel, C#, Go, Rust.
* **Móvil:** React Native, Expo, Flutter, Kotlin, Swift.

### ¿Necesito Internet para usar Cursor?

* **Para programar:** No. Puedes abrir el editor, escribir código, compilar proyectos, usar tu terminal e incluso gestionar tus versiones con Git de forma 100% local y sin conexión.
* **Para la IA:** Sí. Las funciones inteligentes (Chat, Autocompletado, Composer) necesitan conexión a Internet para comunicarse con los modelos en la nube.

### ¿Cursor es gratuito?

**Sí, cuenta con un plan gratuito (Hobby)** que es más que suficiente para aprender y desarrollar proyectos personales.

* Este plan te da acceso gratuito e ilimitado a sus modelos básicos de autocompletado y un número generoso de consultas mensuales de "alta velocidad" con los modelos de IA más avanzados.
* Si superas ese límite mensual, puedes seguir usando la IA de forma gratuita pero a una velocidad menor, o bien optar por un plan de pago si eres un profesional que requiere un uso intensivo diariamente.

---

## ¿Cómo aprender a usar la IA correctamente?

La Inteligencia Artificial puede escribir mucho código por ti, pero **no sustituye tu razonamiento ni tu proceso de aprendizaje**. Si dejas que la IA haga todo sin entenderlo, te costará mucho resolver problemas cuando surja un error que la IA no sepa solucionar.

Te sugerimos cambiar el enfoque de uso:

* **Enfoque Incorrecto (Copiar y pegar):**
> *"Hazme una aplicación de tareas completa."* (Esto genera código que no sabrás cómo modificar si algo falla).


* **Enfoque Correcto (Aprender con la IA):**
> *"Quiero crear una aplicación de tareas. Explícame primero qué estructura de archivos necesito."*
> *"Ahora hagamos la interfaz de usuario paso a paso."*
> *"He escrito este código para guardar las tareas pero me da un error. ¿Me explicas qué está fallando y cómo solucionarlo?"*



---

## Respuestas rápidas de compatibilidad

* **¿Sustituye a la documentación oficial?** No. La documentación oficial es siempre la verdad absoluta. Cursor es fantástico para resumirla, explicar fragmentos confusos o darte ejemplos prácticos basados en ella.
* **¿Funciona con Git y GitHub?** Sí, de forma nativa. Puedes hacer commits, ramas, resolver conflictos de fusión (*merge conflicts*) y subir tu código a GitHub sin salir del editor.
* **¿Sirve en mi sistema operativo?** Sí. Cuenta con instaladores oficiales para **Windows**, **macOS** y **Linux** (con soporte oficial para distribuciones como Ubuntu, Debian, Fedora y Linux Mint).
* **¿Consume muchos recursos?** Su consumo es sumamente moderado, muy similar al de VS Code. Las operaciones pesadas de IA ocurren en servidores externos, por lo que tu computadora no sufrirá por procesar la inteligencia artificial.

---

## ¿Qué ventajas aporta?

### Para un Principiante

* Funciona como un tutor personal 24/7 que no se cansa de responder preguntas.
* Te ayuda a entender mensajes de error complejos de la terminal traduciéndolos a lenguaje sencillo.
* Te escribe comentarios explicativos línea por línea dentro de tu código para que recuerdes qué hace cada parte.

### Para un Profesional

* Automatiza tareas repetitivas y aburridas (como escribir pruebas unitarias o configurar archivos de inicio).
* Permite refactorizar (mejorar la estructura) de múltiples archivos en segundos mediante el uso de Composer.
* Agiliza la búsqueda y corrección de bugs complejos al analizar el contexto completo de todo el repositorio de código.

---

## ¿Cuándo NO deberías usar Cursor?

No dependas de la IA si:

1. Pretendes aprender un lenguaje desde cero saltándote la teoría básica de la programación.
2. Planeas ejecutar comandos en tu terminal o publicar código en producción que no entiendes en absoluto.
3. Pretendes aceptar ciegamente cada sugerencia de autocompletado sin revisar si tiene sentido en tu lógica de negocio.

---

## Resumen del capítulo

* Cursor es un editor moderno basado en VS Code con Inteligencia Artificial integrada nativamente en su núcleo.
* Incluye herramientas clave como **Cursor Tab** (autocompletado), **Chat** (preguntas contextuales) y **Composer** (edición de múltiples archivos).
* Ofrece un **Modo Privacidad** para asegurar que tu código nunca se use para entrenar modelos de IA de terceros.
* Es compatible con Windows, macOS y Linux, y funciona con prácticamente cualquier lenguaje de programación.

---

## Próximo capítulo

En el siguiente documento aprenderemos a instalar Cursor desde cero en **Windows, macOS y Linux Ubuntu/Mint** paso a paso, asegurando que configures el entorno de la manera correcta para empezar a programar.