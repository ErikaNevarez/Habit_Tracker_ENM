# Prompt 04 — Verifica la spec

> **Cuándo usarlo:** Paso 7 del paso a paso. Cuando creas que tu spec está terminada.
>
> **Para qué sirve:** Pasar tu spec por un checklist objetivo antes de commitearla. Si falla, regresas al paso 6.

---

## Cómo usar este prompt

1. Ten tu `spec.md` en versión que tú consideras final.
2. Copia el prompt de abajo.
3. Pega el prompt en Claude con tu spec embebido.
4. Lee el reporte. Si falla algo, **regresas al paso 6** (no le pides a Claude que arregle).
5. Cuando pase, commiteas.

---

## El prompt

```
CONTEXTO:
Tengo una spec terminada para un Habit Tracker. Antes de commitearla quiero
verificar que cumple los requisitos del Diplomado Vibe Coding Profesional.

MI SPEC:
[PEGA TU SPEC COMPLETO AQUÍ]

OBJETIVO:
Evalúa la spec contra este checklist. Para cada ítem responde: ✓ cumple,
✗ no cumple, o ⚠ cumple parcialmente. Si no cumple o cumple parcial,
cita la sección exacta y explica qué falta. No me digas cómo arreglarlo,
solo señala.

CHECKLIST:

A. Los 4 elementos obligatorios
A.1 Existe sección "Objetivo" con una sola línea que describe producto y audiencia
A.2 Existe sección "Scope" con lista de qué SÍ entra
A.3 Existe sección "Criterios de aceptación" numerada
A.4 Existe sección "No-goals" con mínimo 4 ítems explícitos

B. Cobertura del núcleo del proyecto
B.1 Hay criterios para autenticación (registro, login, logout)
B.2 Hay criterios para creación, edición y eliminación de hábitos
B.3 Hay criterios para check-in con comportamiento descrito (incluye qué pasa
    al deshacer si aplica, y qué pasa con frecuencia semanal vs diaria)
B.4 Hay criterios para vista de progreso (qué se muestra)
B.5 Hay criterios que describen cómo se calcula la racha (qué la rompe,
    qué la mantiene)
B.6 Hay criterios para la extensión elegida

C. Verificabilidad
C.1 Cada criterio de aceptación se puede responder sí/no después de probar
    la app
C.2 Ningún criterio usa palabras subjetivas: "bonito", "intuitivo", "rápido",
    "fácil", "amigable"
C.3 Los criterios describen comportamiento observable, no intención interna

D. Decisiones tomadas
D.1 No hay frases tipo "se decidirá después", "ya veremos", "según convenga"
D.2 No hay etiquetas [DECIDIR: ...] sin resolver
D.3 Casos extremos están cubiertos: ¿qué pasa con datos vacíos? ¿qué pasa al
    eliminar un hábito con historial? ¿qué pasa si no hay conexión?

E. Scope realista
E.1 La extensión es exactamente UNA, no varias
E.2 No hay features fuera del núcleo + la extensión declarada
E.3 Los no-goals incluyen explícitamente features que el alumno podría tener
    la tentación de agregar (tipo "no se hacen estadísticas históricas si la
    extensión no es esa")

RESTRICCIONES:
- Sé estricto. Si dudas entre ✓ y ⚠, marca ⚠.
- No inventes problemas. Si algo cumple, di ✓ y sigue.
- No propongas correcciones. Solo señala qué falta.

CRITERIO DE ÉXITO:
Termino con un reporte donde cada uno de los 15 ítems del checklist tiene
una marca clara y, para los que no cumplen, una cita textual del spec que
muestra el problema.
```

---

## Cómo interpretar el reporte

- **Todos ✓:** commitea la spec y vete a dormir.
- **1-3 ⚠ menores:** decide si los arreglas o los aceptas. Algunos parciales son tolerables si tienes razón fuerte (ej. una decisión que prefieres tomar en clase con feedback del grupo). Si los aceptas, déjalo claro en una nota al final del spec: "Pendiente de revisión en clase: [tema]".
- **Algún ✗ en sección A o D:** **no commitees todavía.** Estos son estructurales. Regresa al paso 6.
- **Algún ✗ en sección C:** **no commitees todavía.** Criterios no verificables son bandera roja de la rúbrica. Reescríbelos.

---

## Después del reporte verde

Cuando todos los puntos críticos pasen:

1. Cierra esta conversación con Claude.
2. Lee tu spec una vez más en voz alta. Sí, en voz alta. Detectas problemas que leyendo en silencio se te escapan.
3. Si algo te suena raro al leerlo, arréglalo a mano.
4. Commit:

```bash
git add spec.md README.md
git commit -m "docs: spec inicial del habit tracker"
git push
```

5. Entra a GitHub y verifica que se ve bien renderizado.

---

## Anti-patrón final

**No te enamores de tu spec.** El viernes en clase va a ser criticada. Vas a salir con una versión mejor. Eso no es fracaso, es el método funcionando.

Si llegas el viernes diciendo "mi spec ya está perfecto", o no leíste bien las críticas del paso 5, o estás defendiendo orgullo y no producto. Ninguna de las dos cosas se premia.
