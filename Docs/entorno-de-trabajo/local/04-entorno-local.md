# PARTE I — ENTORNO DE DESARROLLO LOCAL

# Capítulo 4 — IDEs para Flutter

---

# 4. Introducción

Hasta este punto del entorno de desarrollo ya se dispone del **Flutter SDK** y del **Android SDK**, los cuales proporcionan las herramientas necesarias para crear y compilar aplicaciones.

Sin embargo, aún falta el componente con el que el desarrollador interactuará durante la mayor parte del tiempo: el **Entorno de Desarrollo Integrado (IDE)**.

En este proyecto se utilizarán dos alternativas:

* **Cursor**
* **Visual Studio Code**

Ambos están construidos sobre la misma base tecnológica y ofrecen una experiencia muy similar para el desarrollo con Flutter. Por este motivo, la configuración realizada en este capítulo será prácticamente idéntica para ambos.

El objetivo no es aprender un IDE específico, sino preparar un entorno moderno que facilite la escritura de código, la depuración, el control de versiones y el desarrollo profesional de aplicaciones Flutter.

---

# 4.1 ¿Qué es un IDE?

Un **IDE (Integrated Development Environment)** es una aplicación que reúne las herramientas necesarias para desarrollar software desde un único lugar.

Aunque es posible crear una aplicación utilizando únicamente un editor de texto y la terminal, un IDE simplifica enormemente el trabajo diario al integrar funciones como:

* edición de código;
* resaltado de sintaxis;
* autocompletado;
* depuración;
* terminal integrada;
* administración de archivos;
* integración con Git;
* ejecución de aplicaciones.

Arquitectura conceptual:

```text id="ide4a01"
                 Desarrollador

                       │

                       ▼

                     IDE

      ┌───────────────┼───────────────┐

      ▼               ▼               ▼

 Editor          Terminal          Git

      │               │               │

      └───────────────┼───────────────┘

                      ▼

                 Proyecto Flutter
```

El IDE se convierte en el punto central desde el cual el desarrollador interactúa con todas las herramientas del proyecto.

---

# 4.2 ¿Por qué utilizar un IDE?

Flutter puede desarrollarse utilizando diferentes editores de código.

Sin embargo, un IDE aporta ventajas importantes:

* reduce errores de escritura;
* facilita la navegación entre archivos;
* identifica problemas antes de ejecutar la aplicación;
* acelera la escritura mediante autocompletado;
* permite depurar aplicaciones paso a paso;
* integra Git y la terminal en una única interfaz.

Estas funcionalidades mejoran la productividad y permiten concentrarse en el desarrollo de la aplicación.

---

# 4.3 Cursor y Visual Studio Code

En este proyecto se han seleccionado dos IDE ampliamente utilizados.

## Cursor

Cursor es un IDE moderno basado en Visual Studio Code que incorpora herramientas de asistencia para el desarrollo y mantiene compatibilidad con la mayoría de sus extensiones.

Es especialmente útil para proyectos modernos y equipos que desean aprovechar herramientas de asistencia durante la programación.

---

## Visual Studio Code

Visual Studio Code es uno de los editores de código más utilizados para el desarrollo de Flutter.

Dispone de un amplio ecosistema de extensiones y una excelente integración con Flutter y Dart.

---

## ¿Cuál utilizar?

Para este proyecto cualquiera de los dos es válido.

La documentación utilizará procedimientos compatibles con ambos.

---

# 4.4 Arquitectura del entorno con un IDE

Una vez instalado el IDE, el entorno queda organizado de la siguiente manera:

```text id="ide4a02"
                Desarrollador

                      │

                      ▼

        Cursor o Visual Studio Code

                      │

                      ▼

          Extensiones Flutter y Dart

                      │

                      ▼

                 Flutter SDK

                      │

                      ▼

                 Android SDK

                      │

                      ▼

             Dispositivo Android
```

El IDE actúa como intermediario entre el desarrollador y las herramientas instaladas en capítulos anteriores.

---

# 4.5 Instalación del IDE

El proceso general consiste en:

