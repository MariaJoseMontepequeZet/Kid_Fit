# PARTE II — DESARROLLO CLOUD CON FLUTTER

# Capítulo 4 — Creación y configuración del proyecto Firebase

---

# 4. Introducción

Antes de integrar Firebase dentro de una aplicación Flutter es necesario crear y configurar un proyecto dentro de Firebase Console.

El proyecto Firebase será el punto central donde se administrarán todos los servicios Cloud utilizados por la aplicación.

Dentro de un proyecto Firebase estarán asociados:

* la aplicación Flutter;
* usuarios autenticados;
* base de datos Cloud Firestore;
* archivos almacenados;
* notificaciones;
* configuraciones de seguridad;
* métricas de uso.

La relación general será:

```text
 id="v2r8pa"
                  Proyecto Firebase

                         │

        ┌────────────────┼────────────────┐

        ▼                ▼                ▼

 Aplicación Flutter  Servicios Cloud  Configuración


        │                │                │


        ▼                ▼                ▼


     Android       Firestore        Authentication

                   Storage          Messaging
```

---

# 4.1 Requisitos previos

Antes de crear un proyecto Firebase se necesitan algunos elementos básicos.

---

## 4.1.1 Cuenta Google

Firebase forma parte del ecosistema Google, por lo tanto es necesario contar con una cuenta Google.

Esta cuenta permitirá:

* acceder a Firebase Console;
* administrar proyectos;
* gestionar permisos;
* utilizar servicios asociados.

---

## 4.1.2 Navegador web actualizado

Firebase Console funciona desde navegadores modernos como:

* Google Chrome;
* Mozilla Firefox;
* Microsoft Edge.

Se recomienda mantener el navegador actualizado para evitar problemas de compatibilidad.

---

## 4.1.3 Proyecto Flutter preparado

Aunque Firebase puede crearse antes de tener la aplicación terminada, es recomendable contar con un proyecto Flutter inicial.

Ejemplo:

```bash
flutter create app_educativa
```

Resultado:

```text
 id="k5c9vm"
app_educativa

├── android

├── ios

├── lib

├── pubspec.yaml

└── test
```

Este proyecto será conectado posteriormente con Firebase.

---

# 4.2 Acceso a Firebase Console

Firebase Console es la plataforma web donde se administran los proyectos.

El flujo general es:

```text
 id="9s2x0k"
Cuenta Google

        ↓

Firebase Console

        ↓

Crear proyecto

        ↓

Configurar servicios
```

Dentro de Firebase Console se pueden administrar:

* aplicaciones registradas;
* bases de datos;
* autenticación;
* almacenamiento;
* reglas de seguridad.

---

# 4.3 Creación de un nuevo proyecto Firebase

Para crear un proyecto se deben seguir estos pasos:

---

## Paso 1 — Crear proyecto

Desde Firebase Console:

```text
Crear proyecto
```

Firebase solicitará:

* nombre del proyecto;
* configuración de Analytics.

---

## Paso 2 — Definir nombre del proyecto

El nombre debe identificar claramente la aplicación.

Ejemplo:

```text
App Educativa Hábitos Saludables
```

Buenas prácticas:

Usar nombres:

* descriptivos;
* fáciles de identificar;
* relacionados con el proyecto.

Evitar nombres genéricos:

```text
Proyecto1
Prueba
FirebaseTest
```

---

# 4.4 Identificador del proyecto Firebase

Firebase genera automáticamente un identificador único.

Ejemplo:

```text
app-educativa-12345
```

Este identificador será utilizado internamente por Firebase.

Características:

* es único globalmente;
* no puede repetirse;
* generalmente no puede modificarse después.

---

Ejemplo:

```text
Nombre visible:

App Educativa

↓

ID Firebase:

app-educativa-12345
```

---

# 4.5 Google Analytics dentro del proyecto

Durante la creación Firebase pregunta si se desea activar Google Analytics.

Analytics permite recopilar información sobre el uso de la aplicación.

Ejemplos:

* usuarios activos;
* eventos;
* pantallas visitadas;
* comportamiento general.

---

Para este proyecto:

Se recomienda:

```text
Activar Analytics
```

porque permitirá aprender cómo funcionan los servicios de monitoreo Cloud.

---

Arquitectura:

```text
 id="4s0bq7"
Aplicación Flutter

        ↓

Eventos de uso

        ↓

Firebase Analytics

        ↓

Panel de estadísticas
```

---

# 4.6 Selección de cuenta Analytics

Si Analytics está activado, Firebase solicitará seleccionar una cuenta.

Opciones:

* utilizar una existente;
* crear una nueva.

Para un proyecto académico normalmente se recomienda:

```text
Crear una cuenta nueva
```

con un nombre relacionado con el proyecto.

Ejemplo:

```text
Analytics App Educativa
```

---

# 4.7 Finalización de creación del proyecto

Después de confirmar la configuración:

Firebase realizará:

* creación del proyecto;
* configuración inicial;
* activación de recursos.

Proceso:

```text
 id="2x9h1d"
Configuración

      ↓

Firebase crea proyecto

      ↓

Servicios disponibles

      ↓

Panel Firebase Console
```

Al finalizar aparecerá el panel principal.

---

# 4.8 Estructura inicial del proyecto Firebase

Un proyecto recién creado tendrá una estructura similar:

