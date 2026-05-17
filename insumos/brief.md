# Brief: Habit Tracker

## 1. El problema

Construir hábitos requiere consistencia, pero la fricción mata la motivación. Las apps existentes (Habitica, Done, etc.) ofrecen demasiadas características, análisis complejos, y gamificación que distraen del objetivo real: hacer que el usuario vuelva mañana a registrar su hábito.

Lo que falta es una herramienta obsesionada con la acción diaria: un lugar donde registrar un hábito es tan rápido y satisfactorio que se convierte en ritual. Donde ver el progreso genera motivación, no análisis parálisis.

## 2. Núcleo obligatorio

1. **Autenticación y sesión**: Login con email/contraseña vía Supabase. Sesión persistente. Sin complejidad social (sin perfiles públicos ni equipos en el MVP).

2. **Hábitos**: Crear con nombre y descripción breve. Listar y visualizar hábitos activos. Poder pausar/eliminar. *Decisión abierta: ¿Qué información adicional define un hábito? (Categoría, frecuencia esperada, tipo: on/off vs. con cantidad).*

3. **Registro diario**: Check-in del hábito hoy (marcar completado/no completado). Corrección de registros pasados (últimos 7-30 días). Vista simple de "hoy vs. resto". *Decisión abierta: ¿Cómo se distribuyen los hábitos en pantalla? ¿Un hábito por página, lista scrolleable, grid?*

4. **Visualización de progreso**: Streak actual (días consecutivos). Tasa de completado (último mes). Un gráfico visual que muestre la consistencia sin ser abrumador.

## 3. Extensiones (elegir máximo 1)

| Nombre | Descripción |
|--------|------------|
| Recordatorios diarios | Push o email a hora fija recordando registrar hábitos pendientes |
| Metas numéricas | Soportar hábitos cuantitativos (ej: beber 2L agua, ejercitar 30min) con progreso visual |
| Notas y reflexión | Adjuntar nota libre al registrar cada día; revisar notas del histórico |
| Análisis temporal | Gráficos de tendencia semanal/mensual; identificar días con más/menos completado |
| Categorías e informes | Agrupar hábitos; resumen visual por categoría |
| Compartir progreso | Generar imagen estática para compartir (streak, mes actual) |
| Exportar datos | Descargar CSV con todo el histórico de registros |

## 4. Restricciones técnicas

Next.js 15 (App Router), TypeScript estricto, Supabase (Postgres + Auth), Vercel, Tailwind CSS.

## 5. Lo que NO se evalúa

- Diseño premium: interfaz clara, pero sin pulido visual extremo.
- Tests automatizados: prioritario es feature correcta, no cobertura.
- Responsive mobile-first: desktop y tablet son suficientes; mobile optimización es bonus.
- Sincronización en tiempo real: sin WebSockets ni actualizaciones live.
- Gamificación elaborada: sin badges, leaderboards, o niveles de desbloqeo.
