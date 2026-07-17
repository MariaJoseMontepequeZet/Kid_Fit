# README 05 - Conectando Git con GitHub mediante SSH (El Método de los Profesionales)

> **Objetivo del capítulo**
> En este capítulo aprenderás a conectar tu computadora con tu cuenta de GitHub utilizando **SSH (Secure Shell)**. Este es el estándar de seguridad de la industria. Al finalizar este capítulo, tu entorno de Cursor estará configurado al 100% para clonar, subir y descargar código de manera transparente, segura y automática, sin que se te vuelvan a solicitar contraseñas o tokens de acceso en la terminal.

---

## 🔑 ¿Por qué usar SSH si ya vimos el inicio de sesión visual?

En el capítulo anterior aprendimos a iniciar sesión de forma visual en GitHub desde Cursor. Ese método es fantástico para empezar rápidamente, pero tiene limitaciones: las sesiones web pueden expirar, no siempre funcionan bien en entornos de terminal pura y a veces fallan si manejas múltiples cuentas.

**SSH es el "siguiente nivel" por varias razones:**

* **Es permanente:** Una vez configurado, no expira jamás (a menos que tú decidas borrar la llave).
* **Seguridad Criptográfica:** No viajan contraseñas por la red; la autenticación se realiza mediante un sistema de llaves asimétricas.
* **Automatización:** Facilita el uso de scripts, terminales externas y automatizaciones en Cursor sin interrupciones visuales.

---

## 🛡️ Entendiendo el juego: Llave Pública vs. Llave Privada

El protocolo SSH funciona mediante un sistema de **criptografía asimétrica**. Al generar tus credenciales, tu computadora creará un par de archivos (un "llavero" digital):

```
                       [ TU COMPUTADORA ]
                        /              \
                       /                \
        Llave Privada (id_ed25519)     Llave Pública (id_ed25519.pub)
        [ NUNCA SE COMPARTE ]          [ SE SUBE A GITHUB ]
               │                                │
        Es tu firma secreta.             Es el candado que
        La guardas bajo llave.           GitHub aprenderá a abrir.

```

> ⚠️ **REGLA DE ORO DE SEGURIDAD:**
> Tu **llave privada** (`id_ed25519`) es el equivalente físico a la llave de tu casa o la contraseña de tu cuenta bancaria. **Jamás** la subas a un repositorio, la envíes por chat o la compartas. La **llave pública** (`id_ed25519.pub`) es un "candado" que puedes repartir por todo internet sin ningún riesgo.

---

## Paso 1: Verificar si ya tienes llaves SSH creadas

Antes de crear una llave desde cero, es una buena práctica revisar si tu computadora ya tiene alguna guardada en el directorio por defecto (`.ssh`).

* **En Windows (PowerShell):**
```powershell
ls ~\.ssh

```


* **En Linux (Terminal / Ubuntu o Mint):**
```bash
ls -la ~/.ssh

```



### ¿Cómo interpretar el resultado?

* **Si la terminal te da un error o la carpeta está vacía:** Perfecto, no tienes llaves. Continúa al Paso 2.
* **Si ves archivos llamados `id_ed25519` y `id_ed25519.pub`:** Ya tienes una llave generada con el algoritmo moderno. Puedes saltar directamente al **Paso 3**.
* **Si ves archivos con el nombre `id_rsa`:** Es una llave antigua. Aunque funciona, te recomiendo seguir el Paso 2 para generar una llave moderna más segura y ligera.

---

## Paso 2: Generar una nueva llave SSH (Algoritmo Ed25519)

GitHub y la comunidad de seguridad recomiendan actualmente el algoritmo **Ed25519** debido a que es más seguro, rápido y genera llaves mucho más compactas que el antiguo RSA.

Abre tu terminal (o la terminal integrada de Cursor) y ejecuta el siguiente comando reemplazando el correo de ejemplo por el correo con el que registraste tu cuenta de GitHub:

```bash
ssh-keygen -t ed25519 -C "tu-correo@ejemplo.com"

```

### ¿Qué significa cada parte de este comando?

