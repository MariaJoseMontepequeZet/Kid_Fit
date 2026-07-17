# README 04 - Instalación y Configuración de Git para Cursor (Windows y Linux)

---

## Objetivo del capítulo

En este capítulo aprenderás a instalar Git correctamente desde cero, configurar tu identidad como desarrollador y dejar tu sistema preparado para que Cursor y Git trabajen en perfecta sincronía. Además, automatizaremos tu entorno para que **todos tus proyectos inicien siempre con la rama `main**` por defecto.

---

## ¿Qué son Git y GitHub? (Y por qué no son lo mismo)

Es un error muy común entre principiantes confundir estos dos términos. Para evitar enredos, analicemos esta tabla comparativa:

| Característica | Git | GitHub |
| --- | --- | --- |
| **¿Qué es?** | Un software de control de versiones. | Una plataforma web en la nube. |
| **¿Dónde vive?** | Instalado localmente en tu computadora. | En los servidores de Internet de Microsoft. |
| **¿Para qué sirve?** | Toma "fotos" (commits) del historial de tu código. | Guarda una copia de seguridad pública o privada de tus proyectos. |
| **¿Requiere Internet?** | **No.** Funciona 100% sin conexión. | **Sí.** Lo necesitas para subir o descargar proyectos. |

> 💡 **En pocas palabras:** Git es la máquina del tiempo que registra los cambios de tu código en tu máquina; GitHub es la red social y el almacén en la nube donde compartes esa máquina del tiempo con el mundo.

---

## 💻 Instalación de Git

### En Windows

