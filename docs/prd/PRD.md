# PRD · Staff del Interact2Hack

**Versión:** 1.0 · **Fecha:** 24 de noviembre de 2026 · **Equipo:** Mateo Sarango y Esteban Caviedes
**Fuente:** comprensión del encargo y decisiones de trabajo del Avance 1 (`docs/cliente/avance-1.md`)

Este documento describe **qué** debe hacer la herramienta de organización de staff y **qué no**. No describe cómo se construye: tecnologías, datos y pantallas se deciden en las specs. El sistema de diseño vive en `DESIGN.md`.

## 1. Problema y contexto

Durante el Interact2Hack, el staff (estudiantes que apoyan el evento) ejecuta decenas de tareas cortas: abrir una sala, probar un micrófono, recibir al jurado, reponer agua, actualizar el cronograma de la pared. Hoy eso se reparte de boca en boca o en un chat que se pierde. Por eso:

- El administrador no sabe, a mitad de la mañana, qué ya se hizo y qué se está atrasando.
- Cuando una tarea la comparten varias personas, nadie puede decir quién marcó cada paso.
- Si alguien se va del staff, se pierde el rastro de lo que ya había hecho.

La herramienta se usa el día del evento, no durante las inscripciones. Por la mañana el administrador prepara las tareas y las asigna, casi siempre desde una laptop en la mesa de staff. Durante el día los estudiantes las ejecutan desde el celular, en pasillos y salas, con prisa y con un wifi que puede caerse. El administrador mira el tablero para ver lo vencido y lo que está a punto de vencerse, y reasigna cuando alguien falta.

## 2. Usuarios y perfiles

| Perfil | Puede | No puede |
| --- | --- | --- |
| **Administrador** | Crear cuentas y restablecer contraseñas. Eliminar a un estudiante. Crear y editar tareas, su hora límite y sus responsables. Marcar y desmarcar pasos. Reabrir una tarea confirmada. Ver el tablero de todas las tareas. | Borrar o reescribir un paso que ya fue marcado. Borrar el nombre de quien marcó un paso. |
| **Estudiante de staff** | Entrar con su cuenta y reemplazar la contraseña temporal la primera vez. Ver solo sus tareas. Marcar y desmarcar pasos de una tarea suya que aún no está completada. Confirmar una tarea suya cuando todos los pasos están marcados. | Ver tareas de otras personas o el tablero general. Crear tareas, editar el checklist, reabrir una tarea, crear cuentas o restablecer contraseñas. Confirmar si falta algún paso. |

Todos entran con usuario y contraseña. No hay registro: las cuentas las crea un administrador (R2). Puede haber más de un administrador, con los mismos permisos (R18).

## 3. Objetivos y cómo se mide el éxito

| Objetivo | Cómo sabrá el cliente que se cumplió |
| --- | --- |
| Saber quién hizo qué | En una tarea se ve qué paso marcó cada persona, a qué hora, y quién la confirmó, sin abrir un chat ni una hoja de cálculo. |
| Detectar a tiempo lo que se atrasa | En el tablero, lo que está sin responsable y lo vencido aparece antes que lo demás, y lo que entra en los últimos 30 minutos se ve como próxima a vencer. |
| Que el staff trabaje desde el celular | Un estudiante marca un paso y confirma una tarea desde el teléfono, sin pedirle al administrador que lo anote. |
| No perder el historial si alguien se va | Al eliminar a un estudiante, los pasos que marcó siguen mostrando su nombre. Si la tarea quedó sin nadie y no está completada, aparece para reasignar. |

## 4. Alcance (MoSCoW)

