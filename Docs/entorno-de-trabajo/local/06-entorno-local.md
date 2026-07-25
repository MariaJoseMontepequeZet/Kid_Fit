# PARTE I — ENTORNO DE DESARROLLO LOCAL

# Capítulo 6 — Anatomía de un proyecto Flutter

---

# 6. Introducción

Después de instalar el entorno de desarrollo y comprender las herramientas que lo componen, el siguiente paso consiste en conocer la estructura de un proyecto Flutter.

Cuando se crea una aplicación mediante Flutter, el framework genera automáticamente una serie de carpetas y archivos. Cada uno de ellos cumple una función específica dentro del proyecto.

Uno de los errores más comunes entre los desarrolladores principiantes es modificar archivos sin comprender su propósito. Esto puede provocar errores de compilación, pérdida de configuración o dificultades para mantener el proyecto.

En este capítulo se estudiará la organización interna de un proyecto Flutter, explicando la función de cada carpeta y archivo principal, así como las buenas prácticas para mantener una estructura clara y escalable.

Al finalizar este capítulo, el estudiante será capaz de identificar dónde debe escribir el código de la aplicación y qué elementos no deberían modificarse sin conocer su funcionamiento.

---

# 6.1 Creación de un proyecto Flutter

Todo proyecto Flutter comienza con el comando:

```bash id="flt6cmd01"
flutter create mi_aplicacion
```

Este comando genera automáticamente la estructura inicial del proyecto.

Proceso:

```text id="flt6a01"
flutter create

        │

        ▼

Generar estructura

        │

        ▼

Crear archivos

        │

        ▼

Proyecto listo
```

En pocos segundos se crea un proyecto completamente funcional.

---

# 6.2 Arquitectura general del proyecto

La estructura inicial de un proyecto Flutter es similar a la siguiente:

```text id="flt6a02"
mi_aplicacion/

│

├── android/

├── ios/

├── linux/

├── macos/

├── web/

├── windows/

├── lib/

├── test/

├── .dart_tool/

├── build/

├── pubspec.yaml

├── pubspec.lock

├── analysis_options.yaml

├── README.md

└── .gitignore
```

No todas estas carpetas tendrán la misma importancia para este proyecto.

---

# 6.3 ¿Qué carpetas utilizará este proyecto?

Aunque Flutter genera soporte para múltiples plataformas, en esta documentación el desarrollo estará orientado a Android.

Por ello, el trabajo diario se concentrará principalmente en:

```text id="flt6a03"
Proyecto Flutter

│

├── lib/

├── android/

├── test/

├── pubspec.yaml

├── analysis_options.yaml

└── README.md
```

Las demás carpetas forman parte del soporte multiplataforma y normalmente no requerirán modificaciones durante las primeras etapas del proyecto.

---

# 6.4 La carpeta `lib`

La carpeta **lib** es el corazón de cualquier aplicación Flutter.

Aquí se desarrolla prácticamente toda la lógica de negocio y la interfaz gráfica.

Arquitectura:

```text id="flt6a04"
lib/

│

├── main.dart

├── screens/

├── widgets/

├── models/

├── services/

├── repositories/

└── utils/
```

A medida que la aplicación crezca, esta carpeta contendrá la mayor parte del código fuente.

---

## ¿Qué contiene `main.dart`?

El archivo `main.dart` es el punto de entrada de la aplicación.

Cuando Flutter inicia un proyecto, este archivo es el primero en ejecutarse.

Flujo:

```text id="flt6a05"
Usuario

      │

      ▼

Aplicación Flutter

      │

      ▼

main.dart

      │

      ▼

runApp()

      │

      ▼

Interfaz principal
```

En aplicaciones reales, `main.dart` suele encargarse únicamente de realizar configuraciones iniciales y arrancar la aplicación.

---

# 6.5 La carpeta `android`

Esta carpeta contiene el proyecto Android generado automáticamente por Flutter.

