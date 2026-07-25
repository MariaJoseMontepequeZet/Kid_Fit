# PARTE II — DESARROLLO CLOUD CON FLUTTER

# Capítulo 8 — Firebase Storage

---

# 8. Introducción

Las aplicaciones móviles modernas no solo trabajan con datos estructurados como nombres, puntos o configuraciones. También necesitan almacenar archivos multimedia como:

* imágenes;
* fotografías de perfil;
* ilustraciones;
* documentos;
* recursos educativos;
* contenido descargable.

Para gestionar estos archivos, el proyecto utilizará **Firebase Storage**.

Firebase Storage será el servicio encargado de almacenar archivos en la nube y proporcionar acceso controlado desde la aplicación Flutter.

La arquitectura incorporando Storage será:

```text id="8h5m2k"
                    Usuario

                       │

                       ▼

                Aplicación Flutter

                       │

          ┌────────────┼────────────┐

          ▼            ▼            ▼

 Firebase Auth   Firestore     Storage

                       │

                       ▼

              Archivos Cloud
```

---

# 8.1 ¿Qué es Firebase Storage?

Firebase Storage es un servicio de almacenamiento de archivos basado en la infraestructura de Google Cloud.

Permite guardar archivos directamente desde una aplicación móvil o web sin necesidad de crear un servidor propio.

Su función principal es almacenar contenido que no debería guardarse directamente en una base de datos.

---

Ejemplo:

Información del usuario:

```json id="4q8m7x"
{
 "nombre": "Carlos",
 "nivel": 3,
 "puntos": 250
}
```

Puede almacenarse en:

```text id="7p3k9v"
Cloud Firestore
```

Pero una imagen:

```text id="z5m8q2"
perfil_usuario.png
```

Debe almacenarse en:

```text id="y6n4rp"
Firebase Storage
```

---

# 8.2 Diferencia entre Firestore y Storage

Es importante comprender la diferencia entre ambos servicios.

| Servicio         | Función                     |
| ---------------- | --------------------------- |
| Cloud Firestore  | Guardar datos estructurados |
| Firebase Storage | Guardar archivos            |

---

Ejemplo:

Usuario:

```text id="m7q3xs"
Nombre:
Ana

Nivel:
5

Puntos:
400

Imagen:
perfil.png
```

Distribución:

Firestore:

```json id="r5n8vm"
{
 "nombre": "Ana",
 "nivel": 5,
 "puntos": 400,
 "imagenUrl": "https://..."
}
```

Storage:

```text id="c8m4kp"
/usuarios

   └── ana

        └── perfil.png
```

Firestore guarda la referencia.

Storage guarda el archivo real.

---

# 8.3 Casos de uso dentro del proyecto

Firebase Storage será utilizado para recursos multimedia.

Ejemplos:

---

## Imágenes de perfil

Cada estudiante puede tener una imagen asociada.

Flujo:

```text id="h3k8mq"
Usuario selecciona imagen

        ↓

Flutter carga archivo

        ↓

Firebase Storage almacena imagen

        ↓

Firestore guarda URL
```

---

## Recursos educativos

Ejemplo:

```text id="q9m2ws"
Actividades

├── hidratacion.png

├── ejercicio.png

└── reto_diario.png
```

---

## Contenido multimedia futuro

La arquitectura permite agregar:

* videos educativos;
* audios;
* material interactivo.

---

# 8.4 Arquitectura de Firebase Storage

El funcionamiento general es:

```text id="x7v4mz"
              Aplicación Flutter

                      │

                      ▼

              Firebase Storage SDK

                      │

                      ▼

              Firebase Storage

                      │

                      ▼

                Archivo almacenado

                      │

                      ▼

                    URL
```

---

La aplicación no necesita administrar:

* servidores de archivos;
* discos;
* permisos físicos;
* infraestructura.

Firebase administra el almacenamiento.

---

# 8.5 Estructura de archivos en Storage

Firebase Storage utiliza una estructura basada en rutas.

Ejemplo:

```text id="n5k8qp"
Storage

│

├── usuarios

│      │

│      ├── usuario001

│      │        └── perfil.png

│      │

│      └── usuario002

│               └── perfil.png

│

└── actividades

       ├── reto_agua.png

       └── ejercicio.png
```

---

Buenas prácticas:

Organizar archivos por categorías:

```text id="p8x2mk"
usuarios/

actividades/

recursos/

documentos/
```

---

# 8.6 Tipos de archivos soportados

Firebase Storage permite almacenar diferentes formatos.

Ejemplos:

## Imágenes

```text id="r6m3qw"
.png

.jpg

.webp
```

---

## Documentos

```text id="v8n5kp"
.pdf

.docx
```

---

## Multimedia

```text id="x3q7ms"
.mp4

.mp3
```

---

Para este proyecto inicialmente se utilizarán principalmente imágenes.

---

# 8.7 Configuración de Firebase Storage

Desde Firebase Console:

```text id="z8m4qx"
Firebase Console

        ↓

Storage

        ↓

Comenzar

        ↓

Seleccionar ubicación

        ↓

Configurar reglas
```

---

Firebase solicitará:

## Ubicación del almacenamiento

La ubicación determina dónde se almacenan físicamente los recursos.

Buenas prácticas:

Elegir una región cercana al público objetivo.

---

# 8.8 Reglas iniciales de Storage

Firebase Storage utiliza reglas de seguridad para controlar acceso.

Ejemplo:

```text id="m4q8xz"
Usuario autenticado

        ↓

Puede subir archivos

        ↓

Puede acceder a sus recursos
```

---

Sin reglas adecuadas:

```text id="q7n3vp"
Cualquier usuario

        ↓

Puede modificar archivos
```

Esto representa un riesgo.

---

# 8.9 Integración con Flutter

Para utilizar Firebase Storage se instala el paquete:

```bash id="w5k9mr"
flutter pub add firebase_storage
```

---

Arquitectura:

```text id="k3p8mx"
Flutter

   │

   ▼

firebase_storage

   │

   ▼

Firebase Storage
```

---

# 8.10 Inicialización de Firebase Storage

La instancia se obtiene mediante:

```dart id="p7m4vx"
FirebaseStorage.instance;
```

---

Conceptualmente:

```text id="b8q2mz"
Aplicación Flutter

        ↓

Obtiene Storage

        ↓

Puede subir o descargar archivos
```

---

# 8.11 Subir archivos a Firebase Storage

El proceso general es:

```text id="n4x7qp"
Seleccionar archivo

        ↓

Crear referencia

        ↓

Subir archivo

        ↓

Obtener URL

        ↓

Guardar referencia en Firestore
```

---

Ejemplo aplicado:

Usuario cambia imagen de perfil.

```text id="z2m8vk"
Galería del teléfono

        ↓

Imagen seleccionada

        ↓

Firebase Storage

        ↓

URL generada

        ↓

Perfil actualizado
```

---

# 8.12 Referencias en Firebase Storage

Storage utiliza objetos llamados referencias.

Una referencia representa la ubicación del archivo.

Ejemplo:

```text id="q5v9mk"
usuarios/carlos/perfil.png
```

La referencia permite:

* subir;
* descargar;
* eliminar;
* obtener URL.

---

# 8.13 Obtener URL del archivo

Después de subir un archivo, Firebase devuelve una URL.

Ejemplo:

```text id="m8x4qp"
https://storage.firebase.com/imagen123
```

Esta URL puede guardarse en Firestore.

Ejemplo:

Firestore:

```json id="v6k2ms"
{
 "nombre": "Carlos",
 "imagenUrl":
 "https://storage.firebase.com/imagen123"
}
```

---

Flujo completo:

```text id="s7m3qx"
Archivo

 ↓

Firebase Storage

 ↓

URL

 ↓

Firestore

 ↓

Perfil usuario
```

---

# 8.14 Eliminar archivos

Firebase permite eliminar archivos cuando ya no son necesarios.

