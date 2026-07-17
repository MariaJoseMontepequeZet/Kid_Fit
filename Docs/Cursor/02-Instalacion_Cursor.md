# README 02 - Instalación de Cursor desde Cero (Windows, Ubuntu y Linux Mint)

---

## Objetivo del capítulo

Al finalizar esta guía tendrás Cursor instalado de manera correcta en tu sistema operativo, perfectamente integrado y listo para comenzar a programar. No necesitas experiencia previa en desarrollo; explicaremos cada paso de forma sencilla, visual y directa.

---

## Antes de comenzar

### ¿Qué vamos a instalar?

Vamos a instalar únicamente **Cursor**, el editor de código basado en Visual Studio Code que cuenta con Inteligencia Artificial integrada.

> ⚠️ **Importante:** Durante este capítulo **NO** instalaremos Node.js, Git, Android Studio ni ninguna otra herramienta de programación. Esas herramientas son harina de otro costal y tendrán su propio espacio detallado en capítulos posteriores. ¡Vamos paso a paso!

---

## Requisitos previos

Antes de empezar, asegúrate de contar con:

* Una conexión estable a Internet.
* Al menos **1 GB** de espacio libre en disco (recomendado).
* Permisos de administrador para instalar programas en tu computadora.

---

## ¿Desde dónde debemos descargar Cursor?

Para garantizar que tu descarga sea segura, rápida y no contenga software modificado de dudosa procedencia, **utiliza única y exclusivamente los enlaces oficiales**:

