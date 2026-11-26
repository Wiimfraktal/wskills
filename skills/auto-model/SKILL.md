---
name: auto-model
description: >
  Ajusta modelo y esfuerzo cuando el prompt indica un proyecto o trabajo pesado.
  Se activa solo si el usuario no eligió modelo y la tarea es un proyecto
  (código, diseño, depuración, documentos largos, varios pasos). Avisa al
  activarse. Úsalo también con /auto-model.
---

## Cuándo se activa

Solo si se cumplen las dos cosas:
1. El usuario no eligió un modelo para la sesión.
2. El prompt indica un proyecto o trabajo pesado: código, depuración, diseño, refactor, documentos largos, o varios pasos.

Si el usuario eligió modelo, o la tarea es momentánea (una pregunta, una traducción, un dato), no hagas nada.

## Al activarse

1. Avisa en una línea: "Auto-model activado: <modelo> / <esfuerzo> por <motivo>".
2. Aplica la configuración con `set_session_model` y `set_session_effort`.
3. Si esas herramientas no están disponibles, dilo en una línea y sigue con la configuración actual.

## Tabla

| Tipo de tarea | Modelo | Esfuerzo |
|---|---|---|
| Edición de texto, cambios pequeños, búsquedas en proyecto | claude-sonnet-5-5 | low |
| Proyecto pequeño, varios pasos simples | claude-haiku-5-5 | low |
| Depuración, refactor, diseño de código | claude-opus-5-5 | medium |
| Proyecto grande, arquitectura, decisiones difíciles | claude-opus-5-5 | high |

Si la tarea encaja en más de una fila, usa la de esfuerzo más alto.

## Reglas

- No cambies de modelo a mitad de una tarea; hazlo solo al empezar la siguiente.
- Si el usuario pide un modelo o esfuerzo concreto después, eso gana.
