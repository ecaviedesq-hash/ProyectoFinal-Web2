# Turno de piso

**Sistema de diseño** de la herramienta de organización de staff del Interact2Hack.
**Versión:** 1.0 · **Fecha:** 24 de noviembre de 2026 · **Equipo:** Mateo Sarango y Esteban Caviedes
**Manda sobre** el brand board y sobre cualquier boceto de `docs/diseno/direcciones/`. Si algo no coincide, se corrige el tablero, no este archivo.

El producto que viste está en `docs/prd/PRD.md`. Este archivo dice cómo se ve y cómo se comporta la interfaz. No elige framework ni librería de componentes.

## 1. Nombre y propósito

**Turno de piso** sirve para que, en el día del hackathon, un administrador lea el tablero en la laptop y un estudiante marque pasos en el celular sin dudar en qué estado está cada tarea.

No decora el evento. Ordena el turno.

## 2. Brief

| | |
| --- | --- |
| Personalidad | **Directo, legible, en turno.** |
| Referente | La hoja de llamado de un evento en vivo: hora, responsable y una casilla. |
| Quién y dónde | El administrador, en la laptop de la mesa de staff. El estudiante, con el celular en el pasillo, con prisa y con el wifi del evento. |

El brief completo está en `docs/diseno/brief.md`. Lo escribió el equipo.

## 3. Decisiones y porqué

Se eligió la dirección 3 frente a «Señal neón» y «Hoja de llamado». La crítica está en `docs/diseno/criticas/critica-direccion.md`.

1. **Fondo claro.** La mesa de staff y el pasillo no son una sala oscura. Un fondo noche se lee peor con luz de día (C-11).
2. **Un solo acento, el morado del evento `#5B2BB5`.** Es el color de la acción principal (confirmar, guardar, entrar). No pinta ningún estado de tarea: si lo hiciera, «acción» y «estado» serían la misma señal (C-01, C-12).
3. **Una sola familia: Sora.** Es la fuente de texto del evento y se lee a 16 px. Big Shoulders Display se queda en el sitio público (C-02).
4. **Cinco señales de tarea, nunca solo color.** Pendiente, próxima a vencer, vencida, completada y por reasignar. Cada una tiene palabra, icono y un par de color propio. Los nombres son los del PRD (R10, R14).
5. **La tarjeta no se rellena del color del estado.** El color va en la insignia y en un borde izquierdo de 4 px. El título queda en texto principal (C-04).
6. **Por reasignar se suma al estado de tiempo.** Una tarea vencida y sin responsable lleva las dos insignias (R14, C-08).
7. **La fila del checklist es el control.** Alto mínimo 44 px. El paso marcado dice quién y a qué hora (R5, C-07).
8. **El botón no es una píldora.** Radio de 6 px, para no confundirlo con la insignia (C-13).
9. **Sin pulso y sin emoji.** La urgencia es texto. El movimiento dura 120 ms y desaparece si la persona pidió menos movimiento (C-03, C-09, C-14).
10. **La identidad es de esta herramienta** (P-11, S-08). Inspirada en el evento, no copiada del brandboard «Señal Neón».

## 4. Qué tiene que cubrir

| Perfil del PRD | Lo que la interfaz tiene que mostrar |
| --- | --- |
| Estudiante, celular | Lista de sus tareas, tarjeta con estado y hora límite, checklist a medio completar, confirmar, aviso de que no hay conexión. |
| Administrador, laptop | Tablero con indicadores y el orden de R16, insignias, formulario de tarea, reabrir, cuenta y contraseña. |

## 5. Tokens

Un valor nuevo no se inventa en una pantalla. Si falta un rol, se agrega aquí primero y después en el brand board.

### 5.1 Color

Contraste calculado con la fórmula de luminancia relativa de WCAG 2.2. El texto va a 4.5:1 o más. El borde de un control va a 3:1 o más contra la superficie que toca.

