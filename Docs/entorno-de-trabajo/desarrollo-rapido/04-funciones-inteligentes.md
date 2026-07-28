# Desarrollo rápido de aplicaciones Flutter con IA desde la nube

# Capítulo 4 — Crear funciones inteligentes dentro de una aplicación Flutter con Gemini

## Objetivos

Al finalizar este capítulo el estudiante será capaz de:

* Comprender cómo integrar Inteligencia Artificial dentro de una aplicación Flutter.
* Conocer el uso de Gemini como una función propia de la aplicación.
* Crear características inteligentes utilizando IA.
* Diseñar prompts para funciones dentro de una app.
* Generar asistentes, recomendaciones y contenido dinámico.
* Comprender el flujo completo de una aplicación Flutter con Firebase + IA.

---

# 1. Introducción

En los capítulos anteriores construimos la base de nuestra aplicación:

```text
Flutter

↓

Firebase

↓

Authentication

↓

Firestore

↓

Storage
```

Ahora agregaremos una nueva capacidad:

```text
La aplicación podrá utilizar Inteligencia Artificial.
```

Hasta ahora Gemini nos ayudaba como desarrolladores.

Ejemplo:

```text
Desarrollador

↓

Gemini

↓

Código generado
```

Ahora cambiaremos el enfoque.

La aplicación será quien utilice la IA:

```text
Usuario

↓

Aplicación Flutter

↓

Firebase AI Logic

↓

Gemini

↓

Respuesta inteligente

↓

Usuario
```

---

# 2. Diferencia entre Gemini como asistente y Gemini dentro de una aplicación

Es importante entender esta diferencia.

## Gemini como herramienta de desarrollo

Ejemplo:

El programador pregunta:

```text
Crea una pantalla Flutter de login.
```

Gemini responde:

```text
Código Dart generado.
```

---

## Gemini dentro de una aplicación

Ejemplo:

Un usuario abre una app educativa y pregunta:

```text
Explícame la fotosíntesis.
```

La aplicación envía la pregunta a Gemini.

Gemini responde:

```text
La fotosíntesis es el proceso mediante el cual...
```

Aquí la IA forma parte del producto.

---

# 3. Arquitectura de una aplicación Flutter con IA

La arquitectura básica será:

```text
Usuario

↓

Flutter App

↓

Firebase AI Logic

↓

Modelo Gemini

↓

Respuesta generada

↓

Flutter muestra resultado
```

---

Firebase actúa como intermediario para:

* Gestionar conexión.
* Administrar seguridad.
* Controlar acceso.
* Integrar servicios.

---

# 4. Casos de uso reales de IA en aplicaciones móviles

La IA puede utilizarse para crear:

---

## 4.1 Asistente inteligente

Ejemplo:

Aplicación educativa:

Usuario:

```text
¿Cómo puedo mejorar en matemáticas?
```

IA:

```text
Puedes practicar operaciones básicas
durante 20 minutos al día...
```

---

## 4.2 Generación de contenido

Ejemplo:

Una aplicación puede crear:

* Preguntas.
* Ejercicios.
* Resúmenes.
* Explicaciones.

Prompt:

```text
Genera 5 preguntas de ciencias
para un estudiante de 10 años.
```

---

## 4.3 Recomendaciones personalizadas

Ejemplo:

Basándose en progreso:

```text
Usuario:

Terminó nivel básico.

↓

IA recomienda:

Curso intermedio.
```

---

## 4.4 Clasificación de información

Ejemplo:

Una aplicación recibe texto:

```text
"Me siento cansado después de estudiar"
```

La IA puede clasificar:

```text
Categoría:

Descanso recomendado
```

---

# 5. Preparar Firebase para IA

Antes de utilizar funciones inteligentes necesitamos tener:

```text
✓ Proyecto Firebase creado

✓ Aplicación Flutter conectada

✓ Firebase configurado

✓ Usuario autenticado
```

---

Ingresamos a:

```text
Firebase Console
```

Seleccionamos:

```text
Build

↓

AI
```

o las herramientas relacionadas con modelos generativos disponibles.

---

# 6. Crear un servicio de IA en Flutter

Una buena práctica es separar la lógica.

No debemos colocar llamadas de IA directamente dentro de una pantalla.

Ejemplo:

Estructura:

```text
lib

├── screens

├── widgets

├── models

├── services

│   └── ai_service.dart

└── main.dart
```

---

El archivo:

```text
ai_service.dart
```

será responsable de:

* Enviar preguntas.
* Recibir respuestas.
* Manejar errores.

---

# 7. Crear un asistente educativo utilizando IA

Ejemplo:

Queremos una pantalla:

```text
Tutor IA
```

El usuario escribe:

```text
Explícame los planetas.
```

La aplicación responde.

---

Primero pedimos ayuda a Gemini:

Prompt:

```text
Crea un servicio Flutter llamado AIService.

Debe:

- Comunicarse con Gemini.
- Recibir una pregunta.
- Enviar la solicitud.
- Retornar una respuesta.
- Manejar errores.
```

---

