---
name: mejorar-preguntas
description: Convierte automáticamente solicitudes de desarrollo web en prompts técnicos basados en el proyecto y aplícalos en el mismo turno. Úsala para crear o corregir sitios, aplicaciones web y APIs, diagnosticar bugs, revisar seguridad defensiva o mejorar un prompt a petición del usuario.
---

# Mejorar preguntas

Antes de responder a un encargo web, formúlalo internamente como una tarea técnica. Conserva la intención, el formato, el idioma y el alcance autorizado. Si el usuario pide mejorar un prompt sobre otro tema, aplica las mismas reglas de precisión con un rol y un entregable pertinentes a ese tema.

## Formula el encargo web

1. Define el resultado y el flujo afectado. Elige el rol por el trabajo que hará, como frontend para un fallo de renderizado, backend para un contrato de API o revisor de seguridad para una política de acceso. En una corrección, precisa qué comportamiento se debe recuperar y cuáles se deben conservar.
2. Si el encargo se refiere a un proyecto disponible, lee sus instrucciones y consulta la evidencia mínima para situarlo. Usa el manifiesto y el archivo de bloqueo para confirmar stack y versiones cuando sean relevantes. Localiza los archivos, rutas, componentes, servicios, pruebas o configuraciones que gobiernan el flujo y los comandos que el proyecto ya usa para verificarlo.
3. Pide acciones concretas sobre ese contexto. Cada instrucción debe apuntar a un archivo, un flujo, un contrato o un resultado observable. En un proyecto nuevo, parte de los requisitos de producto y justifica las decisiones de stack que afecten la entrega. Si falta información, usa supuestos reversibles identificados o indica el dato que permitiría comprobar la hipótesis. Haz una pregunta enfocada solo si esa decisión bloquea el trabajo.
4. Incluye una comprobación de que el flujo principal funciona y una regresión pertinente cuando propongas un cambio. Si el flujo toca un límite de confianza, como datos del navegador que llegan al servidor o permisos entre cuentas, incluye el control defensivo aplicable y cómo verificarlo.

## Ajusta el prompt al tipo de trabajo

- **Interfaz y funcionalidades**. Especifica qué puede hacer el usuario y qué verá. Reutiliza los componentes y convenciones existentes. Considera móvil, teclado y estados de carga, vacío o error cuando formen parte del flujo.
- **API y datos**. Identifica el contrato y quienes lo consumen. Fija la validación, las transiciones de estado y el comportamiento ante errores o reintentos cuando sean relevantes. Incluye cómo comprobar compatibilidad con los consumidores actuales.
- **Bugs y rendimiento**. Consulta [Diagnóstico de bugs web](references/diagnostico-de-bugs.md). Incorpora el síntoma, las hipótesis que vale la pena comprobar, la evidencia para decidir y la prueba de regresión al prompt.
- **Seguridad defensiva**. Consulta [Revisión de seguridad web](references/seguridad-web.md) ante una revisión de seguridad o un cambio en autenticación, permisos, datos sensibles, entradas externas o configuración expuesta. Incluye los controles afectados, la evidencia esperada y la validación de las correcciones.

## Entrega el resultado

- Por defecto, aplica el prompt y entrega el trabajo pedido en el mismo turno. Para una implementación, usa el punto de entrada habitual del proyecto y reporta el resultado de las verificaciones relevantes. Para un diagnóstico o una revisión, entrega los hallazgos con su evidencia y la corrección propuesta.
- Si te piden únicamente el prompt, usa lo aportado y el contexto del proyecto que te hayan pedido consultar. Devuélvelo listo para copiar y formula las comprobaciones como tareas pendientes. Si te piden el prompt y la solución, muestra el prompt antes del resultado. Incorpora los seguimientos al encargo en curso y conserva las restricciones explícitas del usuario.

## Ejemplo

**Pregunta** «Mi web se queda cargando después de iniciar sesión».

**Prompt reformulado** «Actúa como ingeniero full-stack y diagnostica por qué la interfaz sigue cargando tras iniciar sesión. Identifica el stack en el proyecto y sigue el envío del formulario, la respuesta de autenticación, la creación de la sesión y la redirección. Localiza en el código o los registros el primer paso que se desvía de lo esperado. Corrige la causa y comprueba un inicio correcto y uno fallido. Verifica con una prueba local de autorización que las rutas privadas siguen exigiendo una sesión válida».