| Prioridad | Funcionalidad |
| --- | --- |
| **Must** | Inicio de sesión con los dos perfiles. Alta de cuentas, contraseña temporal y restablecimiento. Eliminar un estudiante con la regla de reasignación. Crear y editar tareas con checklist, hora límite y uno o varios responsables. Marcar y desmarcar pasos, ver quién lo hizo, confirmar y reabrir. Lista de tareas del estudiante. Tablero del administrador con los estados y el orden de la sección 6. Aviso cuando no hay conexión y el cambio no se guarda. |
| **Should** | Filtrar el tablero por estado y por responsable. Buscar una tarea por su título. |
| **Could** | Duplicar una tarea ya hecha para el bloque siguiente del día (por ejemplo, reponer agua otra vez por la tarde). |
| **Won't (esta versión)** | Avisos por correo, mensaje o notificación del teléfono (P-12). Seguir trabajando sin conexión (P-10). Registro por cuenta propia. |

## 5. No-alcance

- Avisos al asignar una tarea o cuando está por vencer (P-12). El estudiante se entera al entrar.
- Guardar cambios sin conexión y sincronizarlos después (P-10).
- Que una persona cree su propia cuenta.
- Inscripciones, equipos de participantes, retos, jurado, puntajes, premios y el sitio público del evento.
- Más perfiles que administrador y estudiante de staff.
- Sanciones, multas o asistencia académica.
- Un archivo histórico de ediciones pasadas del hackathon. Esta versión muestra las tareas del evento en curso.
- Exportar el tablero a una hoja de cálculo.

## 6. Reglas de negocio

| Id | Regla |
| --- | --- |
| R1 | Hay dos perfiles: **administrador** y **estudiante de staff**, con los permisos de la sección 2. |
| R2 | No hay registro. Solo un administrador crea la cuenta. La herramienta le da una contraseña temporal, que el estudiante reemplaza la primera vez que entra. El administrador se la comunica en persona `[SUPUESTO S-05]`. |
| R3 | Si alguien olvida su contraseña, solo un administrador puede restablecerla. El restablecimiento genera otra contraseña temporal, que también se reemplaza al entrar. |
| R4 | Una tarea tiene título, una hora límite (día y hora, en la hora de Quito) y una lista de pasos. Puede tener cero, uno o varios responsables. Sin título, sin al menos un paso o sin hora límite, no se puede crear `[SUPUESTO S-10]` `[SUPUESTO S-11]` `[SUPUESTO S-14]`. |
| R5 | El checklist es **uno solo y compartido**. Cualquier responsable puede marcar o desmarcar cualquier paso mientras la tarea no esté completada, en cualquier orden. Cada marca y cada desmarca guarda quién lo hizo y a qué hora `[SUPUESTO S-03]`. |
| R6 | Un administrador también puede marcar o desmarcar pasos de una tarea no completada. Queda registrado con su nombre `[SUPUESTO S-09]`. |
| R7 | Mientras la tarea no esté completada, el administrador puede cambiar el título, la hora límite y los responsables. Puede agregar pasos, y puede editar o quitar solo pasos que nadie ha marcado. Un paso ya marcado conserva su texto, quién lo marcó y a qué hora: no se edita ni se elimina `[SUPUESTO S-04]` `[SUPUESTO S-13]`. |
| R8 | La tarea se puede confirmar solo cuando **todos** los pasos vigentes están marcados. La confirma cualquiera de sus responsables. Se guarda quién confirmó y la hora real. Hay una sola confirmación por tarea, no una por persona `[SUPUESTO S-01]` `[SUPUESTO S-02]`. |
| R9 | Solo un administrador puede reabrir una tarea confirmada. Al reabrirla, los pasos siguen como estaban y la tarea vuelve al estado que le toque por la hora límite y por sus responsables. |
| R10 | Una tarea no completada está en uno de estos estados de tiempo. **Pendiente:** falta más de 30 minutos para la hora límite. **Próxima a vencer:** faltan 30 minutos o menos y esa hora todavía no llega. **Vencida:** la hora límite ya pasó. **Completada:** un responsable la confirmó (R8). En el instante de la hora límite deja de ser próxima a vencer y pasa a vencida. |
| R11 | El umbral de «próxima a vencer» es fijo: **30 minutos** para todas las tareas. El administrador no lo cambia por tarea. |
| R12 | Una tarea vencida no se bloquea: se pueden seguir marcando pasos y se puede confirmar. La hora que se guarda es la hora real. Si esa hora es posterior a la límite, la tarea queda **completada** y además muestra el texto «completada después de la hora límite». Eso no es un estado nuevo. |
| R13 | Si se quita o se elimina a un responsable y quedan otros, la tarea sigue con los que quedan `[SUPUESTO S-06]`. Si no queda ninguno y la tarea no está completada, queda **por reasignar**. El historial de cada paso conserva el nombre de quien lo marcó, aunque esa persona ya no tenga cuenta. |
| R14 | «Por reasignar» se muestra **junto** al estado de tiempo (pendiente, próxima a vencer o vencida). No lo reemplaza `[SUPUESTO S-07]`. Una tarea completada no pasa a por reasignar: sigue completada y conserva los nombres `[SUPUESTO S-15]`. |
| R15 | Un estudiante solo ve las tareas en las que es responsable, incluidas las ya completadas del evento en curso. No ve el tablero general ni las tareas ajenas. |
| R16 | El tablero del administrador muestra todas las tareas. El orden es: por reasignar, después vencidas, después próximas a vencer, después pendientes, después completadas. En cada tarea se ven el título, la hora límite, los responsables y el estado. |
| R17 | Si no hay conexión al marcar, desmarcar, confirmar o guardar, la herramienta muestra un aviso y **no guarda** ese cambio. La pantalla vuelve al último dato que sí se guardó. No se acumulan cambios para enviarlos después. |
| R18 | Puede haber más de un administrador. Todos tienen los mismos permisos `[SUPUESTO S-12]`. |
| R19 | Esta versión no envía avisos cuando se asigna una tarea ni cuando está próxima a vencer. |

