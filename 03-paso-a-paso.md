# Paso a paso: de cero a spec lista

> Esto es lo que vas a hacer entre hoy y el jueves 23:59. Llegas el viernes con el repo creado y `spec.md` commiteado. Sin eso, no entras a Sesión 2.

---

## Antes de empezar

Lee primero, en este orden:

1. `01-que-es-una-spec.md` (15 min de lectura)
2. `02-brief-habit-tracker.md` (10 min de lectura)

No abras Claude todavía. Léelos en seco. Si arrancas a promptear antes de entender el brief, vas a malgastar prompts y tiempo.

---

## Resumen de los 7 pasos

| # | Paso                          | Tiempo estimado | Producto                                |
|---|-------------------------------|-----------------|------------------------------------------|
| 1 | Crear repo y estructura       | 15 min          | Repo en GitHub con archivos base         |
| 2 | Elegir tu extensión           | 20 min          | Decisión escrita en `spec.md`            |
| 3 | Interrogar el brief           | 30 min          | Lista de preguntas respondidas           |
| 4 | Borrador de spec              | 45 min          | `spec.md` con los 4 elementos            |
| 5 | Criticar el borrador          | 30 min          | Lista de problemas + correcciones        |
| 6 | Iterar hasta pasar el test    | 30-60 min       | `spec.md` final                          |
| 7 | Verificar y commitear         | 15 min          | Commit con la spec en `main`             |

**Total estimado:** 3-4 horas distribuidas en 2-3 días. No lo hagas todo en una sentada — la spec mejora cuando duermes con ella.

---

## Paso 1: Crear repo y estructura inicial

**Objetivo:** tener un lugar donde vivir la spec. Nada más. La app de Next.js no se inicializa todavía — eso lo haremos en Sesión 3.

### 1.1 Crea el repo en GitHub

- Nombre sugerido: `habit-tracker-<tuapellido>` (ejemplo: `habit-tracker-ramirez`).
- Visibilidad: público.
- Inicialízalo con `README.md`.
- Licencia: la que quieras (MIT está bien).

### 1.2 Clona el repo a tu máquina

```bash
git clone https://github.com/<tuusuario>/habit-tracker-<tuapellido>.git
cd habit-tracker-<tuapellido>
```

### 1.3 Crea la estructura mínima

Desde la raíz del repo, crea estos archivos vacíos (o con el contenido placeholder que indico):

```
habit-tracker-<tuapellido>/
├── README.md           ← ya existe, lo editas en el paso 7
├── spec.md             ← vacío, lo llenas en el paso 4
├── CONTEXT.md          ← vacío por ahora, lo usarás en Sesión 3
├── AGENTS.md           ← convenciones del proyecto, lo trabajamos en clase
└── .gitignore          ← agrega `node_modules/`, `.env*`, `.DS_Store`
```

Crea los archivos así (en macOS/Linux):

```bash
touch spec.md CONTEXT.md AGENTS.md
echo "node_modules/" > .gitignore
echo ".env*" >> .gitignore
echo ".DS_Store" >> .gitignore
```

En Windows con PowerShell:

```powershell
New-Item spec.md, CONTEXT.md, AGENTS.md
Set-Content .gitignore "node_modules/`n.env*`n.DS_Store"
```

### 1.4 Primer commit

```bash
git add .
git commit -m "chore: scaffolding inicial del proyecto"
git push
```

**Checkpoint del paso 1:** entras a GitHub y ves los 5 archivos arriba.

---

## Paso 2: Elige tu extensión

**Objetivo:** decidir, antes de tocar Claude, qué extensión vas a sumar al núcleo.

Vuelve al catálogo en `02-brief-habit-tracker.md` y elige **una**. Una sola.

Criterio para elegir:

- ¿Te interesa el dominio? (Vas a vivir con esto 2 semanas, mejor que te lata.)
- ¿La entiendes lo suficiente para describirla en 3 líneas? Si no, elige otra.
- ¿Sabes cómo verificarías que está terminada? Si no, elige otra.

Abre `spec.md` y escribe arriba, como nota temporal:

```
Extensión elegida: [nombre de la extensión]
Por qué la elegí: [3 líneas]
```

Esa nota la vas a borrar más adelante — solo te sirve como ancla mientras escribes el resto.

---

## Paso 3: Interroga el brief con Claude

**Objetivo:** hacer aflorar todas las decisiones que el brief deja abiertas. Si no las haces aflorar ahora, vas a improvisarlas durante el build, y ahí es donde se rompen los proyectos.

Abre Claude Code en el directorio del repo. Usa el prompt:

```
prompts/01-interrogar-brief.md
```

Sigue las instrucciones del prompt. Vas a salir de este paso con **una lista de preguntas críticas y tus respuestas a cada una**.

Guarda esa lista en un archivo temporal en tu máquina (fuera del repo, por ejemplo en `~/notas-habit-tracker.md`). No la commitees al repo — es trabajo de pensamiento, no entregable.

**Checkpoint del paso 3:** tienes mínimo 8 preguntas respondidas con criterio propio.

