# Qué es una spec

> Lectura de 15 minutos. Léela antes de abrir Claude. Si llegas a los prompts sin entender qué es una spec, vas a generar texto que parece spec pero no lo es.

---

## La definición práctica

Una spec es un documento que describe **qué se va a construir** sin describir **cómo se va a construir**.

Esa frase parece obvia. No lo es. La mayoría de los specs que vas a escribir las primeras 5 veces son una de estas dos cosas:

1. **Una lista de features sin criterios.** ("La app tiene login, dashboard, perfil.") No es spec. Es índice.
2. **Un mini diseño técnico.** ("Vamos a usar JWT, una tabla `users` con campos email y password_hash...") Tampoco es spec. Eso es arquitectura.

Una spec real responde 4 preguntas, en este orden:

1. ¿Para qué existe esto? (Objetivo)
2. ¿Qué entra y qué no entra? (Scope)
3. ¿Cómo sabré que está terminado? (Criterios de aceptación)
4. ¿Qué decidí explícitamente no hacer? (No-goals)

Si tu documento no responde las 4, no es spec todavía.

---

## Los 4 elementos, uno por uno

### 1. Objetivo

Una sola línea. Producto + audiencia + propósito.

**Mal:**
> "Una app de hábitos."

**Mejor:**
> "Una app web para personas que quieren sostener hábitos diarios y necesitan visualizar su progreso sin distracciones sociales ni gamificación."

La diferencia: el mal ejemplo aplica a cualquier app de hábitos del mundo. El bueno toma posición sobre quién es el usuario y qué decidió **no** ser (no social, no gamificada).

**Test rápido:** lee tu objetivo. ¿Aplica a 10 apps distintas que ya existen? Entonces no es objetivo, es categoría.

---

### 2. Scope

Dos listas: qué SÍ entra, qué NO entra.

**El scope no es la lista de features.** Es la línea entre lo que prometes y lo que rechazas. Las dos partes importan.

**Ejemplo:**

```
Scope SÍ:
- Autenticación con email y password
- Hábitos personales con frecuencia diaria o semanal
- Check-in del día actual
- Vista de progreso con racha actual

Scope NO:
- Autenticación con OAuth (Google, Apple)
- Hábitos compartidos entre usuarios
- Check-in retroactivo (de días pasados)
- Estadísticas históricas más allá de la racha actual
```

El scope NO es donde matas el alcance que se te puede salir de las manos. Si no lo escribes, vas a tener la tentación durante el build de "ya que estoy, agrego OAuth". Y ahí se te muere el proyecto.

**Test rápido:** ¿tus dos listas tienen aproximadamente el mismo tamaño? Si tu scope NO tiene 1-2 ítems, probablemente no has pensado lo suficiente en qué rechazar.

---

### 3. Criterios de aceptación

Lista de afirmaciones **verificables**. Una afirmación es verificable si, después de probar la app, puedes responder sí o no sin discusión.

**Formato útil:**
> Dado [contexto], cuando [acción del usuario], entonces [resultado observable].

**Mal:**
> "El usuario puede crear hábitos fácilmente."

¿Cómo lo verificas? "Fácilmente" no es observable.

**Bien:**
> "Dado que el usuario está autenticado, cuando hace click en 'Nuevo hábito', llena nombre y frecuencia, y presiona 'Guardar', entonces el hábito aparece en su lista sin recargar la página."

Esto lo pruebas y respondes sí o no.

**Otro ejemplo:**

**Mal:**
> "La racha se calcula correctamente."

¿Qué es "correctamente"? Eso lo decides tú.

**Bien:**
> "La racha actual de un hábito diario es N si el usuario hizo check-in en los últimos N días consecutivos terminando en el día actual. Si hay un día sin check-in entre hoy y el último check-in, la racha es 0."

Esto lo pruebas con datos y respondes sí o no.

**Test rápido:** lee cada criterio y pregúntate: "¿Podría un QA escribir un test manual de esto sin pedirme aclaraciones?" Si no, reescríbelo.

---

### 4. No-goals

Lista de cosas que **decidiste no hacer**, no cosas que se te olvidaron.

La diferencia es enorme. Un no-goal explícito te protege de:

- La tentación de ti mismo durante el build ("ya que estoy...").
- Reclamos en la defensa ("¿por qué no tiene X?").
- Scope creep cuando Claude propone features adicionales.

**Mal:**
> No-goals: ninguno.

(Esto siempre es mentira. Decidiste no hacer un montón de cosas. Escríbelas.)

**Bien:**
```
No-goals:
- No habrá modo offline. La app requiere conexión.
- No habrá notificaciones push. Si quieres recordatorios, te los pones tú en tu calendario.
- No habrá vista en mobile optimizada. Funciona en mobile pero está pensada para desktop.
- No habrá feed social ni elementos comunitarios.
- No habrá importación de datos desde otras apps.
```

**Test rápido:** ¿hay 4+ items en tus no-goals? Si no, tu spec es ambicioso de manera implícita, lo cual es peor que ambicioso de manera explícita.

