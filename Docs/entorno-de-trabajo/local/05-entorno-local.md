# PARTE I — ENTORNO DE DESARROLLO LOCAL

# Capítulo 5 — Git y control de versiones

---

# 5. Introducción

Hasta este momento el entorno de desarrollo ya dispone de los componentes necesarios para crear aplicaciones Flutter. Sin embargo, aún falta una herramienta indispensable en cualquier proyecto de software profesional: el **sistema de control de versiones**.

A medida que una aplicación crece, el código cambia constantemente. Se corrigen errores, se agregan funcionalidades y participan varios desarrolladores al mismo tiempo. Sin un mecanismo para controlar estos cambios, sería muy difícil mantener el proyecto organizado.

Para resolver este problema se utiliza **Git**, un sistema de control de versiones distribuido que registra la evolución del código fuente y permite recuperar versiones anteriores cuando sea necesario.

En este capítulo se estudiará cómo funciona Git, cuál es la diferencia entre Git y GitHub, cómo se organiza un repositorio y cuál será el flujo de trabajo utilizado durante este proyecto.

---

# 5.1 ¿Qué es un sistema de control de versiones?

Un sistema de control de versiones es una herramienta que registra todos los cambios realizados sobre un proyecto a lo largo del tiempo.

Gracias a este sistema es posible:

* recuperar versiones anteriores;
* conocer quién realizó un cambio;
* trabajar en equipo;
* comparar modificaciones;
* mantener un historial completo del proyecto.

Conceptualmente:

```text id="git5a01"
          Proyecto Flutter

                 │

                 ▼

          Sistema de versiones

                 │

      ┌──────────┼──────────┐

      ▼          ▼          ▼

 Versión 1   Versión 2   Versión 3
```

Cada cambio importante queda registrado sin reemplazar el historial anterior.

---

# 5.2 ¿Qué es Git?

Git es un sistema de control de versiones distribuido.

Su función consiste en registrar los cambios realizados sobre un proyecto y permitir que dichos cambios puedan administrarse de forma segura.

Git trabaja directamente sobre el código fuente y almacena el historial completo del proyecto.

Arquitectura:

```text id="git5a02"
Proyecto

     │

     ▼

Git

     │

     ▼

Historial

     │

     ▼

Versiones
```

Git funciona completamente en la computadora del desarrollador, incluso sin conexión a Internet.

---

# 5.3 Git y GitHub no son lo mismo

Es frecuente confundir ambos conceptos.

Aunque trabajan juntos, cumplen responsabilidades diferentes.

## Git

Es la herramienta que administra el historial del proyecto.

Funciona de manera local.

---

## GitHub

Es una plataforma que permite almacenar repositorios Git en la nube y compartirlos con otros desarrolladores.

Arquitectura:

```text id="git5a03"
Computadora

      │

      ▼

Git

      │

      ▼

Repositorio local

      │

      ▼

GitHub

      │

      ▼

Repositorio remoto
```

En resumen:

* Git administra las versiones.
* GitHub almacena y comparte el proyecto.

---

# 5.4 ¿Por qué utilizar Git en este proyecto?

Durante el desarrollo de una aplicación Flutter es habitual modificar el código cientos o miles de veces.

Git permite:

* conservar un historial de cambios;
* trabajar de forma colaborativa;
* recuperar versiones anteriores;
* sincronizar el trabajo con un repositorio remoto;
* evitar la pérdida de código.

Estas características hacen que Git sea una herramienta esencial para cualquier proyecto profesional.

---

# 5.5 Arquitectura del control de versiones

El flujo general utilizado durante el proyecto será el siguiente:

```text id="git5a04"
          Desarrollador

                 │

                 ▼

        Proyecto Flutter

                 │

                 ▼

                Git

                 │

                 ▼

      Repositorio Local

                 │

                 ▼

      Repositorio Remoto

              (GitHub)
```

Todo cambio comienza en el proyecto local y posteriormente se sincroniza con el repositorio remoto.

---

# 5.6 Instalación de Git

El proceso de instalación es sencillo.

```text id="git5a05"
Descargar Git

      │

      ▼

Instalar

      │

      ▼

Abrir terminal

      │

      ▼

Verificar versión
```

Una vez instalado, Git podrá utilizarse desde la terminal integrada del IDE o desde cualquier consola del sistema.

---

# 5.7 Instalación en Windows

Proceso recomendado:

1. Descargar el instalador oficial.
2. Ejecutar el asistente.
3. Mantener la configuración predeterminada.
4. Finalizar la instalación.

Después verificar:

```bash id="git5cmd01"
git --version
```

---

# 5.8 Instalación en Linux

En la mayoría de distribuciones Linux, Git puede instalarse mediante el gestor de paquetes del sistema.

Una vez completada la instalación se recomienda verificarla:

```bash id="git5cmd02"
git --version
```

Si Git responde con su versión instalada, la configuración es correcta.

---

# 5.9 Configuración inicial

Antes de utilizar Git por primera vez es necesario identificar al desarrollador.

Git utilizará esta información para registrar quién realizó cada cambio.

Configuración del nombre:

```bash id="git5cmd03"
git config --global user.name "Nombre Apellido"
```

Configuración del correo electrónico:

```bash id="git5cmd04"
git config --global user.email "correo@ejemplo.com"
```

Estos datos quedarán asociados a los futuros registros del historial del proyecto.

---

# 5.10 ¿Qué es un repositorio?

Un **repositorio** es el lugar donde Git almacena el proyecto junto con todo su historial.

