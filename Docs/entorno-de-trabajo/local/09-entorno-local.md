# PARTE I — ENTORNO DE DESARROLLO LOCAL

# Capítulo 9 — Compilación y depuración

---

# 9. Introducción

Después de crear y ejecutar el primer proyecto Flutter, el siguiente paso consiste en comprender cómo Flutter transforma el código fuente en una aplicación que puede ejecutarse en un dispositivo Android.

Durante el desarrollo no basta con escribir código. Es necesario compilar la aplicación, detectar errores, instalar nuevas dependencias, limpiar archivos temporales y utilizar herramientas que permitan analizar el comportamiento del proyecto.

En este capítulo se estudiarán los comandos más utilizados de Flutter para el trabajo diario, así como el proceso de compilación y las principales herramientas de depuración disponibles en el SDK.

Al finalizar este capítulo el estudiante comprenderá el flujo completo desde la escritura del código hasta la ejecución de la aplicación en un dispositivo Android.

---

# 9.1 ¿Qué significa compilar una aplicación?

El código escrito por un desarrollador no puede ejecutarse directamente en un teléfono Android.

Antes debe pasar por un proceso denominado **compilación**, en el que Flutter y el Android SDK transforman el código fuente en una aplicación ejecutable.

Proceso general:

```text
Código Dart

      │

      ▼

Flutter SDK

      │

      ▼

Compilación

      │

      ▼

Android SDK

      │

      ▼

APK de depuración

      │

      ▼

Dispositivo Android
```

Este proceso ocurre automáticamente cuando se ejecuta `flutter run`.

---

# 9.2 Flujo completo de compilación

Internamente Flutter realiza varias tareas antes de iniciar la aplicación.

```text
flutter run

      │

      ▼

Analizar proyecto

      │

      ▼

Resolver dependencias

      │

      ▼

Compilar código Dart

      │

      ▼

Generar APK

      │

      ▼

Instalar aplicación

      │

      ▼

Iniciar depuración
```

Aunque muchas de estas operaciones son invisibles para el desarrollador, comprenderlas facilita el diagnóstico de errores.

---

# 9.3 El comando `flutter run`

El comando más utilizado durante el desarrollo es:

```bash
flutter run
```

Este comando:

* compila la aplicación;
* instala el APK en el dispositivo;
* inicia la aplicación;
* establece una sesión de depuración;
* habilita Hot Reload y Hot Restart.

Será el comando que más se utilizará durante el desarrollo del proyecto.

---

# 9.4 El comando `flutter devices`

Antes de ejecutar una aplicación es recomendable verificar que Flutter reconoce el dispositivo.

```bash
flutter devices
```

Ejemplo:

```text
Found 1 connected device

Android Device
```

Si el dispositivo no aparece en la lista, Flutter no podrá instalar la aplicación.

---

# 9.5 El comando `flutter doctor`

Uno de los comandos más importantes del SDK es:

```bash
flutter doctor
```

Su función consiste en analizar el entorno de desarrollo.

Comprueba automáticamente:

* Flutter SDK;
* Dart SDK;
* Android SDK;
* Git;
* dispositivos conectados;
* licencias.

Arquitectura:

```text
flutter doctor

      │

      ▼

Analizar entorno

      │

      ├── Flutter

      ├── Android

      ├── Git

      ├── Dispositivos

      └── Licencias
```

Es recomendable ejecutarlo siempre que aparezcan problemas relacionados con la configuración del entorno.

---

# 9.6 El comando `flutter analyze`

Flutter incorpora un analizador estático que revisa el código antes de ejecutarlo.

```bash
flutter analyze
```

Este comando detecta:

* errores de sintaxis;
* variables sin utilizar;
* problemas de estilo;
* advertencias del compilador;
* posibles errores lógicos.

Proceso:

```text
Código Dart

      │

      ▼

flutter analyze

      │

      ▼

Informe de errores
```

Resolver estas advertencias mejora la calidad del código y reduce problemas durante la ejecución.

---

# 9.7 El comando `flutter pub get`

Las aplicaciones Flutter utilizan paquetes externos para incorporar nuevas funcionalidades.

Cada vez que se modifica el archivo `pubspec.yaml` es necesario ejecutar:

```bash
flutter pub get
```

Proceso:

```text
pubspec.yaml

      │

      ▼

Leer dependencias

      │

      ▼

Descargar paquetes

      │

      ▼

Actualizar proyecto
```

Este comando sincroniza el proyecto con las dependencias declaradas.

---

# 9.8 El comando `flutter clean`

Durante el desarrollo pueden generarse archivos temporales que ocasionen problemas de compilación.

Flutter permite eliminarlos mediante:

```bash
flutter clean
```

Proceso:

```text
Proyecto Flutter

      │

      ▼

flutter clean

      │

      ▼

Eliminar build

Eliminar cache temporal

      │

      ▼

Proyecto limpio
```

Este comando no elimina el código fuente del proyecto.

---

# 9.9 El comando `flutter pub upgrade`

Cuando se desea actualizar las dependencias del proyecto se utiliza:

```bash
flutter pub upgrade
```

Este comando busca versiones más recientes compatibles con las restricciones definidas en `pubspec.yaml`.

Debe utilizarse con precaución, ya que una actualización puede introducir cambios incompatibles.

---

# 9.10 Hot Reload

Una de las principales ventajas de Flutter es la velocidad con la que permite visualizar cambios.