Gemini generará una estructura inicial.

---

# 8. Crear la interfaz del asistente

Ahora necesitamos una pantalla.

Prompt:

```text
Crea una pantalla Flutter de chatbot.

Debe incluir:

- Campo de texto.
- Botón enviar.
- Lista de mensajes.
- Diseño tipo conversación.
- Material 3.
```

---

Resultado esperado:

```text
ChatScreen

↓

Mensaje usuario

↓

Respuesta IA
```

---

# 9. Diseñar buenos prompts para la aplicación

La calidad de la respuesta depende del prompt enviado.

---

Ejemplo básico:

```text
Explica matemáticas.
```

Respuesta:

Muy general.

---

Ejemplo mejor:

```text
Explica matemáticas para un niño
de 10 años.

Utiliza ejemplos sencillos.

No uses palabras técnicas.
```

Respuesta:

Más adecuada.

---

# 10. Crear prompts dinámicos

Una aplicación puede modificar el prompt según el usuario.

Ejemplo:

Datos del usuario:

```text
Edad: 10 años

Nivel: básico

Tema: ciencias
```

La aplicación genera:

```text
Explica ciencias para un estudiante
de 10 años con nivel básico.
```

---

Esto permite experiencias personalizadas.

---

# 11. Crear un generador de preguntas educativas

Ejemplo:

La aplicación necesita crear ejercicios.

Prompt:

```text
Genera un cuestionario educativo.

Tema:

Matemáticas.

Nivel:

Primaria.

Cantidad:

5 preguntas.

Incluye respuestas.
```

---

La IA puede devolver:

```text
Pregunta 1

¿Cuánto es 5 + 5?

Respuesta:

10
```

---

# 12. Guardar respuestas generadas en Firestore

Podemos almacenar información generada.

Ejemplo:

Colección:

```text
ai_history
```

Documento:

```text
usuario_001
```

Campos:

```text
pregunta

respuesta

fecha

categoría
```

---

Arquitectura:

```text
Usuario pregunta

↓

Gemini responde

↓

Flutter muestra resultado

↓

Firestore guarda historial
```

---

# 13. Manejo de errores con IA

Una aplicación real debe controlar fallos.

Ejemplos:

## Sin internet

Mostrar:

```text
No se pudo conectar.
Intenta nuevamente.
```

---

## Error del modelo

Mostrar:

```text
La IA no pudo generar una respuesta.
```

---

## Respuesta vacía

Validar:

```text
Si respuesta == vacío

↓

Mostrar mensaje alternativo
```

---

# 14. Seguridad al usar Inteligencia Artificial

Nunca debemos confiar completamente en la entrada del usuario.

Ejemplo:

Usuario escribe:

```text
Ignora todas las instrucciones anteriores...
```

La aplicación debe validar.

---

Buenas prácticas:

* Limitar contenido.
* Validar entradas.
* Controlar costos.
* Proteger servicios.
* Revisar respuestas.

---

# 15. Mejorar una aplicación creada con IA

Gemini también ayuda después de construir.

Ejemplos:

## Optimización

Prompt:

```text
Analiza este código Flutter.

Busca:

- Errores.
- Código repetido.
- Mejoras de rendimiento.
```

---

## Diseño

Prompt:

```text
Mejora esta interfaz Flutter.

Mantén Material 3.

Hazla más accesible.
```

---

## Pruebas

Prompt:

```text
Genera pruebas unitarias
para este servicio Flutter.
```

---

# 16. Flujo completo de desarrollo con IA

El proceso final aprendido en esta parte es:

```text
Idea

↓

Gemini diseña solución

↓

Flutter crea interfaz

↓

Firebase guarda información

↓

Firebase AI Logic conecta Gemini

↓

Usuario utiliza función inteligente

↓

Firestore almacena resultados
```

---

# 17. Proyecto final de ejemplo

Al finalizar esta parte, el estudiante podría crear:

## Aplicación educativa inteligente

Funciones:

```text
✓ Registro de usuarios

✓ Perfil

✓ Cursos

✓ Progreso

✓ Chat con IA

✓ Generación de ejercicios

✓ Recomendaciones personalizadas

✓ Historial en Firebase
```

---

# 18. Resultado del capítulo

Después de este capítulo el estudiante comprende cómo crear aplicaciones que no solamente almacenan información, sino que también pueden:

* Responder preguntas.
* Generar contenido.
* Ayudar usuarios.
* Personalizar experiencias.

La aplicación deja de ser una aplicación tradicional y se convierte en una aplicación inteligente.

---

# Resumen final

En esta parte aprendimos:

```text
Capítulo 1

Preparar Firebase Studio y Gemini


Capítulo 2

Crear aplicaciones Flutter con IA


Capítulo 3

Conectar Flutter con Firebase


Capítulo 4

Agregar funciones inteligentes con Gemini
```

El flujo moderno de desarrollo queda:

```text
Idea

↓

Firebase Studio

↓

Gemini

↓

Flutter

↓

Firebase

↓

IA integrada

↓

Aplicación inteligente
```
