# README 03 - Configuración Inicial de Cursor para Principiantes

> **Objetivo del capítulo**
> En este capítulo aprenderás a configurar Cursor como un desarrollador profesional. No solamente aprenderás dónde hacer clic, sino también el propósito detrás de cada ajuste. Al finalizar tendrás un entorno de trabajo optimizado, cómodo y listo para programar de forma fluida.

---

## Antes de comenzar

En el capítulo anterior dejamos Cursor instalado en tu sistema. Ahora es momento de prepararlo.

Aunque podrías empezar a programar con la configuración por defecto, invertir unos minutos ahora en personalizar tu editor te ahorrará horas de fricción en el futuro. Piensa en esto como limpiar y organizar tu escritorio de estudio antes de abrir los libros: un espacio ordenado despeja la mente.

---

## 🧩 Entendiendo las "Dos Configuraciones" de Cursor

A diferencia de VS Code, en Cursor conviven **dos paneles de configuración diferentes** que debes aprender a diferenciar desde el primer día:

1. **Configuración del Editor (VS Code Standard):** Controla el comportamiento visual, fuentes, tabulaciones y comportamiento del software.
* *Atajo:* `Ctrl + ,` (Windows/Linux) o `Cmd + ,` (macOS).


2. **Configuración de Cursor (Cursor Settings):** Controla los modelos de Inteligencia Artificial, tus modelos preferidos, las reglas del proyecto (`.cursorrules`), el Modo Privacidad y los límites de tu cuenta.
* *Cómo acceder:* Haz clic en el **icono de engranaje (Gear Icon)** ubicado en la esquina superior derecha del editor, o presiona `Ctrl + Shift + J` (Windows/Linux) o `Cmd + Shift + J` (macOS).



---

## Conociendo la interfaz de un vistazo

Al abrir Cursor por primera vez, verás una interfaz dividida en zonas clave diseñadas para mantener tu flujo de trabajo sin distracciones:

```
+-------------------------------------------------------------+
|  Archivo  Editar  Selección  Ver  Ir ...             [⚙️] [👤] | <-- Barra Superior & Ajustes Cursor
+-------------------------------------------------------------+
| ☰ |                                                         |
|   | Explorer (Carpetas)                                     |
| Q | Search (Buscador Global)                                |
| Y | Source Control (Git)             Área de Trabajo         |
| D | Run & Debug                      (Tus archivos abiertos) |
| X | Extensions (Marketplace)                                |
|   |                                                         |
|---+---------------------------------------------------------|
| Chat (Ctrl+L) | Composer (Ctrl+I)                           | <-- Panel de IA (Normalmente a la derecha o flotante)
+-------------------------------------------------------------+

```

### Elementos clave de la barra lateral:

* **Explorer (Explorador):** Tu navegador de archivos. Aquí creas, eliminas y arrastras tus carpetas de código.
* **Search (Buscador):** Busca y reemplaza texto en todos los archivos de tu proyecto simultáneamente.
* **Source Control (Git):** El historial de versiones de tu proyecto. Sabrás qué líneas cambiaste y podrás subirlas a GitHub.
* **Extensions (Extensiones):** La tienda oficial para instalar herramientas que añaden superpoderes a tu editor.
* **Chat e IA:** El panel exclusivo de Cursor donde la Inteligencia Artificial interactúa directamente con tu código.

---

## ⚙️ Ajustes Recomendados del Editor

Para aplicar estas configuraciones, abre el panel de **Configuración del Editor** (`Ctrl + ,` o `Cmd + ,`), busca el nombre del ajuste en la barra de búsqueda superior y aplica el cambio sugerido:

### 1. Guardado Automático (Auto Save)

* **Buscar:** `Auto Save`
* **Configuración:** Cambiar de `off` a **`afterDelay`**.
* **¿Por qué?** Guarda tus cambios automáticamente tras un breve instante sin escribir. Te olvidarás para siempre de perder código por un apagón o por olvidar presionar guardar.

### 2. Retraso de Guardado (Auto Save Delay)

* **Buscar:** `Auto Save Delay`
* **Configuración:** Escribe **`1000`** (corresponde a 1000 milisegundos / 1 segundo).
* **¿Por qué?** Evita que el editor guarde constantemente a cada milisegundo, dándote un segundo de respiro cuando pausas tu escritura.

