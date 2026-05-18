# Prompt 03 — Critica la spec

> **Cuándo usarlo:** Paso 5 del paso a paso. Después de tener el borrador en `spec.md`.
>
> **Para qué sirve:** Encontrar los problemas de tu spec antes de que los encuentre el viernes el grupo. La defensa pública premia honestidad sobre el proceso, pero castiga ingenuidad sobre la spec.

---

## Cómo usar este prompt

1. Ten `spec.md` en su versión de borrador.
2. Copia el prompt de abajo.
3. Pégalo en Claude, con tu spec completo embebido donde dice `[PEGA TU SPEC AQUÍ]`.
4. Lee las críticas con atención. Anótalas en una lista.
5. **No le pidas a Claude que arregle nada.** Solo crítica. El arreglo lo haces tú en el paso 6.

---

## El prompt

```
CONTEXTO:
Soy alumno del Diplomado Vibe Coding Profesional. Tengo un borrador de spec
para un Habit Tracker. El curso evalúa specs sobre estos puntos:

- Claridad del objetivo
- Scope realista para 3 horas de build asistido por IA
- Criterios de aceptación verificables (no aspiracionales)
- No-goals explícitos
- Decisiones tomadas (no "ya veremos")

Banderas rojas que descalifican automáticamente el proyecto:
- Spec genérico sin criterios verificables
- Decisiones implícitas que se van a improvisar en el build
- Criterios subjetivos tipo "intuitivo", "bonito", "rápido"

MI SPEC:
[PEGA TU SPEC COMPLETO AQUÍ]

OBJETIVO:
Critica este spec desde 3 perspectivas distintas. No me lo reescribas. Solo
señala problemas. Quiero salir con una lista de cosas a arreglar.

PERSPECTIVA 1 — Senior en code review:
¿Qué decisiones técnicas implícitas hay que el spec no toma?
¿Qué casos extremos no se contemplan? (concurrencia, datos vacíos, errores)
¿Qué supuestos del autor pueden romperse?

PERSPECTIVA 2 — QA que va a probar la app:
¿Qué criterios de aceptación NO son verificables?
¿Cuáles dependen de juicio subjetivo?
¿Para qué criterios no podrías escribir un caso de prueba?

PERSPECTIVA 3 — Otro alumno que va a implementarlo sin hablar conmigo:
¿Qué partes del spec quedan ambiguas?
¿Qué decisiones le tocaría inventar a quien implemente?
¿Qué información necesitaría preguntarle al autor?

RESTRICCIONES:
- No propongas redacciones alternativas. Solo señala el problema.
- No me digas "está bien" si está bien. Asume que hay problemas. Búscalos.
- Sé específico: cita el criterio o sección exacta, no generalidades.
- No inventes problemas que no existen. Si una sección está sólida, no la
  toques.

CRITERIO DE ÉXITO:
Termino con una lista de mínimo 5 problemas concretos, cada uno citando el
texto exacto del spec que tiene el problema y describiendo en qué consiste el
problema.
```

---

## Qué hacer con las críticas

1. Cópialas a un archivo temporal (puede ser el mismo `~/notas-habit-tracker.md`).
2. Para cada crítica, decide:
   - **¿Tiene razón?** Si sí, va a la lista de "arreglar".
   - **¿Es falsa alarma?** Si Claude inventó un problema que no existe, descártalo.
   - **¿No la entiendes?** Pide a Claude que la aclare con un follow-up del tipo: "Explícame el problema X con un ejemplo concreto."

3. Cuando tengas tu lista de arreglos definitiva, **cierra esta conversación con Claude**. El paso 6 (iterar) lo haces editando a mano.

---

## Por qué no le pides que lo arregle

Si le dices a Claude "ahora arregla los problemas", va a entregar un texto más bonito que no resuelve los problemas estructurales. Va a maquillar:

- Criterios subjetivos los va a reescribir con más palabras pero igual de subjetivos.
- Decisiones faltantes las va a inventar para que no se note el hueco.
- Ambigüedades las va a "aclarar" con frases vacías tipo "como sea apropiado".

**Tú editando a mano produces mejor spec que Claude reescribiendo.** Porque tú sabes qué decidiste y por qué. Claude no.

---

## Si todas las críticas son cosméticas

Si Claude solo encuentra problemas tipo "podrías usar mejor formato" o "sería más claro si reordenas", una de dos:

- Tu spec genuinamente está sólido y puedes ir al paso 7 directo.
- Tu spec está tan genérico que Claude no encontró nada concreto que criticar.

Para distinguir cuál es: lee tu spec en voz alta. Si suena como podría aplicar a cualquier habit tracker del mundo, es la segunda. Regresa al paso 3 y haz tus decisiones más específicas.
