# 🎮 VideoGame

Colección de minijuegos web de un solo archivo (HTML + CSS + JavaScript) inspirados en el **principio de Fermat**: la luz, o una pelota, siempre toma el camino más corto o rápido.

| Juego | Descripción | Jugadores |
|---|---|---|
| [Game1 · Trayectoria Óptima](./Game1) | Elige el punto A–G que da el recorrido más corto | 1 |
| [Game3 · Fermat's Light: Co-Op](./Game3) | Guía láseres con espejos hasta el objetivo central | 2 (local) |

## Estructura

```
VideoGame/
├── Game1/
│   ├── index.html                     # Trayectoria Óptima
│   └── README.md
└── Game3/
    └── fermat_s_light_co_op_v3.html   # Fermat's Light: Co-Op (V3)
```

## Ejecutar

Clona el repositorio y abre el HTML del juego en un navegador moderno:

```bash
git clone https://github.com/alextristanc/VideoGame.git
cd VideoGame
```

- **Game1:** abre `Game1/index.html`. Sin dependencias ni conexión.
- **Game3:** abre `Game3/fermat_s_light_co_op_v3.html`. Requiere internet para cargar Tailwind (CDN), Tone.js y la fuente Press Start 2P.

No hace falta servidor ni proceso de build.

---

## Game1 · Trayectoria Óptima

Una pelota sale del jugador, toca un punto de la línea inferior y llega al objetivo. Elige el punto **A–G** que produzca el recorrido más corto.

- **2 intentos** por ronda, sin repetir punto.
- Contador en vivo de tiempo y distancia mientras la pelota avanza.
- Al terminar se revela la ruta óptima y una tabla compara **Óptimo**, **Anterior** y **Mejor** (punto, tiempo y distancia).
- Marcador de aciertos, racha y mejor racha (guardada en `localStorage`).
- Controles: clic, teclas `A`–`G`, `Tab` + `Enter`; `Enter` inicia una nueva ronda.
- Modo oscuro automático.

Más detalle en [`Game1/README.md`](./Game1/README.md).

## Game3 · Fermat's Light: Co-Op

Juego cooperativo local para dos jugadores en una cuadrícula de 15×15. Dos emisores láser (rojo y cian) deben llegar al **objetivo central** colocando espejos.

### Cómo se juega

1. Pulsa **INICIAR ENLACE** (activa el audio; los controles no responden antes).
2. Cada jugador mueve su cursor y coloca espejos para desviar su láser.
3. El nivel se supera cuando **todos los láseres** llegan al objetivo.
4. Al superar los 4 niveles aparece la pantalla **PRUEBA SUPERADA**.

### Controles

| | Jugador 1 (rojo) | Jugador 2 (cian) |
|---|---|---|
| Mover cursor | `W` `A` `S` `D` | Flechas |
| Espejo | `Espacio` | `Enter` |

Cada pulsación de espejo alterna la casilla: **vacía → `/` → `\` → vacía**. No se pueden colocar espejos sobre muros, emisores ni el objetivo.

### Reglas

- Los láseres avanzan en línea recta y rebotan en los espejos.
- Los muros detienen el láser.
- Un contador **REFLEJOS** muestra cuántos espejos hay en el tablero.

### Niveles

1. El Laberinto
2. La Bifurcación
3. El Reloj
4. La Prisión

### Tecnología

- Canvas 2D para el tablero y los láseres.
- [Tone.js](https://tonejs.github.io/) para música y efectos.
- Tailwind CSS (CDN) y la fuente Press Start 2P.