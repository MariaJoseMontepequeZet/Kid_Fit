# PARTE II — DESARROLLO CLOUD CON FLUTTER

# Capítulo 9 — Firebase Cloud Messaging (FCM)

---

# 9. Introducción

Una aplicación móvil educativa necesita mantener una comunicación constante con sus usuarios.

En este proyecto, la aplicación debe poder enviar recordatorios y mensajes que ayuden a los estudiantes a mantener hábitos saludables, como:

* recordatorios de hidratación;
* avisos de nuevas actividades;
* mensajes motivacionales;
* notificaciones de logros;
* actualizaciones importantes.

Para implementar esta funcionalidad se utilizará **Firebase Cloud Messaging (FCM)**.

Firebase Cloud Messaging es el servicio encargado de enviar notificaciones push desde la nube hacia dispositivos móviles.

---

La arquitectura incorporando notificaciones será:

```text id="m7x4kp"

              Firebase Cloud Messaging

                         │

                         ▼

                Servicio de Firebase

                         │

                         ▼

                Aplicación Flutter

                         │

                         ▼

                 Dispositivo usuario

```

---

# 9.1 ¿Qué es Firebase Cloud Messaging?

Firebase Cloud Messaging (FCM) es un servicio de mensajería en la nube que permite enviar información desde Firebase hacia aplicaciones móviles, web y otros dispositivos.

Su función principal es entregar mensajes sin que la aplicación tenga que estar abierta permanentemente.

---

Ejemplo:

Sin FCM:

```text id="x8m3qv"

Aplicación abierta

        ↓

Consulta servidor

        ↓

Busca novedades

```

---

Con FCM:

```text id="p5k9mw"

Firebase envía mensaje

        ↓

Dispositivo recibe notificación

        ↓

Usuario interactúa

```

---

# 9.2 Objetivo de FCM dentro del proyecto

Dentro de la aplicación educativa, FCM permitirá crear un sistema de comunicación con los estudiantes.

Ejemplos:

---

## Recordatorios de hidratación

Caso:

El estudiante debe tomar agua.

Flujo:

```text id="w4m8ks"

Hora programada

        ↓

Firebase envía mensaje

        ↓

Usuario recibe notificación

        ↓

Completa actividad

```

---

## Reconocimiento de logros

Ejemplo:

```text id="q8n5mv"

"¡Felicitaciones!

Has alcanzado el nivel 5"
```

---

## Nuevas actividades

Ejemplo:

```text id="r3m7qx"

"Nueva actividad disponible:

Reto de movimiento"
```

---

# 9.3 Arquitectura de Firebase Cloud Messaging

FCM utiliza varios componentes.

Arquitectura general:

```text id="k6v2mx"

                 Firebase Console

                        │

                        ▼

              Firebase Cloud Messaging

                        │

                        ▼

                FCM Server

                        │

                        ▼

             Android / iOS Device

                        │

                        ▼

              Aplicación Flutter

```

---

# 9.4 Conceptos fundamentales de FCM

Antes de implementarlo es necesario comprender algunos conceptos.

---

# 9.4.1 Mensaje

Un mensaje es la información enviada al dispositivo.

Ejemplo:

```json id="n5m8qx"

{
 "title": "Recordatorio",
 "body": "Es hora de beber agua"
}

```

---

Un mensaje puede contener:

* título;
* descripción;
* datos adicionales;
* acciones.

---

# 9.4.2 Token del dispositivo

Cada instalación de la aplicación recibe un identificador único llamado:

```text id="x7q3mv"

FCM Token

```

Este token permite identificar un dispositivo específico.

Ejemplo:

```text id="p8m4ks"

Usuario:

Carlos


Dispositivo:

Android


Token:

a83kd92js82

```

---

Flujo:

```text id="m2x8qp"

Aplicación Flutter

        ↓

Solicita token FCM

        ↓

Firebase genera token

        ↓

Guarda identificación del dispositivo

```

---

# 9.4.3 Topic (Tema)