| Token | Hex | Rol | Contraste |
| --- | --- | --- | --- |
| `--color-fondo` | `#F3F1F7` | Fondo de la página | — |
| `--color-superficie` | `#FFFFFF` | Tarjetas, filas, campos | — |
| `--color-superficie-alta` | `#E8E4F2` | Fondo de apoyo, esqueleto de carga | — |
| `--color-borde` | `#D9D4E4` | Separador de tarjeta. No es el borde de un control. | — |
| `--color-borde-control` | `#6E6880` | Borde de campo, casilla y botón secundario | 5.31:1 sobre superficie · 4.74:1 sobre fondo · 4.25:1 sobre superficie alta |
| `--color-texto` | `#1A1523` | Texto principal | 17.87:1 sobre superficie · 15.94:1 sobre fondo · 14.30:1 sobre superficie alta |
| `--color-texto-suave` | `#5C5670` | Hora, ayuda, meta | 6.95:1 sobre superficie · 6.20:1 sobre fondo · 5.57:1 sobre superficie alta |
| `--color-acento` | `#5B2BB5` | Acción principal y anillo de foco | 8.54:1 del texto blanco sobre el acento · 7.62:1 del acento sobre el fondo |
| `--color-sobre-acento` | `#FFFFFF` | Texto del botón primario | 8.54:1 sobre el acento |

Estados de una tarea. El primer color es el texto y el icono; el segundo es el fondo de la insignia. El par cumple 4.5:1.

| Token de texto | Token de fondo | Estado del PRD | Hex | Contraste del par | También sobre superficie |
| --- | --- | --- | --- | --- | --- |
| `--color-pendiente` | `--color-pendiente-fondo` | Pendiente | `#1E4E8C` / `#E4EEF8` | 7.09:1 | 8.32:1 |
| `--color-proxima` | `--color-proxima-fondo` | Próxima a vencer | `#8A5A00` / `#FCF0D6` | 5.24:1 | 5.93:1 |
| `--color-vencida` | `--color-vencida-fondo` | Vencida | `#B42318` / `#FDE7E5` | 5.55:1 | 6.57:1 |
| `--color-completada` | `--color-completada-fondo` | Completada | `#276B43` / `#E4F3EA` | 5.60:1 | 6.42:1 |
| `--color-reasignar` | `--color-reasignar-fondo` | Por reasignar | `#7A3E12` / `#F8E8DC` | 6.96:1 | 8.32:1 |

El texto de error del formulario usa `--color-vencida` (6.57:1 sobre superficie). No se crea un rojo nuevo.

### 5.2 Tipografía

| Token | Valor |
| --- | --- |
| `--fuente-texto` | `"Sora", system-ui, sans-serif` |
| Título | 28 px / 34 px · peso 700 |
| Sección | 20 px / 26 px · peso 700 |
| Cuerpo | 16 px / 24 px · peso 400 |
| Pequeño | 14 px / 20 px · peso 400. La insignia y el pequeño en negrita usan peso 700. |

No hay segunda familia. No se baja de 14 px.

### 5.3 Espaciado

Escala de 4 px. Solo estos pasos: `--espacio-1` 4 · `--espacio-2` 8 · `--espacio-3` 12 · `--espacio-4` 16 · `--espacio-5` 24 · `--espacio-6` 32 · `--espacio-7` 48 · `--espacio-8` 64.

### 5.4 Radios, tacto y movimiento

| Token | Valor | Uso |
| --- | --- | --- |
| `--radio-control` | 6 px | Botón y campo |
| `--radio-tarjeta` | 10 px | Tarjeta, panel, aviso |
| `--radio-insignia` | 999 px | Insignia de estado |
| `--alto-tactil` | 44 px | Botón, campo y fila de checklist |
| `--duracion` | 120 ms | Solo color de fondo o de borde |
| `--borde-estado` | 4 px | Borde izquierdo de la tarjeta, del color del estado de tiempo |

Si el sistema pide menos movimiento (`prefers-reduced-motion`), `--duracion` pasa a 0 ms. No hay animación de entrada, pulso ni desplazamiento.

## 6. Componentes y estados

Los textos de ejemplo son del staff del evento. Las fechas son de muestra: el cliente no fijó el calendario 2027.

### 6.1 Tarjeta de tarea

Siempre muestra, en este orden: insignia o insignias, título, hora límite, responsables y «n de m pasos».