Ejemplo:

Usuario cambia imagen:

```text id="p9k5mz"
Imagen antigua

        ↓

Eliminar

        ↓

Subir nueva imagen
```

---

Esto evita almacenar archivos innecesarios.

---

# 8.15 Integración Storage + Firestore

La arquitectura recomendada es:

```text id="x8q3mp"
              Firebase Storage

                     │

                     │ URL

                     ▼

              Cloud Firestore

                     │

                     ▼

              Aplicación Flutter
```

---

Ejemplo:

Storage:

```text id="w5n9vk"
usuarios/carlos/avatar.png
```

---

Firestore:

```json id="r8m2qp"
{
 "usuario": "Carlos",
 "avatar":
 "usuarios/carlos/avatar.png"
}
```

---

# 8.16 Seguridad en Firebase Storage

La seguridad es una parte fundamental.

Las reglas deben controlar:

* quién puede subir archivos;
* quién puede leerlos;
* quién puede eliminarlos.

---

Ejemplo:

Usuario autenticado:

```text id="z7m4xq"
Puede modificar su propia imagen
```

Otro usuario:

```text id="n6p8vk"
No puede modificarla
```

---

Regla conceptual:

```text id="q4m7xs"
Si usuario autenticado

Y ruta pertenece al usuario

Permitir acceso
```

---

# 8.17 Validación de archivos

Antes de subir archivos se recomienda validar:

---

## Tamaño

Ejemplo:

```text id="v3q8mk"
Imagen máxima:

5 MB
```

---

## Tipo

Permitir:

```text id="b8x2mq"
.jpg

.png

.webp
```

Evitar:

```text id="m5q7vp"
.exe

.zip desconocidos
```

---

## Nombre del archivo

Evitar:

```text id="q9m3kx"
imagen final nueva nueva.png
```

Preferir:

```text id="r7x5mv"
perfil_usuario_001.png
```

---

# 8.18 Buenas prácticas con Storage

---

## Separar archivos por categorías

Correcto:

```text id="p4m8xq"
usuarios/

actividades/

recursos/
```

---

## No guardar archivos grandes innecesarios

Optimizar:

* imágenes;
* resolución;
* formatos.

---

## Usar nombres organizados

Ejemplo:

```text id="n8q3mv"
usuario_UID_tipo_fecha
```

---

## Proteger mediante reglas

Nunca dejar Storage abierto permanentemente.

---

# 8.19 Caso práctico del proyecto

Ejemplo:

Un estudiante desbloquea un logro.

La aplicación muestra una imagen.

Flujo:

```text id="k6m9qx"
Usuario completa actividad

        ↓

Firestore actualiza logro

        ↓

Flutter solicita imagen

        ↓

Firebase Storage entrega recurso

        ↓

Aplicación muestra premio
```

---

# 8.20 Arquitectura final después de Storage

Después de integrar Storage:

```text id="s8m2vx"
                    Flutter

                       │

                       ▼

              Firebase Authentication

                       │

                       ▼

              Cloud Firestore

                       │

             ┌─────────┴─────────┐

             ▼                   ▼

        Datos usuario       Firebase Storage

                                 │

                                 ▼

                              Archivos
```

---

# Conclusión del capítulo

Firebase Storage proporciona la capacidad de almacenar archivos multimedia dentro de la arquitectura Cloud del proyecto.

Su función complementa a Firestore:

```text id="q7m4px"
Firestore

↓

Información estructurada


Storage

↓

Archivos multimedia
```

En el proyecto permitirá manejar:

* imágenes de usuarios;
* recursos educativos;
* contenido multimedia futuro.

Con Authentication, Firestore y Storage integrados, la siguiente etapa será agregar comunicación activa con los usuarios mediante:

# Capítulo 9 — Firebase Cloud Messaging

Donde se documentará:

* arquitectura de notificaciones push;
* configuración FCM;
* permisos Android;
* envío de mensajes;
* casos de uso dentro de la aplicación educativa.