* `ssh-keygen`: La herramienta del sistema que genera el par de llaves.
* `-t ed25519`: Indica que utilizaremos el algoritmo de cifrado moderno *Ed25519*.
* `-C "tu-correo@ejemplo.com"`: Añade una etiqueta o comentario (normalmente tu correo) al final de la llave para que sepas a quién le pertenece cuando la veas en GitHub.

### Durante la generación, la terminal te hará dos preguntas:

1. **`Enter file in which to save the key...`** (¿Dónde deseas guardar el archivo?)
* **Qué hacer:** Simplemente presiona **`Enter`**. Esto guardará la llave en la ruta por defecto (`~/.ssh/id_ed25519`) que es donde todos los programas (incluyendo Cursor) irán a buscarla de forma automática.


2. **`Enter passphrase (empty for no passphrase)...`** (¿Deseas una contraseña de seguridad?)
* **Opción A (Recomendada para uso personal/estudio):** Presiona **`Enter`** dos veces para dejarla vacía. Esto significa que no tendrás que escribir una contraseña adicional cada vez que uses Git.
* **Opción B (Recomendada para entornos profesionales/computadoras compartidas):** Escribe una contraseña segura y presiona Enter. Esto añade una capa extra de seguridad: si alguien roba tu archivo físico de llave privada, no podrá usarlo sin conocer tu contraseña.



Al finalizar, verás un diseño artístico en caracteres ASCII en tu terminal. ¡Tu par de llaves ha sido creado!

---

## Paso 3: Activar el Agente SSH (El talón de Aquiles de Windows)

El **SSH Agent** es un programa que corre en segundo plano y se encarga de recordar tus llaves privadas para que no tengas que lidiar con ellas manualmente. Configurarlo correctamente es vital, especialmente en Windows, donde suele venir desactivado por defecto.

### 🐧 En Linux (Ubuntu / Mint)

Abre tu terminal y ejecuta:

```bash
# Iniciar el agente en segundo plano
eval "$(ssh-agent -s)"

# Registrar tu nueva llave privada en el agente
ssh-add ~/.ssh/id_ed25519

```

### 💻 En Windows (PowerShell)

En Windows, el servicio del agente suele estar deshabilitado. Necesitamos activarlo y configurarlo para que inicie automáticamente cada vez que enciendas tu PC.

> 💡 **Nota:** Para ejecutar estos comandos de forma exitosa en Windows, debes abrir tu **PowerShell como Administrador** (Haz clic derecho sobre el icono de PowerShell y selecciona "Ejecutar como administrador").

```powershell
# 1. Configurar el servicio para que inicie de forma automática
Get-Service ssh-agent | Set-Service -StartupType Automatic

# 2. Iniciar el servicio en este momento
Start-Service ssh-agent

# 3. Registrar tu llave privada en el agente
ssh-add $env:USERPROFILE\.ssh\id_ed25519

```

Si todo sale bien, la consola te devolverá un mensaje confirmando: *Identity added...*

---

## Paso 4: Copiar tu llave pública al portapapeles

Ahora necesitamos extraer el contenido de nuestra **llave pública** (`.pub`) para enseñársela a GitHub. Utiliza el comando correspondiente a tu sistema operativo para copiar el texto de manera limpia, sin añadir espacios ni saltos de línea invisibles:

* **En Windows (PowerShell):**
```powershell
Get-Content ~\.ssh\id_ed25519.pub | clip

```


*(Este comando copia el contenido directamente a tu portapapeles. No verás texto en pantalla, solo ve al Paso 5 y pega).*
* **En Linux (Terminal):**
```bash
cat ~/.ssh/id_ed25519.pub

```


*(Este comando imprimirá un texto largo que empieza por `ssh-ed25519 ...`. Selecciónalo por completo con tu ratón y cópialo manualmente).*

---

## Paso 5: Agregar la llave pública a tu cuenta de GitHub

