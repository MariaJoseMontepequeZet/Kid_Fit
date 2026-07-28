# Desarrollo rápido de aplicaciones Flutter con IA desde la nube

# Capítulo 3 — Conectar Flutter con Firebase y crear datos utilizando IA

## Objetivos

Al finalizar este capítulo el estudiante será capaz de:

* Conectar una aplicación Flutter creada con IA a Firebase.
* Configurar Firebase Authentication.
* Crear una base de datos Firestore.
* Diseñar colecciones utilizando Gemini.
* Generar modelos Dart con Inteligencia Artificial.
* Crear servicios para comunicarse con Firebase.
* Utilizar IA para acelerar la configuración del backend.

---

# 1. Introducción

En el capítulo anterior creamos la estructura inicial de una aplicación Flutter utilizando Gemini.

Hasta este momento tenemos:

```text id="7y3w5m"
Flutter

↓

Pantallas

↓

Widgets

↓

Modelos iniciales
```

Pero una aplicación real necesita almacenar información.

Por ejemplo:

* Usuarios.
* Perfiles.
* Cursos.
* Progreso.
* Configuraciones.

Para eso utilizaremos Firebase.

La arquitectura será:

```text id="m5f8s1"
Aplicación Flutter

↓

Firebase Authentication

↓

Cloud Firestore

↓

Firebase Storage

↓

Gemini IA
```

---

# 2. ¿Qué agregará Firebase a nuestra aplicación?

Firebase funcionará como el backend de la aplicación.

Antes:

```text id="4h5kq8"
Aplicación Flutter

↓

Datos temporales
```

Después:

```text id="s0s8wp"
Aplicación Flutter

↓

Firebase

↓

Datos guardados permanentemente
```

---

Firebase nos permitirá agregar:

## Usuarios

Ejemplo:

```text id="6cx4nv"
Nombre

Correo

Perfil

Fecha registro
```

---

## Información de la aplicación

Ejemplo:

```text id="q9d8za"
Cursos

Progreso

Puntos

Recompensas
```

---

## Archivos

Ejemplo:

```text id="4q2q6t"
Imágenes

Documentos

Avatares
```

---

# 3. Preparar Firebase para la aplicación

Entramos a:

```text
Firebase Console
```

Seleccionamos nuestro proyecto.

Ejemplo:

```text id="f7m7dz"
healthy-kids-ai
```

---

En el panel veremos:

```text id="8m7z7d"
Build

├── Authentication

├── Firestore Database

├── Storage

└── Hosting
```

Trabajaremos principalmente con:

```text id="k8b0pm"
Authentication

Firestore

Storage
```

---

# 4. Registrar una aplicación Flutter en Firebase

Dentro de Firebase:

Seleccionar:

```text id="j8v8cd"
Agregar aplicación
```

Elegir:

```text id="x4k6st"
Android
```

---

Firebase solicitará:

## Nombre del paquete Android

Ejemplo:

```text id="q8j5ad"
com.example.healthy_kids_ai
```

Este identificador debe coincidir con Flutter.

---

Después Firebase proporciona:

```text id="n6v8qx"
google-services.json
```

Este archivo conecta Android con Firebase.

---

# 5. Utilizar FlutterFire para conectar Firebase

Abrimos la terminal del proyecto.

Ejemplo:

```bash
cd healthy_kids_ai
```

Ejecutamos:

```bash
flutterfire configure
```

---

La herramienta preguntará:

```text id="k4z6fv"
¿Qué proyecto Firebase utilizar?
```

Seleccionamos:

```text id="1j6x7p"
healthy-kids-ai
```

---

Después se genera:

```text id="7s5f8m"
lib/firebase_options.dart
```

La estructura queda:

```text id="a7c9x2"
lib

├── main.dart

├── firebase_options.dart

├── screens

├── services

└── models
```

---

# 6. Inicializar Firebase en Flutter

Ahora Firebase debe iniciarse cuando abre la aplicación.

Gemini puede ayudarnos.

Prompt:

```text id="r9x4vq"
Configura Firebase en Flutter.

Necesito:

- Inicialización en main.dart.
- Uso de firebase_options.dart.
- Código actualizado para Flutter.
```

---

El resultado será una configuración similar:

```dart
await Firebase.initializeApp(
 options: DefaultFirebaseOptions.currentPlatform,
);
```

---

# 7. Crear autenticación de usuarios

Firebase Authentication permite gestionar usuarios.

Activamos:

```text id="k5f7qs"
Firebase Console

↓

Authentication

↓

Comenzar
```

---

Seleccionamos método:

```text id="p4j9mv"
Correo electrónico y contraseña
```

Activar:

```text id="m3j8wp"
Habilitar
```

---

Ahora la aplicación puede tener:

```text id="b6w9zq"
Registro

↓

Login

↓

Usuario autenticado
```

---

# 8. Crear Login con Gemini

Prompt:

```text id="y6v8c3"
Crea una pantalla Login Flutter.

Debe utilizar Firebase Authentication.

Incluye:

- Campo correo.
- Campo contraseña.
- Botón iniciar sesión.
- Manejo de errores.
- Diseño Material 3.
```