Hot Reload actualiza únicamente las partes modificadas de la aplicación.

Proceso:

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

Actualizar interfaz
```

Esto permite desarrollar aplicaciones de manera muy ágil.

---

# 9.11 Hot Restart

Cuando los cambios afectan al estado de la aplicación, Hot Reload puede no ser suficiente.

En ese caso se utiliza **Hot Restart**.

```text
Modificar lógica

       │

       ▼

Hot Restart

       │

       ▼

main()

       │

       ▼

Aplicación reiniciada
```

A diferencia de Hot Reload, este proceso reinicia completamente la ejecución.

---

# 9.12 Diferencias entre Hot Reload y Hot Restart

| Característica         | Hot Reload | Hot Restart |
| ---------------------- | ---------- | ----------- |
| Reinicia la aplicación | No         | Sí          |
| Conserva el estado     | Sí         | No          |
| Actualiza la interfaz  | Sí         | Sí          |
| Velocidad              | Muy alta   | Alta        |

Durante el desarrollo se utilizará Hot Reload siempre que sea posible y Hot Restart cuando los cambios requieran reinicializar la aplicación.

---

# 9.13 Depuración de aplicaciones

La depuración consiste en ejecutar una aplicación mientras se analiza su comportamiento.

Durante una sesión de depuración es posible:

* inspeccionar variables;
* seguir el flujo del programa;
* identificar errores;
* revisar mensajes de la consola;
* comprobar excepciones.

Arquitectura:

```text
Aplicación

      │

      ▼

Flutter Debugger

      │

      ▼

IDE

      │

      ▼

Desarrollador
```

---

# 9.14 Breakpoints

Un **breakpoint** es un punto de interrupción que detiene temporalmente la ejecución de la aplicación.

Cuando la ejecución se detiene es posible:

* inspeccionar variables;
* revisar el estado de la aplicación;
* continuar paso a paso.

Proceso:

```text
Aplicación

      │

      ▼

Breakpoint

      │

      ▼

Pausa

      │

      ▼

Analizar variables
```

Los breakpoints son una de las herramientas más importantes para localizar errores.

---

# 9.15 Consola de depuración

Mientras la aplicación está en ejecución, Flutter muestra información en la consola.

En ella pueden observarse:

* mensajes informativos;
* errores;
* excepciones;
* advertencias;
* resultados de instrucciones `print()` y `debugPrint()`.

La consola constituye una fuente fundamental de información durante el desarrollo.

---

# 9.16 Errores de compilación y errores de ejecución

Es importante distinguir ambos tipos de errores.

## Errores de compilación

Impiden generar la aplicación.

Ejemplos:

* errores de sintaxis;
* dependencias inexistentes;
* configuración incorrecta.

---

## Errores de ejecución

Aparecen mientras la aplicación ya está funcionando.

Ejemplos:

* excepciones;
* acceso a datos inexistentes;
* errores lógicos.

Comprender esta diferencia facilita el diagnóstico y la resolución de problemas.

---

# 9.17 Problemas frecuentes

## Flutter no compila el proyecto

Posibles causas:

* errores en el código;
* dependencias faltantes;
* Android SDK incompleto.

---

## Las dependencias no se descargan

Ejecutar:

```bash
flutter pub get
```

y comprobar la conexión a Internet.

---

## Hot Reload no refleja los cambios

Algunas modificaciones requieren Hot Restart o incluso volver a ejecutar la aplicación.

---

## El proyecto presenta errores después de actualizar dependencias

Ejecutar:

```bash
flutter clean
flutter pub get
```

y volver a compilar la aplicación.

---

## Flutter Doctor informa errores

Revisar cuidadosamente el informe generado por:

```bash
flutter doctor
```

y resolver cada advertencia antes de continuar.

---

# 9.18 Buenas prácticas

Durante el desarrollo diario se recomienda:

* ejecutar `flutter doctor` cuando aparezcan problemas de configuración;
* utilizar `flutter analyze` antes de compartir cambios;
* mantener actualizadas las dependencias únicamente cuando sea necesario;
* preferir Hot Reload para cambios en la interfaz;
* utilizar Hot Restart cuando se modifique la inicialización de la aplicación;
* mantener la consola visible para detectar errores de forma temprana.

---

# 9.19 Flujo completo del desarrollo Flutter

El ciclo habitual de trabajo durante el proyecto será el siguiente:

```text
Modificar código

        │

        ▼

flutter analyze

        │

        ▼

flutter run

        │

        ▼

Aplicación instalada

        │

        ▼

Hot Reload

        │

        ▼

Continuar desarrollando

        │

        ▼

Commit en Git
```

Este flujo resume el trabajo diario de un desarrollador Flutter.

---

# Conclusión del capítulo

En este capítulo se explicó el proceso de compilación de una aplicación Flutter y las herramientas de depuración que forman parte del SDK. Se estudiaron los comandos más utilizados durante el desarrollo, como `flutter run`, `flutter doctor`, `flutter analyze`, `flutter pub get` y `flutter clean`, además de las diferencias entre Hot Reload y Hot Restart.

Con este conocimiento, el estudiante dispone de un entorno local completamente funcional y comprende el ciclo de trabajo necesario para desarrollar, ejecutar, depurar y mantener aplicaciones Flutter. La siguiente parte de la documentación se centrará en el desarrollo en la nube, comenzando con los conceptos fundamentales de la arquitectura cloud y la integración de Flutter con Firebase.
