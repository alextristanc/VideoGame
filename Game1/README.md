# 🎯 Trayectoria Óptima

Juego web de un solo archivo (`index.html`). Una pelota sale del jugador, toca un punto de la línea inferior y llega al objetivo. Tu meta es elegir el punto **A–G** que produzca el recorrido más corto.

## Cómo jugar

1. Elige un punto (A–G) con clic, con teclado o con `Tab` + `Enter`.
2. La pelota recorre `jugador → punto → objetivo` a velocidad constante. Mientras avanza, se muestran en vivo el **tiempo** y la **distancia** recorrida.
3. Tienes **2 intentos** por ronda y no puedes repetir punto.
4. Al terminar se revela la ruta óptima (en verde) y una tabla compara **Óptimo**, **Anterior** y **Mejor**.

## Controles

| Acción | Entrada |
|---|---|
| Elegir punto | Clic, o teclas `A`–`G` |
| Nueva ronda | Botón **Nueva ronda**, o `Enter` al terminar la ronda |
| Navegar puntos | `Tab`, y `Enter` o espacio para elegir |

## Características

- Posiciones aleatorias del jugador y del objetivo en cada ronda.
- Contador en vivo de tiempo (s) y distancia recorrida (u) durante la animación.
- Trayectorias de cada intento marcadas (naranja el 1.º, morado el 2.º).
- Tabla de resultados con letra, tiempo y distancia de cada fila:

  | | Punto | Tiempo | Distancia |
  |---|---|---|---|
  | **Óptimo** | Punto óptimo (`?` hasta terminar la ronda) | | |
  | **Anterior** | Primer intento (al elegir el segundo) | | |
  | **Mejor** | Mejor intento completado | | |

- Veredicto y diferencia con el óptimo, en segundos y porcentaje.
- Marcador: aciertos/rondas, racha actual y mejor racha.
- Modo oscuro automático (`prefers-color-scheme`).
- Tema forzable con `<html data-theme="dark">` o `<html data-theme="light">`.
- Sin dependencias ni build: HTML + CSS + JavaScript.

## La matemática

Con velocidad constante, tiempo = distancia / velocidad, así que el punto óptimo minimiza:

```
d(jugador, P) + d(P, objetivo)
```

Es el problema clásico de la **reflexión** (principio de Fermat): la ruta más corta es la que iguala el ángulo de entrada y de salida respecto a la línea. El juego lo resuelve por fuerza bruta calculando el total para cada uno de los 7 puntos.

## Ejecutar

Abre `index.html` en cualquier navegador moderno. No requiere servidor.

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
index.html   # marcado, estilos y lógica
```

Funciones principales: `newRound()`, `select(i)`, `animate(p, done)`, `setLive(s)`, `renderCmp()`, `finish()`.