---

Gemini generará:

* Interfaz.
* Controladores.
* Llamadas Firebase.

---

# 9. Crear registro de usuarios

Prompt:

```text id="w4s9qp"
Crea una pantalla de registro Flutter.

Utiliza Firebase Authentication.

Campos:

- Nombre.
- Correo.
- Contraseña.

Después del registro guarda el perfil del usuario en Firestore.
```

---

Flujo:

```text id="r8n5cq"
Usuario escribe datos

↓

Firebase Authentication crea cuenta

↓

Firestore guarda perfil

↓

Usuario entra a la aplicación
```

---

# 10. Crear la base de datos Firestore

Firestore funciona utilizando colecciones y documentos.

Ejemplo:

```text id="g5m2hx"
Colección

↓

Documento

↓

Campos
```

---

Ejemplo:

Colección:

```text id="q3v6zn"
users
```

Documento:

```text id="u9x4ka"
usuario_001
```

Campos:

```text id="c6q8vz"
nombre

correo

edad

progreso
```

---

# 11. Diseñar Firestore utilizando Gemini

En lugar de diseñar todo manualmente podemos pedir ayuda.

Prompt:

```text id="f3m7xw"
Diseña una estructura Firestore
para una aplicación educativa infantil.

Necesito almacenar:

- Usuarios.
- Cursos.
- Progreso.
- Recompensas.

Explica colecciones y documentos.
```

---

Gemini puede generar:

```text id="s8q1lm"
users

├── uid

├── nombre

├── correo


courses

├── titulo

├── descripción


progress

├── usuario

├── curso

├── porcentaje


rewards

├── nombre

├── puntos
```

---

# 12. Crear modelos Dart con IA

Los datos de Firebase deben representarse en Flutter.

Prompt:

```text id="z6m8wr"
Crea un modelo Dart llamado UserModel.

Campos:

- uid.
- nombre.
- correo.
- fechaRegistro.

Incluye:

- Constructor.
- fromFirestore.
- toMap.
```

---

Resultado:

```text id="v7k2hx"
UserModel

↓

Firebase Document

↓

Objeto Flutter
```

---

# 13. Crear servicios Firebase con Gemini

Una buena práctica es separar la lógica.

Estructura:

```text id="c8p4yr"
lib

├── services

│   └── firebase_service.dart

├── models

├── screens

└── widgets
```

---

Prompt:

```text id="x5q9bd"
Crea un servicio Firebase para Flutter.

Debe permitir:

- Crear usuarios.
- Leer datos Firestore.
- Actualizar perfiles.

Utiliza buenas prácticas.
```

---

# 14. Crear reglas básicas Firestore con IA

Firestore necesita seguridad.

Prompt:

```text id="m8z4qk"
Genera reglas Firestore.

Requisitos:

- Solo usuarios autenticados pueden acceder.
- Cada usuario solamente puede modificar sus datos.
- Evita acceso público.
```

---

La IA puede generar una propuesta.

Pero siempre debemos revisar antes de publicar.

---

# 15. Agregar almacenamiento con Firebase Storage

Storage permite guardar archivos.

Ejemplos:

* Fotos de perfil.
* Imágenes de cursos.
* Archivos educativos.

Activar:

```text id="v6n8sd"
Firebase Console

↓

Storage

↓

Comenzar
```

---

Prompt:

```text id="h7k2m9"
Crea un servicio Flutter para subir imágenes utilizando Firebase Storage.
```

---

# 16. Flujo completo utilizando IA

El proceso real queda:

```text id="x7q4mt"
Diseñar pantalla

↓

Gemini genera Flutter

↓

Crear Firebase

↓

Gemini genera conexión

↓

Crear Firestore

↓

Gemini genera modelos

↓

Probar aplicación
```

---

# 17. Errores comunes

## Firebase no inicia

Posible causa:

* Falta configuración.
* firebase_options.dart incorrecto.

Solución:

Pedir a Gemini:

```text id="a5n9rx"
Analiza este error de Firebase Flutter.
Explica la causa y solución.
```

---

## Error de permisos Firestore

Mensaje:

```text
Permission denied
```

Causa:

Reglas incorrectas.

Solución:

Revisar:

```text id="j6c8vz"
Firestore Rules
```

---

# 18. Resultado del capítulo

Al finalizar este capítulo la aplicación tendrá:

```text id="p9z6kw"
Proyecto Flutter

↓

Firebase conectado

↓

Usuarios funcionando

↓

Firestore creado

↓

Modelos generados

↓

Servicios preparados
```

---

# Resumen

En este capítulo conectamos una aplicación Flutter creada con IA con Firebase.

Aprendimos a utilizar Gemini para:

* Crear autenticación.
* Diseñar bases de datos.
* Generar modelos.
* Crear servicios.
* Resolver configuraciones.

El flujo moderno queda:

```text id="n4v8xm"
Gemini

↓

Flutter

↓

Firebase

↓

Aplicación funcional
```

En el siguiente capítulo agregaremos funciones inteligentes utilizando Gemini dentro de la aplicación, creando experiencias como asistentes, generación de contenido y características basadas en Inteligencia Artificial.
