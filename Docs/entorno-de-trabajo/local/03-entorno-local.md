# PARTE I — ENTORNO DE DESARROLLO LOCAL

# Capítulo 3 — Android Studio y Android SDK

---

# 3. Introducción

En el capítulo anterior se instaló el **Flutter SDK**, que proporciona las herramientas necesarias para desarrollar aplicaciones Flutter. Sin embargo, Flutter por sí solo no puede generar una aplicación Android ejecutable.

Para ello necesita apoyarse en otra herramienta: el **Android SDK**.

En este proyecto **Android Studio no será utilizado como entorno principal de desarrollo**. El código se escribirá en **Cursor** o **Visual Studio Code**. Android Studio se instalará únicamente porque proporciona el Android SDK, las herramientas de compilación y otras utilidades necesarias para que Flutter pueda generar aplicaciones Android.

Comprender esta diferencia es importante, ya que muchos principiantes creen que Flutter depende de Android Studio para programar. En realidad, Flutter solo necesita los componentes que Android Studio instala y administra.

Al finalizar este capítulo, el entorno dispondrá de un Android SDK completamente configurado y preparado para trabajar con Flutter.

---

# 3.1 ¿Qué es Android Studio?

Android Studio es el Entorno de Desarrollo Integrado (IDE) oficial para el desarrollo de aplicaciones Android.

Incluye numerosas herramientas para diseñar interfaces, programar aplicaciones, realizar pruebas y administrar dispositivos virtuales.

En este proyecto su función será mucho más específica:

* instalar el Android SDK;
* administrar las herramientas de compilación;
* aceptar las licencias requeridas;
* mantener actualizado el entorno Android.

El desarrollo diario continuará realizándose desde Cursor o Visual Studio Code.

---

# 3.2 ¿Qué es Android SDK?

El **Android Software Development Kit (SDK)** es un conjunto de herramientas que permite construir aplicaciones compatibles con Android.

Flutter utiliza este SDK cada vez que necesita:

* compilar una aplicación;
* generar un archivo APK;
* instalar una aplicación;
* comunicarse con un dispositivo Android.

Arquitectura:

```text id="and3a01"
             Flutter SDK

                  │

                  ▼

            Android SDK

      ┌───────────┼───────────┐

      ▼           ▼           ▼

 Platform     Build Tools    ADB

   Tools

                  │

                  ▼

          Dispositivo Android
```

---

# 3.3 ¿Por qué Flutter necesita Android SDK?

Flutter genera el código de la aplicación, pero necesita las herramientas del ecosistema Android para convertir ese proyecto en una aplicación que pueda instalarse en un teléfono.

El flujo es el siguiente:

```text id="and3a02"
Código Flutter

       │

       ▼

Flutter SDK

       │

       ▼

Android SDK

       │

       ▼

APK Debug

       │

       ▼

Teléfono Android
```

Sin Android SDK Flutter no puede construir aplicaciones Android.

---

# 3.4 Componentes principales del Android SDK

El Android SDK está formado por diferentes herramientas.

Cada una cumple una responsabilidad específica.

```text id="and3a03"
Android SDK

│

├── Platform Tools

├── Build Tools

├── SDK Platforms

├── Command Line Tools

└── Android Debug Bridge
```

---

## Platform Tools

Incluye herramientas utilizadas para comunicar la computadora con un dispositivo Android.

Entre ellas se encuentra **ADB**, una de las utilidades más importantes para Flutter.

---

## Build Tools

Permiten construir la aplicación Android.

Estas herramientas generan el APK o el AAB que posteriormente podrá instalarse en un dispositivo.

---

## SDK Platforms

Contienen los archivos necesarios para compilar aplicaciones destinadas a versiones específicas de Android.

Flutter utilizará la plataforma configurada para el proyecto.

---

## Command Line Tools

Incluyen utilidades que permiten administrar el SDK desde la terminal.

Muchas herramientas de Flutter dependen de estos componentes.

---

# 3.5 Android Debug Bridge (ADB)

Uno de los componentes más importantes del Android SDK es **Android Debug Bridge (ADB)**.

ADB permite establecer comunicación entre la computadora y un dispositivo Android.

Gracias a esta herramienta Flutter puede:

* detectar teléfonos conectados;
* instalar aplicaciones;
* iniciar procesos de depuración;
* obtener registros del sistema;
* eliminar aplicaciones de prueba.

Arquitectura:

```text id="and3a04"
Flutter

      │

      ▼

ADB

      │

      ▼

Cable USB

      │

      ▼

Teléfono Android
```

Sin ADB no sería posible ejecutar la aplicación directamente desde Flutter.

---

# 3.6 Arquitectura completa del entorno Android

Después de instalar Android SDK, el entorno comienza a tomar la siguiente forma:

```text id="and3a05"
Desarrollador

      │

      ▼

Cursor / VS Code

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
```

Cada componente depende del anterior para completar el proceso de desarrollo.

---

# 3.7 Instalación de Android Studio

La instalación de Android Studio es sencilla.

Proceso general:

```text id="and3a06"
Descargar Android Studio

          │

          ▼

Ejecutar instalador

          │

          ▼

Instalar Android SDK

          │

          ▼

Abrir Android Studio

          │

          ▼

Completar configuración inicial
```

