# PARTE II — DESARROLLO CLOUD CON FLUTTER

# Capítulo 6 — Firebase Authentication

---

# 6. Introducción

Una aplicación moderna necesita conocer quién está utilizando el sistema.

Esta capacidad se conoce como **autenticación**.

La autenticación permite que una aplicación pueda:

* identificar usuarios;
* crear cuentas;
* iniciar sesiones;
* proteger información privada;
* controlar acceso a recursos.

Dentro de la arquitectura del proyecto, Firebase Authentication será el servicio encargado de administrar la identidad de los usuarios.

Arquitectura:

```text id="f3k8pv"
              Usuario

                 │

                 ▼

          Aplicación Flutter

                 │

                 ▼

      Firebase Authentication

                 │

                 ▼

          Usuario verificado
```

---

# 6.1 ¿Qué es Firebase Authentication?

Firebase Authentication es un servicio de Firebase que permite implementar sistemas de autenticación sin crear un backend propio.

Tradicionalmente, un sistema de usuarios requiere construir:

```text id="r6h2mz"
Aplicación Flutter

        ↓

API Backend

        ↓

Servidor

        ↓

Base de datos usuarios

        ↓

Sistema de seguridad
```

Firebase simplifica este proceso:

```text id="v8s4qn"
Aplicación Flutter

        ↓

Firebase Authentication

        ↓

Usuario autenticado
```

---

# 6.2 Objetivo de Authentication dentro del proyecto

En la aplicación educativa, Firebase Authentication permitirá gestionar:

* estudiantes registrados;
* cuentas personales;
* sesiones activas;
* identificación del usuario actual.

Ejemplo:

Un estudiante abre la aplicación:

```text id="y2k9mf"
Usuario:

Carlos

        ↓

Firebase verifica identidad

        ↓

Carga su progreso
```

---

# 6.3 Conceptos fundamentales de autenticación

Antes de utilizar Firebase Authentication es necesario comprender algunos conceptos.

---

# 6.3.1 Usuario

Un usuario representa una persona identificada dentro del sistema.

Ejemplo:

```text id="q4h7wx"
Usuario

ID:
abc123

Correo:
estudiante@email.com

Nombre:
Carlos
```

Firebase genera un identificador único para cada usuario.

Este identificador se conoce como:

```text
UID
```

(User Identifier)

---

# 6.3.2 UID del usuario

El UID es un código único generado por Firebase.

Ejemplo:

```text id="p7z8kc"
Usuario:

Carlos


UID:

x83hd92kL0
```

El UID permite relacionar datos del usuario con Firestore.

Ejemplo:

```text id="v9w2qm"
Authentication

        │

        ▼

UID: usuario123

        │

        ▼

Firestore

usuarios/usuario123
```

---

# 6.3.3 Registro

El registro es el proceso donde un nuevo usuario crea una cuenta.

Ejemplo:

```text id="s5m9qy"
Usuario introduce:

Correo

Contraseña

Nombre


        ↓


Firebase crea cuenta


        ↓


Usuario registrado
```

---

# 6.3.4 Inicio de sesión

El inicio de sesión permite comprobar la identidad de un usuario existente.

Flujo:

```text id="x8r4kp"
Usuario

        ↓

Correo + contraseña

        ↓

Firebase Authentication

        ↓

Acceso permitido
```

---

# 6.3.5 Sesión

Una sesión representa el período durante el cual un usuario permanece identificado.

Ejemplo:

```text id="k7m3pd"
Usuario inicia sesión

        ↓

Firebase guarda sesión

        ↓

Aplicación reconoce usuario

        ↓

Usuario cierra sesión
```

---

# 6.4 Métodos de autenticación disponibles

Firebase Authentication soporta diferentes proveedores.

Los principales son:

---

# 6.4.1 Email y contraseña

Es el método más común para aplicaciones educativas.

Funcionamiento:

```text id="h2m8vf"
Registro:

Nombre

Correo

Contraseña


        ↓


Firebase Authentication


        ↓


Cuenta creada
```

---

Ventajas:

* fácil de implementar;
* no requiere servicios externos;
* ideal para proyectos académicos.

---