Puede existir de dos formas:

* repositorio local;
* repositorio remoto.

Arquitectura:

```text id="git5a06"
Repositorio

│

├── Código fuente

├── Historial

├── Configuración Git

└── Versiones
```

Todo proyecto administrado por Git contiene un repositorio.

---

# 5.11 Repositorio local y remoto

Durante este proyecto se trabajará con ambos.

```text id="git5a07"
Repositorio Local

        │

        ▼

       Git

        │

        ▼

Repositorio Remoto

      (GitHub)
```

El repositorio local se encuentra en la computadora del desarrollador.

El remoto se almacena en GitHub para facilitar el trabajo colaborativo y el respaldo del proyecto.

---

# 5.12 Flujo de trabajo con Git

El flujo básico utilizado será:

```text id="git5a08"
Modificar código

       │

       ▼

Guardar cambios

       │

       ▼

Commit

       │

       ▼

Repositorio Local

       │

       ▼

Push

       │

       ▼

Repositorio Remoto
```

Este ciclo se repetirá durante todo el desarrollo del proyecto.

---

# 5.13 Comandos básicos

## Clonar un proyecto

Permite descargar un repositorio existente.

```bash id="git5cmd05"
git clone <URL-del-repositorio>
```

---

## Consultar el estado

Muestra los archivos modificados.

```bash id="git5cmd06"
git status
```

---

## Registrar cambios

Crea un nuevo registro en el historial.

```bash id="git5cmd07"
git commit -m "Descripción del cambio"
```

---

## Descargar cambios del repositorio remoto

```bash id="git5cmd08"
git pull
```

---

## Enviar cambios

```bash id="git5cmd09"
git push
```

---

# 5.14 ¿Qué ocurre durante un commit?

Cuando se ejecuta un commit, Git registra una nueva versión del proyecto.

Proceso:

```text id="git5a09"
Modificar archivos

        │

        ▼

Guardar cambios

        │

        ▼

Commit

        │

        ▼

Nueva versión

        │

        ▼

Historial actualizado
```

Cada commit representa un punto de recuperación del proyecto.

---

# 5.15 Ramas (Branches)

Una rama permite desarrollar nuevas funcionalidades sin modificar la versión principal del proyecto.

Conceptualmente:

```text id="git5a10"
main

 │

 ├────────► Funcionalidad A

 │

 └────────► Funcionalidad B
```

Esto permite trabajar en paralelo sin afectar el código estable.

En este proyecto, las ramas se utilizarán siguiendo las políticas definidas por el equipo de desarrollo.

---

# 5.16 Integración con Cursor y Visual Studio Code

Ambos IDE incorporan herramientas para trabajar con Git.

Desde su interfaz es posible:

* visualizar cambios;
* confirmar modificaciones;
* cambiar de rama;
* sincronizar el repositorio;
* resolver conflictos.

Arquitectura:

```text id="git5a11"
IDE

│

├── Editor

├── Git

├── Terminal

└── Proyecto Flutter
```

Aunque estas funciones pueden utilizarse gráficamente, es recomendable comprender también los comandos básicos de Git.

---

# 5.17 Buenas prácticas

Durante el desarrollo del proyecto se recomienda:

* realizar commits pequeños y frecuentes;
* utilizar mensajes descriptivos;
* sincronizar el repositorio antes de comenzar a trabajar;
* evitar modificar directamente la rama principal sin seguir el flujo definido por el equipo;
* mantener el repositorio organizado y actualizado.

Estas prácticas facilitan el trabajo colaborativo y reducen la posibilidad de conflictos.

---

# 5.18 Problemas frecuentes

## Git no es reconocido

Posibles causas:

* instalación incompleta;
* terminal sin reiniciar;
* variable `PATH` incorrecta.

---

## No es posible enviar cambios

Generalmente ocurre por:

* falta de autenticación;
* cambios pendientes de otros desarrolladores;
* conflictos entre ramas.

---

## Conflictos de fusión

Los conflictos aparecen cuando dos cambios afectan el mismo fragmento de código.

En estos casos es necesario revisar manualmente el contenido antes de continuar.

---

# 5.19 Arquitectura del entorno después de configurar Git

Con Git instalado, el entorno de desarrollo queda preparado para trabajar de forma profesional.

```text id="git5a12"
                 Desarrollador

                       │

                       ▼

          Cursor / Visual Studio Code

                       │

                       ▼

                Proyecto Flutter

                       │

                       ▼

                      Git

                       │

          ┌────────────┴────────────┐

          ▼                         ▼

 Repositorio Local        Repositorio Remoto

                                 (GitHub)
```

A partir de este punto, todo cambio realizado en el proyecto podrá registrarse, recuperarse y compartirse con el resto del equipo.

---

# Conclusión del capítulo

Git constituye una herramienta esencial para el desarrollo profesional de software. Más que un simple mecanismo de respaldo, permite gestionar la evolución del proyecto, colaborar con otros desarrolladores y mantener un historial completo de todos los cambios realizados.

En este capítulo se explicó qué es un sistema de control de versiones, la diferencia entre Git y GitHub, cómo se organiza un repositorio, el flujo básico de trabajo y los comandos fundamentales que se utilizarán durante el desarrollo del proyecto.

Con el control de versiones configurado, el siguiente paso será estudiar la **anatomía de un proyecto Flutter**, comprendiendo la función de cada carpeta y archivo generado automáticamente al crear una nueva aplicación. Este conocimiento permitirá navegar y organizar el código de forma eficiente desde el inicio del desarrollo.
