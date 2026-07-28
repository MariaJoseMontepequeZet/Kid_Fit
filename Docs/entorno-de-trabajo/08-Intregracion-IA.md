# Capítulo 8 — Herramientas Firebase CLI y FlutterFire CLI (Configuración adicional)

## Objetivos

Al finalizar este capítulo el estudiante será capaz de:

* Comprender qué son Firebase CLI y FlutterFire CLI.
* Instalar Firebase CLI en Linux Mint Cinnamon, Ubuntu y Windows.
* Instalar FlutterFire CLI.
* Iniciar sesión con una cuenta Firebase.
* Verificar que las herramientas funcionan correctamente.
* Comprender cuándo utilizar cada herramienta dentro de un proyecto Flutter.
* Preparar el entorno profesional antes de integrar Firebase en una aplicación móvil.

---

# 1. Introducción

En los capítulos anteriores aprendimos a preparar Flutter, crear proyectos y conectar aplicaciones con Firebase.

Para realizar esta integración de una manera moderna, Firebase proporciona herramientas de línea de comandos (CLI).

CLI significa:

```text
Command Line Interface

Interfaz de línea de comandos
```

Esto permite administrar servicios utilizando comandos desde una terminal.

El flujo profesional utiliza:

```text
Terminal

↓

Firebase CLI

↓

Proyecto Firebase

↓

FlutterFire CLI

↓

Aplicación Flutter
```

---

# 2. ¿Qué es Firebase CLI?

Firebase CLI es una herramienta oficial de Google que permite administrar proyectos Firebase desde la terminal.

Con Firebase CLI podemos:

* Iniciar sesión en Firebase.
* Crear y administrar proyectos.
* Configurar servicios.
* Desplegar aplicaciones.
* Ejecutar herramientas Firebase.
* Trabajar con diferentes entornos.

---

Ejemplo:

Sin Firebase CLI:

```text
Abrir navegador

↓

Buscar Firebase Console

↓

Configurar manualmente
```

Con Firebase CLI:

```bash
firebase login
```

El usuario queda conectado desde la terminal.

---

# 3. ¿Qué es FlutterFire CLI?

FlutterFire CLI es una herramienta creada específicamente para conectar proyectos Flutter con Firebase.

Su función principal es automatizar la configuración.

Antes:

El desarrollador debía configurar manualmente:

* Android.
* iOS.
* Archivos de configuración.
* Claves.
* Servicios Firebase.

Ahora:

```bash
flutterfire configure
```

Genera automáticamente:

```text
lib/firebase_options.dart
```

Este archivo permite que Flutter conozca:

* Qué proyecto Firebase utilizar.
* Qué plataformas están conectadas.
* Qué configuración corresponde a cada sistema.

---

# 4. Diferencia entre Firebase CLI y FlutterFire CLI

Aunque tienen nombres parecidos, cumplen funciones diferentes.

| Herramienta     | Función                       |
| --------------- | ----------------------------- |
| Firebase CLI    | Administrar Firebase          |
| FlutterFire CLI | Conectar Flutter con Firebase |

Ejemplo:

Firebase CLI:

```text
Crear proyecto Firebase
Gestionar servicios
Desplegar funciones
```

FlutterFire CLI:

```text
Configurar aplicación Flutter
Generar firebase_options.dart
Conectar plataformas
```

---

# 5. Instalación de Firebase CLI en Linux Mint Cinnamon y Ubuntu

Firebase CLI funciona mediante Node.js.

Primero debemos verificar que Node.js esté instalado.

Abrir terminal:

```bash
node --version
```

Debe mostrar una versión:

Ejemplo:

```text
v22.x.x
```

También verificar npm:

```bash
npm --version
```

Resultado:

```text
10.x.x
```

---

# 6. Instalar Firebase CLI en Linux

Ejecutar:

```bash
npm install -g firebase-tools
```

La opción:

```text
-g
```

significa instalación global.

Esto permite utilizar Firebase desde cualquier carpeta.

---

Verificar instalación:

```bash
firebase --version
```

Ejemplo:

```text
14.x.x
```

Si aparece una versión:

```text
Firebase CLI instalado correctamente
```

---

# 7. Instalación de Firebase CLI en Windows

Primero instalar Node.js.

Descargar desde:

[https://nodejs.org/](https://nodejs.org/)

Seleccionar versión:

```text
LTS
```

---

Abrir PowerShell.

Verificar:

```powershell
node --version
```

Después:

```powershell
npm --version
```

---

Instalar Firebase CLI:

```powershell
npm install -g firebase-tools
```

---

Comprobar:

```powershell
firebase --version
```

Resultado esperado:

```text
Número de versión Firebase CLI
```

---

# 8. Iniciar sesión en Firebase CLI

Después de instalar Firebase CLI debemos vincular nuestra cuenta Google.

Ejecutar:

```bash
firebase login
```

Se abrirá el navegador.

Seleccionar:

```text
Cuenta Google utilizada para Firebase
```

Aceptar permisos.

Cuando termine aparecerá:

```text
Success! Logged in as usuario@gmail.com
```

---

# 9. Verificar proyectos Firebase disponibles

Ejecutar:

```bash
firebase projects:list
```

Firebase mostrará:

```text
Proyecto 1

Proyecto 2

Proyecto 3
```

Ejemplo:

```text
healthy-kids-ai
```

Esto confirma que la terminal tiene acceso a Firebase.

---

# 10. Instalación de FlutterFire CLI

Ahora instalaremos la herramienta para Flutter.

Ejecutar:

```bash
dart pub global activate flutterfire_cli
```

Flutter descargará FlutterFire CLI.

---

Verificar:

```bash
flutterfire --version
```

Resultado:

```text
FlutterFire CLI version
```

---

# 11. Configurar FlutterFire dentro de un proyecto Flutter

Abrir la carpeta del proyecto.

Ejemplo:

```bash
cd healthy_kids_ai
```

Ejecutar:

```bash
flutterfire configure
```

La herramienta preguntará:

```text
Which Firebase project do you want to use?
```

Seleccionar:

```text
healthy-kids-ai
```

---

Después:

Seleccionar plataformas:

```text
Android

iOS

Web
```

FlutterFire generará:

```text
lib/firebase_options.dart
```

---

# 12. Archivo firebase_options.dart

Este archivo es fundamental.

Ejemplo:

```text
lib

├── main.dart

├── firebase_options.dart

├── screens

├── services

└── models
```

Contiene la configuración necesaria para conectar Flutter con Firebase.

Normalmente no se modifica manualmente.

---

# 13. Flujo completo de configuración

El proceso profesional sería:

```text
Instalar Node.js

↓

Instalar Firebase CLI

↓

firebase login

↓

Instalar FlutterFire CLI

↓

Crear proyecto Flutter

↓

flutterfire configure

↓

Conectar Firebase
```

---

# 14. Uso dentro del desarrollo de una aplicación

Ejemplo:

Tenemos:

```text
Aplicación educativa Flutter
```

Necesitamos:

* Usuarios.
* Base de datos.
* Archivos.
* IA.

Proceso:

```text
Firebase Console

↓

Crear proyecto

↓

Firebase CLI

↓

Autenticar usuario

↓

FlutterFire CLI

↓

Conectar Flutter

↓

Desarrollar aplicación
```

---

# 15. Errores comunes

## Error: firebase command not found

Mensaje:

```text
firebase: command not found
```

Causa:

Firebase CLI no está agregado al PATH.

Solución:

Cerrar y abrir nuevamente la terminal.

---

## Error: flutterfire command not found

Mensaje:

```text
flutterfire: command not found
```

Solución:

Agregar Dart global packages al PATH.

Linux:

Agregar:

```bash
export PATH="$PATH:$HOME/.pub-cache/bin"
```

Después:

```bash
source ~/.bashrc
```

---

## Error de permisos en Linux

Si aparece:

```text
permission denied
```

Evitar usar:

```bash
sudo npm install -g firebase-tools
```

Preferir configurar correctamente Node.js mediante un gestor como NVM.

---

# 16. Buenas prácticas

## Mantener herramientas actualizadas

Revisar versiones:

```bash
firebase --version
```

```bash
flutterfire --version
```

---

## Utilizar siempre la cuenta correcta

Un proyecto Firebase pertenece a una cuenta Google.

Verificar:

```bash
firebase login:list
```

---

## No compartir configuraciones privadas

No publicar:

* Tokens.
* Credenciales.
* Archivos sensibles.

---

# 17. Checklist antes del desarrollo Firebase

Antes de continuar con una aplicación Flutter + Firebase debemos tener:

```text
✓ Node.js instalado

↓

✓ Firebase CLI instalado

↓

✓ Firebase login realizado

↓

✓ Flutter instalado

↓

✓ FlutterFire CLI instalado

↓

✓ Proyecto Flutter creado

↓

✓ flutterfire configure ejecutado
```

---

# Resumen

Firebase CLI y FlutterFire CLI son herramientas fundamentales para trabajar profesionalmente con Flutter y Firebase.

Firebase CLI permite administrar la plataforma Firebase desde la terminal.

FlutterFire CLI simplifica la conexión entre Flutter y Firebase.

El flujo final queda:

```text
Flutter

↓

Firebase CLI

↓

FlutterFire CLI

↓

Firebase

↓

Gemini IA

↓

Aplicación inteligente
```

Con estas herramientas configuradas, el estudiante estará preparado para desarrollar aplicaciones móviles completas utilizando Flutter, Firebase e Inteligencia Artificial.