# 6.4.2 Inicio de sesión con Google

Permite utilizar una cuenta Google existente.

Flujo:

```text id="w5k3yp"
Usuario

        ↓

Botón "Continuar con Google"

        ↓

Cuenta Google

        ↓

Firebase Authentication

        ↓

Usuario autenticado
```

---

Ventajas:

* usuario no crea otra contraseña;
* proceso rápido;
* seguridad gestionada por Google.

---

# 6.4.3 Autenticación anónima

Permite crear usuarios temporales sin registro.

Ejemplo:

```text id="b4v8ns"
Usuario abre aplicación

        ↓

Firebase crea usuario temporal

        ↓

Puede utilizar funciones básicas
```

---

Uso común:

* pruebas;
* juegos;
* aplicaciones con acceso inicial.

---

# 6.5 Arquitectura de autenticación del proyecto

La arquitectura será:

```text id="n9q2hk"
                  Usuario

                     │

                     ▼

              Aplicación Flutter

                     │

                     ▼

          Firebase Authentication

                     │

                     ▼

                    UID

                     │

                     ▼

             Cloud Firestore

```

---

Ejemplo:

Firebase Authentication guarda:

```json
 id="z6m4kp"
{
  "uid": "a8f93d",
  "email": "usuario@email.com"
}
```

Firestore guarda información adicional:

```json
 id="m7r2qv"
{
  "uid": "a8f93d",
  "nombre": "Carlos",
  "nivel": 3,
  "puntos": 250
}
```

---

# 6.6 Configuración de Firebase Authentication

Para utilizar Authentication primero se debe habilitar el servicio.

Proceso:

```text id="c8x5mt"
Firebase Console

        ↓

Authentication

        ↓

Configurar método de acceso

        ↓

Activar proveedor
```

---

# 6.7 Activar autenticación por correo y contraseña

En Firebase Console:

```text id="q7v3ns"
Authentication

        ↓

Sign-in method

        ↓

Email/Password

        ↓

Activar
```

---

Después Firebase permitirá:

* crear usuarios;
* iniciar sesión;
* administrar cuentas.

---

# 6.8 Integración con Flutter

Para utilizar Authentication en Flutter se agrega el paquete:

```bash
 id="r5q8kw"
flutter pub add firebase_auth
```

---

La arquitectura del proyecto queda:

```text id="w4m7sx"
Flutter

    │

    ├── firebase_core

    │

    └── firebase_auth

             │

             ▼

 Firebase Authentication
```

---

# 6.9 Inicialización del servicio Authentication

Ejemplo conceptual:

```dart
 id="a8q4my"
FirebaseAuth auth = FirebaseAuth.instance;
```

Esta instancia permite acceder a:

* registro;
* login;
* logout;
* usuario actual.

---

# 6.10 Registro de usuarios

Método utilizado:

```dart
createUserWithEmailAndPassword()
```

Flujo:

```text id="g9m2xw"
Formulario registro

        ↓

Flutter recibe datos

        ↓

Firebase Authentication

        ↓

Cuenta creada

        ↓

UID generado
```

---

Ejemplo:

Datos:

```text id="h5v8pq"
Correo:

estudiante@email.com


Contraseña:

********
```

Resultado:

```text id="k3n7wd"
Usuario creado

UID:

8shd72ks
```

---

# 6.11 Inicio de sesión

Método:

```dart
signInWithEmailAndPassword()
```

Flujo:

```text id="q9x6jm"
Usuario introduce credenciales

        ↓

Flutter envía información

        ↓

Firebase valida

        ↓

Sesión iniciada
```

---

Resultado:

```text id="p3w7ms"
Usuario autenticado:

UID: 8shd72ks
```

---

# 6.12 Cierre de sesión

Cerrar sesión elimina la sesión activa.

Método:

```dart
signOut()
```

Flujo:

```text id="x7k5vq"
Usuario pulsa salir

        ↓

Firebase elimina sesión

        ↓

Aplicación vuelve al login
```

---

# 6.13 Usuario actualmente autenticado

Firebase permite conocer qué usuario está conectado.

Ejemplo conceptual:

```dart
 id="f6n2cz"
FirebaseAuth.instance.currentUser;
```

Retorna:

```text id="b8v5mw"
Usuario actual

UID

Correo

Información básica
```

---

# 6.14 Integración Authentication + Firestore

Normalmente Authentication no almacena toda la información del usuario.

Se utiliza junto con Firestore.

Arquitectura:

```text id="j9m3qp"
Firebase Authentication

        │

        │ UID

        ▼

Cloud Firestore


usuarios

 └── UID

      ├── nombre

      ├── edad

      ├── progreso

      └── logros
```

---

Ejemplo:

Authentication:

```json
 id="n6q8tr"
{
 "uid": "123abc",
 "email": "usuario@gmail.com"
}
```

Firestore:

```json
 id="v3x7mk"
{
 "nombre": "Ana",
 "nivel": 2,
 "puntos": 150
}
```

---

# 6.15 Seguridad con Firebase Authentication

Authentication es la primera capa de seguridad.

Permite establecer:

* usuarios válidos;
* sesiones activas;
* identidad del usuario.

Pero debe combinarse con reglas de seguridad.

Ejemplo:

```text id="k8p2ws"
Usuario autenticado

        ↓

Puede acceder a sus datos

        ↓

No puede modificar datos de otros usuarios
```

---

# 6.16 Reglas de seguridad relacionadas

Ejemplo conceptual de regla Firestore:

```text id="r2w7mz"
Si UID solicitado

=

UID autenticado

Permitir acceso
```

---

Esto evita:

```text id="s8k4vp"
Usuario A

        ❌

Modificar datos Usuario B
```

---

# 6.17 Manejo de errores

Una aplicación profesional debe controlar errores.

Ejemplos:

## Correo inválido

```text id="x2m6qn"
Correo no válido
```

---

## Contraseña débil

```text id="w5p8sk"
Contraseña insuficiente
```

---

## Usuario inexistente

```text id="c3v7mh"
Cuenta no encontrada
```

---

## Contraseña incorrecta

```text id="m9q4xr"
Credenciales incorrectas
```

---

# 6.18 Buenas prácticas

## No almacenar contraseñas manualmente

Incorrecto:

```dart
String password = "123456";
```

---

Firebase administra:

* cifrado;
* almacenamiento seguro;
* validación.

---

## Separar autenticación de perfiles

Recomendado:

```text id="q8n5vx"
Authentication

↓

Identidad


Firestore

↓

Información del perfil
```

---

## Mantener sesiones correctamente

Controlar:

* usuario conectado;
* cierre de sesión;
* expiración.

---

## Aplicar validaciones

Antes de enviar información:

* comprobar correo;
* validar contraseña;
* mostrar errores claros.

---

# 6.19 Flujo completo del usuario en el proyecto

Ejemplo:

```text id="w7m3qk"
Usuario abre aplicación

          ↓

Pantalla Login

          ↓

Firebase Authentication

          ↓

Usuario validado

          ↓

Obtener UID

          ↓

Consultar Firestore

          ↓

Mostrar progreso
```

---

# 6.20 Arquitectura final después de Authentication

Después de este capítulo:

```text id="p6x9mw"
                 Flutter

                    │

                    ▼

              Firebase Core

                    │

                    ▼

          Firebase Authentication

                    │

                    ▼

                   UID

                    │

                    ▼

             Cloud Firestore
```

---

# Conclusión del capítulo

Firebase Authentication proporciona la identidad necesaria para que la aplicación pueda reconocer y gestionar usuarios.

En el proyecto educativo permitirá:

* registrar estudiantes;
* iniciar sesiones;
* proteger información personal;
* relacionar usuarios con su progreso.

El flujo fundamental aprendido es:

```text id="v8k5rz"
Usuario

   ↓

Flutter

   ↓

Firebase Authentication

   ↓

UID

   ↓

Datos del usuario en Firestore
```

Con la autenticación implementada, el siguiente paso será trabajar con el almacenamiento principal de información:

# Capítulo 7 — Cloud Firestore

Donde se documentará el modelo NoSQL, colecciones, documentos, consultas, almacenamiento de progreso y reglas de seguridad.
