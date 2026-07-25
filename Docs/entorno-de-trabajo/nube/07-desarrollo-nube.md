# PARTE II — DESARROLLO CLOUD CON FLUTTER

# Capítulo 7 — Cloud Firestore

---

# 7. Introducción

Una aplicación móvil moderna necesita almacenar información que pueda ser consultada y actualizada por diferentes usuarios y dispositivos.

En este proyecto, la información principal de los estudiantes será almacenada utilizando **Cloud Firestore**, la base de datos Cloud de Firebase.

Firestore será responsable de almacenar información como:

* perfiles de usuarios;
* progreso educativo;
* puntos obtenidos;
* niveles;
* actividades completadas;
* logros desbloqueados;
* configuraciones del usuario.

La arquitectura del sistema después de incorporar Firestore será:

```text id="8z4m2x"
                 Usuario

                    │

                    ▼

             Aplicación Flutter

                    │

                    ▼

          Firebase Authentication

                    │

                    ▼

              UID Usuario

                    │

                    ▼

             Cloud Firestore

                    │

                    ▼

          Datos de la aplicación
```

---

# 7.1 ¿Qué es Cloud Firestore?

Cloud Firestore es una base de datos NoSQL administrada por Firebase diseñada para aplicaciones móviles y web.

Permite almacenar información en la nube utilizando una estructura basada en:

```text id="m5q8vx"
Colecciones

      ↓

Documentos

      ↓

Campos
```

A diferencia de una base de datos relacional tradicional basada en tablas y filas, Firestore utiliza documentos flexibles.

---

Ejemplo comparación:

## Base de datos SQL tradicional

```text id="a7n2pk"
Tabla Usuarios

--------------------------------
ID | Nombre | Edad | Nivel
--------------------------------
1  | Ana    | 10   | 3
2  | Luis   | 11   | 2
```

---

## Cloud Firestore

```text id="p8r5ks"
Colección: usuarios


Documento: usuario001

{
 nombre: "Ana",
 edad: 10,
 nivel: 3
}
```

---

# 7.2 Características principales de Firestore

Cloud Firestore proporciona características importantes para aplicaciones móviles.

---

## 7.2.1 Base de datos NoSQL

Firestore no utiliza tablas tradicionales.

Utiliza:

* colecciones;
* documentos;
* campos.

Ejemplo:

```text id="x4m8qd"
usuarios

 ├── usuario001

 │      ├── nombre

 │      ├── edad

 │      └── nivel

 │

 └── usuario002

        ├── nombre

        └── puntos
```

---

## 7.2.2 Sincronización en tiempo real

Firestore puede actualizar información automáticamente cuando cambia un dato.

Ejemplo:

Un estudiante completa una actividad:

```text id="h9q6sw"
Actividad completada

        ↓

Firestore actualiza datos

        ↓

Flutter recibe cambio

        ↓

Pantalla actualizada
```

---

## 7.2.3 Trabajo offline

Firestore permite almacenar temporalmente información localmente cuando no existe conexión.

Flujo:

```text id="j6r8vk"
Usuario sin Internet

        ↓

Flutter guarda cambios locales

        ↓

Internet vuelve

        ↓

Firestore sincroniza datos
```

---

## 7.2.4 Escalabilidad automática

Firebase administra la infraestructura.

El desarrollador no debe configurar:

* servidores;
* balanceadores;
* almacenamiento físico.

---

# 7.3 Modelo de datos de Firestore

Firestore utiliza una estructura jerárquica.

La organización básica es:

```text id="n7w4qm"
Colección

      ↓

Documento

      ↓

Campo
```

---

# 7.3.1 Colecciones

Una colección es un grupo de documentos relacionados.

Ejemplo:

```text id="b3x7mp"
Colección:

usuarios
```

Contiene:

```text id="z5k2vq"
usuarios

 ├── usuario001

 ├── usuario002

 └── usuario003
```

---

# 7.3.2 Documentos

Un documento representa un registro individual.

Ejemplo:

```text id="q8m5zs"
usuarios

 └── usuario001
```

Contenido:

```json
{
 "nombre": "Carlos",
 "edad": 10,
 "nivel": 3
}
```

---

# 7.3.3 Campos

Los campos contienen los valores del documento.

Ejemplo:

```json
{
 "nombre": "Carlos",
 "puntos": 250,
 "activo": true
}
```