Los topics permiten enviar mensajes a grupos de usuarios.

Ejemplo:

```text id="z5m7qx"

Topic:

estudiantes_nivel_1

```

Usuarios suscritos:

```text id="v8k3mp"

Ana

Luis

Carlos

```

Mensaje enviado:

```text id="r6m2qs"

Todos reciben:

"Nueva actividad disponible"

```

---

# 9.5 Tipos de mensajes FCM

Firebase permite diferentes tipos de mensajes.

---

# 9.5.1 Mensajes de notificación

Son mensajes visibles directamente para el usuario.

Ejemplo:

```text id="q4m8xs"

Título:

Recordatorio


Mensaje:

Toma agua para completar tu objetivo

```

---

Uso:

* recordatorios;
* anuncios;
* avisos.

---

# 9.5.2 Mensajes de datos

Transportan información para que la aplicación procese.

Ejemplo:

```json id="h7m3qx"

{
 "tipo": "logro",
 "nivel": "5"
}

```

La aplicación decide qué hacer.

---

Uso:

* navegación interna;
* actualización de contenido;
* acciones personalizadas.

---

# 9.6 Integración FCM con Flutter

Para utilizar Firebase Cloud Messaging se instala:

```bash id="x3m8qv"

flutter pub add firebase_messaging

```

---

Arquitectura:

```text id="n7k2mp"

Flutter

   │

   ▼

firebase_messaging

   │

   ▼

Firebase Cloud Messaging

```

---

# 9.7 Configuración inicial de FCM

El proceso general es:

```text id="w8m4kx"

Agregar dependencia

        ↓

Solicitar permisos

        ↓

Obtener token FCM

        ↓

Configurar recepción

        ↓

Procesar mensajes

```

---

# 9.8 Permisos de notificaciones

En Android moderno las aplicaciones necesitan solicitar permisos para mostrar notificaciones.

Flujo:

```text id="m5q8vx"

Aplicación inicia

        ↓

Solicita permiso

        ↓

Usuario acepta

        ↓

Notificaciones habilitadas

```

---

Ejemplo:

```text id="k8m4qp"

"Permitir que App Educativa

envíe notificaciones"

```

---

# 9.9 Obtener token FCM

Cada instalación necesita conocer su token.

Flujo:

```text id="z7x3mv"

Flutter

   ↓

Firebase Messaging

   ↓

Genera token

   ↓

Guardar token

```

---

El token puede almacenarse en Firestore:

Ejemplo:

```json id="r8m2kx"

{
 "usuario": "Carlos",
 "fcmToken": "a83kd92js82"
}

```

---

# 9.10 Recepción de mensajes en Flutter

FCM maneja diferentes estados de la aplicación.

---

# 9.10.1 Aplicación abierta

Estado:

```text id="q5m8xs"

Flutter activo

```

El mensaje puede ser procesado directamente.

---

# 9.10.2 Aplicación en segundo plano

Estado:

```text id="v4k9mp"

Aplicación minimizada

```

El sistema muestra la notificación.

---

# 9.10.3 Aplicación cerrada

Estado:

```text id="n8m3qx"

Aplicación terminada

```

El usuario recibe la notificación al dispositivo.

---

# 9.11 Arquitectura de notificaciones del proyecto

Ejemplo:

Sistema de hidratación:

```text id="x6m2qv"

Servicio programado

        │

        ▼

Firebase Cloud Messaging

        │

        ▼

Dispositivo estudiante

        │

        ▼

Notificación

        │

        ▼

Usuario registra consumo de agua

        │

        ▼

Firestore actualiza progreso

```

---

# 9.12 Integración FCM + Firestore

FCM y Firestore trabajan juntos.

Firestore almacena:

* preferencias;
* horarios;
* progreso.

FCM envía:

* mensajes;
* recordatorios.

---

Ejemplo:

Firestore:

```json id="p7m4xs"

{
 "usuario": "Carlos",
 "recordatorioAgua": true,
 "hora": "10:00"
}

```

---

Sistema:

