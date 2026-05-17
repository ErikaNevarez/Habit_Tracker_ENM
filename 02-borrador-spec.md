# Prompt 02 — Borrador de spec

> **Cuándo usarlo:** Paso 4 del paso a paso. Después de tener tus 10 preguntas respondidas.
>
> **Para qué sirve:** Convertir tus decisiones en una primera versión de `spec.md` con los 4 elementos obligatorios.

---

## Cómo usar este prompt

1. Ten a la mano tu lista de preguntas/respuestas del paso 3.
2. Copia el prompt de abajo.
3. Llena los huecos `[ASÍ]`. Especialmente el bloque de DECISIONES — ahí pegas tus respuestas del paso anterior.
4. Manda el prompt.
5. Pega el resultado en `spec.md`. **No lo edites todavía.** Lo vas a criticar en el siguiente paso.

---

## El prompt

```
CONTEXTO:
Soy alumno del Diplomado Vibe Coding Profesional. Estoy escribiendo la spec
de un Habit Tracker. Stack: Next.js 15 + Supabase + Vercel.

NÚCLEO OBLIGATORIO DEL PROYECTO:
- Autenticación email + password
- CRUD de hábitos (nombre, descripción, frecuencia diaria o semanal)
- Check-in diario
- Vista de progreso con racha actual

EXTENSIÓN ELEGIDA:
[NOMBRE DE TU EXTENSIÓN + 2 LÍNEAS DE QUÉ HACE]

DECISIONES QUE YA TOMÉ:
[PEGA AQUÍ TUS 10 PREGUNTAS DEL PASO 3 CON TUS RESPUESTAS]

OBJETIVO:
Generar el borrador de `spec.md` con exactamente esta estructura:

## Objetivo
Una sola línea que diga qué es el producto y para quién.

## Scope
Dos sublistas:
- Qué SÍ entra en este proyecto
- Qué NO entra (no-goals explícitos)

## Criterios de aceptación
Lista numerada. Cada criterio debe poder responderse sí/no después de probar
la app. Formato sugerido: "Dado [contexto], cuando [acción], entonces [resultado
observable]."

Cubre mínimo:
- Autenticación (registro, login, logout)
- CRUD de hábitos (crear, editar, eliminar)
- Check-in (marcar, comportamiento descrito en mis decisiones)
- Vista de progreso (lo que se muestra, cómo se calcula la racha)
- La extensión que elegí

## No-goals
Lista explícita de cosas que decidí NO hacer en este proyecto. Mínimo 4 ítems.

RESTRICCIONES:
- No inventes decisiones que no estén en mi bloque "DECISIONES QUE YA TOMÉ".
  Si falta información para un criterio, escribe [DECIDIR: pregunta concreta]
  en vez de inventar.
- No agregues features que no estén en el núcleo o en mi extensión.
- Criterios verificables, no aspiracionales. Nada de "la app es rápida" o
  "la interfaz es intuitiva".
- Sin código. Sin nombres de tablas ni endpoints. Esto es spec, no diseño técnico.

CRITERIO DE ÉXITO:
Otro alumno del diplomado podría leer este spec y empezar a hacer ADRs sin
necesidad de hablar conmigo. Cada criterio de aceptación es testeable.
```

---

## Qué hacer con el resultado

1. Pégalo tal cual en `spec.md`.
2. Lee el spec completo de corrido. ¿Suena como tu proyecto? Si suena genérico, hay algo mal.
3. Busca etiquetas `[DECIDIR: ...]`. Si quedaron, regresa al paso 3 — esas son preguntas que no respondiste.
4. **No edites el archivo todavía.** Pasa al siguiente prompt (`03-critica-spec.md`).

---

## Cuándo este prompt sale mal

**Sale mal si:** el spec resultante incluye features que tú no decidiste (por ejemplo, "el usuario puede compartir hábitos" cuando tu extensión era otra). Esto significa que Claude inventó. Repite el prompt y refuerza la restricción.

**Sale mal si:** todos los criterios son tipo "el usuario puede ver sus hábitos" sin detalle. Esto significa que tus decisiones del paso 3 fueron vagas. Regresa al paso 3 y profundiza.

**Sale bien si:** cada criterio menciona condiciones concretas (qué pasa cuando X, qué se ve en pantalla, qué se guarda en DB) y los no-goals son específicos a tu proyecto, no genéricos.

---

## Anti-patrón clave

**No le pidas a Claude "mejóralo" después de que te entregue el borrador.** Eso es desperdicio de prompt y va a tirar texto más bonito sin resolver los problemas reales. La mejora viene del paso 5 (crítica explícita) y el paso 6 (tú editando a mano).
