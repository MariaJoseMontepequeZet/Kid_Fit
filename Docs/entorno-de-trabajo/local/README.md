# PARTE I — ENTORNO LOCAL

## Objetivo de esta parte

Esta sección tiene como finalidad preparar completamente el entorno de desarrollo local necesario para trabajar en el proyecto. Al finalizar esta parte, cualquier integrante del equipo será capaz de:

* Configurar Flutter correctamente.
* Verificar que todas las herramientas funcionan.
* Clonar el proyecto.
* Abrir el proyecto en Visual Studio Code o Cursor.
* Conectar un dispositivo Android físico mediante USB.
* Ejecutar la aplicación.
* Utilizar Hot Reload y Hot Restart.
* Resolver los problemas más frecuentes durante la configuración inicial.

Esta documentación **no utiliza emuladores Android** como flujo principal de desarrollo. Todas las pruebas se realizarán utilizando un dispositivo Android físico conectado mediante un cable USB, ya que este método ofrece un mejor rendimiento, reduce el consumo de recursos del computador y refleja con mayor precisión el comportamiento real de la aplicación.

---

# Estructura propuesta

## PARTE I — ENTORNO DE DESARROLLO LOCAL

### Capítulo 1 — Arquitectura del entorno de desarrollo Flutter

> Antes de instalar cualquier herramienta, el estudiante comprenderá cómo funciona todo el ecosistema Flutter.

* 1. Introducción
* 1.1 ¿Qué es un entorno de desarrollo?
* 1.2 Arquitectura general del entorno Flutter
* 1.3 Componentes del entorno
* 1.4 Flujo completo de desarrollo
* 1.5 ¿Qué ocurre cuando ejecutamos `flutter run`?
* 1.6 Herramientas que instalará el estudiante
* 1.7 Requisitos de hardware y software
* 1.8 Buenas prácticas antes de comenzar
* Conclusión

---

### Capítulo 2 — Flutter SDK

No solamente instalar.

También comprender.

* ¿Qué es Flutter?
* ¿Qué contiene el SDK?
* Flutter vs Dart
* Canales Stable/Beta
* Instalación Windows
* Instalación Linux
* Variables PATH
* flutter doctor explicado
* Problemas frecuentes

---

### Capítulo 3 — Android Studio y Android SDK

Aquí quitaría mucho contenido innecesario.

En este proyecto Android Studio será únicamente un proveedor del Android SDK.

Explicar:

* Android SDK
* Platform Tools
* Build Tools
* ADB
* Licencias
* SDK Manager

---

### Capítulo 4 — IDEs para Flutter

Unificar VS Code y Cursor.

Explicar:

* ¿Qué es un IDE?
* Cursor
* VS Code
* Diferencias
* Extensiones
* Configuración recomendada
* Flutter dentro del IDE
* Dart Analysis Server
* IntelliSense

---

### Capítulo 5 — Git y control de versiones

Mucho más orientado al proyecto.

* Git
* GitHub
* SSH
* Clonar
* Pull
* Push
* Branch
* Flujo del proyecto

---

### Capítulo 6 — Anatomía de un proyecto Flutter

Uno de los capítulos más importantes.

Explicar:

```text
lib/

android/

ios/

linux/

windows/

web/

test/

pubspec.yaml

analysis_options.yaml
```

Y explicar absolutamente todo.

---

### Capítulo 7 — Preparación del dispositivo Android

No hablar todavía de programar.

Explicar:

* USB Debugging
* Opciones de desarrollador
* ADB
* Detectar dispositivo
* Drivers (Windows)
* udev (Linux)

---

### Capítulo 8 — Primer proyecto Flutter

Aquí sí.

```bash
flutter create
```

Explicar:

Qué genera.

Qué carpetas aparecen.

Cómo abrirlo.

Cómo ejecutarlo.

---

### Capítulo 9 — Compilación y depuración

Explicar:

* flutter run
* flutter clean
* flutter pub get
* flutter pub upgrade
* flutter analyze
* Hot Reload
* Hot Restart

---

### Capítulo 10 — Recursos oficiales y documentación

Algo corto.

Con enlaces oficiales:

* Flutter Docs
* Cookbook
* Dart
* Firebase
* Android Developers
* pub.dev

Como el "MDN" de Flutter.

---

## Justificación del uso de dispositivos físicos

Como política del proyecto, las pruebas de desarrollo se realizarán utilizando dispositivos Android físicos conectados mediante un cable USB.

Esta decisión responde a criterios técnicos y operativos:

* Reduce significativamente el consumo de memoria RAM y CPU en comparación con un emulador Android.
* Permite que equipos con especificaciones modestas puedan participar en el desarrollo sin afectar su rendimiento.
* Refleja de forma más precisa el comportamiento real de la aplicación en un entorno de uso cotidiano.
* Facilita la validación de funcionalidades relacionadas con sensores, conectividad y hardware del dispositivo.
* Aprovecha el mecanismo de **Hot Reload** de Flutter, que permite visualizar cambios casi en tiempo real durante el desarrollo.

El uso de emuladores no forma parte del flujo oficial descrito en esta documentación. En caso de que un desarrollador decida emplearlos para pruebas específicas, dicha configuración será considerada opcional y no será un requisito para participar en el proyecto.