| Estado | Qué se ve |
| --- | --- |
| Pendiente | Insignia «Pendiente» y borde izquierdo pendiente. Ejemplo: Abrir la sala de pitch, hasta el 18 abr 2027 09:00, 2 de 3 pasos. |
| Próxima a vencer | Insignia «Próxima a vencer» y borde de ese color. Ejemplo: Recibir al jurado en la entrada principal, hasta el 18 abr 2027 08:30. |
| Vencida | Insignia «Vencida». La hora límite también va en color vencida, además de la insignia. Ejemplo: Reponer el agua de la sala de mentores, hora límite 18 abr 2027 07:30. |
| Completada | Insignia «Completada», más quién confirmó y la hora real. Si fue tarde, el texto «completada después de la hora límite» (R12). Ejemplo: Entregar kits de bienvenida al staff, Andrés Vela, 07:15. |
| Por reasignar | Segunda insignia «Por reasignar», junto a la de tiempo. Ejemplo: una tarea vencida y sin responsable. |
| Sin tareas | Título y una frase. No es una tarjeta vacía de color. |

En el celular la tarjeta ocupa el ancho útil. No pide scroll horizontal.

### 6.2 Ítem de checklist

| Estado | Qué se ve |
| --- | --- |
| Sin marcar | Casilla vacía con borde de control, el texto del paso y «Sin marcar». |
| Marcado | Casilla con visto, el texto del paso, el nombre y la hora. Ejemplo: «Probar micrófono y proyector. Marcado por Camila Ruiz, 07:55». |
| Lista a medias | Los dos estados anteriores en la misma tarea, más «2 de 3 pasos» en la tarjeta. |

La fila entera recibe el toque o el clic. Desmarcar solo existe si la tarea no está completada (R5).

### 6.3 Insignia de estado

Píldora con icono SVG y el nombre exacto del estado: Pendiente, Próxima a vencer, Vencida, Completada, Por reasignar. El icono es decorativo si el texto ya está; el texto no se esconde.

### 6.4 Formulario

Cada campo tiene etiqueta visible. El alto del control es al menos 44 px.

| Estado | Qué se ve |
| --- | --- |
| En blanco o con valor | Borde de control, texto principal. |
| Error | Borde en color vencida, más el mensaje en color vencida. El borde no es el único aviso. Ejemplo: «Escribe la hora límite. Sin ella no se sabe cuándo vence.» |
| Deshabilitado | No se usa para un paso ya marcado: ese paso se muestra como texto, no como campo bloqueado pintado de gris. |

### 6.5 Botón

| Estado | Qué se ve |
| --- | --- |
| Primario | Fondo acento, texto sobre acento. Una acción por bloque: Confirmar tarea, Guardar tarea, Entrar. |
| Secundario | Fondo superficie, texto acento, borde de control. Ejemplo: Reasignar, Ver tarea. |
| Peligro | Fondo superficie, texto y borde en color vencida. Ejemplo: Eliminar cuenta. Pide confirmación antes de borrar. |
| Deshabilitado | El primario baja a 50 % de opacidad y no recibe el clic. Al lado, el motivo en texto. Ejemplo: «Falta un paso por marcar.» |
| Foco | Anillo de 3 px en color acento, separado 2 px del control. No se quita. |

### 6.6 Aviso

Icono más frase. Borde izquierdo de 4 px. No sustituye a la insignia de la tarea.

| Tipo | Uso | Ejemplo |
| --- | --- | --- |
| Éxito | Una acción ya guardada | «Tarea confirmada. Entregar kits de bienvenida al staff quedó completada.» |
| Advertencia | Próxima a vencer, dentro de la tarea | «Faltan menos de 30 minutos para la hora límite.» |
| Error | No se pudo hacer | «No hay conexión. Este cambio no se guardó. Márcalo de nuevo cuando vuelva el wifi.» |
| Información | Algo que conviene saber y no es un fallo | «La contraseña temporal se cambia la primera vez que entras.» |

### 6.7 Indicador del tablero

Un número en 28 px y, debajo, el nombre del grupo. El número usa el color de ese estado y las palabras también: no es un recuadro de color solo.

El orden de lectura sigue a R16: por reasignar, vencidas, próximas a vencer, pendientes, completadas. Si el número es 0, el texto dice «Ninguna» más el nombre («Ninguna vencida»), para que el cero no dependa del color.

## 7. Accesibilidad

- Texto a 4.5:1 como mínimo. Los pares y sus cifras están en la sección 5.1.
- Borde de control a 3:1 como mínimo. `#6E6880` da 5.31:1 sobre blanco.
- Foco visible: anillo de 3 px `#5B2BB5` (7.62:1 sobre el fondo, 8.54:1 sobre blanco), offset 2 px, en botones, campos, filas y enlaces.
- Área táctil mínima: 44 × 44 px.
- El estado no depende solo del color: hay palabra e icono. La hora de una tarea vencida se repite en color vencida y en la insignia.
- El aviso de conexión usa `role="alert"`. El de éxito usa `role="status"`.
- La primera vez que entra, el estudiante puede cambiar la contraseña sin leer un texto de 12 px: la ayuda va a 14 px.