```text id="ide4a03"
Descargar IDE

      │

      ▼

Instalar

      │

      ▼

Abrir aplicación

      │

      ▼

Instalar extensiones

      │

      ▼

Configurar Flutter
```

La instalación es similar tanto en Windows como en Linux.

---

# 4.6 Extensiones para Flutter

El IDE obtiene la mayor parte de sus funcionalidades mediante extensiones.

Para este proyecto se recomienda instalar las siguientes.

| Extensión | Propósito                              |
| --------- | -------------------------------------- |
| Flutter   | Integración del SDK Flutter con el IDE |
| Dart      | Soporte para el lenguaje Dart          |

Estas dos extensiones son indispensables.

Sin ellas el IDE no podrá reconocer correctamente un proyecto Flutter.

---

# 4.7 ¿Qué hace la extensión Flutter?

Muchos principiantes creen que la extensión Flutter instala Flutter.

Esto no es correcto.

Flutter ya fue instalado en el capítulo anterior.

La extensión únicamente conecta el IDE con el Flutter SDK.

Arquitectura:

```text id="ide4a04"
IDE

     │

Flutter Extension

     │

Flutter SDK

     │

Proyecto Flutter
```

Gracias a esta integración el IDE puede:

* ejecutar la aplicación;
* detectar dispositivos;
* mostrar errores;
* iniciar la depuración;
* utilizar Hot Reload.

---

# 4.8 ¿Qué hace la extensión Dart?

La extensión Dart proporciona soporte para el lenguaje utilizado por Flutter.

Entre sus funciones destacan:

* coloreado de sintaxis;
* autocompletado;
* análisis de errores;
* navegación entre clases;
* formateo automático del código;
* refactorización.

Arquitectura:

```text id="ide4a05"
Código Dart

      │

      ▼

Extensión Dart

      │

      ▼

Analysis Server

      │

      ▼

IDE
```

---

# 4.9 Dart Analysis Server

Una de las herramientas más importantes que utilizan Flutter y Dart es el **Dart Analysis Server**.

Su función consiste en analizar continuamente el código mientras el desarrollador escribe.

Proceso:

```text id="ide4a06"
Escribir código

        │

        ▼

Analysis Server

        │

        ├── Detecta errores

        ├── Sugiere mejoras

        ├── Autocompleta código

        └── Actualiza el IDE
```

Gracias a este proceso muchos errores pueden corregirse antes de ejecutar la aplicación.

---

# 4.10 IntelliSense

El sistema de autocompletado del IDE recibe el nombre de **IntelliSense**.

Su objetivo es acelerar la escritura del código mostrando:

* variables;
* métodos;
* clases;
* widgets;
* documentación;
* parámetros.

Ejemplo conceptual:

```text id="ide4a07"
Escribir:

Cont...

        │

        ▼

IDE sugiere

Container

Context

Controller
```

Esto reduce errores de escritura y facilita el aprendizaje de nuevas bibliotecas.

---

# 4.11 Terminal integrada

Cursor y Visual Studio Code incorporan una terminal integrada.

Desde ella es posible ejecutar todos los comandos de Flutter sin abandonar el IDE.

Ejemplos:

Mostrar la versión instalada:

```bash id="ide4cmd01"
flutter --version
```

Diagnosticar el entorno:

```bash id="ide4cmd02"
flutter doctor
```

Mostrar dispositivos:

```bash id="ide4cmd03"
flutter devices
```

La terminal integrada utiliza los mismos comandos que una terminal convencional.

---

# 4.12 Explorador de archivos

El explorador permite administrar la estructura del proyecto.

Ejemplo:

```text id="ide4a08"
Proyecto Flutter

│

├── lib

├── android

├── ios

├── linux

├── web

├── test

└── pubspec.yaml
```

En capítulos posteriores se estudiará detalladamente la función de cada uno de estos elementos.

---

# 4.13 Integración con Git

Ambos IDE incorporan herramientas para trabajar con Git sin abandonar el editor.

Entre las operaciones más comunes se encuentran:

* visualizar cambios;
* confirmar modificaciones (*commit*);
* sincronizar repositorios;
* resolver conflictos;
* cambiar de rama.

Arquitectura:

```text id="ide4a09"
Proyecto Flutter

        │

        ▼

Git

        │

        ▼

Repositorio remoto
```

Aunque estas funciones pueden ejecutarse desde la interfaz gráfica, también es recomendable conocer los comandos de Git desde la terminal.

---

# 4.14 Depuración de aplicaciones

Una de las funciones más importantes del IDE es la depuración.

Durante una sesión de depuración es posible:

* ejecutar la aplicación;
* inspeccionar variables;
* detener la ejecución;
* analizar errores;
* reiniciar la aplicación.

Arquitectura:

```text id="ide4a10"
IDE

     │

Flutter Debugger

     │

Flutter SDK

     │

Aplicación

     │

Dispositivo Android
```

En este proyecto la depuración se realizará utilizando un dispositivo Android físico conectado mediante USB.

---

# 4.15 Configuración recomendada

Para mantener un entorno uniforme en todo el equipo de desarrollo se recomienda:

* utilizar un único tema de color durante las prácticas;
* activar el guardado automático del código;
* habilitar el formateo automático al guardar;
* mantener actualizadas las extensiones;
* evitar instalar extensiones que no sean necesarias para el proyecto.

Una configuración sencilla facilita el aprendizaje y reduce posibles conflictos.

---

# 4.16 Problemas frecuentes

## Flutter no aparece en el IDE

Posibles causas:

* Flutter SDK no está instalado.
* El `PATH` no está configurado correctamente.
* La extensión Flutter no está instalada.

---

## El IDE no reconoce Dart

Generalmente ocurre porque la extensión Dart no está instalada o está deshabilitada.

---

## No aparece el botón para ejecutar la aplicación

Comprobar:

* que el proyecto Flutter esté abierto correctamente;
* que Flutter SDK sea reconocido por el IDE;
* que exista un dispositivo Android conectado.

---

## El autocompletado no funciona

Verificar:

* instalación de la extensión Dart;
* instalación de la extensión Flutter;
* que el proyecto haya terminado de indexarse.

---

# 4.17 Buenas prácticas

Durante el desarrollo del proyecto se recomienda:

* trabajar siempre con un único IDE;
* mantener actualizadas las extensiones;
* utilizar la terminal integrada para ejecutar comandos Flutter;
* aprovechar IntelliSense antes de escribir código manualmente;
* revisar los avisos del Analysis Server antes de ejecutar la aplicación;
* mantener organizada la estructura del proyecto.

---

# 4.18 Arquitectura del entorno después de configurar el IDE

Con el IDE configurado, el entorno de desarrollo queda prácticamente preparado para comenzar a programar.

```text id="ide4a11"
                Desarrollador

                      │

                      ▼

        Cursor / Visual Studio Code

                      │

          Flutter Extension

                      │

           Dart Extension

                      │

          Dart Analysis Server

                      │

                 Flutter SDK

                      │

                 Android SDK

                      │

                      ▼

              Dispositivo Android
```

En el siguiente capítulo se incorporará Git como sistema de control de versiones, permitiendo gestionar el código fuente del proyecto y colaborar de forma organizada con otros desarrolladores.

---

# Conclusión del capítulo

El IDE es la herramienta con la que el desarrollador interactúa durante la mayor parte del tiempo. Aunque Cursor y Visual Studio Code presentan diferencias en su interfaz y funcionalidades adicionales, ambos ofrecen una integración prácticamente idéntica con Flutter gracias a las extensiones oficiales.

En este capítulo se explicó qué es un IDE, cómo se integra con el Flutter SDK, cuál es el papel de las extensiones Flutter y Dart, cómo funciona el **Dart Analysis Server** y qué herramientas proporciona el editor para facilitar el desarrollo, la depuración y el control del código.

Con esta configuración, el entorno de desarrollo está listo para incorporar el sistema de control de versiones y comenzar a trabajar de forma organizada en el proyecto.