```text id="w3q8mv"

Lee configuración

        ↓

Envía notificación FCM

        ↓

Usuario recibe aviso

```

---

# 9.13 Notificaciones personalizadas

La aplicación puede crear mensajes dinámicos.

Ejemplo:

Usuario alcanza un objetivo:

Firestore:

```json id="m8x4qp"

{
 "nivel": 10,
 "logro": "Maestro hidratado"
}

```

FCM:

```text id="h5m9vx"

"¡Excelente!

Has conseguido el logro Maestro hidratado"

```

---

# 9.14 Configuración Android

Para Android, FCM utiliza los servicios de Google Play.

Requisitos:

* aplicación registrada en Firebase;
* configuración Android correcta;
* permisos establecidos.

---

La integración utiliza:

```text id="q7m2ks"

Flutter

 ↓

Firebase Messaging

 ↓

Android SDK

 ↓

Google Play Services

```

---

# 9.15 Seguridad en Firebase Cloud Messaging

Aunque FCM entrega mensajes, debe utilizarse correctamente.

Buenas prácticas:

---

## No guardar tokens públicamente

Los tokens son identificadores de dispositivos.

Deben protegerse.

---

## Validar usuarios

Enviar mensajes solamente a usuarios autorizados.

---

## Evitar abuso de notificaciones

No enviar:

* demasiados mensajes;
* contenido innecesario;
* notificaciones repetitivas.

---

# 9.16 Casos de uso futuros

La arquitectura permite agregar:

---

## Sistema de retos diarios

Ejemplo:

```text id="s5m8qx"

Cada mañana:

"Nueva actividad disponible"

```

---

## Recordatorios inteligentes

Ejemplo:

```text id="z8k4mp"

"Te falta completar tu objetivo diario"

```

---

## Mensajes educativos

Ejemplo:

```text id="n4m7xq"

"Consejo saludable del día"

```

---

# 9.17 Buenas prácticas de diseño

---

## Usar mensajes útiles

Una notificación debe aportar valor.

Incorrecto:

```text id="k3m8vp"

"Abre la aplicación"

```

Correcto:

```text id="r5q2mx"

"Completa tu reto de hidratación
y gana 20 puntos"

```

---

## Respetar al usuario

Permitir:

* activar/desactivar avisos;
* configurar horarios;
* elegir tipos de mensajes.

---

## Separar lógica de notificación

No colocar reglas directamente en la interfaz.

Recomendado:

```text id="m7x3qp"

Flutter UI

      ↓

Servicio de notificaciones

      ↓

Firebase Messaging

```

---

# 9.18 Arquitectura completa del proyecto después de FCM

Después de incorporar notificaciones:

```text id="x5m8qv"

                    Flutter

                       │

        ┌──────────────┼──────────────┐

        ▼              ▼              ▼

 Firebase Auth    Firestore       Storage

        │              │              │

        └──────────────┼──────────────┘

                       │

                       ▼

              Firebase Cloud Messaging

                       │

                       ▼

                  Usuario final

```

---

# 9.19 Resumen del capítulo

Firebase Cloud Messaging permite agregar comunicación activa entre la aplicación y los estudiantes.

En este proyecto será utilizado para:

* recordatorios de hidratación;
* avisos educativos;
* mensajes motivacionales;
* notificación de logros.

El flujo principal es:

```text id="v6m2kx"

Firebase

    ↓

Cloud Messaging

    ↓

Dispositivo

    ↓

Notificación

    ↓

Usuario

```

Con los servicios principales integrados:

* Firebase Authentication;
* Cloud Firestore;
* Firebase Storage;
* Firebase Cloud Messaging;

la siguiente etapa será preparar el entorno de desarrollo en la nube.

# Capítulo 10 — Project IDX como entorno Cloud opcional

En este capítulo se documentará:

* qué es Project IDX;
* integración con Flutter;
* configuración del workspace;
* desarrollo desde navegador;
* ventajas y limitaciones;
* comparación con entorno local tradicional.