```text id="flt6a06"
android/

│

├── app/

├── gradle/

├── build.gradle

├── settings.gradle

└── gradle.properties
```

Aquí se almacenan las configuraciones específicas de Android.

Durante el desarrollo cotidiano rara vez será necesario modificar estos archivos, salvo para integrar determinados servicios, como Firebase.

---

# 6.6 Las carpetas de otras plataformas

Flutter también genera carpetas para otros sistemas operativos.

```text id="flt6a07"
ios/

linux/

macos/

windows/

web/
```

Cada una contiene la configuración necesaria para ejecutar la aplicación en su plataforma correspondiente.

En este proyecto no se utilizarán activamente, pero forman parte de la estructura estándar de Flutter.

---

# 6.7 La carpeta `test`

Flutter incorpora soporte para pruebas automatizadas.

Las pruebas se almacenan dentro de:

```text id="flt6a08"
test/
```

Aquí pueden escribirse diferentes tipos de pruebas para verificar el funcionamiento de la aplicación.

Aunque este proyecto se centrará inicialmente en el desarrollo de funcionalidades, mantener esta carpeta organizada facilitará incorporar pruebas en etapas posteriores.

---

# 6.8 El archivo `pubspec.yaml`

Uno de los archivos más importantes del proyecto es:

```text id="flt6a09"
pubspec.yaml
```

Este archivo actúa como la configuración principal del proyecto.

Entre otras funciones permite definir:

* nombre de la aplicación;
* versión;
* dependencias;
* recursos gráficos;
* fuentes tipográficas;
* configuración general.

Arquitectura:

```text id="flt6a10"
pubspec.yaml

│

├── Información

├── Dependencias

├── Assets

├── Fonts

└── Configuración
```

Flutter consulta este archivo constantemente durante el desarrollo.

---

# 6.9 ¿Qué ocurre cuando ejecutamos `flutter pub get`?

Cada vez que se agregan nuevas dependencias al proyecto es necesario ejecutar:

```bash id="flt6cmd02"
flutter pub get
```

Este comando realiza el siguiente proceso:

```text id="flt6a11"
pubspec.yaml

        │

        ▼

Leer dependencias

        │

        ▼

Descargar paquetes

        │

        ▼

Actualizar proyecto

        │

        ▼

Aplicación lista
```

Por este motivo es uno de los comandos más utilizados durante el desarrollo.

---

# 6.10 El archivo `pubspec.lock`

Después de descargar las dependencias, Flutter genera automáticamente:

```text id="flt6a12"
pubspec.lock
```

Este archivo registra las versiones exactas de los paquetes instalados.

Su objetivo es garantizar que todos los desarrolladores del equipo trabajen con las mismas versiones de las dependencias.

Generalmente no debe modificarse manualmente.

---

# 6.11 El archivo `analysis_options.yaml`

Flutter utiliza este archivo para definir reglas de análisis del código.

Ejemplo de responsabilidades:

* reglas de estilo;
* advertencias;
* recomendaciones;
* análisis estático.

Arquitectura:

```text id="flt6a13"
Código Dart

      │

      ▼

Analysis Server

      │

analysis_options.yaml

      │

      ▼

Sugerencias
```

Este archivo ayuda a mantener un código uniforme y de mayor calidad.

---

# 6.12 El archivo `.gitignore`

Git utiliza este archivo para indicar qué elementos no deben almacenarse en el repositorio.

Ejemplos habituales:

* archivos temporales;
* compilaciones;
* cachés;
* configuraciones locales.

Arquitectura:

```text id="flt6a14"
Proyecto

      │

.gitignore

      │

      ▼

Git ignora archivos
```

Gracias a este mecanismo se evita incluir archivos innecesarios en el control de versiones.

---

# 6.13 La carpeta `.dart_tool`

Flutter genera automáticamente esta carpeta para almacenar información utilizada por las herramientas del SDK.