## 7. Épicas

| Id | Épica | Descripción | Prioridad |
| --- | --- | --- | --- |
| E1 | Acceso y cuentas | Entrada con los dos perfiles, alta de cuentas, contraseña temporal, restablecimiento y eliminación de un estudiante sin borrar el historial de lo que marcó (R1, R2, R3, R13, R18). | Must |
| E2 | Tareas y checklist | El administrador arma tareas con pasos, hora límite y uno o varios responsables, y puede corregirlas sin perder lo ya marcado (R4, R7, R14). | Must |
| E3 | Ejecución del staff | El estudiante, desde el celular, marca pasos en cualquier orden sobre el checklist compartido y confirma la tarea cuando no queda ninguno; el administrador es el único que reabre (R5, R6, R8, R9, R12, R15, R17). | Must |
| E4 | Tablero de cumplimiento | El administrador ve primero lo que está sin responsable o atrasado, y distingue pendiente, próxima a vencer, vencida y completada (R10, R11, R16, R19). | Must |

## 8. Supuestos y puntos abiertos

La columna de respuesta del cliente en el Avance 1 llegó vacía. Cada supuesto de abajo es una decisión del equipo para que la regla no quede ambigua. Todos están pendientes de validar en el Avance 3.

| Id | Supuesto | Por qué lo decidimos así | Estado |
| --- | --- | --- | --- |
| S-01 | Solo se confirma una tarea cuando todos los pasos vigentes están marcados (R8). | Si se pudiera cerrar a medias, «completada» no diría que el checklist terminó. | `[SUPUESTO]` · validar en el Avance 3 |
| S-02 | Hay una sola confirmación por tarea, hecha por cualquier responsable (R8). | P-06 hace el checklist compartido. Una confirmación por persona crearía varios «completada» para el mismo trabajo. | `[SUPUESTO]` · validar en el Avance 3 |
| S-03 | Antes de confirmar, cualquier responsable puede desmarcar un paso (R5). | P-07 solo impide reabrir lo ya confirmado. Un error anterior se corrige desmarcando, y queda registrado. | `[SUPUESTO]` · validar en el Avance 3 |
| S-04 | Un paso ya marcado no se edita ni se elimina (R7). | P-04 pide conservar lo completado. Cambiar el texto dejaría un nombre asociado a un paso distinto. | `[SUPUESTO]` · validar en el Avance 3 |
| S-05 | La contraseña temporal se reemplaza al primer ingreso y se dice en persona (R2). | P-02 la llama temporal, y P-12 impide avisarla por correo o mensaje. | `[SUPUESTO]` · validar en el Avance 3 |
| S-06 | Quitar a uno de varios responsables no deja la tarea sin nadie (R13). | P-01 habla de la tarea que se queda sola. Si queda alguien, el trabajo sigue. | `[SUPUESTO]` · validar en el Avance 3 |
| S-07 | «Por reasignar» se muestra además del estado de tiempo, no en su lugar (R14). | Si lo tapara, el administrador no vería que además ya venció. | `[SUPUESTO]` · validar en el Avance 3 |
| S-08 | La identidad visual la propone el equipo, inspirada en el evento, sin copiar el sitio público. | P-11 dejó la marca al equipo. El tablero «Señal Neón» es del sitio oficial 2027, que es otro producto. | `[SUPUESTO]` · validar en el Avance 3 |
| S-09 | Un administrador puede marcar y desmarcar pasos, a su nombre (R6). | Está en la mesa de staff. Si un estudiante no puede entrar, el paso no se queda bloqueado, y el historial no miente. | `[SUPUESTO]` · validar en el Avance 3 |
| S-10 | Toda tarea tiene día y hora límite (R4). | Sin ese momento, «próxima a vencer» y «vencida» no se pueden decidir. | `[SUPUESTO]` · validar en el Avance 3 |
| S-11 | La hora límite usa la hora de Quito (R4). | El evento es presencial en la USFQ, en Cumbayá. | `[SUPUESTO]` · validar en el Avance 3 |
| S-12 | Puede haber varios administradores con los mismos permisos (R18). | La mesa de staff no es una sola persona durante todo el día. | `[SUPUESTO]` · validar en el Avance 3 |
| S-13 | Mientras la tarea no esté completada se pueden cambiar título, hora límite y responsables (R7). | P-04 ya permite tocar el checklist. La ficha de la tarea sigue la misma regla. | `[SUPUESTO]` · validar en el Avance 3 |
| S-14 | Se puede crear una tarea todavía sin responsables (R4, R13). | Por la mañana el administrador arma la lista antes de saber quién llegó. Esa tarea queda por reasignar. | `[SUPUESTO]` · validar en el Avance 3 |
| S-15 | Una tarea completada no pasa a por reasignar (R14). | El cumplimiento ya quedó. Quitar la cuenta después no reabre el trabajo. | `[SUPUESTO]` · validar en el Avance 3 |

