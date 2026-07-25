# PARTE I — ENTORNO DE DESARROLLO LOCAL

# Capítulo 1 — Arquitectura del entorno de desarrollo Flutter

---

# 1. Introducción

Antes de escribir la primera línea de código o instalar cualquier herramienta, es importante comprender cómo funciona el entorno de desarrollo de Flutter.

Muchos problemas que aparecen durante el desarrollo no se deben a errores en la programación, sino a una configuración incorrecta del entorno de trabajo. Comprender cómo interactúan las diferentes herramientas permitirá diagnosticar incidencias con mayor facilidad y trabajar de forma más eficiente.

En este capítulo se presenta la arquitectura completa del entorno de desarrollo utilizado en este proyecto, identificando el propósito de cada componente y la forma en que colaboran durante la creación, compilación y ejecución de una aplicación Flutter.

Al finalizar este capítulo, el lector comprenderá el flujo general del desarrollo antes de comenzar con la instalación del software necesario.

---

# 1.1 ¿Qué es un entorno de desarrollo?

Un **entorno de desarrollo** es el conjunto de herramientas, programas y configuraciones que permiten crear, ejecutar, depurar y mantener una aplicación.

En Flutter, el entorno de desarrollo está compuesto por varias herramientas que trabajan de forma coordinada. Cada una cumple una función específica y ninguna sustituye a las demás.

Por ejemplo:

* El **IDE** permite escribir el código.
* El **Flutter SDK** compila la aplicación.
* El **Dart SDK** interpreta el lenguaje Dart.
* El **Android SDK** prepara la aplicación para dispositivos Android.
* **ADB** instala y ejecuta la aplicación en un dispositivo físico.

Aunque el desarrollador interactúa principalmente con el IDE, detrás de cada acción intervienen múltiples componentes.

---

# 1.2 Arquitectura general del entorno Flutter

La arquitectura del entorno de desarrollo utilizada en este proyecto es la siguiente:

```text
                      Desarrollador

                            │

                            ▼

               Cursor o Visual Studio Code

                            │

                            ▼

                    Flutter Extension

                            │

                            ▼

                     Flutter SDK

                            │

                ┌───────────┴───────────┐

                ▼                       ▼

            Dart SDK              Android SDK

                │                       │

                └───────────┬───────────┘

                            ▼

                           ADB

                            │

                            ▼

                  Dispositivo Android

                            │

                            ▼

                 Aplicación Flutter
```

Esta arquitectura representa el flujo principal utilizado durante el desarrollo local del proyecto.

---

# 1.3 Componentes del entorno

## Desarrollador

Es la persona que diseña, programa, prueba y mantiene la aplicación.

Todas las acciones comienzan con una instrucción del desarrollador, como escribir código, ejecutar un comando o iniciar una depuración.

---

## IDE

El **Entorno de Desarrollo Integrado (IDE)** es la aplicación utilizada para escribir y administrar el código fuente.

En este proyecto se utilizarán dos opciones:

* Cursor.
* Visual Studio Code.

Ambos utilizan prácticamente el mismo sistema de extensiones y permiten trabajar con Flutter de manera muy similar.

---

## Flutter SDK

El Flutter SDK es el conjunto principal de herramientas necesarias para desarrollar aplicaciones Flutter.

Entre sus responsabilidades se encuentran:

* crear proyectos;
* compilar aplicaciones;
* ejecutar pruebas;
* administrar dependencias;
* comunicarse con Android SDK;
* generar versiones de depuración y producción.

El Flutter SDK constituye el núcleo del entorno de desarrollo.

---

## Dart SDK

Flutter utiliza el lenguaje de programación Dart.

El Dart SDK incluye el compilador, las bibliotecas estándar y las herramientas necesarias para transformar el código fuente en una aplicación ejecutable.

El desarrollador no instala Dart por separado, ya que se distribuye junto con Flutter.

---

## Android SDK

El Android SDK proporciona las herramientas necesarias para construir aplicaciones destinadas al sistema operativo Android.

Entre sus componentes más importantes se encuentran:

* Platform Tools;
* Build Tools;
* SDK Manager;
* herramientas de compilación.