Durante la instalación se recomienda mantener la configuración predeterminada.

---

# 3.8 Instalación en Windows

Pasos recomendados:

1. Descargar Android Studio desde el sitio oficial.
2. Ejecutar el instalador.
3. Mantener la configuración predeterminada.
4. Permitir la instalación del Android SDK.
5. Finalizar el asistente.

Una vez concluida la instalación, Android Studio descargará automáticamente los componentes necesarios.

---

# 3.9 Instalación en Linux

Proceso general:

1. Descargar el paquete oficial correspondiente a la distribución.
2. Extraer o instalar el paquete.
3. Ejecutar Android Studio.
4. Completar el asistente inicial.
5. Instalar Android SDK.

Al finalizar, el entorno Android quedará preparado para Flutter.

---

# 3.10 SDK Manager

Android Studio incorpora una herramienta denominada **SDK Manager**.

Su función consiste en administrar todos los componentes del Android SDK.

Desde esta herramienta es posible:

* instalar nuevas plataformas Android;
* actualizar Build Tools;
* instalar Platform Tools;
* administrar Command Line Tools;
* eliminar versiones antiguas.

Arquitectura:

```text id="and3a07"
Android Studio

        │

        ▼

SDK Manager

        │

        ├── SDK Platforms

        ├── Build Tools

        ├── Platform Tools

        └── Command Line Tools
```

---

# 3.11 Componentes mínimos recomendados

Para este proyecto se recomienda instalar únicamente los componentes necesarios.

| Componente                     | Propósito                           |
| ------------------------------ | ----------------------------------- |
| Android SDK Platform           | Compilar aplicaciones Android       |
| Android SDK Build Tools        | Generar APK y AAB                   |
| Android SDK Platform Tools     | Comunicación mediante ADB           |
| Android SDK Command-line Tools | Herramientas utilizadas por Flutter |

No es necesario instalar componentes destinados a desarrollo nativo que no serán utilizados en este proyecto.

---

# 3.12 Aceptación de licencias

El Android SDK requiere aceptar diversas licencias antes de utilizar algunas herramientas.

Flutter permite verificar este estado mediante:

```bash id="and3cmd01"
flutter doctor --android-licenses
```

Si existen licencias pendientes, el asistente solicitará aceptarlas.

Una vez completado el proceso, Flutter podrá utilizar correctamente el Android SDK.

---

# 3.13 Verificación mediante Flutter Doctor

Después de instalar Android SDK se recomienda ejecutar:

```bash id="and3cmd02"
flutter doctor
```

Flutter comprobará que puede localizar:

* Android SDK;
* Platform Tools;
* Build Tools;
* Command Line Tools.

Resultado esperado:

```text id="and3a08"
Flutter

✓

Android Toolchain

✓
```

Esto confirma que Flutter reconoce correctamente el entorno Android.

---

# 3.14 Problemas frecuentes

## Flutter no encuentra Android SDK

Posibles causas:

* instalación incompleta;
* SDK no descargado;
* ubicación incorrecta del SDK.

---

## Android Toolchain aparece con error

Generalmente ocurre porque:

* faltan licencias;
* Build Tools no están instaladas;
* Command Line Tools no existen.

---

## ADB no detecta dispositivos

Las posibles causas son:

* depuración USB desactivada;
* cable USB incompatible;
* permisos insuficientes;
* controladores faltantes (Windows).

Estos aspectos se estudiarán con detalle en el capítulo dedicado a la preparación del dispositivo Android.

---

# 3.15 Buenas prácticas

Para mantener un entorno estable se recomienda:

* instalar únicamente componentes oficiales;
* mantener actualizado el Android SDK;
* evitar eliminar Platform Tools;
* aceptar siempre las licencias pendientes;
* verificar periódicamente el entorno con `flutter doctor`;
* instalar solo las plataformas Android necesarias para el proyecto.

---

# 3.16 Arquitectura del entorno después de instalar Android SDK

Una vez configurado Android Studio y el Android SDK, la arquitectura queda de la siguiente manera:

```text id="and3a09"
                 Desarrollador

                       │

                       ▼

          Cursor / Visual Studio Code

                       │

                       ▼

                  Flutter SDK

                       │

                       ▼

                  Android SDK

      ┌───────────────┼───────────────┐

      ▼               ▼               ▼

 Platform Tools   Build Tools      ADB

                       │

                       ▼

              Dispositivo Android
```

El entorno ya dispone de las herramientas necesarias para compilar aplicaciones Android. En el siguiente capítulo se configurará el IDE desde el cual se desarrollará el proyecto y se instalarán las extensiones que integran Flutter y Dart con el editor.

---

# Conclusión del capítulo

El Android SDK constituye el puente entre Flutter y el sistema operativo Android. Aunque Android Studio es un IDE muy completo, en este proyecto su función principal será proporcionar y administrar las herramientas necesarias para compilar y ejecutar aplicaciones en dispositivos Android.

Tras completar este capítulo, el entorno cuenta con un Android SDK funcional, listo para integrarse con **Cursor** o **Visual Studio Code**, donde se desarrollará el resto del proyecto.