**Puntos abiertos:**

- El cliente no dio las fechas de Interact2Hack 2027. No cambian estas reglas. Los días que aparecen en el brand board son datos de ejemplo.
- No está definido si, al cerrar el evento, las tareas se archivan. En esta versión siguen visibles.
- No está definido un informe descargable del día. Queda fuera (sección 5).

El registro de huecos que se aceptaron o se rechazaron al revisar este PRD está en `docs/prd/refinamiento.md`.

## 9. Trazabilidad

| Regla | Origen |
| --- | --- |
| R1 | Comprensión del encargo (dos perfiles: administrador y estudiante) |
| R2 | P-02 y S-05 |
| R3 | P-03 |
| R4 | Comprensión del encargo, S-10, S-11 y S-14 |
| R5 | P-05, P-06 y S-03 |
| R6 | S-09 |
| R7 | P-04, S-04 y S-13 |
| R8 | Comprensión del encargo («confirma la tarea al terminar»), S-01 y S-02 |
| R9 | P-07 |
| R10 | Comprensión del encargo (pendiente, próxima a vencer, cumplida) y P-09 |
| R11 | P-08 |
| R12 | P-09 |
| R13 | P-01 y S-06 |
| R14 | S-07 y S-15 |
| R15 | Comprensión del encargo («ve sus tareas») |
| R16 | Comprensión del encargo (el tablero) y P-08 |
| R17 | P-10 |
| R18 | S-12 |
| R19 | P-12 |
