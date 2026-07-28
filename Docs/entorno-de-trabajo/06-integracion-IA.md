# Capítulo 6 — Crear una aplicación Flutter con Firebase e Inteligencia Artificial paso a paso

## Objetivos

Al finalizar este capítulo el estudiante será capaz de:

* Crear un proyecto Firebase desde cero.
* Conectar una aplicación Flutter con Firebase.
* Configurar servicios fundamentales como Authentication y Cloud Firestore.
* Utilizar herramientas de Inteligencia Artificial para generar interfaces Flutter.
* Utilizar IA para diseñar estructuras de datos.
* Crear modelos Dart con ayuda de IA.
* Generar servicios Firebase utilizando asistentes inteligentes.
* Comprender el flujo moderno de desarrollo Flutter + Firebase + Gemini.
* Crear la base de una aplicación inteligente.

---

# 1. Introducción

En los capítulos anteriores aprendimos:

* Qué es la Inteligencia Artificial aplicada al desarrollo.
* Cómo utilizar Gemini como asistente.
* Qué es Firebase Studio.
* Cómo funciona Firebase AI Logic.
* Cómo preparar el entorno.

Ahora realizaremos el proceso completo.

El objetivo será construir una aplicación Flutter utilizando:

```text
id="6fl001"
Flutter

↓

Firebase

↓

Firestore

↓

Authentication

↓

Gemini IA

↓

Aplicación inteligente
```

Durante este capítulo el estudiante aprenderá el flujo utilizado actualmente por muchos desarrolladores:

```text
Idea

↓

Crear proyecto

↓

Diseñar arquitectura con IA

↓

Crear interfaces con IA

↓

Configurar Firebase

↓

Guardar información

↓

Agregar funciones inteligentes
```

---

# 2. Proyecto que construiremos

Para aprender utilizaremos una aplicación educativa sencilla.

Nombre del proyecto:

```text
Healthy Kids AI
```

Objetivo:

Crear una aplicación para niños de 8 a 12 años que permita:

* Crear usuarios.
* Registrar hábitos saludables.
* Mostrar progreso.
* Guardar información.
* Recibir recomendaciones inteligentes.

Arquitectura final:

```text
                    Usuario

                       ↓

                Aplicación Flutter

                       ↓

        ┌──────────────┴──────────────┐

        ↓                             ↓

 Firebase Services              Firebase AI Logic

        ↓                             ↓

 Authentication                  Gemini

 Firestore

 Storage
```

---

# 3. Crear el proyecto Flutter

Abrir una terminal.

Crear proyecto:

```bash
flutter create healthy_kids_ai
```

Entrar:

```bash
cd healthy_kids_ai
```

Abrir proyecto:

```bash
code .
```

La estructura inicial:

```text
healthy_kids_ai

├── android
├── ios
├── lib
│
│── main.dart
│
├── test
│
└── pubspec.yaml
```

---

# 4. Preparar la estructura del proyecto utilizando IA

Antes de programar, utilizaremos IA para organizar la aplicación.

Prompt para Gemini:

```
Estoy creando una aplicación Flutter educativa llamada Healthy Kids AI.

Necesito una arquitectura organizada.

Incluye:

- Pantallas.
- Widgets reutilizables.
- Modelos.
- Servicios Firebase.
- Manejo de datos.

Utiliza buenas prácticas Flutter.
```

Una posible respuesta:

```text
lib

├── core
│
├── models
│
├── screens
│
├── widgets
│
├── services
│
└── main.dart
```

La IA ayuda a crear una base inicial, pero el desarrollador decide si la estructura es adecuada.

---

# 5. Crear proyecto Firebase

Ingresar a:

Firebase Console

Seleccionar:

```text
Crear proyecto
```

---

## Paso 1 — Nombre

Ejemplo:

```
healthy-kids-ai
```

---

## Paso 2 — Google Analytics

Para aprendizaje:

Puede activarse.

Después seleccionar:

```
Crear proyecto
```

Firebase comenzará la configuración.

Al finalizar:

```
Proyecto Firebase creado correctamente
```

---

# 6. Registrar aplicación Android en Firebase

Dentro del proyecto Firebase:

Seleccionar:

```
Agregar aplicación
```

Elegir:

```
Android
```

---

Firebase solicita:

## Nombre del paquete

Buscar:

```
android/app/build.gradle
```

o:

```
android/app/build.gradle.kts
```

Ejemplo:

```text
com.example.healthy_kids_ai
```

---

Registrar aplicación.

Firebase generará:

```
google-services.json
```

Descargar archivo.

Colocar en:

```
android/app/google-services.json
```

---

# 7. Instalar FlutterFire CLI

Flutter necesita una herramienta para conectarse con Firebase.

Ejecutar:

```bash
dart pub global activate flutterfire_cli
```

Comprobar:

```bash
flutterfire --version
```

---

# 8. Configurar Firebase en Flutter

Dentro del proyecto:

Ejecutar:

```bash
flutterfire configure
```

Seleccionar:

```
healthy-kids-ai
```

Elegir plataformas:

```
Android
iOS
Web
```

Firebase generará:

```
lib/firebase_options.dart
```

Este archivo contiene la configuración del proyecto.

---

# 9. Instalar Firebase en Flutter

Agregar Firebase Core:

```bash
flutter pub add firebase_core
```

---

Abrir:

```
lib/main.dart
```

Configurar Firebase:

```dart
import 'package:flutter/material.dart';
import 'package:firebase_core/firebase_core.dart';
import 'firebase_options.dart';


void main() async {

  WidgetsFlutterBinding.ensureInitialized();

  await Firebase.initializeApp(
    options: DefaultFirebaseOptions.currentPlatform,
  );

  runApp(
    const MyApp()
  );

}
```

