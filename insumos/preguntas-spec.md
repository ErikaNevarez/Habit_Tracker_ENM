# Preguntas críticas para especificar Habit Tracker

## 1. Modelo de datos: un tipo vs. dos tipos

Un hábito on/off (meditar) y uno cuantitativo (beber 2L) ¿son almacenados como un único tipo con variantes, o son tipos separados en la BD?

- a) Un tipo único con campo "modo" (on/off vs. cantidad)
- b) Dos tipos separados (HabitoBinario, HabitoCuantitativo)

## 2. Check-in retroactivo: ventana de edición

¿En qué rango temporal puedo registrar o editar un check-in?

- a) Solo el día actual
- b) Hoy y los últimos 7 días
- c) Cualquier día pasado sin límite

## 3. Corrección de error: limpiar vs. editar

Si registré mal un check-in hoy, ¿qué opciones tiene el usuario?

- a) Solo "editar" (cambiar el valor, no volver a "sin registrar")
- b) Solo "limpiar" (vuelve a estado vacío/no registrado)
- c) Ambas acciones disponibles

## 4. Racha rota: día faltante vs. meta no alcanzada

¿Qué rompe la racha de un usuario?

- a) Faltarse un día completo (no registrar nada)
- b) Registrar pero no alcanzar la meta (si la racha de un hábito cuantitativo cae por debajo)
- c) Ambas: cualquier día faltante O cualquier meta no alcanzada rompe

## 5. Racha: global vs. por hábito

¿El usuario tiene una racha global o cada hábito tiene su propia racha?

- a) Racha por hábito (cada uno es independiente)
- b) Una racha global del usuario
- c) Ambas (racha individual + racha global)

## 6. Historial al borrar hábito

Si borro un hábito, ¿qué pasa con sus registros históricos?

- a) Se eliminan permanentemente
- b) Se archivan (invisible en UI pero recuperable administrativamente)
- c) Soft delete (invisible pero técnicamente rescatable)

## 7. Meta cuantitativa: ¿fija o editable?

La meta de un hábito cuantitativo (ej: "30 min de coding") ¿es fija desde la creación o editable después?

- a) Se define al crear y es inmodificable
- b) Es editable en cualquier momento
- c) Editable pero solo prospectivamente (no afecta días anteriores)

## 8. Retroactividad de cambio de meta

Si cambio la meta de "30 min" a "45 min", ¿cómo recalcula la racha histórica?

- a) Recalcula retroactivamente toda la racha con la nueva meta
- b) La nueva meta aplica solo a partir de mañana, el histórico mantiene la vieja meta
- c) El usuario elige qué día aplica el cambio

## 9. Input del check-in cuantitativo

¿Qué registra el usuario al hacer check-in de un hábito cuantitativo?

- a) El valor exacto logrado (ej: "ingresé 25 minutos")
- b) Sí/No binario: "¿alcanzaste la meta de 30 min?"
- c) Ambas opciones: ingresar valor + un checkbox "alcancé meta"

## 10. Visualización del progreso cuantitativo

En la pantalla de hoy, ¿cómo se visualiza el progreso de un hábito cuantitativo?

- a) Fracción: "25 / 30 min"
- b) Porcentaje: "83%"
- c) Barra visual sin números