Campos:

```text id="v9k3wx"
nombre

puntos

activo
```

---

# 7.4 Firestore dentro del proyecto educativo

La estructura inicial será:

```text id="w4n8cq"
Firestore

│

├── usuarios

│      └── UID_usuario

│              ├── nombre

│              ├── edad

│              ├── puntos

│              ├── nivel

│              └── progreso

│

├── actividades

│      └── actividad_id

│              ├── titulo

│              ├── descripción

│              └── recompensa

│

└── logros

       └── logro_id

               ├── nombre

               └── condición
```

---

# 7.5 Relación entre Authentication y Firestore

Firebase Authentication identifica al usuario.

Firestore almacena la información adicional.

La relación se realiza mediante el UID.

Arquitectura:

```text id="m2q9yv"
Firebase Authentication

        │

        │ UID

        ▼

Cloud Firestore


usuarios

 └── UID_usuario

        ├── nombre

        ├── puntos

        ├── nivel

        └── progreso
```

---

Ejemplo:

Authentication:

```json
{
 "uid": "a82jd91",
 "email": "usuario@gmail.com"
}
```

Firestore:

```json
{
 "nombre": "Ana",
 "nivel": 4,
 "puntos": 350
}
```

---

# 7.6 Tipos de datos en Firestore

Firestore permite diferentes tipos de información.

---

## Texto

```json
{
 "nombre": "Carlos"
}
```

---

## Número

```json
{
 "puntos": 250
}
```

---

## Booleano

```json
{
 "activo": true
}
```

---

## Fecha

```json
{
 "fechaRegistro": "2026-07-24"
}
```

---

## Lista

```json
{
 "logros": [
   "Primer reto",
   "Nivel 2"
 ]
}
```

---

## Objeto

```json
{
 "perfil": {
   "edad": 10,
   "ciudad": "Guatemala"
 }
}
```

---

# 7.7 Crear una base de datos Firestore

Desde Firebase Console:

```text id="h5w7kp"
Firestore Database

        ↓

Crear base de datos

        ↓

Seleccionar ubicación

        ↓

Configurar reglas
```

---

Firebase solicitará elegir:

## Modo prueba

Permite desarrollar rápidamente.

Ejemplo:

```text id="r7p3nx"
Acceso temporal abierto
```

---

## Modo producción

Utiliza reglas más restrictivas.

Ejemplo:

```text id="d4m8qs"
Solo usuarios autorizados
```

---

Para aprendizaje:

Se puede iniciar con modo prueba, pero posteriormente se deben crear reglas seguras.

---

# 7.8 Integración de Firestore con Flutter

Primero se agrega el paquete:

```bash id="h2z8mq"
flutter pub add cloud_firestore
```

---

Arquitectura:

```text id="y8m4pz"
Flutter

   │

   ▼

cloud_firestore

   │

   ▼

Cloud Firestore
```

---

# 7.9 Inicialización de Firestore

Firestore utiliza Firebase Core como base.

Ejemplo conceptual:

```dart
FirebaseFirestore firestore =
    FirebaseFirestore.instance;
```

---

Esta instancia permite:

* crear documentos;
* leer datos;
* actualizar información;
* eliminar registros.

---

# 7.10 Crear documentos en Firestore

Existen dos formas principales.

---

# 7.10.1 Crear documento con ID automático

Ejemplo:

```text id="p3x8qn"
usuarios

 └── AutoID123
```

Firebase genera el identificador.

---

Uso recomendado:

* registros temporales;
* listas;
* colecciones donde el ID no importa.

---

# 7.10.2 Crear documento con ID personalizado

Ejemplo:

```text id="f5m7qs"
usuarios

 └── UID_usuario
```

Es recomendado para perfiles de usuario.

---

Ejemplo:

```json
{
 "nombre": "Carlos",
 "nivel": 2
}
```

---

# 7.11 Leer información desde Firestore

Flutter puede consultar documentos.

Ejemplo:

```text id="n9q2mf"
Flutter solicita datos

        ↓

Firestore busca documento

        ↓

Devuelve información

        ↓

Flutter actualiza interfaz
```

---

Ejemplo del proyecto:

El usuario abre la aplicación:

```text id="q7v5km"
Solicitar progreso

        ↓

Buscar UID

        ↓

Leer Firestore

        ↓

Mostrar nivel y puntos
```