---

## Cómo se ve una spec bien escrita (ejemplo de otro dominio)

Para que no copies, te muestro un spec corto de un proyecto distinto: un **lector de RSS personal**.

```markdown
# Spec: RSS Reader Personal

## Objetivo
Un lector de RSS web para mí, con foco en lectura tranquila de blogs técnicos, sin contadores de "no leídos" ni notificaciones.

## Scope

### Sí entra
- Agregar feeds RSS pegando URL
- Lista de artículos ordenados por fecha de publicación, más nuevos primero
- Vista de lectura del artículo (título, contenido, link a la fuente)
- Marcar artículo como leído al abrirlo

### No entra
- Categorías o tags de feeds
- Buscador
- Modo "no leídos" o contador
- Importar OPML
- Sincronización entre dispositivos

## Criterios de aceptación

1. Dado que el usuario está en la pantalla principal, cuando pega una URL de RSS válida en el campo "agregar feed" y presiona Enter, entonces los artículos de ese feed aparecen en la lista sin recargar la página.

2. Dado que el usuario pega una URL que no responde con RSS válido, cuando presiona Enter, entonces se muestra un mensaje "URL no válida" debajo del campo y la lista de artículos no cambia.

3. Dado que la lista tiene artículos, cuando el usuario hace click en un artículo, entonces se abre la vista de lectura mostrando título, contenido y link a la fuente, y el artículo queda marcado como leído.

4. Dado que un artículo está marcado como leído, cuando vuelve a aparecer en la lista, entonces se muestra con opacidad reducida.

5. Dado que el usuario tiene N feeds agregados, cuando entra a la app, entonces ve los últimos artículos de todos los feeds en una sola lista ordenada por fecha descendente.

## No-goals
- No se persisten feeds entre sesiones diferentes del navegador. Es lector de uso único por sesión. (Esta decisión simplifica el scope; si después se requiere persistencia, será spec aparte.)
- No habrá autenticación. La app es personal y corre local.
- No se actualizan los feeds automáticamente en background. Se actualizan solo cuando el usuario refresca.
- No hay diseño mobile.
- No hay tema oscuro.
```

Cosas que notar de este ejemplo:

- El objetivo toma posición ("sin contadores de no leídos") — no es genérico.
- El scope NO tiene casi el mismo tamaño que el SÍ.
- Cada criterio describe **comportamiento observable**, no intención.
- Los no-goals incluyen una decisión sorprendente ("no se persisten feeds") con una justificación corta.
- En total son menos de 400 palabras. Un spec no es largo. Es **decidido**.

---

## Los errores más comunes en specs de alumnos del diplomado

**Error 1: Criterios que son features disfrazados.**

> "El usuario puede ver sus hábitos."

Eso es un feature, no un criterio. Un criterio es:

> "Dado que el usuario está autenticado y tiene N hábitos creados, cuando entra a `/dashboard`, entonces ve una lista con los N hábitos mostrando para cada uno: nombre, frecuencia, estado del día actual, y racha actual."

**Error 2: No-goals genéricos.**

> "No se hará una app perfecta."

Eso no es no-goal, es disclaimer. Un no-goal es algo específico que decidiste no construir:

> "No se implementará selector de zona horaria. La app asume que el usuario vive en su zona local del navegador."

**Error 3: Scope que crece durante el build.**

Si durante el build sientes la tentación de "ya que estoy, agrego una pantalla de configuración", **para**. O modificas el spec antes de implementar (y lo documentas en CONTEXT.md), o no lo haces.

Un spec que se modifica en el build sin documentar es spec que mentiste.

**Error 4: Objetivo aspiracional.**

> "Una app que cambie la forma en que la gente construye hábitos."

Eso es eslogan, no objetivo. El objetivo dice qué hace la app, no qué provoca en el mundo.

---

## El test final

Antes de cerrar tu spec, hazle esta pregunta:

> ¿Otro alumno del diplomado podría implementar esto sin hablar conmigo, y al terminar yo podría revisarlo y decir "sí cumple" o "no cumple" sin discutir?

Si la respuesta es sí, tienes spec.
Si la respuesta es no, todavía no.

---

## Por qué importa tanto esto

En el modelo viejo de programar, podías empezar a codear y descubrir el problema en el camino. La compu te aguantaba tu confusión: tú parabas, pensabas, retomabas.

Con vibe coding, no. Si tú no tienes claro qué quieres, **Claude lo va a decidir por ti, rápido**. Y lo va a decidir genérico, porque eso es lo que sabe hacer cuando no le das criterio.

El spec es donde tú metes tu criterio antes de que Claude meta el suyo.

Si la spec está vaga, la app va a salir genérica. Si la spec está decidida, la app va a salir tuya.

Por eso este paso vale 20 puntos de la rúbrica y por eso sin spec decente reprueba el proyecto entero. No es burocracia. Es la palanca de criterio más importante que tienes.
