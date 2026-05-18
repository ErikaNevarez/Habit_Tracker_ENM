# Prompt 01 — Interrogar el brief

> **Cuándo usarlo:** Paso 3 del paso a paso. Antes de escribir nada de spec.
>
> **Para qué sirve:** Hacer aflorar las decisiones que el brief deja abiertas. Si no las decides ahora, las improvisas en el build.

---

## Cómo usar este prompt

1. Abre Claude Code en el directorio de tu repo.
2. Copia el prompt de abajo.
3. Llena los huecos `[ASÍ]` con tu contexto real. **No lo pegues sin llenar los huecos.**
4. Manda el prompt.
5. Responde TÚ cada pregunta. No le pidas a Claude que las responda por ti.
6. Guarda la lista de preguntas/respuestas en tu máquina (fuera del repo).

---

## El prompt

```
CONTEXTO:
Estoy diseñando la spec de un proyecto llamado "Habit Tracker" para el Diplomado
Vibe Coding Profesional. Es una app de seguimiento de hábitos con:

- Autenticación email + password
- CRUD de hábitos (nombre, descripción, frecuencia diaria o semanal)
- Check-in diario sobre los hábitos
- Vista de progreso con racha actual

Stack obligatorio: Next.js 15 + Supabase + Vercel.

La extensión que elegí sumar al núcleo es: [NOMBRE DE TU EXTENSIÓN].
La razón por la que la elegí: [2-3 LÍNEAS DE POR QUÉ].

Mi contexto personal sobre el dominio:
[2-3 LÍNEAS: ¿usas habit trackers? ¿qué te frustra de los que conoces?
¿qué tipo de hábitos esperas trackear?]

OBJETIVO:
Antes de escribir la spec, necesito hacer aflorar todas las decisiones que el
brief deja abiertas. Quiero ver el espacio de decisiones, no que las tomes tú.

Hazme 10 preguntas críticas que debo decidir antes de escribir la spec.
Las preguntas deben cubrir al menos estas áreas:

1. Modelo de datos (qué se guarda, qué relaciones existen)
2. Reglas del check-in (deshacer, retroactivo, semanal vs diario)
3. Cálculo de la racha (qué la rompe, qué la mantiene)
4. Comportamiento de edición/borrado (qué pasa con el historial)
5. Mi extensión específica (qué decisiones requiere)

RESTRICCIONES:
- No me propongas soluciones. Solo preguntas.
- Cada pregunta debe tener 2 o 3 opciones implícitas, no ser abierta tipo
  "¿cómo quieres que funcione X?"
- Las preguntas deben ser respondibles con criterio, no requerir investigación.

CRITERIO DE ÉXITO:
Termino con 10 preguntas concretas. Cada una tiene opciones claras. Yo puedo
responderlas en menos de 1 minuto cada una usando mi criterio.
```

---

## Qué hacer con las preguntas

Cuando Claude te dé las 10 preguntas:

1. Pégalas en un archivo en tu máquina (`~/notas-habit-tracker.md` o similar).
2. **Bajo cada pregunta, escribe TU respuesta.** Frase corta, decisión clara.
3. Si alguna pregunta no la entiendes, pídele a Claude que te la aclare — pero la decisión la sigues tomando tú.
4. Si Claude te dio menos de 8 preguntas útiles, pídele 5 más: "Dame 5 preguntas más sobre [área que falta]".

**Ejemplo de cómo se ve una respuesta bien tomada:**

> **Pregunta:** Cuando el usuario edita el nombre de un hábito existente, ¿qué pasa con el historial de check-ins ya registrados? (a) Se conservan asociados al hábito (b) Se borran (c) Se conservan pero quedan marcados como "del nombre anterior".
>
> **Mi decisión:** (a). Razón: el hábito es el mismo, solo cambió su etiqueta. Borrar historial castiga al usuario que renombra.

Ese nivel de claridad es lo que necesitas para el paso 4.

---

## Anti-patrones de este paso

**Anti-patrón 1: Pedirle a Claude que responda las preguntas.**
Resultado: spec con las decisiones que Claude habría tomado, no las tuyas. Cuando defiendas en clase, no sabrás por qué decidiste así.

**Anti-patrón 2: Responder "lo que recomiendes" a una pregunta.**
Es lo mismo que el anti-patrón 1 disfrazado. Decide tú.

**Anti-patrón 3: Saltarte preguntas porque "no aplican".**
Si Claude te hizo la pregunta, es porque el brief no la cubre. "No aplica" en realidad significa "no he pensado en eso todavía". Piénsalo.
