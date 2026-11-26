---
name: auto-model
description: >
  Elige modelo y esfuerzo según la tarea y los aplica a la sesión. Úsalo con
  /auto-model, "elige el modelo", "cambia modelo según la tarea", o al empezar
  una tarea que no es trivial. Nota: solo cambia la configuración de la sesión
  si la herramienta de sesión está disponible.
---

Antes de empezar una tarea, clasifícala y aplica la configuración de la tabla
con `set_session_model` y `set_session_effort` (herramientas de gestión de sesión).

## Tabla

| Tipo de tarea | Modelo | Esfuerzo |
|---|---|---|
| Pregunta simple, resumen corto, formato, traducción | claude-haiku-5-5 | low |
| Edición de texto, cambios pequeños en código, búsquedas | claude-sonnet-5-5 | medium |
| Depuración, refactor, diseño de código o arquitectura | claude-opus-5-5 | high |
| Revisión profunda, seguridad, cambios grandes y ambiguos | claude-opus-5-5 | xhigh |

## Reglas

1. Si la tarea encaja en más de una fila, usa la de esfuerzo más alto.
2. No cambies de modelo a mitad de una tarea; hazlo solo al empezar la siguiente.
3. Si el usuario pide un modelo o esfuerzo concreto, eso gana sobre la tabla.
4. Si no puedes cambiar la configuración de la sesión, dilo en una línea y sigue con la configuración actual.
5. Informa en una línea qué modelo y esfuerzo elegiste y por qué.