### 3. Autoformatear al Guardar (Format On Save)

* **Buscar:** `Format On Save`
* **Configuración:** **Activar (✔)**.
* **¿Por qué?** Cada vez que el editor guarde, acomodará automáticamente las sangrías, llaves y espacios de tu código bajo las reglas de estilo profesionales. Tu código siempre lucirá impecable sin esfuerzo manual.

### 4. Ajuste de Línea (Word Wrap)

* **Buscar:** `Word Wrap`
* **Configuración:** Cambiar a **`on`**.
* **¿Por qué?** Si una línea de código es demasiado larga, el editor la ajustará visualmente para que quepa en tu pantalla en lugar de crear una molesta barra de desplazamiento horizontal.

### 5. Tamaño de Tabulación (Tab Size)

* **Buscar:** `Tab Size`
* **Configuración:** Cambiar a **`2`** (o `4` según tu preferencia, aunque `2` es el estándar moderno en desarrollo web).
* **¿Por qué?** Define cuántos espacios de sangría se aplican al pulsar la tecla `Tab`, manteniendo el código legible y ordenado.

### 6. Animación del Cursor (Cursor Smooth Caret Animation)

* **Buscar:** `Cursor Smooth Caret Animation`
* **Configuración:** Cambiar a **`on`**.
* **¿Por qué?** Hace que el cursor parpadeante se desplace de manera suave y fluida mientras escribes, mejorando la experiencia visual sin consumir recursos.

### 7. Zoom con la Rueda del Ratón (Mouse Wheel Zoom)

* **Buscar:** `Mouse Wheel Zoom`
* **Configuración:** **Activar (✔)**.
* **¿Por qué?** Te permite aumentar o reducir el tamaño de la letra rápidamente manteniendo presionada la tecla `Ctrl` (o `Cmd` en Mac) mientras deslizas la rueda de tu ratón.

---

## 🎨 Aspecto Visual: Temas e Iconos

Programar durante horas requiere una interfaz amigable con la vista. Puedes cambiar el aspecto de Cursor fácilmente:

### Elegir un Tema de Color

Ve a **Archivo > Preferencias > Tema de color** (o usa el atajo `Ctrl + K, Ctrl + T` / `Cmd + K, Cmd + T`).

* **Recomendado para empezar:** **Dark Modern** o **Dark+** (reducen significativamente la fatiga ocular).

### Instalar Iconos de Archivos Profesionales

Por defecto, los iconos de las carpetas y tecnologías en Cursor son muy planos. Vamos a cambiarlos:

1. Abre el panel de **Extensions** (`Ctrl + Shift + X` o `Cmd + Shift + X`).
2. Busca e instala: **`Material Icon Theme`**.
3. Una vez instalado, presiona `Ctrl + Shift + P` (o `Cmd + Shift + P`) para abrir la **Paleta de Comandos**.
4. Escribe `File Icon Theme` y selecciona **Material Icon Theme**. Ahora tus archivos HTML, CSS o JS tendrán iconos hermosos y fáciles de identificar.

---

## 🔌 Extensiones Esenciales para tu Aprendizaje

Instala estas extensiones desde el panel de **Extensions**. Harán que programar sea una experiencia mucho más guiada y amigable:

| Extensión | ¿Qué hace? | ¿Por qué la necesitas? |
| --- | --- | --- |
| **Prettier - Code Formatter** | Formatea tu código bajo estándares profesionales. | Garantiza que tu código esté ordenado, sin importar cómo lo escribas. |
| **ESLint** | Analiza tu código en tiempo real buscando malas prácticas. | Te avisa de posibles errores lógicos o variables declaradas que nunca usaste. |
| **Error Lens** | Resalta los errores de código directamente en la línea afectada. | **Vital para principiantes.** Ya no tienes que buscar en la consola pequeña de abajo para saber dónde te equivocaste. |
| **Path Intellisense** | Autocompleta los nombres y rutas de tus archivos. | Evita errores de escritura al enlazar imágenes, estilos o scripts en tu proyecto. |
| **Code Spell Checker** | Revisa la ortografía de tu código en inglés y español. | Te ayuda a no pasar horas buscando un error causado por escribir mal una variable. |
| **Better Comments** | Permite crear comentarios coloridos (`// TODO:`, `// ! Warning`). | Te ayuda a organizar tus notas de estudio dentro del propio código. |

