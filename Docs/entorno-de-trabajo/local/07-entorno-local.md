# PARTE I — ENTORNO DE DESARROLLO LOCAL

# Capítulo 7 — Preparación del dispositivo Android

---

# 7. Introducción

Hasta este punto ya se ha preparado el entorno de desarrollo en la computadora. Se instalaron el Flutter SDK, el Android SDK, el IDE y Git, además de conocer la estructura de un proyecto Flutter.

El siguiente paso consiste en preparar el **dispositivo Android** donde se ejecutarán las aplicaciones durante el desarrollo.

A diferencia de otros cursos, **en este proyecto no se utilizarán emuladores**. Todas las pruebas se realizarán sobre un teléfono Android físico mediante **depuración USB**.

Trabajar directamente sobre un dispositivo físico presenta varias ventajas:

* menor consumo de memoria RAM;
* mayor rendimiento durante la depuración;
* comportamiento idéntico al de un usuario final;
* acceso a sensores reales del dispositivo;
* reducción del tiempo de configuración del entorno.

Al finalizar este capítulo el teléfono estará preparado para comunicarse con Flutter y ejecutar aplicaciones en modo de desarrollo.

---

# 7.1 ¿Por qué utilizar un dispositivo físico?

Flutter permite ejecutar aplicaciones mediante:

* emuladores Android;
* dispositivos físicos.

En este proyecto se utilizará únicamente la segunda opción.

Arquitectura:

```text
             Proyecto Flutter

                    │

                    ▼

               Flutter SDK

                    │

                    ▼

                   ADB

                    │

                    ▼

          Dispositivo Android

                    │

                    ▼

          Aplicación en ejecución
```

Esta arquitectura simplifica el entorno de desarrollo y evita los problemas habituales asociados a los emuladores.

---

# 7.2 Ventajas frente a un emulador

Utilizar un teléfono físico aporta varios beneficios durante el aprendizaje.

| Dispositivo físico        | Emulador                   |
| ------------------------- | -------------------------- |
| Menor consumo de recursos | Alto consumo de RAM y CPU  |
| Rendimiento real          | Rendimiento simulado       |
| Sensores reales           | Sensores virtuales         |
| Configuración sencilla    | Configuración más compleja |
| Menor tiempo de inicio    | Inicio más lento           |

Para equipos con recursos limitados, el uso de un dispositivo físico suele ofrecer una mejor experiencia.

---

# 7.3 Requisitos del dispositivo

Antes de comenzar, el teléfono debe cumplir algunos requisitos mínimos.

Se recomienda disponer de:

* Android 8.0 o superior;
* batería suficiente;
* cable USB para transferencia de datos (no solo carga);
* espacio libre para instalar aplicaciones;
* acceso a las opciones de desarrollador.

---

# 7.4 ¿Qué es la depuración USB?

La **depuración USB** es una función de Android que permite que herramientas de desarrollo, como Flutter, se comuniquen con el dispositivo.

Gracias a ella es posible:

* instalar aplicaciones;
* ejecutar aplicaciones en modo desarrollo;
* depurar errores;
* visualizar registros del sistema;
* utilizar Hot Reload y Hot Restart.

Sin esta opción activada, Flutter no podrá instalar ni ejecutar la aplicación en el teléfono.

---

# 7.5 ¿Cómo funciona la comunicación?

Cuando se ejecuta una aplicación Flutter ocurre el siguiente proceso:

```text
flutter run

      │

      ▼

Flutter SDK

      │

      ▼

Android SDK

      │

      ▼

ADB

      │

      ▼

Cable USB

      │

      ▼

Teléfono Android

      │

      ▼

Aplicación Flutter
```

Cada componente participa en la instalación y ejecución de la aplicación.

---

# 7.6 Activar las opciones de desarrollador

Por motivos de seguridad, Android mantiene ocultas las herramientas para desarrolladores.

Para habilitarlas:

1. Abrir **Ajustes**.
2. Entrar en **Información del teléfono** o **Acerca del dispositivo**.
3. Buscar el apartado **Número de compilación**.
4. Pulsar varias veces sobre dicho apartado hasta que Android indique que las opciones de desarrollador han sido habilitadas.

El nombre de los menús puede variar ligeramente según el fabricante del dispositivo.

---

# 7.7 Activar la depuración USB

Una vez disponibles las opciones de desarrollador:

1. Abrir **Ajustes**.
2. Acceder a **Opciones de desarrollador**.
3. Buscar **Depuración USB**.
4. Activarla.
5. Confirmar el mensaje de seguridad mostrado por Android.

A partir de ese momento el dispositivo estará preparado para aceptar conexiones de desarrollo.

---

# 7.8 Autorizar la computadora

La primera vez que se conecta el teléfono mediante USB aparecerá un mensaje solicitando autorización.

```text
¿Permitir depuración USB?

[Cancelar]

[Aceptar]
```

Es recomendable marcar la opción para recordar la autorización si se trata de un equipo personal.

Una vez aceptada, el dispositivo podrá comunicarse con ADB.

---

# 7.9 Verificar la conexión

Con el dispositivo conectado, Flutter puede comprobar si es reconocido correctamente mediante:

```bash
flutter devices
```

Si la configuración es correcta, el comando mostrará el nombre del dispositivo y su identificador.

Ejemplo conceptual:

```text
Found 1 connected device

Android Device
```

Esto confirma que Flutter puede utilizar el teléfono para ejecutar aplicaciones.

---

# 7.10 Verificación mediante ADB

También es posible comprobar la conexión directamente con ADB.

```bash
adb devices
```

Resultado esperado:

```text
List of devices attached

XXXXXXXXXXXX    device
```

Si el estado es **device**, la comunicación es correcta.

---

# 7.11 Estados de un dispositivo

ADB puede mostrar diferentes estados.

| Estado           | Significado                                  |
| ---------------- | -------------------------------------------- |
| `device`         | El dispositivo está listo para usarse        |
| `unauthorized`   | Falta aceptar la autorización en el teléfono |
| `offline`        | Existe un problema de comunicación           |
| Sin dispositivos | No se detecta ningún teléfono                |

Conocer estos estados facilita el diagnóstico de problemas.

---

# 7.12 ¿Qué ocurre cuando ejecutamos `flutter run`?

Una vez detectado el dispositivo, el comando `flutter run` realiza automáticamente varias acciones.

```text
flutter run

      │

      ▼

Compilar aplicación

      │

      ▼

Generar APK de depuración

      │

      ▼

ADB instala APK

      │

      ▼

Android inicia aplicación

      │

      ▼

Flutter conecta Hot Reload
```

Todo este proceso se realiza automáticamente.

---

# 7.13 Hot Reload y Hot Restart

Durante el desarrollo se utilizarán dos funciones fundamentales.

## Hot Reload

Actualiza la interfaz sin reiniciar completamente la aplicación.

Permite visualizar cambios casi de forma inmediata.

---

## Hot Restart

Reinicia la aplicación desde el método `main()`.

Se utiliza cuando los cambios requieren reinicializar el estado de la aplicación.

---

Arquitectura:

```text
Modificar código

        │

        ▼

Guardar archivo

        │

        ▼

Hot Reload

        │

        ▼

Aplicación actualizada
```

---

# 7.14 Desconectar correctamente el dispositivo

Antes de desconectar el teléfono se recomienda:

* detener la ejecución de la aplicación;
* cerrar la sesión de depuración;
* desconectar el cable USB de forma segura.

Esto evita interrupciones durante la compilación o la transferencia de datos.

---

# 7.15 Problemas frecuentes

## Flutter no detecta el teléfono

Posibles causas:

* depuración USB desactivada;
* cable USB solo para carga;
* conexión USB defectuosa;
* autorización pendiente.

---

## El dispositivo aparece como `unauthorized`

Aceptar la autorización mostrada en el teléfono y volver a ejecutar:

```bash
adb devices
```

---

## El dispositivo aparece como `offline`

Generalmente basta con:

* desconectar el cable;
* volver a conectarlo;
* reiniciar ADB;
* aceptar nuevamente la autorización.

---

## Windows no reconoce el teléfono

En algunos fabricantes es necesario instalar los controladores USB oficiales para que el sistema operativo detecte correctamente el dispositivo.

---

## Linux no detecta el dispositivo

Algunas distribuciones Linux requieren configurar reglas **udev** para permitir que ADB acceda al teléfono sin privilegios elevados.

Estas reglas dependen del fabricante del dispositivo y pueden consultarse en la documentación oficial de Android.

---

# 7.16 Buenas prácticas

Para mantener un entorno estable se recomienda:

* utilizar un cable USB de buena calidad y con soporte para transferencia de datos;
* mantener activada la depuración USB únicamente durante el desarrollo;
* autorizar únicamente computadoras de confianza;
* verificar la conexión con `flutter devices` antes de comenzar a programar;
* mantener cargada la batería del dispositivo durante sesiones largas de desarrollo.

---

# 7.17 Arquitectura completa del entorno local

Después de preparar el dispositivo Android, el entorno de desarrollo queda completamente operativo.

```text
                 Desarrollador

                       │

                       ▼

        Cursor / Visual Studio Code

                       │

                       ▼

                 Flutter SDK

                       │

                       ▼

                 Android SDK

                       │

                       ▼

                      ADB

                       │

                       ▼

                 Cable USB

                       │

                       ▼

             Dispositivo Android

                       │

                       ▼

             Aplicación Flutter
```

Con esta arquitectura ya es posible desarrollar, ejecutar y depurar aplicaciones Flutter directamente sobre un dispositivo Android físico.

---

# Conclusión del capítulo

En este capítulo se preparó el dispositivo Android para formar parte del entorno de desarrollo local. Se explicó el funcionamiento de la depuración USB, el papel de ADB en la comunicación entre Flutter y el teléfono, el proceso de autorización del dispositivo y las herramientas para verificar que la conexión funciona correctamente.

A partir de este punto, el entorno local está completamente preparado para comenzar a desarrollar aplicaciones Flutter. En el siguiente capítulo se creará el primer proyecto, se analizará la estructura generada por Flutter y se ejecutará la primera aplicación sobre el dispositivo Android configurado en este capítulo.