```text id="flt6a15"
.dart_tool/
```

Su contenido cambia constantemente durante el desarrollo.

No debe modificarse manualmente.

---

# 6.14 La carpeta `build`

Cuando la aplicación se compila, Flutter genera:

```text id="flt6a16"
build/
```

Esta carpeta contiene archivos temporales y artefactos de compilación.

Puede eliminarse en cualquier momento.

Flutter la volverá a generar automáticamente cuando sea necesario.

---

# 6.15 El archivo `README.md`

Este archivo contiene información general sobre el proyecto.

Puede incluir:

* descripción;
* instrucciones de instalación;
* estructura;
* dependencias;
* documentación técnica.

Mantener este documento actualizado facilita la incorporación de nuevos integrantes al equipo.

---

# 6.16 Organización recomendada para `lib`

Aunque Flutter únicamente crea `main.dart`, es recomendable organizar el código desde el inicio.

Ejemplo:

```text id="flt6a17"
lib/

│

├── main.dart

├── config/

├── core/

├── models/

├── repositories/

├── services/

├── screens/

├── widgets/

├── routes/

└── utils/
```

Una estructura organizada facilita el mantenimiento y el crecimiento del proyecto.

---

# 6.17 Flujo interno de una aplicación Flutter

Una aplicación Flutter sigue un flujo similar al siguiente:

```text id="flt6a18"
main.dart

      │

      ▼

runApp()

      │

      ▼

MaterialApp

      │

      ▼

Pantallas

      │

      ▼

Widgets

      │

      ▼

Usuario
```

Comprender este flujo permitirá entender con mayor facilidad la arquitectura de la aplicación en capítulos posteriores.

---

# 6.18 Archivos que normalmente no deben modificarse

Algunos archivos son gestionados automáticamente por Flutter.

Entre ellos:

* `.dart_tool`
* `build`
* `pubspec.lock` (salvo casos específicos)
* archivos internos de Gradle
* archivos generados automáticamente

Modificar estos elementos sin conocer su función puede provocar errores de compilación.

---

# 6.19 Buenas prácticas

Durante el desarrollo del proyecto se recomienda:

* mantener organizada la carpeta `lib`;
* utilizar nombres descriptivos para archivos y carpetas;
* separar la lógica de negocio de la interfaz;
* evitar colocar todo el código en `main.dart`;
* documentar la estructura del proyecto;
* no modificar archivos generados automáticamente sin una razón justificada.

---

# 6.20 Arquitectura completa del proyecto Flutter

Después de comprender la función de cada componente, la arquitectura general del proyecto puede representarse así:

```text id="flt6a19"
                 Proyecto Flutter

                        │

        ┌───────────────┼────────────────┐

        ▼               ▼                ▼

      lib/          android/          test/

        │

        ▼

    main.dart

        │

        ▼

   Pantallas

        │

        ▼

    Widgets

        │

        ▼

   Servicios

        │

        ▼

     Firebase
```

Esta estructura proporciona una base clara y escalable para desarrollar aplicaciones Flutter siguiendo buenas prácticas de organización.

---

# Conclusión del capítulo

La estructura generada por Flutter constituye el punto de partida para cualquier aplicación desarrollada con este framework. Conocer la función de cada carpeta y archivo permite trabajar con mayor seguridad, evitar modificaciones innecesarias y mantener el proyecto organizado a medida que crece.

En este capítulo se explicó la anatomía de un proyecto Flutter, el papel de directorios como `lib`, `android` y `test`, así como la importancia de archivos fundamentales como `pubspec.yaml`, `analysis_options.yaml` y `.gitignore`.

Con este conocimiento, el entorno de desarrollo está preparado para interactuar con un dispositivo Android físico. En el siguiente capítulo se configurará el teléfono para realizar pruebas mediante **depuración USB**, estableciendo el puente entre el proyecto Flutter y el dispositivo donde se ejecutará la aplicación.
