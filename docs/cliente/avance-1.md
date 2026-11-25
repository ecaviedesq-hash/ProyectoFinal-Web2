# Avance 1 · Preguntas para el cliente

**Proyecto:** herramienta para organizar al staff del Interact2Hack
**Integrantes:** Mateo Sarango y Esteban Caviedes
**Actualizado:** 24 de noviembre de 2026

Este documento es el del Avance 1, completado para el Avance 2. La columna «Respuesta del cliente» del archivo original llegó vacía: no hay una cita textual de la sesión que contradiga o confirme cada supuesto. Para no dejar el producto ambiguo, el equipo **adopta el supuesto** como decisión de trabajo y lo marca `[SUPUESTO]`, pendiente de validar con el cliente en el Avance 3. Si la sesión dijo otra cosa, se cambia aquí primero y después en el PRD.

## 1. Lo que entendimos

La herramienta ayuda a organizar al staff durante el Interact2Hack. Los administradores crean tareas en forma de checklist y las asignan a uno o varios estudiantes. Cada estudiante entra con su cuenta, ve sus tareas, marca los pasos que completa y confirma la tarea al terminar. El administrador revisa en un tablero qué tareas están cumplidas, pendientes o próximas a vencer.

En un día del hackathon, el administrador prepara las tareas de la mañana y las asigna; el staff las ejecuta durante el evento desde su dispositivo; el administrador monitorea el avance y detecta a tiempo lo que se retrasa. Así se sabe en todo momento quién hizo qué.

Esa comprensión no es un supuesto: es el encargo. Las reglas que salen de aquí se trazan como «comprensión del encargo».

## 2. Preguntas, supuestos y decisión de trabajo

### P-01 · Usuarios y perfiles · Alta

**Pregunta.** Si se elimina a un estudiante que tiene tareas asignadas sin completar, ¿qué pasa con esas tareas: quedan sin responsable, se reasignan solas o se cancelan?

**Por qué importa.** Define si hace falta reasignación y qué pasa con el historial de cumplimiento.

**Supuesto original.** La tarea queda sin responsable, marcada para reasignar, y el historial conserva el nombre del usuario eliminado.

**Respuesta del cliente.** No consta en el documento de la sesión.

**Estado.** Adoptado, pendiente de validar. Decisión de trabajo: si no queda ningún responsable y la tarea no está completada, queda marcada para reasignar. El nombre de quien marcó cada paso se conserva. Si quedan otros responsables, la tarea sigue con ellos (`S-06`, `S-15`).

### P-02 · Acceso · Alta

**Pregunta.** ¿Cómo recibe un estudiante su primera contraseña: la define el administrador, el sistema la genera o él mismo se registra?

**Por qué importa.** Define el flujo de creación de cuentas y quién controla quién entra.

**Supuesto original.** El administrador crea la cuenta y el sistema genera una contraseña temporal.

**Respuesta del cliente.** No consta en el documento de la sesión.

**Estado.** Adoptado, pendiente de validar. Decisión de trabajo: no hay registro propio. La contraseña es temporal y el estudiante la reemplaza la primera vez que entra. Como esta versión no envía avisos, el administrador se la dice en persona (`S-05`).

### P-03 · Acceso · Media

**Pregunta.** Si un estudiante olvida su contraseña en pleno evento, ¿la restablece él o solo un administrador?

**Por qué importa.** Define si hace falta recuperación autónoma o basta una acción del administrador.

**Supuesto original.** Solo el administrador la restablece, porque está presente en el evento.

**Respuesta del cliente.** No consta en el documento de la sesión.

**Estado.** Adoptado, pendiente de validar. El restablecimiento genera otra contraseña temporal.

### P-04 · Tareas y checklist · Alta

**Pregunta.** Si un estudiante ya marcó pasos de una tarea, ¿el administrador todavía puede agregar, quitar o cambiar pasos del checklist?

**Por qué importa.** Define si la tarea se bloquea al iniciar y qué pasa con el progreso ya registrado.

**Supuesto original.** El administrador puede editar, pero los pasos ya completados se conservan.

**Respuesta del cliente.** No consta en el documento de la sesión.

**Estado.** Adoptado, pendiente de validar. Decisión de trabajo: puede agregar pasos y puede editar o quitar solo pasos que nadie ha marcado. Un paso marcado no se reescribe ni se elimina (`S-04`).

### P-05 · Tareas y checklist · Media

**Pregunta.** ¿Los pasos deben completarse en orden, o el estudiante puede marcarlos en cualquier orden?

**Por qué importa.** Cambia la pantalla de ejecución y las reglas de validación.

**Supuesto original.** Se pueden marcar en cualquier orden.

**Respuesta del cliente.** No consta en el documento de la sesión.