---

## Paso 4: Genera el borrador de spec

**Objetivo:** producir la primera versión de `spec.md` con los 4 elementos obligatorios:

1. Objetivo (1 línea)
2. Scope (qué sí entra, qué no entra)
3. Criterios de aceptación verificables
4. No-goals

Usa el prompt:

```
prompts/02-borrador-spec.md
```

El prompt tiene huecos `[CONTEXTO]` que llenas con la lista de preguntas/respuestas del paso 3 y la extensión que elegiste en el paso 2.

Pega el resultado en `spec.md`. Es **borrador** — no lo defiendas todavía, criticarlo es el siguiente paso.

**Checkpoint del paso 4:** `spec.md` tiene los 4 elementos visibles, aunque tengan problemas.

---

## Paso 5: Critica el borrador

**Objetivo:** encontrar los problemas de tu propia spec antes de que los encuentre el viernes el grupo.

Usa el prompt:

```
prompts/03-critica-spec.md
```

Le pasas tu `spec.md` completo y le pides a Claude que la critique desde 3 perspectivas distintas: un senior que la va a revisar, un QA que va a probarla, y un alumno nuevo que la va a implementar sin hablar contigo.

Vas a recibir una lista de problemas. **Anótalos. No le pidas a Claude que los arregle.** El arreglo lo haces tú a mano en el paso 6.

**Checkpoint del paso 5:** tienes una lista escrita de mínimo 5 problemas de tu spec.

---

## Paso 6: Itera hasta pasar el test

**Objetivo:** dejar la spec en un estado donde pasa esta prueba:

> Otro programador podría implementar esto sin hablar conmigo.

Toma los problemas del paso 5 y arréglalos en `spec.md`. Edita directamente el archivo. No le pidas a Claude que lo reescriba — lo reescribes tú, leyendo cada criterio de aceptación y preguntándote si es verificable.

**Un criterio es verificable si puedes responder sí/no después de probar la app.**

| Criterio                                              | ¿Verificable?           |
|-------------------------------------------------------|-------------------------|
| "La app es intuitiva."                                | No. Subjetivo.          |
| "El usuario puede crear un hábito en menos de 3 clicks." | Sí. Cuento clicks.    |
| "Los datos se guardan."                               | No. ¿Dónde? ¿cuándo?    |
| "Al hacer click en 'Guardar', el hábito aparece en la lista sin recargar la página." | Sí. |

Si encuentras criterios no verificables, reescríbelos. Si encuentras decisiones no tomadas (cosas tipo "ya veremos"), tómalas ahora.

**Repite el paso 5 sobre la nueva versión** si crees que cambió mucho. Para de iterar cuando los problemas que encuentras son cosméticos, no estructurales.

**Checkpoint del paso 6:** todos los criterios de aceptación son verificables y los no-goals están explícitos.

---

## Paso 7: Verifica y commitea

**Objetivo:** confirmar que la spec está completa y dejarla en el repo lista para el viernes.

### 7.1 Usa el prompt de verificación

```
prompts/04-verificar-spec.md
```

Le pasas la spec y te devuelve un checklist de cumplimiento. Si algo falla, regresas al paso 6.

### 7.2 Actualiza el README.md

Reemplaza el contenido del `README.md` (que viene de GitHub por defecto) por algo así:

```markdown
# Habit Tracker

Proyecto del Diplomado Vibe Coding Profesional - Instituto Inadaptados.

Ver `spec.md` para el spec del proyecto.

**Estado:** spec en revisión. Build en Sesión 3.
```

### 7.3 Commit final

```bash
git add spec.md README.md
git commit -m "docs: spec inicial del habit tracker"
git push
```

**Checkpoint del paso 7:** entras a GitHub, abres `spec.md`, lo lees como si no fuera tuyo, y te convence.

---

## Qué traer el viernes

Lee `checklist-viernes.md`. En resumen:

- Repo público en GitHub con `spec.md` commiteado.
- Tu lista de preguntas/respuestas del paso 3 (en tu máquina, no en el repo).
- La identificación de qué extensión elegiste y por qué.
- Disposición a que tu spec sea criticada en público. Vas a salir de Sesión 2 con una versión mejor.

---

## Errores comunes que vas a cometer (y cómo evitarlos)

**Error 1: Saltarte el paso 3 porque "ya sé qué quiero hacer".**
Resultado: spec con decisiones implícitas que después chocan en el build.

**Error 2: Aceptar el borrador del paso 4 como final.**
Resultado: spec genérico que Claude generó sin criterio. Repruebas el checkpoint.

**Error 3: Pedirle a Claude que arregle los problemas del paso 5.**
Resultado: spec maquillado, no corregido. Sigues teniendo los mismos problemas escondidos.

**Error 4: Elegir 2 o 3 extensiones "por si las dudas".**
Resultado: bandera roja automática. Repruebas el proyecto.

**Error 5: Llegar el viernes sin haber leído tu propio spec en voz alta.**
Resultado: te trabas defendiéndolo en clase. Lee tu spec antes de salir el viernes.