1. Abre tu navegador web e ingresa a [GitHub](https://github.com).
2. Haz clic en tu **foto de perfil** en la esquina superior derecha y selecciona **Settings** (Configuración).
3. En el menú lateral izquierdo, busca y haz clic en **SSH and GPG keys**.
4. Haz clic en el botón verde **New SSH key** (Nueva llave SSH).
5. Completa el formulario con los siguientes datos:
* **Title (Título):** Escribe un nombre que te recuerde a qué computadora pertenece esta llave. Ejemplos: `Laptop Lenovo Trabajo`, `PC Escritorio Casa`, `Ubuntu Partición Secundaria`.
* **Key type:** Déjalo en **Authentication Key** (Llave de Autenticación).
* **Key (Llave):** Pega aquí todo el texto que copiaste en el Paso 4. Asegúrate de que empiece por `ssh-ed25519` y termine con tu correo electrónico.


6. Haz clic en **Add SSH key**. (Es posible que GitHub te pida ingresar tu contraseña o usar tu autenticador móvil por seguridad).

---

## Paso 6: La prueba de fuego 🚀

Vamos a verificar que la conexión se realice de manera exitosa. Abre cualquier terminal y ejecuta el siguiente comando:

```bash
ssh -T git@github.com

```

### ¿Qué pasará la primera vez que ejecutes esto?

La terminal se detendrá y te mostrará una advertencia similar a esta:

```text
The authenticity of host 'github.com (140.82.112.4)' can't be established.
ED25519 key fingerprint is SHA256:+DiY3w9n98SyCDHg...
Are you sure you want to continue connecting (yes/no/[fingerprint])?

```

* **¿Qué significa?** Tu computadora te está advirtiendo que es la primera vez que se comunica con los servidores de GitHub y te pregunta si confías en ellos.
* **Qué hacer:** Escribe la palabra completa **`yes`** y presiona **`Enter`**. (No te preocupes, esto solo ocurre la primerísima vez).

### El mensaje de éxito esperado:

Si todo se configuró correctamente, verás este mensaje en tu terminal:

> **`Hi [TuUsuario]! You've successfully authenticated, but GitHub does not provide shell access.`**

> ⚠️ **¡No te asustes!**
> Muchos principiantes piensan que la frase *"but GitHub does not provide shell access"* (pero GitHub no provee acceso a consola) es un mensaje de error. **No lo es.** Es una advertencia informativa de seguridad que te dice que tu conexión es exitosa, pero que no puedes usar los servidores de GitHub para correr comandos de Linux de forma remota. Si ves tu nombre de usuario de GitHub ahí, ¡tu configuración ha sido un éxito total!

---

## 🛠️ Cómo migrar tus proyectos existentes de HTTPS a SSH

Si ya tenías proyectos clonados antes de hacer esta configuración, es muy probable que sigan usando el protocolo HTTPS. No tienes que volver a descargarlos de internet. Puedes actualizarlos para que usen SSH con este sencillo truco en segundos:

1. Ve a tu repositorio en GitHub mediante tu navegador.
2. Haz clic en el botón verde **Code** y copia la URL bajo la pestaña **SSH** (Debe tener un formato como `git@github.com:usuario/repositorio.git`).
3. Abre la terminal en la carpeta de tu proyecto local en Cursor y cambia la URL remota con este comando:
```bash
git remote set-url origin git@github.com:usuario/repositorio.git

```


4. Para verificar que el cambio se aplicó correctamente ejecuta:
```bash
git remote -v

```


*(Ahora deberías ver que las direcciones de descarga (fetch) y subida (push) inician con `git@github.com`).*

---

## Checklist final de Cursores Completado

¡Felicidades! Has llegado al final de la ruta de instalación e inicialización de tu entorno de desarrollo. Verifica que tu checklist del capítulo esté completo:

* [ ] Comprendo la diferencia conceptual entre una llave pública (`.pub`) y una privada.
* [ ] Generé mi par de llaves usando el algoritmo moderno `ed25519`.
* [ ] Activé correctamente el servicio `ssh-agent` en mi sistema operativo (esencial en Windows).
* [ ] Vinculé mi llave pública en la sección "SSH and GPG keys" de mi cuenta de GitHub.
* [ ] Ejecuté `ssh -T git@github.com` y obtuve el mensaje de bienvenida oficial de GitHub.
* [ ] Sé cómo cambiar un proyecto de HTTPS a SSH si es necesario.