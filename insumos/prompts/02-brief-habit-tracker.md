# Brief: Habit Tracker

> Esto es el **brief del proyecto**, no la spec. El brief describe qué se quiere construir en lenguaje de producto. La spec la escribes tú a partir de este brief.

---

## El problema

Mucha gente quiere construir hábitos pero no sostiene el seguimiento. Las apps que existen son demasiado pesadas (sociales, gamificadas, con suscripción) o demasiado ligeras (una nota en el teléfono). Falta algo intermedio: una app simple, seria, que te permita declarar tus hábitos y revisar tu progreso sin fricción.

Eso es lo que vas a construir.

---

## Núcleo obligatorio

Estas 4 capacidades son **innegociables**. Si tu spec no las cubre, no es habit tracker, es otra cosa.

### 1. Autenticación

El usuario se registra y entra a la app con email y password. Cada usuario ve solo sus propios hábitos.

### 2. CRUD de hábitos

El usuario puede crear, editar y eliminar hábitos. Cada hábito tiene mínimo:

- Nombre
- Descripción
- Frecuencia (diaria o semanal — tú decides cómo modelas "semanal")

Eliminar un hábito borra también su historial. O lo archiva. Tú decides — pero lo decides en el spec, no improvisando en el build.

### 3. Check-in diario

El usuario puede marcar un hábito como cumplido **en el día actual**. Una vez marcado, queda registrado.

Casos que tienes que decidir y dejar en el spec:

- ¿Se puede desmarcar el check-in del día?
- ¿Se puede hacer check-in de un día pasado?
- ¿Qué pasa con hábitos semanales? ¿Se marcan una vez por semana o se cuenta diferente?

No hay respuesta correcta. Hay respuesta **decidida y documentada**.

### 4. Vista de progreso

El usuario ve una lista de sus hábitos con:

- Estado del día actual (cumplido / no cumplido)
- Racha actual (cuántos días consecutivos cumpliendo)

La racha se rompe cuando hay un día sin check-in. O no. Tú decides cómo se calcula y lo dejas claro en el spec.

---

## Extensiones (elige máximo 1)

Tu spec puede incluir **una sola** de estas. No más.

Si entregas con más de una extensión y tu núcleo está incompleto, repruebas el proyecto sin importar lo demás.

| Extensión               | Pista de qué implica                                                                |
|-------------------------|-------------------------------------------------------------------------------------|
| Recordatorios           | El usuario configura una hora del día y la app le manda aviso. Decide el canal: email, push, in-app. |
| Estadísticas históricas | Gráfico o tabla con cumplimiento por semana/mes. Decide qué métricas valen la pena. |
| Categorías o etiquetas  | Cada hábito pertenece a una categoría (salud, trabajo, etc). Decide si las categorías son fijas o las define el usuario. |
| Hábitos compartidos     | Un usuario puede invitar a otro a ver o coparticipar en un hábito. Decide los permisos. |
| Importar/exportar       | El usuario descarga su historial en CSV o JSON y puede reimportarlo. Decide el formato. |
| Personalización visual  | Modo oscuro, colores por hábito, íconos. Decide hasta dónde llega.                   |

**No está en este catálogo (lo trabajamos en la siguiente unidad del diplomado):**
- Integración con agente IA que recomiende, analice o conteste sobre tus hábitos.

Si tu idea de extensión no está en la tabla, elige una que sí esté. No vamos a aprobar extensiones custom para esta sesión.

---

## Restricciones técnicas

- Frontend: Next.js 15 con App Router.
- Backend / DB: Supabase (Postgres + Auth).
- Deploy: Vercel.
- TypeScript estricto. Nada de `any` salvo justificado en CONTEXT.md.
- Estilos: Tailwind. Sin librerías de componentes pesadas (no Material UI, no Chakra). Si quieres usar shadcn/ui, se vale.

No discutas este stack en tu spec. No es decisión que tomes — es restricción del curso. Tus ADRs en clase serán sobre **cómo** usar este stack, no sobre **si** usarlo.

---

## Lo que NO se evalúa

Para que no pierdas tiempo en lo que no cuenta:

- **Diseño visual.** Que se vea decente, no que se vea premium. Una app fea con buen pipeline pasa.
- **Performance.** Salvo que tu app cargue en más de 5 segundos, no nos importa.
- **Cobertura de tests.** En este proyecto no se piden tests automatizados.
- **Responsive perfecto.** Se prueba en desktop. Mobile-friendly es bonus, no requisito.

---

## Lo que SÍ se evalúa (recordatorio)

- Spec con los 4 elementos: objetivo, scope, criterios de aceptación verificables, no-goals.
- ADRs defendibles (los harás en clase).
- Plan con tareas atómicas.
- Calidad del prompting durante el build.
- Honestidad en CONTEXT.md sobre lo que editaste a mano.
- Defensa pública del proceso.

La rúbrica completa la viste en `00-fundamentos/criterios-aprobacion.md`. Si no la has leído, léela antes de seguir.

---

## La regla más importante de este brief

> Una decisión no documentada es una decisión no tomada.

Cuando dudes entre dos opciones (¿se puede deshacer un check-in? ¿la racha se rompe a las 24h o a las 48h? ¿qué pasa si edito el nombre de un hábito con historial?), la respuesta no es "ya veremos en el build". La respuesta es: **decide ahora y escríbelo en el spec**.

Si no lo decides tú, lo va a decidir Claude por ti — y no necesariamente como tú quieres.