1. Abre tu navegador e ingresa al sitio oficial: [https://git-scm.com/downloads](https://git-scm.com/downloads).
2. Haz clic en **Download for Windows** y ejecuta el archivo descargado (normalmente llamado `Git-2.xx.x-64-bit.exe`).
3. **El Asistente de Instalación:** Verás una gran cantidad de opciones avanzadas. Si estás empezando, **deja absolutamente todas las opciones predeterminadas** y haz clic en *Next* (Siguiente) hasta llegar a *Install*.
4. Al finalizar, haz clic en **Finish**.

### En Ubuntu y Linux Mint

En la gran mayoría de distribuciones Linux, Git ya viene preinstalado. Vamos a comprobarlo:

1. Abre una terminal con `Ctrl + Alt + T`.
2. Escribe el comando:
```bash
git --version

```


3. Si la terminal te devuelve un número de versión (ej. `git version 2.xx.x`), ya estás listo. Si te dice "command not found", instálalo ejecutando:
```bash
sudo apt update && sudo apt install git -y

```



---

## ⚙️ Configuración Inicial Obligatoria (Tu Firma)

Git necesita saber quién eres. Cada vez que guardes un cambio importante, Git firmará ese registro con tu nombre y correo. Si no haces esto, no te dejará crear registros más adelante.

Abre tu terminal (o la terminal integrada de Cursor con `Ctrl + ``)  ejecuta los siguientes comandos:

### 1. Registrar tu Nombre y Correo
```bash

git config --global user.name "TuNombreDeGitHub"
git config --global user.email "tu-correo@ejemplo.com"
```

> ⚠️ **Nota:** Intenta utilizar el mismo correo electrónico con el que creaste (o crearás) tu cuenta de GitHub.


### 2. Automatizar la Rama Principal a `main` (¡Importante!)

Por motivos históricos, Git solía crear por defecto una rama llamada `master`. Hoy en día, el estándar de la industria mundial es usar **`main`**. Para evitar tener que cambiarlo manualmente en cada proyecto, ejecuta este comando para automatizarlo de golpe:

```bash
git config --global init.defaultBranch main

```

A partir de ahora, cada nuevo repositorio que crees nacerá configurado con la rama correcta de forma inmediata.

### 3. Vincular Cursor como el Editor Oficial de Git


Cuando Git necesita que redactes un mensaje o resuelvas un conflicto, abrirá un editor de texto. Dependiendo de si usas Cursor, Visual Studio Code o si te gusta alternar entre ambos, puedes definir tu preferido con uno de estos comandos:

Si tu editor principal es Cursor:

```bash

git config --global core.editor "cursor --wait"

```
    
Si prefieres usar Visual Studio Code (o alternas constantemente):
    
```bash
    
git config --global core.editor "code --wait"
    
```
    🚨 Nota sobre el PATH: Para que cualquiera de estos comandos funcione, debes tener el editor correspondiente agregado al PATH de tu sistema (en Cursor se activa desde la Paleta de Comandos Ctrl+Shift+P -> Install 'cursor' command in PATH).


### 4. Configurar el formato visual y finales de línea (Opcional)

Añadiremos colores legibles a la consola y configuraremos cómo Git procesa los saltos de línea (Windows y Linux gestionan los invisibles saltos de línea de forma distinta):

```bash
# Colores automáticos para la terminal
git config --global color.ui auto

# Si estás en Windows ejecuta este:
git config --global core.autocrlf true

# Si estás en Ubuntu / Linux Mint ejecuta este en su lugar:
git config --global core.autocrlf input

```

---

## 🔍 Verificar tus Configuraciones

Para asegurarte de que escribiste todo bien y no hay errores tipográficos, ejecuta:

```bash
git config --list

```

La terminal imprimirá una lista. Busca que aparezcan tus datos tal que así:

```text
user.name=Ejemplo_nombre
user.email=correo@gmail.com
init.defaultbranch=main
core.editor=cursor --wait
color.ui=auto
...

```

*(Puedes salir de esa lista presionando la tecla `Q` en tu teclado).*

---
## 🔑 El Método más Fácil: Iniciar Sesión en GitHub desde Cursor

Olvídate de configurar complejas llaves de seguridad o escribir contraseñas raras en la terminal cada vez que quieras subir un archivo. El ecosistema de Cursor (al igual que VS Code) te permite vincular tu cuenta de GitHub de forma visual en segundos:

1. Abre **Cursor**.
2. En la esquina inferior izquierda del editor, haz clic en el icono de **Cuentas (Accounts)** (representado por la silueta de un usuario 👤).
3. Selecciona la opción **Sign in with GitHub** (Iniciar sesión con GitHub).
4. Se abrirá tu navegador web. Si ya tienes tu cuenta de GitHub abierta, solo haz clic en **Autorizar (Authorize)**.
5. El navegador te pedirá permiso para volver a abrir Cursor. Acepta.
6. **¡Listo!** Cursor guardará tus credenciales de forma segura. Ahora podrás subir, descargar y sincronizar repositorios de GitHub sin que el editor te vuelva a pedir credenciales.

---

### Paso 2: El Panel Visual de Source Control

En la barra lateral izquierda verás el icono de una rama (**Source Control**). Al hacer clic, Cursor te mostrará de forma visual todos los archivos que has creado o modificado.

* Si ves una **`U`** al lado de un archivo, significa *Untracked* (Archivo nuevo que Git aún no está vigilando).
* Si ves una **`M`**, significa *Modified* (Archivo existente que ha sufrido cambios).

### Paso 3: Tu primer Commit de prueba

Para guardar formalmente los archivos en tu máquina del tiempo a través de la consola, ejecuta:

```bash
git add .
git commit -m "Mi primer commit en la rama main"

```

*(No te preocupes si no dominas estos comandos aún; en capítulos posteriores explicaremos a fondo la lógica detrás de `add` y `commit`).*

---

## Solución de errores comunes

### 1. Git dice: "Fatal: not a git repository"

* **Causa:** Intentaste ejecutar un comando de Git (como `git status` o `git add`) en una carpeta que no ha sido inicializada.
* **Solución:** Ejecuta primero `git init` en esa carpeta.

### 2. Escribí mal mi nombre o mi correo electrónico

* **Solución:** No te preocupes, las configuraciones globales se sobrescriben simplemente volviendo a ejecutar el comando con el dato correcto. Ejemplo: `git config --global user.name "NombreCorrecto"`.

---

## Checklist de control

Antes de pasar a la conexión con servidores remotos, valida que todo esté en orden:

* [ ] Ejecuto `git --version` y obtengo una respuesta válida.
* [ ] Configuré mi nombre y correo electrónico global.
* [ ] Ejecuté el comando para forzar el uso de la rama `main` por defecto.
* [ ] Vinculé `cursor --wait` como mi editor de Git y tengo Cursor agregado al PATH del sistema.
* [ ] Puedo ver mi lista completa de configuraciones usando `git config --list`.

---

## Próximo capítulo (Opcional)

En el siguiente capítulo explicaremos cómo configurar **llaves SSH en GitHub**.

> ⚠️ **Nota Importante:** Este capítulo será **100% opcional**. Si ya iniciaste sesión en GitHub de forma visual desde tu editor (tal como lo aprendimos arriba), ya tienes todo lo necesario para subir tus proyectos. Solo te recomendamos seguir el siguiente capítulo si trabajas en redes corporativas muy restrictivas, si prefieres gestionar tus credenciales de forma manual por consola o si quieres una capa de seguridad criptográfica avanzada en tu máquina.