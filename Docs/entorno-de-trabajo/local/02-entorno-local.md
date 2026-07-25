# PARTE I — ENTORNO DE DESARROLLO LOCAL

# Capítulo 2 — Flutter SDK

---

# 2. Introducción

Después de comprender cómo funciona el entorno de desarrollo de Flutter, el siguiente paso consiste en instalar su componente principal: el **Flutter SDK**.

El Flutter SDK reúne las herramientas necesarias para crear, compilar, ejecutar y depurar aplicaciones desarrolladas con Flutter. Además, incorpora el **Dart SDK**, por lo que no es necesario instalar el lenguaje Dart de forma independiente.

En este capítulo se explicará qué es el Flutter SDK, cómo está organizado internamente, cuáles son sus componentes principales y cómo instalarlo correctamente en Windows y Linux.

Al finalizar este capítulo el entorno dispondrá de un Flutter SDK completamente funcional y preparado para integrarse posteriormente con Android SDK y el IDE.

---

# 2.1 ¿Qué es Flutter?

Flutter es un **framework de desarrollo de aplicaciones multiplataforma** creado por Google.

Permite desarrollar una única base de código que posteriormente puede ejecutarse en diferentes plataformas, entre ellas:

* Android
* iOS
* Windows
* Linux
* macOS
* Web

Conceptualmente:

```text id="flt2a01"
               Código Flutter

                      │

                      ▼

               Framework Flutter

                      │

      ┌───────────────┼───────────────┐

      ▼               ▼               ▼

   Android          Windows          Linux

```

En este proyecto el objetivo será desarrollar aplicaciones para **Android**, utilizando un dispositivo físico para las pruebas.

---

# 2.2 ¿Qué es el Flutter SDK?

El **Software Development Kit (SDK)** de Flutter es el conjunto de herramientas necesarias para desarrollar aplicaciones.

No se trata únicamente del comando `flutter`.

El SDK incluye:

* Framework Flutter.
* Dart SDK.
* Herramientas de compilación.
* Herramientas de depuración.
* Plantillas de proyectos.
* Gestor de dependencias.
* Utilidades de línea de comandos.

Arquitectura:

```text id="flt2a02"
              Flutter SDK

                     │

      ┌──────────────┼──────────────┐

      ▼              ▼              ▼

 Framework      Dart SDK      Herramientas CLI

      │              │              │

      ▼              ▼              ▼

 Widgets       Compilador      flutter doctor

                              flutter run

                              flutter create

                              flutter pub
```

---

# 2.3 Flutter vs Dart

Una duda frecuente entre quienes comienzan es la diferencia entre Flutter y Dart.

Aunque trabajan juntos, cumplen funciones diferentes.

## Dart

Es el lenguaje de programación.

Con Dart se escriben:

* variables;
* funciones;
* clases;
* objetos;
* lógica del programa.

Ejemplo:

```dart
void main() {
  print("Hola Flutter");
}
```

---

## Flutter

Es el framework.

Su responsabilidad consiste en construir la interfaz gráfica y proporcionar componentes reutilizables.

Ejemplo conceptual:

```text id="flt2a03"
Dart

↓

Lógica

↓

Flutter

↓

Interfaz

↓

Aplicación
```

En otras palabras:

* **Dart dice qué debe hacer la aplicación.**
* **Flutter define cómo se presenta al usuario.**

---

# 2.4 Componentes internos del Flutter SDK

Aunque normalmente se instala como una única herramienta, el SDK está formado por varios componentes.

```text id="flt2a04"
Flutter SDK

│

├── bin

├── packages

├── examples

├── cache

├── Dart SDK

└── Herramientas Flutter
```

---

## Carpeta `bin`

Contiene el ejecutable principal de Flutter.

Es el directorio que posteriormente se agregará al `PATH` del sistema operativo.

---

## Dart SDK

Incluye:

* compilador;
* bibliotecas estándar;
* herramientas de análisis;
* gestor de paquetes.

---

## Cache

Almacena archivos descargados automáticamente.

Ejemplos:

* motores de Flutter;
* artefactos de compilación;
* herramientas auxiliares.

---

## Packages

Contiene paquetes internos utilizados por Flutter.

---

# 2.5 ¿Qué hace realmente el comando `flutter`?

Cuando se escribe un comando como:

```bash
flutter run
```

no ocurre una única acción.

Flutter ejecuta una secuencia de tareas.

```text id="flt2a05"
Comando Flutter

        │

        ▼

Analiza parámetros

        │

        ▼

Verifica SDK

        │

        ▼

Carga proyecto

        │

        ▼

Ejecuta herramienta solicitada

        │

        ▼

Muestra resultado
```

Por ello, un único comando puede realizar múltiples operaciones automáticamente.

---

# 2.6 Canales de Flutter

Flutter dispone de diferentes canales de distribución.

Cada canal ofrece un nivel distinto de estabilidad.

| Canal  | Características                           |
| ------ | ----------------------------------------- |
| Stable | Recomendado para producción y aprendizaje |
| Beta   | Funcionalidades próximas a liberarse      |
| Main   | Desarrollo activo del proyecto            |

Para este proyecto se utilizará siempre el canal:

```text id="flt2a06"
Stable
```

Esto garantiza mayor estabilidad y compatibilidad con la documentación.

---

# 2.7 Instalación del Flutter SDK

La instalación consiste en descargar el SDK oficial y ubicarlo en una carpeta permanente del sistema.

Proceso general:

```text id="flt2a07"
Descargar Flutter

        │

        ▼

Extraer archivos

        │

        ▼

Ubicar SDK

        │

        ▼

Configurar PATH

        │

        ▼

Verificar instalación
```

---

# 2.8 Instalación en Windows