En este proyecto será utilizado principalmente para generar aplicaciones Android y comunicarse con dispositivos físicos.

---

## Android Debug Bridge (ADB)

ADB es una herramienta incluida en Android SDK que permite la comunicación entre la computadora y un dispositivo Android.

Gracias a ADB es posible:

* detectar dispositivos conectados;
* instalar aplicaciones;
* iniciar procesos de depuración;
* consultar registros del sistema.

Flutter utiliza ADB de forma automática cuando se ejecuta una aplicación en un dispositivo físico.

---

# 1.4 Flujo general del desarrollo

Cuando el desarrollador ejecuta una aplicación Flutter ocurre el siguiente proceso:

```text
Escribir código

        │

        ▼

Guardar archivo

        │

        ▼

Flutter analiza cambios

        │

        ▼

Compila código Dart

        │

        ▼

Android SDK genera aplicación

        │

        ▼

ADB instala la aplicación

        │

        ▼

La aplicación inicia en el dispositivo
```

Aunque el proceso parece simple desde el IDE, internamente participan varias herramientas de manera coordinada.

---

# 1.5 ¿Qué ocurre cuando ejecutamos `flutter run`?

El comando `flutter run` inicia una secuencia automatizada de tareas.

De forma simplificada, el flujo es el siguiente:

```text
flutter run

      │

      ▼

Verifica Flutter SDK

      │

      ▼

Verifica Dart SDK

      │

      ▼

Lee pubspec.yaml

      │

      ▼

Compila el proyecto

      │

      ▼

Utiliza Android SDK

      │

      ▼

ADB instala la aplicación

      │

      ▼

Conecta Hot Reload

      │

      ▼

Aplicación lista para depuración
```

Comprender este flujo facilitará el diagnóstico de errores que puedan aparecer durante el desarrollo.

---

# 1.6 Herramientas que se instalarán

A lo largo de esta primera parte se preparará el siguiente entorno de trabajo:

| Herramienta                   | Propósito                                        |
| ----------------------------- | ------------------------------------------------ |
| Git                           | Control de versiones y gestión del código fuente |
| Flutter SDK                   | Desarrollo de aplicaciones Flutter               |
| Android SDK                   | Compilación para Android                         |
| Cursor o Visual Studio Code   | Edición y depuración del código                  |
| Extensiones de Flutter y Dart | Integración del SDK con el IDE                   |
| ADB                           | Comunicación con dispositivos Android            |

Cada una será instalada y configurada en capítulos posteriores.

---

# 1.7 Requisitos generales

Para seguir esta documentación se recomienda disponer de:

**Hardware**

* Procesador de 64 bits con soporte para virtualización (aunque no se utilizarán emuladores).
* 8 GB de memoria RAM como mínimo (16 GB recomendados).
* Al menos 20 GB de espacio libre en disco.
* Un dispositivo Android físico con cable USB para realizar pruebas.

**Software**

* Windows 11 o una distribución Linux compatible.
* Git.
* Flutter SDK.
* Android SDK.
* Cursor o Visual Studio Code.

---

# 1.8 Buenas prácticas antes de comenzar

Antes de instalar cualquier herramienta se recomienda:

* mantener el sistema operativo actualizado;
* utilizar una cuenta con permisos de instalación;
* disponer de una conexión estable a Internet;
* evitar instalar múltiples versiones de Flutter simultáneamente;
* seguir el orden de instalación definido en esta documentación.

Una preparación adecuada reducirá significativamente los problemas de configuración.

---

# Conclusión del capítulo

En este capítulo se presentó la arquitectura general del entorno de desarrollo Flutter y el papel que desempeña cada una de las herramientas que se utilizarán durante el proyecto.

Comprender cómo interactúan el IDE, Flutter SDK, Dart SDK, Android SDK y ADB proporciona una base sólida para afrontar la instalación y configuración del entorno con mayor seguridad.

En el siguiente capítulo se estudiará en profundidad el **Flutter SDK**, su estructura interna, los componentes que incluye y el procedimiento completo para instalarlo y configurarlo correctamente en Windows y Linux.
