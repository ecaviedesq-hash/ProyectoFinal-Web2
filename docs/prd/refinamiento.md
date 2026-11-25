# Refinamiento del PRD

**Fecha:** 24 de noviembre de 2026 · **Equipo:** Mateo Sarango y Esteban Caviedes

Revisión del PRD buscando reglas ambiguas, casos borde y contradicciones, antes de cerrar la versión 1.0. Lo aceptado quedó escrito en el PRD. Lo rechazado no entra.

## Los tres huecos más graves

Son los tres que, si se quedaban abiertos, hacían que el Avance 3 construyera otro producto. Los demás hallazgos de abajo cambian un detalle. Estos cambian el modelo.

### 1. Cuántas veces se confirma una tarea con varios responsables

**Qué decía el PRD.** El borrador heredaba dos frases a la vez. La comprensión del encargo decía que cada estudiante confirma la tarea al terminar. P-06 decía que el checklist es uno solo, compartido, y que cada paso guarda quién lo marcó. R8 todavía no existía: no había una frase que dijera si «completada» ocurre una vez o una vez por persona.

**Por qué era un problema.** Con tres responsables, un agente puede construir tres confirmaciones o una. Si son tres, el tablero no sabe cuándo la tarea está cumplida. Si es una, y el texto sigue diciendo «cada estudiante confirma», el otro agente hace lo contrario. Es el hueco de la pregunta clave P-06.

**Cómo quedó.** Hay una sola confirmación por tarea. La hace cualquiera de los responsables, solo cuando todos los pasos vigentes están marcados, y se guarda quién confirmó y la hora real (R8, S-01, S-02).

**Quién lo encontró.** La IA, al cruzar la comprensión del encargo con P-06. El equipo aceptó el cierre.

### 2. «Por reasignar» podía tapar el atraso, y borrar a una persona podía soltar a las otras

**Qué decía el PRD.** P-01, tal como lo adoptó el borrador, decía una sola cosa: si se elimina a un estudiante, la tarea queda sin responsable, marcada para reasignar, y el historial conserva su nombre. No decía qué pasa si esa persona era una de tres. No decía si «por reasignar» sustituye a pendiente, próxima a vencer o vencida. No decía qué pasa si la tarea ya estaba completada y después se borra la cuenta.

**Por qué era un problema.** El administrador mira el tablero para ver lo atrasado. Si «por reasignar» reemplaza a «vencida», deja de ver que además ya se pasó la hora. Si al eliminar a uno se sueltan los otros dos, una baja de staff desarma tareas que alguien más sigue haciendo. Si una tarea ya cumplida pasa a por reasignar, el historial de cumplimiento se reabre solo. Es el hueco de la pregunta clave P-01.

**Cómo quedó.** Si quedan otros responsables, la tarea sigue con ellos (R13, S-06). «Por reasignar» se muestra junto al estado de tiempo, no en su lugar (R14, S-07). Una tarea completada no pasa a por reasignar: sigue completada y conserva los nombres (R14, S-15).

**Quién lo encontró.** La IA, al probar el caso de tres responsables, el caso vencida y el caso ya completada. El equipo aceptó los tres cierres.

### 3. «No se guarda hasta que haya conexión» se leía como una cola offline

**Qué decía el PRD.** P-10 decía que, si se cae el wifi, se muestra un aviso y los cambios no se guardan hasta que haya conexión. El borrador todavía no tenía R17. La frase «hasta que haya conexión» no decía si el cambio espera en el celular o si hay que marcarlo otra vez.

**Por qué era un problema.** Una cola offline es otro producto: el estudiante cree que el paso ya quedó, el tablero sigue desactualizado, y al volver el wifi aparecen marcas que nadie ve en el momento. El supuesto de P-10 pedía lo contrario, un aviso y no guardar, pero la redacción alcanzaba para construir la cola. Cambia el alcance y el comportamiento en el evento.

**Cómo quedó.** Sin conexión, el aviso dice que ese cambio no se guardó y hay que repetirlo cuando vuelva el wifi. La pantalla vuelve al último dato guardado. No se acumulan cambios (R17). La cola quedó rechazada (Z-06).

**Quién lo encontró.** La IA, al leer «hasta que haya conexión» como una sincronización pendiente. El equipo aceptó que no hay cola.

## Aceptado

| Id | Hallazgo | Decisión |
| --- | --- | --- |
| A-01 | «Confirma la tarea al terminar» no decía si hacen falta todos los pasos. | Hacen falta todos (S-01, R8). |
| A-02 | Con tres responsables, «cada estudiante confirma» chocaba con el checklist compartido de P-06. | Una sola confirmación, de cualquier responsable (S-02, R8). |
| A-03 | P-07 cierra la reapertura, pero no decía si un paso se puede desmarcar antes de confirmar. | Sí se puede, y queda quién y a qué hora (S-03, R5). |
| A-04 | «Los pasos ya completados se conservan» podía leerse como «se pueden borrar si se copia el texto». | No se editan ni se eliminan (S-04, R7). |
| A-05 | P-01 no decía qué pasa si la tarea tenía tres responsables y se elimina solo a uno. | Sigue con los otros. Por reasignar solo si no queda nadie (S-06, R13). |
| A-06 | Por reasignar y vencida podían pisarse. | Se muestran los dos (S-07, R14). |
| A-07 | Una tarea ya completada podía quedar «por reasignar» si después se borra la cuenta. | No. Sigue completada, con los nombres del historial (S-15, R14). |
| A-08 | «Contraseña temporal» no decía temporal respecto de qué, y P-12 impide enviarla. | Se cambia al primer ingreso y se dice en persona (S-05, R2). |
| A-09 | Sin hora límite, P-08 no se puede aplicar. | Toda tarea lleva día y hora, en la hora de Quito, y esa hora puede caer al día siguiente (S-10, S-11, R4). |
| A-10 | El administrador de la mesa no podía destrabar un paso si el estudiante no entra. | Puede marcarlo, a su nombre (S-09, R6). |
| A-11 | Completar después de la hora límite podía inventar un sexto estado. | Sigue siendo completada, con el texto «completada después de la hora límite» (R12). |
| A-12 | P-10 podía leerse como «se guarda solo cuando vuelva el wifi», es decir una cola. | No hay cola. El aviso dice que ese cambio no se guardó y hay que repetirlo (R17). |

## Rechazado

| Id | Propuesta | Por qué no |
| --- | --- | --- |
| Z-01 | Un tercer perfil «coordinador», distinto del administrador. | El encargo solo separa a quien organiza y a quien ejecuta. |
| Z-02 | Bloquear la tarea al llegar la hora límite. | Contradice P-09. |
| Z-03 | Obligar el orden de los pasos. | Contradice P-05. |
| Z-04 | Un checklist distinto por cada responsable. | Contradice P-06. |
| Z-05 | Aviso push o correo a los 30 minutos. | Contradice P-12. |
| Z-06 | Cola offline que se envía al volver el wifi. | El supuesto de P-10 dice que el cambio no se guarda. Una cola lo guardaría en el dispositivo y el estudiante creería que ya quedó. |
| Z-07 | Reasignar solo la tarea al eliminar la cuenta, eligiendo a otra persona en automático. | P-01 no nombra un reemplazo automático. La tarea queda marcada para que un administrador decida. |
| Z-08 | Copiar el brandboard «Señal Neón» del sitio oficial como interfaz de esta herramienta. | P-11 deja la identidad al equipo, y ese tablero es de otro producto (S-08). La inspiración se resuelve en `DESIGN.md`, no aquí. |