## Paso 1. Descargar Flutter

Descargar la versión **Stable** desde el sitio oficial de Flutter.

---

## Paso 2. Extraer el SDK

Se recomienda utilizar una ubicación sencilla.

Ejemplo:

```text
C:\flutter
```

Evitar instalar Flutter dentro de:

```text
C:\Program Files
```

ya que algunas configuraciones pueden requerir permisos adicionales.

---

## Paso 3. Configurar la variable PATH

Agregar al PATH del sistema la carpeta:

```text
C:\flutter\bin
```

Esto permitirá ejecutar Flutter desde cualquier terminal.

Arquitectura:

```text id="flt2a08"
Terminal

     │

     ▼

PATH

     │

     ▼

C:\flutter\bin

     │

     ▼

flutter
```

---

# 2.9 Instalación en Linux

## Paso 1. Descargar Flutter

Descargar la versión Stable.

---

## Paso 2. Extraer el SDK

Ubicar el SDK en una carpeta permanente.

Ejemplo:

```text
~/development/flutter
```

---

## Paso 3. Configurar PATH

Agregar al archivo correspondiente del intérprete de comandos la ruta del SDK.

Ejemplo conceptual:

```text
PATH

↓

~/development/flutter/bin
```

Después de guardar los cambios será necesario recargar la configuración de la terminal o iniciar una nueva sesión.

---

# 2.10 Verificación de la instalación

La forma más sencilla de comprobar que Flutter está correctamente instalado es ejecutar:

```bash
flutter --version
```

Si la instalación fue correcta se mostrará información similar a:

```text
Flutter x.x.x

Dart x.x.x
```

Esto confirma que el SDK puede ejecutarse desde la terminal.

---

# 2.11 ¿Qué hace `flutter doctor`?

Uno de los comandos más importantes del SDK es:

```bash
flutter doctor
```

Muchos desarrolladores lo ejecutan sin conocer realmente su función.

Este comando realiza un diagnóstico completo del entorno de desarrollo.

Proceso interno:

```text id="flt2a09"
flutter doctor

      │

      ▼

Busca Flutter SDK

      │

      ▼

Busca Dart SDK

      │

      ▼

Busca Android SDK

      │

      ▼

Busca Git

      │

      ▼

Busca dispositivos

      │

      ▼

Genera informe
```

El objetivo es detectar configuraciones incompletas antes de comenzar a desarrollar.

---

# 2.12 Interpretación del resultado

El informe utiliza indicadores visuales para mostrar el estado de cada componente.

```text
✓ Correctamente configurado

!

Configuración parcial

✗ Requiere atención
```

La meta es que todos los componentes aparezcan correctamente configurados antes de continuar con la instalación del resto del entorno.

---

# 2.13 Comandos básicos del Flutter SDK

Durante el desarrollo se utilizarán con frecuencia los siguientes comandos.

| Comando             | Función                          |
| ------------------- | -------------------------------- |
| `flutter doctor`    | Diagnosticar el entorno          |
| `flutter --version` | Mostrar la versión instalada     |
| `flutter create`    | Crear un nuevo proyecto          |
| `flutter run`       | Ejecutar la aplicación           |
| `flutter devices`   | Mostrar dispositivos disponibles |
| `flutter clean`     | Limpiar archivos temporales      |
| `flutter analyze`   | Analizar el código               |
| `flutter pub get`   | Descargar dependencias           |

Cada uno de estos comandos será estudiado con mayor profundidad en capítulos posteriores.

---

# 2.14 Problemas frecuentes

## El comando `flutter` no existe

Posibles causas:

* PATH incorrecto.
* Terminal sin reiniciar.
* SDK no instalado.

---

## Flutter Doctor muestra errores

Posibles causas:

* Android SDK inexistente.
* Git no instalado.
* Licencias pendientes.

Estos problemas se resolverán en los siguientes capítulos.

---

## Se instalaron varias versiones de Flutter

No es recomendable mantener múltiples instalaciones del SDK si aún se está aprendiendo.

Durante este proyecto se utilizará una única instalación del canal **Stable** para evitar conflictos.

---

# 2.15 Buenas prácticas

Para mantener un entorno estable se recomienda:

* utilizar siempre el canal **Stable**;
* instalar Flutter en una ubicación permanente;
* evitar mover la carpeta del SDK después de configurar el `PATH`;
* verificar periódicamente el entorno con `flutter doctor`;
* mantener una única instalación activa del SDK;
* consultar la documentación oficial antes de realizar actualizaciones importantes.

---

# 2.16 Arquitectura del entorno después de instalar Flutter

Una vez instalado el SDK, la arquitectura del entorno queda de la siguiente forma:

```text id="flt2a10"
                Desarrollador

                      │

                      ▼

            Cursor / Visual Studio Code

                      │

                      ▼

                 Flutter SDK

          ┌───────────┴───────────┐

          ▼                       ▼

     Dart SDK              Herramientas CLI

          │

          ▼

     Código Flutter
```

En los siguientes capítulos se incorporará el **Android SDK**, que permitirá compilar y ejecutar la aplicación en dispositivos Android.

---

# Conclusión del capítulo

El Flutter SDK constituye el núcleo del entorno de desarrollo y proporciona todas las herramientas necesarias para crear aplicaciones con Flutter.

En este capítulo se explicó su arquitectura, los componentes que lo integran, la diferencia entre Flutter y Dart, el propósito de los principales comandos y el procedimiento general para instalarlo y verificar su funcionamiento tanto en Windows como en Linux.

Con el SDK correctamente instalado, el siguiente paso será preparar el entorno Android mediante la instalación y configuración del **Android SDK**, componente indispensable para compilar y ejecutar aplicaciones en dispositivos Android físicos.
