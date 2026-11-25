# Crítica de las direcciones

**Fecha:** 24 de noviembre de 2026 · **Equipo:** Mateo Sarango y Esteban Caviedes
**Revisado:** los tres style tiles de `docs/diseno/direcciones/`.
**Elegida:** dirección 3, Turno de piso. El `DESIGN.md` manda sobre el boceto.

No se ejecutó `/impeccable init` ni `/impeccable document`. La crítica de abajo usa las mismas preguntas (contraste, jerarquía, estado que no dependa solo del color, área táctil, movimiento, densidad en el evento). El equipo decide; la herramienta no.

## Por qué esta y no las otras

**Señal neón** se siente como el sitio público: de noche, con glow y con Big Shoulders Display. En un pasillo de día el fondo `#0B0612` refleja la pantalla, el morado se usa a la vez como marca y como estado, y «próxima a vencer» en magenta compite con el acento. Sirve para un afiche. No para una lista que se mira diez segundos.

**Hoja de llamado** se lee como el referente (hora, responsable, casilla) y separa bien lo atrasado. En el celular, la monoespaciada a 14 px cansa, el papel crema baja el contraste de los sellos rojos, y no hay nada que recuerde que esto es el staff del Interact2Hack. Es una hoja escaneada, no una herramienta que se toca.

**Turno de piso** se queda con la lista clara de la hoja de llamado y con un solo acento tomado del evento (`#5B2BB5`), sobre fondo claro. Los estados tienen color propio, texto e icono. Esa es la dirección.

## Aceptado (entra al DESIGN.md)

| Id | Hallazgo | Qué se hace |
| --- | --- | --- |
| C-01 | Si el morado del evento pinta también un estado, deja de significar «acción». | El acento es solo para la acción principal. Pendiente, próxima, vencida, completada y por reasignar tienen otro color, más la palabra y un icono. |
| C-02 | Big Shoulders Display no se lee en un paso de checklist. | La interfaz usa solo Sora. La display se queda en el sitio público. |
| C-03 | El boceto de la dirección 3 usa ○, ⏳ y ✓. | Prohibido. Cada estado lleva un icono SVG y el nombre del estado. |
| C-04 | Una tarjeta entera pintada del color del estado esconde el título. | El color del estado va en la insignia y en un borde izquierdo de 4 px. El fondo de la tarjeta sigue siendo superficie. |
| C-05 | En el celular, la hora límite tiene que verse sin abrir la tarea. | La tarjeta muestra título, insignia, hora límite y «n de m pasos» antes que el detalle. |
| C-06 | El wifi se cae (R17). Un punto rojo no dice qué hacer. | El aviso trae icono y la frase: el cambio no se guardó y hay que repetirlo cuando haya conexión. |
| C-07 | Marcar un paso con un cuadrito de 16 px falla en el pasillo. | La fila entera es el control y mide al menos 44 px de alto. |
| C-08 | «Por reasignar» en ámbar se confunde con «próxima a vencer». | Lleva su propio par de color, la palabra «Por reasignar» y un icono de persona. Convive con la insignia de tiempo (R14). |
| C-09 | Un pulso animado en lo próximo a vencer depende del movimiento y cansa en un tablero abierto todo el día. | No hay pulso. La urgencia es texto, icono y color. La transición visible dura 120 ms y se apaga si el sistema pide menos movimiento. |
| C-10 | Bajar el cuerpo a 13 px para meter más tareas. | El cuerpo se queda en 16 px. La densidad sale del orden del tablero (R16), no de achicar la letra. |

## Rechazado

| Id | Propuesta | Por qué no |
| --- | --- | --- |
| C-11 | Tema oscuro «porque el hackathon es de noche». | La laptop de la mesa está en un lobby claro y el celular se usa entre salas. El fondo claro se lee en las dos luces. |
| C-12 | Copiar los tokens de «Señal Neón» tal cual. | Ese tablero es del sitio oficial, otro producto (S-08). De ahí se toma el morado como acento y la familia Sora, nada más. |
| C-13 | Botones pastilla, iguales a la insignia. | La insignia es un estado y el botón es una acción. El botón lleva radio de 6 px; la insignia es píldora. |
| C-14 | Emoji como icono de estado. | Se ve distinto en cada teléfono y no tiene un nombre accesible estable. |