## 8. Reglas para el agente

Al construir la interfaz, el agente **debe**:

- Usar los nombres de estado del PRD, escritos igual: Pendiente, Próxima a vencer, Vencida, Completada, Por reasignar.
- Mostrar en cada paso marcado el nombre de la persona y la hora.
- Mostrar «n de m pasos» cuando el checklist no está vacío.
- Poner el aviso de sin conexión con la frase de la sección 6.6, no un punto de color.
- Mantener el orden del tablero de R16.
- Dejar el foco visible y las áreas de 44 px.
- Escribir la interfaz en español.

El agente **no debe**:

- Agregar colores, fuentes, radios o sombras que no estén en la sección 5.
- Usar el morado de acento como color de un estado.
- Usar emoji como icono de estado, de error o de carga.
- Animar un pulso en lo próximo a vencer, ni mover tarjetas al aparecer.
- Esconder el texto de una insignia y dejar solo el color.
- Instalar una librería de componentes o un kit visual para «resolver» estos tokens.
- Copiar el brandboard del sitio público del evento.
- Inventar un sexto estado para «completada con retraso»: es el texto de R12 sobre la insignia Completada.
- Mostrarle a un estudiante el tablero general ni las tareas de otra persona.

## 9. Criterios verificables

| Id | Criterio | Cómo se comprueba |
| --- | --- | --- |
| D-01 | Los colores de la interfaz son los tokens de la sección 5.1. | Se buscan hexadecimales en la pantalla y todos aparecen en esa tabla. |
| D-02 | La única familia es Sora. Título 28/34, sección 20/26, cuerpo 16/24, pequeño 14/20. | Se inspecciona el estilo computado de un título, una tarjeta, un cuerpo y una meta. |
| D-03 | Cada estado de tarea usa su insignia con icono y el nombre del PRD. | Se abre una pendiente, una próxima a vencer, una vencida, una completada y una por reasignar. |
| D-04 | Por reasignar no reemplaza al estado de tiempo. | Una tarea sin responsable y vencida muestra las dos insignias. |
| D-05 | La tarjeta no rellena el fondo con el color del estado. El color está en la insignia y en el borde izquierdo de 4 px. | Se mira el fondo computado de la tarjeta: es `--color-superficie`. |
| D-06 | Un checklist a medias muestra pasos marcados (nombre y hora), pasos sin marcar y el texto «n de m pasos». | Se usa la tarea «Abrir la sala de pitch», 2 de 3. |
| D-07 | La fila de checklist y los botones miden al menos 44 px de alto. | Se mide la caja del control. |
| D-08 | El botón primario es acento con texto blanco. El de peligro usa el color vencida en texto y borde, sobre superficie. | Se comparan Confirmar tarea y Eliminar cuenta. |
| D-09 | Un campo con error tiene mensaje en `--color-vencida`, no solo el borde. | Se envía una tarea sin hora límite. |
| D-10 | El aviso de sin conexión trae icono y dice que el cambio no se guardó. | Se corta la conexión y se marca un paso. |
| D-11 | El indicador del tablero tiene número y nombre del grupo. El cero dice «Ninguna» más el nombre. | Se mira el grupo con cero y el grupo de vencidas. |
| D-12 | El orden visual del tablero es por reasignar, vencidas, próximas, pendientes, completadas. | Se lee la lista de arriba a abajo. |
| D-13 | El foco se ve como anillo de 3 px en `--color-acento`. | Se recorre con teclado un botón, un campo y una fila. |
| D-14 | Con menos movimiento, la duración es 0 ms y no hay pulso. | Se activa `prefers-reduced-motion: reduce` y se cambia un estado. |
| D-15 | A 390 px de ancho, la tarjeta del estudiante no genera scroll horizontal. | Se estrecha el viewport a 390 px y se recorre la lista. |
| D-16 | No hay emoji de estado ni un sexto estado para lo completado tarde. | Lo completado tarde dice «completada después de la hora límite» junto a la insignia Completada. |

El tablero visual está en `docs/diseno/brand-board.html`.
