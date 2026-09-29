# 🎯 Trayectoria Óptima

Juego web de un solo archivo (`trayectoria-optima.html`). Una pelota sale del jugador, toca un punto de la línea inferior y llega al objetivo. Tu meta es elegir el punto **A–G** que produzca el recorrido más corto.

## Cómo jugar

1. Elige un punto (A–G) con clic, con teclado o con `Tab` + `Enter`.
2. La pelota recorre `jugador → punto → objetivo` a velocidad constante y se muestra su tiempo.
3. Tienes **2 intentos** por ronda y no puedes repetir punto.
4. Al terminar se revela la ruta óptima (en verde) y se compara tu mejor tiempo con el óptimo.

## Controles

| Acción | Entrada |
|---|---|
| Elegir punto | Clic, o teclas `A`–`G` |
| Nueva ronda | Botón **Nueva ronda**, o `Enter` al terminar la ronda |
| Navegar puntos | `Tab`, y `Enter` o espacio para elegir |

## Características

- Posiciones aleatorias del jugador y del objetivo en cada ronda.
- Tiempo por intento y trayectorias marcadas (naranja el 1.º, morado el 2.º).
- Resultado con diferencia en segundos y porcentaje contra el óptimo.
- Marcador: aciertos/rondas, racha actual y mejor racha.
- Modo oscuro automático (`prefers-color-scheme`).
- Sin dependencias ni build: HTML + CSS + JavaScript.

## La matemática

Con velocidad constante, tiempo = distancia / velocidad, así que el punto óptimo minimiza:

```
d(jugador, P) + d(P, objetivo)
```

Es el problema clásico de la **reflexión** (principio de Fermat): la ruta más corta es la que iguala el ángulo de entrada y de salida respecto a la línea. El juego lo resuelve por fuerza bruta calculando el total para cada uno de los 7 puntos.

## Ejecutar

Abre `trayectoria-optima.html` en cualquier navegador moderno. No requiere servidor.

## Configuración

Constantes al inicio del `<script>`:

| Constante | Valor | Descripción |
|---|---|---|
| `SPEED` | `115` | Velocidad de la pelota (unidades SVG por segundo) |
| `MAX` | `2` | Intentos por ronda |
| `LINE_Y` | `335` | Altura de la línea de puntos |
| `xs` | `[145 … 565]` | Posiciones X de los puntos A–G |

## Persistencia

Solo la **mejor racha** se guarda en `localStorage` (clave `trayectoria`). Si el almacenamiento no está disponible, el juego funciona igual.

## Estructura

```
trayectoria-optima.html   # marcado, estilos y lógica
```

Funciones principales: `newRound()`, `select(i)`, `animate(p, done)`, `finish()`.