* **Sitio web oficial:** [https://cursor.com](https://cursor.com)
* **Página oficial de descargas:** [https://cursor.com/downloads](https://cursor.com/downloads)

Al entrar a la página oficial, el sistema detectará automáticamente qué sistema operativo utilizas y te sugerirá el instalador adecuado.

---

## 💻 Instalación en Windows

### Paso 1 - Descargar el instalador

1. Abre tu navegador web (Chrome, Edge, Firefox, etc.).
2. Dirígete a [https://cursor.com/downloads](https://cursor.com/downloads).
3. Haz clic en el botón **Download for Windows**.
4. Se iniciará la descarga de un archivo ejecutable, que normalmente se llamará algo parecido a:
```text
CursorSetup.exe

```



### Paso 2 - Ejecutar el instalador

1. Una vez finalizada la descarga, abre tu explorador de archivos y ve a la carpeta **Descargas**.
2. Haz doble clic sobre el archivo `CursorSetup.exe`.
3. Si el sistema te muestra una ventana de advertencia de seguridad de Windows preguntando: *¿Desea permitir que esta aplicación realice cambios en el dispositivo?*, haz clic en **Sí**.

### Paso 3 - Esperar la instalación

A diferencia de otros programas, el instalador de Cursor es extremadamente minimalista. No verás un largo asistente de "Siguiente, Siguiente, Aceptar". El programa se instalará de forma automática en segundo plano durante unos segundos.

### Paso 4 - Primer inicio

Al finalizar, Cursor se abrirá automáticamente en tu pantalla. También podrás encontrarlo de ahora en adelante en tu menú de Inicio de Windows escribiendo simplemente **"Cursor"**.

---

## 🐧 Instalación en Ubuntu y Linux Mint

Dado que Linux Mint está basado en Ubuntu, el proceso de instalación es exactamente idéntico en ambas distribuciones.

Cursor ofrece oficialmente un paquete **`.deb`** (que es la opción recomendada por ser más limpia y automática) y un archivo portátil **AppImage** como alternativa.

---

### OPCIÓN 1 (Recomendada): Instalación mediante paquete `.deb`

El archivo `.deb` es el instalador estándar para sistemas basados en Debian, Ubuntu y Linux Mint. Al usar este método, **el sistema se encarga de todo**: crea los accesos directos en tu menú y gestiona el programa de forma nativa.

#### Paso 1 - Descargar el archivo

1. Abre tu navegador e ingresa a [https://cursor.com/downloads](https://cursor.com/downloads).
2. Haz clic en el botón **Download for Linux** (automáticamente te descargará el archivo `.deb`).
3. En tu carpeta de **Descargas** tendrás un archivo con un nombre similar a:
```text
cursor_x.xx.x_amd64.deb

```



#### Paso 2 - Instalar (Método Visual - El más fácil)

1. Abre tu gestor de archivos y entra a la carpeta **Descargas**.
2. Haz **doble clic** sobre el archivo `.deb`.
3. Se abrirá la **Tienda de Software** de tu sistema (o el instalador de paquetes *GDebi*).
4. Haz clic en el botón **Instalar** (o *Install Package*).
5. El sistema te pedirá tu contraseña de usuario por seguridad. Escríbela y presiona continuar.
6. ¡Listo! Al terminar el proceso, ya puedes buscar "Cursor" en el menú de aplicaciones e iniciarlo.

#### Paso 3 - Instalar usando la Terminal (Alternativa rápida)

Si prefieres usar la consola, puedes hacer la instalación con un solo comando:

1. Abre una terminal con la combinación de teclas `Ctrl + Alt + T`.
2. Muévete a tu carpeta de descargas e instala el paquete con `apt`:
```bash
cd ~/Descargas
sudo apt install ./cursor*.deb

```


3. Escribe tu contraseña de Linux, presiona `Enter` y deja que el gestor haga su magia.

---

### OPCIÓN 2 (Alternativa): Instalación mediante AppImage

Utiliza esta opción únicamente si tienes problemas con el paquete `.deb` o si prefieres usar Cursor de manera portátil sin instalarlo formalmente en el sistema.

#### Paso 1 - Descargar el archivo

1. Asegúrate de descargar el formato de Linux adecuado para AppImage si no quieres el instalador `.deb`.
2. Tendrás un archivo en **Descargas** con un nombre similar a:
```text
Cursor-x.x.x-x86_64.AppImage

```



#### Paso 2 - Otorgar permisos de ejecución

Para poder abrir un AppImage, debes autorizar al sistema para ejecutarlo como un programa:

1. Haz **clic derecho** sobre el archivo `.AppImage` y selecciona **Propiedades**.
2. Ve a la pestaña **Permisos**.
3. Activa la casilla que dice **"Permitir ejecutar el archivo como un programa"** (en Linux Mint suele decir *"Permitir ejecutar como un programa"*).
4. Cierra la ventana de propiedades.

*(Opcional por terminal)*:

```bash
cd ~/Descargas
chmod +x Cursor*.AppImage

```

#### Paso 3 - Ejecutar e Integrar

1. Haz **doble clic** sobre el archivo `.AppImage`.
2. Si te pregunta si deseas integrar la aplicación con el sistema (*"Would you like to integrate Cursor with your system?"*), selecciona **Yes** para que te cree un acceso directo en el menú principal.

---

🔑 Paso Final Obligatorio: Configuración de Bienvenida y Cuenta

Una vez que abras Cursor por primera vez (ya sea en Windows o Linux), aparecerá un asistente de configuración inicial (Welcome Wizard).
1. Ajustes del teclado y datos

El asistente te hará tres preguntas rápidas:

    Keyboard Settings: Te preguntará si quieres importar los atajos de teclado de otro editor. Si eres principiante o venías usando VS Code, selecciona Visual Studio Code.

    Language: Te permitirá elegir el idioma base.

    Code Privacy: Te preguntará si quieres activar el Modo Privacidad desde el inicio. Puedes dejarlo por defecto o activarlo si no deseas que tus datos se procesen para entrenar modelos.

2. ¿Por qué es obligatorio crear una cuenta?

Justo después de los ajustes iniciales, verás una pantalla que te pedirá iniciar sesión o registrarte (Sign In / Sign Up).

    💡 La Razón: Las funciones de Inteligencia Artificial (el Chat, las explicaciones de errores y el autocompletado inteligente) consumen recursos en servidores en la nube. Cursor necesita que te identifiques para poder asignarte tus créditos gratuitos mensuales del plan Hobby. Sin una cuenta vinculada, la IA estará completamente apagada.

3. Pasos para crear tu cuenta de forma gratuita:

    En la pantalla del asistente, haz clic en Sign Up (Registrarse).

    Se abrirá una pestaña en tu navegador web oficial.

    Puedes registrarte al instante utilizando tu cuenta existente de Google o tu cuenta de GitHub (muy recomendado para el futuro). También puedes ingresar un correo electrónico y una contraseña.

    Una vez registrado en la web, el navegador te mostrará un mensaje flotante diciendo: ¿Desea abrir Cursor?. Haz clic en Abrir o Permitir.

    Tu navegador le enviará la señal al editor y ¡listo! Verás tu nombre o correo en la esquina inferior izquierda de Cursor, confirmando que tu plan gratuito está activo.
---

## 🛠️ Pro-Tip de Desarrollador: Comando directo en la terminal

Una de las mejores prácticas y hábitos más comunes de los programadores es abrir carpetas de proyectos directamente desde la terminal escribiendo el comando `cursor` seguido de un punto (que significa "abrir esta carpeta aquí").

```bash
cursor .

```

Si al escribir este comando tu computadora te dice que no lo reconoce (lo cual es normal según el método de instalación), puedes activarlo de forma nativa en segundos:

1. Abre **Cursor**.
2. Presiona la combinación de teclas:
* **Windows / Linux:** `Ctrl + Shift + P`
* **macOS:** `Cmd + Shift + P`


3. Esto abrirá un buscador interno llamado la **Paleta de Comandos**. Escribe:
```text
Shell Command

```


4. Haz clic en la opción que dice: **"Shell Command: Install 'cursor' command in PATH"**.
5. ¡Listo! Cierra la terminal actual, abre una nueva en cualquier carpeta y podrás ejecutar el comando sin problemas.

---

## Solución de problemas comunes

### 1. Error de dependencias rotas al instalar el `.deb` en Linux

* **Causa:** A veces el sistema necesita instalar librerías adicionales antes de completar la instalación.
* **Solución:** Abre la terminal (`Ctrl + Alt + T`) y ejecuta estos comandos para solucionar dependencias de forma automática y reintentar:
```bash
sudo apt --fix-broken install
sudo apt install ./cursor*.deb

```



### 2. El programa no abre al hacer doble clic (En el caso de AppImage)

* **Causa probable:** Olvidaste otorgarle permisos de ejecución al archivo.
* **Solución:** Repite el **Paso 2** de la sección de AppImage y asegúrate de marcar la casilla de permisos.

### 3. No encuentro el programa en mi menú de aplicaciones

* **En Windows:** Presiona la tecla `Inicio` y escribe la palabra **Cursor**. Si aun así no aparece, es posible que la instalación se haya visto interrumpida; vuelve a ejecutar el archivo `.exe`.
* **En Linux (Si usas AppImage sin integrar):** El archivo sigue viviendo en tu carpeta de Descargas de forma aislada. Mueve el archivo manualmente a una carpeta segura (como una carpeta llamada `Programas` en tu directorio personal) y ejecútalo desde ahí. Si instalaste la versión `.deb`, este problema no debería ocurrir.

---

## Buenas prácticas de seguridad

* **Actualizaciones automáticas:** Cursor te avisará mediante una pequeña notificación flotante en la esquina inferior derecha cuando haya una nueva versión disponible. Acostúmbrate a presionar **Update** para mantener tu editor seguro y con acceso a las últimas mejoras de IA.
* **Nunca uses instaladores de terceros:** Evita portales de descarga alternativos o videos de YouTube que ofrezcan "Cursor Pro Activado" u ofertas similares. Podrían infectar tu computadora con malware. El plan gratuito de Cursor es oficial y sumamente generoso.

---

## Checklist de instalación

Antes de pasar al siguiente capítulo, asegúrate de poder marcar cada una de estas casillas con un **Sí**:

* [ ] Descargué el instalador directamente de `cursor.com`.
* [ ] Pude abrir la aplicación sin problemas en mi pantalla.
* [ ] Logro localizar a Cursor desde el buscador del menú de inicio de mi sistema operativo.
* [ ] No se generó ningún mensaje de error durante el proceso de instalación.

Si has completado todos los puntos, ¡felicidades! Tienes tu editor listo para la acción. En el próximo capítulo realizaremos la **configuración inicial de Cursor**, adaptando el entorno, los atajos de teclado y la Inteligencia Artificial para que trabajen a tu favor desde el primer día.