---

Probar:

```bash
flutter run
```

Si la aplicación inicia correctamente:

Firebase está conectado.

---

# 10. Crear sistema de usuarios con Firebase Authentication

Firebase permite crear usuarios sin construir todo el sistema desde cero.

Servicios disponibles:

* Correo y contraseña.
* Google Login.
* Teléfono.
* Otros proveedores.

---

Entrar en Firebase:

```
Authentication

↓

Comenzar
```

Activar:

```
Correo electrónico / contraseña
```

---

Instalar paquete:

```bash
flutter pub add firebase_auth
```

---

# 11. Crear servicio de autenticación utilizando IA

En lugar de escribir todo manualmente:

Solicitamos ayuda:

Prompt:

```
Crea un servicio Flutter llamado AuthService.

Debe utilizar Firebase Authentication.

Debe incluir:

- Registrar usuario.
- Iniciar sesión.
- Cerrar sesión.
- Manejo de errores.

Utiliza buenas prácticas.
```

La IA genera una primera versión.

El desarrollador debe:

* Revisar.
* Adaptar.
* Probar.

---

# 12. Crear base de datos Firestore

Firestore será nuestra base de datos.

Entrar:

```
Firestore Database

↓

Crear base de datos
```

Seleccionar:

```
Modo prueba
```

(Únicamente para aprendizaje)

---

Crear colección:

```
users
```

Ejemplo:

```text
users

 └── usuario001

       nombre:
       Carlos

       edad:
       10

       progreso:
       75
```

---

# 13. Diseñar Firestore utilizando IA

La IA puede ayudarnos a diseñar la estructura.

Prompt:

```
Diseña una base de datos Firestore
para una aplicación educativa infantil.

Necesito almacenar:

- Usuarios.
- Hábitos saludables.
- Progreso.
- Recompensas.
- Actividades.
```

Resultado esperado:

```text
users

habits

progress

rewards

activities
```

---

# 14. Crear modelos Dart utilizando IA

Los modelos representan los datos.

Ejemplo:

Modelo usuario.

Prompt:

```
Crea un modelo Dart llamado UserModel.

Campos:

id
nombre
edad
correo
progreso

Incluye:

constructor

fromJson

toJson
```

Resultado:

```dart
class UserModel {

final String id;
final String nombre;
final int edad;

}
```

---

# 15. Generar interfaces Flutter con IA

Ahora crearemos pantallas.

Ejemplo:

Pantalla principal.

Prompt:

```
Crea una pantalla Flutter Dashboard.

Debe incluir:

- Material 3.
- Tarjeta de progreso.
- Lista de hábitos.
- Diseño infantil.
- Código organizado.
```

La IA puede generar:

* Scaffold.
* AppBar.
* Cards.
* Buttons.
* Widgets.

---

# 16. Crear widgets reutilizables con IA

Ejemplo:

Tarjeta de progreso.

Prompt:

```
Crea un widget Flutter reutilizable llamado ProgressCard.

Debe recibir:

- título.
- porcentaje.
- color.

Debe utilizar Material 3.
```

Resultado:

Un componente que puede reutilizarse varias veces.

---

# 17. Conectar Flutter con Firestore

Instalar:

```bash
flutter pub add cloud_firestore
```

---

Crear servicio:

Prompt:

```
Crea un FirestoreService en Flutter.

Debe permitir:

- Guardar usuario.
- Obtener usuario.
- Actualizar progreso.

Utiliza cloud_firestore.
```

---

# 18. Agregar Inteligencia Artificial a la aplicación

Ahora incorporaremos Gemini.

Ejemplo:

Función:

"Asistente saludable".

Usuario:

```
No tomé agua hoy
```

La aplicación envía:

```text
Flutter

↓

Firebase AI Logic

↓

Gemini

↓

Respuesta
```

Respuesta:

```
Recuerda beber agua durante el día.
Puedes activar recordatorios.
```

---

# 19. Flujo completo de desarrollo utilizando IA

El proceso aprendido:

```text
Crear idea

↓

Pedir arquitectura a IA

↓

Crear proyecto Flutter

↓

Configurar Firebase

↓

Generar pantallas

↓

Crear modelos

↓

Crear servicios

↓

Agregar IA

↓

Probar

↓

Mejorar
```

---

# 20. Buenas prácticas durante el desarrollo

Siempre:

## Revisar código generado

La IA puede crear errores.

---

## Comprender antes de usar

No copiar código sin analizar.

---

## Trabajar por pequeñas funciones

Ejemplo:

Incorrecto:

```
Crea toda la aplicación.
```

Correcto:

```
Crea primero la autenticación.
```

Después:

```
Crea la pantalla principal.
```

---

## Mantener seguridad

Nunca enviar:

* Contraseñas.
* Llaves privadas.
* Información sensible.

---

# 21. Resultado final del capítulo

Al terminar este capítulo el estudiante tendrá:

```text
Aplicación Flutter

        +

Firebase conectado

        +

Usuarios funcionando

        +

Firestore configurado

        +

Interfaces creadas con IA

        +

Modelos generados

        +

Servicios Firebase

        +

Base para integrar Gemini
```

---

# Resumen

Este capítulo representa el flujo real moderno de desarrollo:

El programador define la idea, utiliza Inteligencia Artificial para acelerar tareas, conecta servicios Firebase y construye una aplicación funcional.

La IA no sustituye el aprendizaje de Flutter, Firebase o programación. Su función es aumentar la velocidad del desarrollador y permitir construir aplicaciones más completas en menos tiempo.

En el siguiente capítulo se estudiarán las **buenas prácticas, seguridad y recursos oficiales**, donde se aprenderá cómo utilizar IA profesionalmente evitando errores comunes.
