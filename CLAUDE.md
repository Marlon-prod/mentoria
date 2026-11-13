# Instrucciones para Claude

Este repo es el **segundo cerebro** del usuario (ver `segundo-cerebro/README.md`). Respondé en español.

## Tablero de tareas
- Tablero publicado: "Mi Segundo Cerebro" (fuente: `app/segundo-cerebro.html`). Sus datos viven en la base de datos del artifact, no en el HTML.
- Colección `tasks`, documento por tarea:
  `{title, area, status: "backlog"|"semana"|"haciendo"|"bloqueada"|"hecho", priority: "alta"|"media"|"baja", due: "AAAA-MM-DD"|null, notes, recurring: bool, sprints: ["2026-W46", ...], created, doneAt, checkins: [{date, result: "avance"|"sin-avance"|"bloqueada"|"terminada", note}]}`
- Colección `inbox`: `{text, created, source: "texto"|"voz", processed: bool}`.

## Cuando el usuario pase texto o audio
1. Extraer tareas concretas (verbo + objeto), una por documento en `tasks`.
2. Asignar área/proyecto, prioridad y fecha si se menciona. Preguntar si falta algo crítico (fecha límite de impuestos, etc.).
3. Marcar como `processed: true` las capturas de `inbox` ya convertidas.
4. Guardar notas o documentación relevante en la carpeta PARA que corresponda.

## Check-in y revisión semanal
- Diario: preguntar por cada tarea en `semana`/`haciendo` si hubo avance; registrar en `checkins`.
- Semanal (sprint lunes a domingo): escribir `segundo-cerebro/revisiones/AAAA-Wnn.md` con comprometidas, hechas, % cumplimiento, arrastradas, bloqueos y plan siguiente.