**Estado.** Adoptado, pendiente de validar.

### P-06 · Asignación · Alta · Pregunta clave

**Pregunta.** Si una tarea tiene tres responsables, ¿el checklist es uno compartido, donde cualquiera marca pasos, o cada responsable completa el suyo?

**Por qué importa.** Cambia el modelo de la tarea y lo que ve cada estudiante.

**Supuesto original.** El checklist es compartido y cada paso registra quién lo marcó.

**Respuesta del cliente.** No consta en el documento de la sesión.

**Estado.** Adoptado, pendiente de validar. Decisión de trabajo: hay una sola confirmación de la tarea, hecha por cualquiera de los responsables cuando todos los pasos están marcados (`S-01`, `S-02`).

### P-07 · Ejecución y estados · Media

**Pregunta.** Cuando un estudiante confirma una tarea y se da cuenta de que se equivocó, ¿puede reabrirla o solo el administrador puede hacerlo?

**Por qué importa.** Define si «completada» es definitivo y qué estados de retroceso existen.

**Supuesto original.** Solo el administrador puede reabrir una tarea confirmada.

**Respuesta del cliente.** No consta en el documento de la sesión.

**Estado.** Adoptado, pendiente de validar. Antes de confirmar, un responsable puede desmarcar un paso (`S-03`).

### P-08 · Tablero de cumplimiento · Alta

**Pregunta.** ¿Cuánto tiempo antes de la hora límite una tarea debe aparecer como «próxima a vencer»: un tiempo fijo, un porcentaje de su duración o lo define el administrador en cada tarea?

**Por qué importa.** El documento usa el término sin definirlo; afecta alertas y filtros del tablero.

**Supuesto original.** Un tiempo fijo de 30 minutos para todas las tareas.

**Respuesta del cliente.** No consta en el documento de la sesión.

**Estado.** Adoptado, pendiente de validar.

### P-09 · Vencimientos · Alta · Pregunta clave

**Pregunta.** Cuando una tarea llega a su hora límite con pasos pendientes, ¿queda vencida pero se puede seguir completando, o se bloquea?

**Por qué importa.** Define el estado «vencida» y si el estudiante puede actuar después del límite.

**Supuesto original.** Se marca como vencida, pero se puede seguir completando y se registra la hora real.

**Respuesta del cliente.** No consta en el documento de la sesión.

**Estado.** Adoptado, pendiente de validar. Si se confirma después de la hora límite, la tarea queda completada y el texto indica que fue después de la hora límite. No es un estado distinto.

### P-10 · Contexto de uso · Alta

**Pregunta.** Si el wifi del evento se cae mientras un estudiante marca pasos, ¿puede seguir trabajando y guardar al volver la conexión, o basta un aviso?

**Por qué importa.** Define cuánta tolerancia a fallos necesita el producto en el evento.

**Supuesto original.** Se muestra un aviso y los cambios no se guardan hasta que haya conexión.

**Respuesta del cliente.** No consta en el documento de la sesión.

**Estado.** Adoptado, pendiente de validar. No hay cola de cambios sin conexión.

### P-11 · Marca y diseño · Media

**Pregunta.** ¿El Interact2Hack tiene una identidad visual que debamos seguir, o podemos proponerla nosotros?

**Por qué importa.** Determina si el brand board parte de una marca existente o de cero.

**Supuesto original.** Proponemos una identidad propia inspirada en el evento.

**Respuesta del cliente.** No consta en el documento de la sesión.

**Estado.** Adoptado, pendiente de validar (`S-08`). El tablero «Señal Neón» y las fuentes Big Shoulders Display y Sora pertenecen al brief del sitio oficial 2027 (Desarrollo Web 1). Esta herramienta no los copia enteros: se inspira en el evento y define su propio sistema en `DESIGN.md`.

### P-12 · Alcance · Media

**Pregunta.** ¿Los estudiantes deben recibir avisos (al asignarles una tarea o cuando esté por vencer), o eso queda fuera de esta versión?

**Por qué importa.** Define si las notificaciones entran al alcance.

**Supuesto original.** Fuera de alcance: el estudiante ve sus tareas al entrar al sistema.

**Respuesta del cliente.** No consta en el documento de la sesión.

**Estado.** Adoptado, pendiente de validar. Queda en «Won't» de esta versión.

## 3. Las tres preguntas clave

Se plantean primero, en este orden.

| Id | Por qué es clave |
| --- | --- |
| P-06 | Define cómo se comparte un checklist entre varios responsables y cambia el modelo de la tarea. |
| P-09 | Define qué pasa con una tarea vencida y si el estudiante puede seguir actuando. |
| P-01 | Define qué pasa con las tareas y el historial cuando se elimina a un usuario. |
