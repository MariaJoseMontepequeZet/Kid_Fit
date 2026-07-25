# PARTE II — DESARROLLO CLOUD CON FLUTTER

# Capítulo 5 — Integración Firebase con Flutter (FlutterFire)

---

# 5. Introducción

Después de crear el proyecto Firebase, el siguiente paso consiste en conectar la aplicación Flutter con la plataforma Firebase.

Esta integración se realiza mediante **FlutterFire**, un conjunto oficial de plugins desarrollado para utilizar Firebase dentro de aplicaciones Flutter.

La conexión permitirá que la aplicación pueda comunicarse con servicios como:

* Firebase Authentication;
* Cloud Firestore;
* Firebase Storage;
* Firebase Cloud Messaging;
* Firebase Analytics;
* Firebase Crashlytics.

La arquitectura después de la integración será:

```text id="6yq8vk"
                  Aplicación Flutter

                         │

                         ▼

                  FlutterFire SDK

                         │

                         ▼

                  Firebase SDK

                         │

                         ▼

                  Servicios Firebase

        ┌────────────┬────────────┬────────────┐

        ▼            ▼            ▼

 Authentication  Firestore    Storage

```

---

# 5.1 ¿Qué es FlutterFire?

FlutterFire es el conjunto oficial de plugins que permite utilizar Firebase desde Flutter.

Firebase proporciona SDKs para diferentes plataformas:

```text id="g6p3bw"
Firebase SDK

      │

      ├── Android

      ├── iOS

      ├── Web

      └── Flutter (FlutterFire)
```

FlutterFire actúa como puente entre la aplicación Flutter y los servicios Firebase.

---

Ejemplo:

Sin FlutterFire:

```text id="r5m1kx"
Flutter

    ❌

Firebase directamente
```

Con FlutterFire:

```text id="6c7w3d"
Flutter

    ↓

FlutterFire Plugin

    ↓

Firebase
```

---

# 5.2 Componentes utilizados en la integración

La integración Firebase + Flutter utiliza varias herramientas.

---

# 5.2.1 Firebase Console

Es la plataforma web donde se administra el proyecto Firebase.

Responsabilidades:

* crear proyectos;
* registrar aplicaciones;
* activar servicios;
* configurar permisos.

---

# 5.2.2 Firebase CLI

Firebase CLI es una herramienta de línea de comandos que permite interactuar con Firebase desde la terminal.

Permite:

* iniciar sesión;
* administrar proyectos;
* ejecutar configuraciones;
* utilizar herramientas Firebase.

Ejemplo:

```bash id="kz2q4j"
firebase login
```

---

# 5.2.3 FlutterFire CLI

FlutterFire CLI es una herramienta específica para proyectos Flutter.

Su función principal es configurar automáticamente la conexión entre Flutter y Firebase.

Realiza tareas como:

* detectar plataformas disponibles;
* vincular proyecto Firebase;
* generar configuración;
* crear archivos necesarios.

---

# 5.2.4 Firebase Core

`firebase_core` es el paquete base necesario para cualquier integración Firebase.

Su función es inicializar Firebase dentro de Flutter.

Ejemplo conceptual:

```text id="v8q3kd"
Aplicación Flutter inicia

        ↓

Firebase Core carga configuración

        ↓

Servicios Firebase disponibles
```

---

# 5.3 Flujo completo de integración

El proceso general será:

```text id="x5j9rq"
Proyecto Firebase creado

          ↓

Instalar Firebase CLI

          ↓

Instalar FlutterFire CLI

          ↓

Registrar aplicación Flutter

          ↓

Generar configuración Firebase

          ↓

Agregar dependencias Flutter

          ↓

Inicializar Firebase

          ↓

Usar servicios Cloud
```

---

# 5.4 Preparación del entorno

Antes de comenzar se debe verificar que las herramientas necesarias estén instaladas.

Requisitos:

* Flutter SDK;
* Dart SDK;
* Node.js;
* npm;
* Firebase CLI;
* FlutterFire CLI.

---

Verificar Flutter:

```bash id="8m5x7h"
flutter --version
```

Ejemplo:

```text id="1u5n0s"
Flutter 3.x.x
Dart 3.x.x
```

---

Verificar Node.js:

```bash id="7x0b2a"
node --version
```

---

Verificar npm:

```bash id="0l5g3r"
npm --version
```

---

# 5.5 Instalación de Firebase CLI

Firebase CLI se instala mediante npm.

Comando:

```bash id="7q5h3r"
npm install -g firebase-tools
```

---

Después se verifica:

```bash id="0v8s6c"
firebase --version
```

Resultado esperado:

```text id="r6x1fk"
Firebase CLI versión instalada
```

---

# 5.6 Autenticación con Firebase CLI

Para utilizar Firebase CLI es necesario iniciar sesión con la cuenta Google asociada al proyecto.

Comando:

```bash id="n6y2bx"
firebase login
```

El navegador abrirá una ventana para:

1. seleccionar cuenta Google;
2. autorizar Firebase CLI;
3. confirmar acceso.

---

Después del inicio de sesión:

```bash id="5k7x9z"
firebase projects:list
```

Este comando muestra los proyectos disponibles.

Ejemplo:

```text id="s3v8qj"
Proyecto:

app-educativa

ID:

app-educativa-12345
```

---

# 5.7 Instalación de FlutterFire CLI

FlutterFire CLI se instala mediante Dart.

Comando:

```bash id="h3v7sa"
dart pub global activate flutterfire_cli
```

---

Verificación:

```bash id="9x6j2q"
flutterfire --version
```

---

Si el sistema no encuentra el comando puede ser necesario agregar el directorio de paquetes globales Dart al PATH.

---

# 5.8 Preparar el proyecto Flutter

Dentro del proyecto Flutter:

Ejemplo:

```bash id="g0z8bp"
cd app_educativa
```

La estructura esperada:

```text id="9p2m4w"
app_educativa

├── android

├── ios

├── lib

│    └── main.dart

├── pubspec.yaml

└── test
```

---

# 5.9 Configuración mediante FlutterFire CLI

Desde la raíz del proyecto Flutter se ejecuta:

```bash id="x7n2kf"
flutterfire configure
```

---

Este comando realiza varias acciones:

1. Detecta el proyecto Flutter.
2. Solicita seleccionar proyecto Firebase.
3. Detecta plataformas disponibles.
4. Registra aplicaciones.
5. Genera archivos de configuración.

---

Ejemplo del flujo:

```text id="3j7w9m"
flutterfire configure

        ↓

Seleccionar Firebase Project

        ↓

Seleccionar Android

        ↓

Generar configuración

        ↓

firebase_options.dart creado
```

---

# 5.10 Archivo firebase_options.dart

Durante la configuración FlutterFire genera:

```text id="f8s1xq"
lib/

└── firebase_options.dart
```

Este archivo contiene la configuración necesaria para conectar Flutter con Firebase.

Ejemplo conceptual:

```dart id="k5h9p0"
FirebaseOptions(
  apiKey: "...",
  appId: "...",
  projectId: "app-educativa"
)
```

---

Este archivo permite que Flutter conozca:

* qué proyecto Firebase utilizar;
* qué aplicación está registrada;
* qué credenciales públicas usar.

---

# 5.11 Instalación del paquete Firebase Core

Para iniciar Firebase es necesario agregar:

```bash id="q3x8mz"
flutter pub add firebase_core
```

---

Esto modifica:

```text id="d8x4ks"
pubspec.yaml
```

Agregando:

```yaml
dependencies:
  firebase_core:
```

---

Después:

```bash id="p5s9wa"
flutter pub get
```

---

# 5.12 Inicialización de Firebase en Flutter

La inicialización se realiza normalmente en:

```text id="w7k3hj"
lib/main.dart
```

Flujo:

```text id="9h3q2m"
main()

 ↓

WidgetsFlutterBinding

 ↓

Firebase.initializeApp()

 ↓

runApp()

 ↓

Aplicación iniciada
```

---

Ejemplo conceptual:

```dart id="2k7x5v"
void main() async {

  WidgetsFlutterBinding.ensureInitialized();

  await Firebase.initializeApp();

  runApp(MyApp());

}
```