> ⚠️ **REGLA DE ORO DE CURSOR:** **No instales extensiones de Inteligencia Artificial externas** (como *GitHub Copilot*, *Tabnine* o *Blackbox AI*). Cursor ya cuenta con su propia IA nativa optimizada en su núcleo; añadir otras creará conflictos graves de rendimiento, lentitud en el autocompletado y un consumo excesivo de memoria en tu computadora.

---

## ⌨️ Atajos de Teclado Imprescindibles (Cheat Sheet)

Memorizar estos atajos poco a poco transformará por completo tu velocidad al desarrollar.

| Acción | Windows / Linux | macOS |
| --- | --- | --- |
| **Abrir Configuración** | `Ctrl + ,` | `Cmd + ,` |
| **Abrir Ajustes de Cursor (IA)** | `Ctrl + Shift + J` | `Cmd + Shift + J` |
| **Paleta de Comandos (Buscar funciones)** | `Ctrl + Shift + P` | `Cmd + Shift + P` |
| **Buscar Archivo por Nombre** | `Ctrl + P` | `Cmd + P` |
| **Buscador de Texto Global** | `Ctrl + Shift + F` | `Cmd + Shift + F` |
| **Abrir / Cerrar Terminal** | `Ctrl + `` (Backtick) | `Ctrl + `` (Backtick) |
| **Abrir Panel de Extensiones** | `Ctrl + Shift + X` | `Cmd + Shift + X` |
| **Dividir la Pantalla en Dos** | `Ctrl + \` | `Cmd + \` |
| **Cerrar la Pestaña Actual** | `Ctrl + W` | `Cmd + W` |
| **Deshacer / Rehacer** | `Ctrl + Z` / `Ctrl + Y` | `Cmd + Z` / `Cmd + Shift + Z` |

---

## 💡 Consejos prácticos para tus primeros pasos

* **Menos es más:** No llenes tu editor de extensiones estéticas o "paquetes de snippets" enormes de internet. Cuantas más extensiones tengas activas, más lento iniciará tu editor.
* **Aprovecha la terminal integrada:** No abras consolas externas de tu sistema operativo. Usa el atajo `Ctrl + `` para abrir la terminal dentro de Cursor; esto mantiene todo tu entorno centralizado en una única ventana.
* **Usa la Paleta de Comandos:** Si olvidas cómo hacer algo o no recuerdas un atajo, presiona `Ctrl + Shift + P` e inténtalo buscar escribiendo lo que deseas hacer. Es el "buscador maestro" del editor.

---

## Checklist de preparación

Asegúrate de marcar todas las casillas antes de dar por concluido este capítulo:

* [ ] Entiendo la diferencia entre la Configuración Estándar y las Configuraciones de Cursor (IA).
* [ ] Configuré `Auto Save` en modo `afterDelay`.
* [ ] Activé `Format On Save` y `Word Wrap`.
* [ ] Instalé el tema de iconos `Material Icon Theme`.
* [ ] Instalé `Prettier`, `ESLint` y `Error Lens`.
* [ ] He verificado que **no** tengo extensiones de IA de terceros instaladas.
* [ ] Sé cómo abrir la terminal integrada y la Paleta de Comandos mediante atajos de teclado.

Si has completado todos los puntos con éxito, ¡tu espacio de trabajo está listo! Tienes una estación de programación de nivel profesional esperándote.

---

## Próximo capítulo

En el siguiente capítulo nos sumergiremos en el verdadero núcleo de este editor: **Cursor AI desde cero**.

Aprenderemos a utilizar de forma correcta y práctica:

* El **Chat** y sus atajos contextuales (`@files`, `@folders`).
* El **Inline Chat** (`Ctrl + K`) para editar código directamente en la línea seleccionada.
* **Composer** (`Ctrl + I`) para crear estructuras y proyectos multi-archivo de forma automatizada.
* El **Agent Mode** para resolver problemas complejos de forma guiada.
* Cómo redactar instrucciones (*prompts*) efectivas y cómo evitar depender ciegamente de la IA para convertirte en un desarrollador real y autosuficiente.
