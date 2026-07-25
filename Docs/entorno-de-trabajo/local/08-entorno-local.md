# PARTE I — ENTORNO DE DESARROLLO LOCAL

# Capítulo 8 — Primer proyecto Flutter

---

# 8. Introducción

Después de preparar completamente el entorno de desarrollo, ha llegado el momento de crear la primera aplicación Flutter.

Hasta este punto se instalaron todas las herramientas necesarias:

* Flutter SDK.
* Android SDK.
* Cursor o Visual Studio Code.
* Git.
* Un dispositivo Android configurado para depuración USB.

En este capítulo se aprenderá a generar un proyecto Flutter desde cero, comprender la estructura inicial creada automáticamente por el framework, abrir el proyecto en el IDE y ejecutar la primera aplicación en un dispositivo Android.

El objetivo no es desarrollar una aplicación completa, sino verificar que todo el entorno funciona correctamente y comprender el flujo básico de trabajo que se utilizará durante el resto del proyecto.

---

# 8.1 El ciclo de desarrollo en Flutter

Antes de crear un proyecto es importante comprender el flujo de trabajo habitual.

Durante el desarrollo este ciclo se repetirá continuamente.

```text
Crear proyecto

      │

      ▼

Escribir código

      │

      ▼

Guardar cambios

      │

      ▼

Flutter compila

      │

      ▼

Aplicación actualizada

      │

      ▼

Continuar desarrollando
```

Una vez comprendido este ciclo, será mucho más sencillo trabajar con Flutter.

---

# 8.2 Crear un proyecto Flutter

La creación de un proyecto se realiza desde la terminal mediante el comando:

```bash
flutter create mi_primer_proyecto
```

Donde:

* `flutter` ejecuta las herramientas del SDK.
* `create` indica que se creará un nuevo proyecto.
* `mi_primer_proyecto` corresponde al nombre del proyecto.

Después de ejecutar el comando, Flutter generará automáticamente toda la estructura inicial.

---

# 8.3 ¿Qué ocurre internamente?

Aunque la creación parece instantánea, Flutter realiza varias tareas automáticamente.

```text
flutter create

       │

       ▼

Crear estructura

       │

       ▼

Generar archivos

       │

       ▼

Descargar dependencias

       │

       ▼

Configurar plataformas

       │

       ▼

Proyecto listo
```

Al finalizar, la aplicación estará lista para ejecutarse sin necesidad de configuraciones adicionales.

---

# 8.4 Elegir un nombre para el proyecto

Flutter utiliza el nombre del proyecto en diferentes partes de la aplicación.

Por ello conviene seguir algunas recomendaciones.

Se recomienda utilizar:

* letras minúsculas;
* guiones bajos (`_`);
* nombres descriptivos;
* palabras en inglés cuando sea posible.

Ejemplos correctos:

```text
agenda_personal

control_gastos

mi_primer_proyecto

tienda_virtual
```

Ejemplos que deben evitarse:

```text
Mi Proyecto

Proyecto Flutter

Mi-App

123Proyecto
```

Un nombre adecuado facilita el mantenimiento del proyecto y evita problemas durante la compilación.

---

# 8.5 Abrir el proyecto en el IDE

Una vez creado el proyecto, este debe abrirse en el IDE.

Proceso:

```text
Proyecto Flutter

       │

       ▼

Cursor / Visual Studio Code

       │

       ▼

Abrir carpeta

       │

       ▼

Indexar proyecto

       │

       ▼

Proyecto listo
```

Es importante abrir **la carpeta raíz del proyecto** y no únicamente algunos de sus archivos.

---

# 8.6 Primera sincronización del proyecto

La primera vez que se abre un proyecto Flutter, el IDE realiza diferentes tareas en segundo plano.

Entre ellas:

* indexar el código;
* iniciar el Dart Analysis Server;
* reconocer Flutter SDK;
* detectar el dispositivo conectado;
* preparar IntelliSense.

Es recomendable esperar unos segundos hasta que el proceso finalice antes de comenzar a trabajar.

---

# 8.7 Comprender el archivo `main.dart`

Flutter genera automáticamente un archivo denominado:

```text
lib/main.dart
```

Este archivo constituye el punto de entrada de la aplicación.

Flujo:

```text
main.dart

      │

      ▼

main()

      │

      ▼

runApp()

      │

      ▼

Widget principal

      │

      ▼

Interfaz
```

Durante las primeras prácticas la mayor parte del código se escribirá en este archivo.

En aplicaciones más grandes, el código se distribuirá entre diferentes carpetas y archivos para facilitar su mantenimiento.

---

# 8.8 Ejecutar la aplicación

Con el dispositivo Android conectado, la aplicación puede ejecutarse mediante:

```bash
flutter run
```

Flutter iniciará automáticamente el proceso de compilación.

Arquitectura:

```text
flutter run

       │

       ▼

Compilar proyecto

       │

       ▼

Generar APK

       │

       ▼

ADB instala aplicación

       │

       ▼

Android inicia aplicación

       │

       ▼

Flutter conecta depuración
```

La primera compilación suele tardar más tiempo porque Flutter debe preparar el proyecto y generar archivos temporales.

---

# 8.9 Verificar el dispositivo

Si existen varios dispositivos conectados, Flutter permite consultarlos mediante:

```bash
flutter devices
```

Ejemplo conceptual:

```text
2 connected devices

Android Device

Chrome
```

En este proyecto siempre se utilizará el dispositivo Android físico para las pruebas.

---

# 8.10 La primera ejecución

Cuando la compilación finaliza correctamente, la aplicación aparecerá instalada en el teléfono.

El resultado será la aplicación de ejemplo generada por Flutter.

Esta aplicación tiene como finalidad comprobar que:

* Flutter funciona correctamente;
* Android SDK está configurado;
* ADB establece la comunicación;
* el dispositivo responde adecuadamente.

Si la aplicación se ejecuta correctamente, el entorno local está completamente operativo.

---

# 8.11 ¿Qué hace Hot Reload?

Una de las características más importantes de Flutter es **Hot Reload**.

Permite actualizar la interfaz sin reiniciar completamente la aplicación.

Proceso:

```text
Modificar código

        │

        ▼

Guardar archivo

        │

        ▼

Hot Reload

        │

        ▼

Actualizar interfaz
```

Gracias a esta funcionalidad es posible observar cambios casi instantáneamente.

---

# 8.12 ¿Qué hace Hot Restart?

En algunas situaciones es necesario reiniciar completamente la aplicación.

Flutter ofrece para ello **Hot Restart**.

```text
Modificar lógica

        │

        ▼

Hot Restart

        │

        ▼

main()

        │

        ▼

Aplicación reiniciada
```

Hot Restart reinicia el estado completo de la aplicación y vuelve a ejecutar el método `main()`.

---

# 8.13 Detener la aplicación

Una vez finalizada la prueba, la ejecución puede detenerse desde la terminal donde se ejecutó `flutter run`.

Al hacerlo:

* se cierra la sesión de depuración;
* Flutter libera los recursos utilizados;
* la aplicación permanece instalada en el dispositivo, salvo que se desinstale manualmente.

---

# 8.14 Problemas frecuentes

## Flutter no encuentra el dispositivo

Verificar:

* conexión USB;
* depuración USB;
* autorización del dispositivo.

Comprobar con:

```bash
flutter devices
```

---

## Error durante la compilación

Generalmente ocurre porque:

* Android SDK está incompleto;
* existen dependencias sin descargar;
* hay errores en el proyecto.

Se recomienda ejecutar:

```bash
flutter doctor
```

para verificar el estado del entorno.

---

## El proyecto tarda demasiado en iniciar

La primera compilación siempre requiere más tiempo.

Las siguientes ejecuciones suelen ser considerablemente más rápidas gracias a la reutilización de archivos generados.

---

## El IDE muestra errores inmediatamente después de abrir el proyecto

Esperar a que finalice la indexación del proyecto y el análisis del código.

Durante este proceso pueden aparecer advertencias temporales que desaparecen una vez completada la sincronización.

---

# 8.15 Buenas prácticas

Durante el desarrollo inicial se recomienda:

* crear los proyectos dentro de una carpeta dedicada, por ejemplo `~/Development` o `C:\Development`;
* utilizar nombres descriptivos y consistentes;
* abrir siempre la carpeta raíz del proyecto;
* comprobar que `flutter doctor` no reporta errores antes de comenzar;
* ejecutar la aplicación en un dispositivo físico para validar el entorno;
* realizar cambios pequeños y verificar el funcionamiento mediante Hot Reload.

---

# 8.16 Flujo completo del primer proyecto

Después de completar este capítulo, el flujo de trabajo será el siguiente:

```text
Crear proyecto

        │

        ▼

Abrir en Cursor / VS Code

        │

        ▼

Conectar dispositivo

        │

        ▼

flutter run

        │

        ▼

Aplicación instalada

        │

        ▼

Modificar código

        │

        ▼

Hot Reload

        │

        ▼

Continuar desarrollando
```

Este será el flujo de trabajo habitual durante el desarrollo de aplicaciones Flutter.

---

# 8.17 Arquitectura del entorno completamente operativo

Con el primer proyecto ejecutándose correctamente, el entorno de desarrollo local queda completamente preparado.

```text
                    Desarrollador

                          │

                          ▼

          Cursor / Visual Studio Code

                          │

                          ▼

                  Proyecto Flutter

                          │

                          ▼

                     Flutter SDK

                          │

                          ▼

                     Android SDK

                          │

                          ▼

                          ADB

                          │

                          ▼

                 Dispositivo Android

                          │

                          ▼

              Aplicación Flutter en ejecución
```

A partir de este momento, el equipo dispone de un entorno funcional para comenzar el desarrollo de aplicaciones Flutter.

---

# Conclusión del capítulo

En este capítulo se creó el primer proyecto Flutter, se explicó cómo se genera su estructura inicial, cómo abrirlo correctamente en el IDE y cómo ejecutarlo en un dispositivo Android físico. Además, se presentó el flujo básico de trabajo que se repetirá durante todo el desarrollo: crear, ejecutar, modificar y verificar la aplicación mediante Hot Reload y Hot Restart.

Con el entorno completamente operativo, el siguiente capítulo se centrará en los comandos más utilizados de Flutter para gestionar proyectos, dependencias, compilaciones y tareas de mantenimiento, proporcionando una base sólida para el trabajo diario con el framework.