---

# 7.12 Actualizar documentos

Firestore permite modificar información existente.

Ejemplo:

Antes:

```json
{
 "puntos": 100
}
```

Después:

```json
{
 "puntos": 150
}
```

---

Caso del proyecto:

Usuario completa actividad:

```text id="k4m9xp"
Actividad completada

        ↓

Actualizar puntos

        ↓

Actualizar nivel

        ↓

Guardar progreso
```

---

# 7.13 Eliminar documentos

También permite eliminar información.

Ejemplo:

```text id="w6z2pn"
Eliminar actividad antigua

        ↓

Firestore elimina documento
```

---

Debe utilizarse con cuidado porque la eliminación puede afectar información importante.

---

# 7.14 Consultas en Firestore

Firestore permite realizar búsquedas.

Ejemplos:

Buscar usuarios activos:

```text id="m8x5qr"
usuarios

donde:

activo = true
```

---

Buscar actividades disponibles:

```text id="v3n7pk"
actividades

donde:

nivel >= 3
```

---

# 7.15 Índices en Firestore

Firestore utiliza índices para mejorar consultas.

Cuando una consulta necesita un índice adicional, Firebase puede solicitar crearlo.

Ejemplo:

```text id="j5q8mw"
Buscar:

nivel + fecha

↓

Crear índice compuesto
```

---

Los índices permiten:

* consultas rápidas;
* mejor rendimiento;
* escalabilidad.

---

# 7.16 Reglas de seguridad de Firestore

Las reglas controlan quién puede acceder a los datos.

Ejemplo:

Usuario autenticado:

```text id="w9m3vk"
Puede leer sus propios datos
```

Usuario diferente:

```text id="x7q2mp"
No puede acceder
```

---

Ejemplo conceptual:

```text id="b5n8qy"
Si usuario autenticado

Y UID coincide

Permitir acceso
```

---

# 7.17 Buenas prácticas de diseño Firestore

---

## Diseñar antes de crear colecciones

No crear datos sin planificación.

Ejemplo:

Incorrecto:

```text id="f7m2qx"
datos1

datos2

datosfinal
```

---

Correcto:

```text id="v8p4ms"
usuarios

actividades

logros
```

---

## Evitar documentos demasiado grandes

Un documento debe contener información relacionada.

---

## Usar nombres claros

Correcto:

```text id="q2n5vx"
usuarios

actividades

progreso
```

Incorrecto:

```text id="p7x3mq"
data1

info2
```

---

## Diseñar pensando en consultas

Firestore debe organizarse según cómo se leerán los datos.

---

# 7.18 Arquitectura final con Firestore

Después de este capítulo:

```text id="r6m8xk"
                    Flutter

                       │

                       ▼

             Firebase Authentication

                       │

                       ▼

                      UID

                       │

                       ▼

                Cloud Firestore

                       │

          ┌────────────┼────────────┐

          ▼            ▼            ▼

      Usuarios     Progreso     Actividades

```

---

# 7.19 Caso práctico del proyecto

Ejemplo:

Un estudiante completa un reto de hidratación.

Flujo:

```text id="z3m7kp"
1. Usuario pulsa "Tomé agua"

            ↓

2. Flutter procesa evento

            ↓

3. Firestore actualiza progreso

            ↓

4. Puntos aumentan

            ↓

5. Flutter muestra nuevo nivel
```

Datos almacenados:

```json
{
 "usuario": "Carlos",
 "agua": 8,
 "puntos": 500,
 "nivel": 5
}
```

---

# Conclusión del capítulo

Cloud Firestore será el núcleo de almacenamiento de información del proyecto.

A través de Firestore la aplicación podrá:

* guardar perfiles;
* registrar progreso;
* almacenar actividades;
* consultar información;
* sincronizar datos.

La arquitectura aprendida es:

```text id="h8q4mx"
Usuario

 ↓

Flutter

 ↓

Authentication

 ↓

UID

 ↓

Cloud Firestore

 ↓

Datos del usuario
```

Con Firestore integrado, el siguiente paso será trabajar con archivos y recursos multimedia.

# Capítulo 8 — Firebase Storage

En este capítulo se documentará:

* almacenamiento de imágenes;
* gestión de archivos;
* subida desde Flutter;
* obtención de URLs;
* seguridad de recursos almacenados.