---

# 5.13 ¿Por qué inicializar Firebase antes de ejecutar la aplicación?

Porque los servicios Firebase necesitan estar disponibles antes de que Flutter cargue las pantallas.

Ejemplo:

Incorrecto:

```text id="w4m9cz"
Aplicación inicia

↓

Pantalla login

↓

Firebase todavía no conectado
```

Correcto:

```text id="j6s0pn"
Firebase inicia

↓

Aplicación inicia

↓

Usuario utiliza servicios Cloud
```

---

# 5.14 Configuración para múltiples plataformas

Flutter permite desarrollar para:

* Android;
* iOS;
* Web.

Firebase puede configurarse para cada plataforma.

Ejemplo:

```text id="e2z6hq"
Proyecto Firebase

        │

        ├── Android App

        │

        ├── iOS App

        │

        └── Web App
```

---

Para este proyecto inicialmente:

```text id="u9d4pk"
Plataforma principal:

Android
```

---

# 5.15 Dependencias Firebase futuras

Después de la configuración inicial se agregarán servicios según necesidad.

Ejemplo:

Authentication:

```bash
flutter pub add firebase_auth
```

Firestore:

```bash
flutter pub add cloud_firestore
```

Storage:

```bash
flutter pub add firebase_storage
```

Messaging:

```bash
flutter pub add firebase_messaging
```

---

La aplicación crecerá progresivamente:

```text id="h5m8ws"
Firebase Core

        ↓

Authentication

        ↓

Firestore

        ↓

Storage

        ↓

Messaging
```

---

# 5.16 Buenas prácticas de integración

## Mantener Firebase separado de la interfaz

Evitar colocar llamadas Firebase directamente dentro de widgets.

Ejemplo incorrecto:

```text id="v4c8nh"
Widget

 ↓

Firebase

 ↓

Base de datos
```

---

Mejor:

```text id="p7w2nx"
Widget

 ↓

Servicio Firebase

 ↓

Firebase
```

---

## Mantener configuración organizada

Ejemplo:

```text id="8y3m6q"
lib

├── main.dart

├── firebase_options.dart

├── services

│     └── firebase_service.dart

└── screens
```

---

## No modificar manualmente firebase_options.dart

Este archivo debe ser generado por FlutterFire CLI.

Si cambia la configuración:

```bash
flutterfire configure
```

---

# 5.17 Verificación de integración

Una integración correcta debe cumplir:

Checklist:

| Elemento                       | Estado esperado |
| ------------------------------ | --------------- |
| Firebase CLI instalado         | ✓               |
| FlutterFire CLI instalado      | ✓               |
| Proyecto Firebase creado       | ✓               |
| Aplicación registrada          | ✓               |
| firebase_options.dart generado | ✓               |
| firebase_core instalado        | ✓               |
| Firebase inicializado          | ✓               |

---

# 5.18 Arquitectura final después de la integración

Después de este capítulo la arquitectura queda:

```text id="r8v2jq"
                  Flutter App

                      │

                      ▼

              firebase_core

                      │

                      ▼

             FlutterFire Plugins

                      │

                      ▼

                Firebase SDK

                      │

                      ▼

             Firebase Services

       ┌──────────────┼──────────────┐

       ▼              ▼              ▼

 Authentication   Firestore     Storage

```

---

# Conclusión del capítulo

La integración mediante FlutterFire conecta oficialmente la aplicación Flutter con Firebase.

A partir de este punto, la aplicación ya tiene la infraestructura necesaria para comenzar a utilizar servicios Cloud.

El flujo aprendido es:

```text id="v7s3kx"
Firebase Console

        ↓

Firebase CLI

        ↓

FlutterFire CLI

        ↓

firebase_options.dart

        ↓

Firebase.initializeApp()

        ↓

Servicios Firebase disponibles
```

Con Firebase correctamente conectado, el siguiente paso será implementar el primer servicio funcional:

# Capítulo 6 — Firebase Authentication

Donde se documentará la gestión de usuarios, registro, inicio de sesión, sesiones y seguridad básica.