```text
 id="8w7k4m"
Proyecto Firebase

│

├── Configuración general

│

├── Aplicaciones

│

├── Authentication

│

├── Firestore Database

│

├── Storage

│

├── Cloud Messaging

│

├── Analytics

│

└── Crashlytics
```

---

# 4.9 Configuración general del proyecto

Dentro de la configuración del proyecto se encuentran datos importantes.

Ruta:

```text
Configuración del proyecto

↓

General
```

Información disponible:

* nombre del proyecto;
* ID del proyecto;
* número del proyecto;
* aplicaciones registradas.

---

Ejemplo:

```text
Nombre:

App Educativa


ID:

app-educativa-12345


Número:

123456789
```

---

# 4.10 Organización recomendada de proyectos Firebase

En proyectos profesionales se recomienda separar ambientes.

Ejemplo:

```text
 id="5m7v9a"
Organización Firebase


├── app-educativa-dev

│      Desarrollo


├── app-educativa-test

│      Pruebas


└── app-educativa-prod

       Producción
```

---

Para una etapa educativa inicial puede utilizarse un solo proyecto.

Sin embargo, es importante conocer esta práctica porque será utilizada en proyectos profesionales.

---

# 4.11 Activación inicial de servicios

Después de crear el proyecto, Firebase permite habilitar servicios según las necesidades.

Para este proyecto se utilizarán:

---

## Authentication

Estado inicial:

```text
Crear y administrar usuarios
```

---

## Cloud Firestore

Estado inicial:

```text
Base de datos Cloud
```

---

## Storage

Estado inicial:

```text
Archivos multimedia
```

---

## Cloud Messaging

Estado inicial:

```text
Notificaciones push
```

---

## Analytics

Estado inicial:

```text
Métricas de uso
```

---

# 4.12 Configuración del plan Firebase

Firebase ofrece diferentes planes.

Para este proyecto se utilizará:

# Plan Spark

Características:

* gratuito;
* adecuado para aprendizaje;
* límites definidos;
* sin configuración de facturación.

---

Arquitectura económica:

```text
 id="3n9h2m"
Aplicación Flutter

        ↓

Firebase Spark

        ↓

Servicios gratuitos disponibles
```

---

Cuando una aplicación crece, puede migrarse al plan Blaze.

---

# 4.13 Configuración de facturación

Aunque Firebase permite crear proyectos gratuitos, algunos servicios avanzados pueden requerir configuración de facturación.

Para el proyecto académico:

```text
No activar facturación inicialmente
```

La configuración debe mantenerse dentro del plan gratuito.

---

# 4.14 Reglas iniciales de seguridad

Después de crear servicios como Firestore y Storage, Firebase solicitará elegir reglas iniciales.

Existen normalmente dos modos:

---

## Modo prueba

Permite acceso temporal amplio.

Ejemplo:

```text
Cualquier usuario puede leer/escribir
```

Ventaja:

* facilita aprendizaje.

Desventaja:

* inseguro para producción.

---

## Modo producción

Aplica restricciones desde el inicio.

Ejemplo:

```text
Solo usuarios autenticados pueden acceder
```

---

Para aprendizaje:

Puede utilizarse modo prueba durante configuración inicial.

Pero antes de publicar la aplicación:

```text
Cambiar reglas de seguridad
```

---

# 4.15 Buenas prácticas al crear el proyecto

## Usar nombres claros

Correcto:

```text
app-habitos-saludables
```

Incorrecto:

```text
test123
```

---

## Mantener documentación

Registrar:

* nombre del proyecto;
* ID Firebase;
* servicios activos;
* configuraciones importantes.

---

## No compartir información sensible

Nunca publicar:

* claves privadas;
* archivos administrativos;
* credenciales.

---

## Crear una estructura organizada

Ejemplo:

```text
Documentación

├── Firebase

│      ├── Configuración

│      ├── Servicios

│      └── Seguridad


├── Flutter

│      └── Integración

└── Deploy
```

---

# 4.16 Preparación para conectar Flutter

Después de crear el proyecto Firebase, el siguiente paso será registrar la aplicación Android.

El flujo completo será:

```text
 id="x8m1vp"
Proyecto Firebase creado

          ↓

Registrar aplicación Android

          ↓

Descargar configuración Firebase

          ↓

Instalar FlutterFire

          ↓

Inicializar Firebase
```

---

# 4.17 Resumen del capítulo

En este capítulo se creó la base Cloud del proyecto.

Se aprendió:

* qué es un proyecto Firebase;
* cómo crear uno;
* cómo organizarlo;
* cómo activar servicios;
* cómo seleccionar el plan adecuado;
* cómo preparar la integración con Flutter.

La arquitectura creada queda:

```text
 id="7kq2fs"
                 Firebase Project

                        │

        ┌───────────────┼───────────────┐

        ▼               ▼               ▼

 Authentication   Firestore        Storage


                        │


                        ▼


              Cloud Messaging


                        │


                        ▼


               Flutter Application
```

---

# Próximo capítulo

# Capítulo 5 — Integración Firebase con Flutter (FlutterFire)

En el siguiente capítulo se realizará la conexión técnica entre Flutter y Firebase utilizando:

* Firebase CLI;
* FlutterFire CLI;
* configuración del proyecto;
* archivo `firebase_options.dart`;
* inicialización de Firebase dentro de la aplicación Flutter.
