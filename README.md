# NY Knicks: Análisis Estadístico de la Franquicia (2000–2024)

---

## Descripción

Los New York Knicks acaban de conquistar su tercer campeonato de la NBA el pasado 13 de junio de 2026, poniendo fin a 53 años de sequía. Liderados por un Jalen Brunson nombrado MVP de las Finales tras anotar 45 puntos en el quinto partido, derrotaron a los San Antonio Spurs por 4-1 en una serie marcada por la mayor remontada de la historia de las Finales. Es el título más esperado en décadas para la franquicia neoyorquina y el primero desde los legendarios equipos de Willis Reed y Walt Frazier.

Este proyecto realiza un análisis exploratorio completo de las estadísticas históricas de los New York Knicks desde la temporada 2000-01 hasta la 2023-24. El objetivo es identificar patrones de rendimiento individual y colectivo, estudiar la evolución de la franquicia a lo largo del tiempo y extraer conclusiones sobre los jugadores y temporadas más destacados.

El análisis parte de un dataset histórico que abarca desde 1951, del cual se filtra y limpia el período moderno (2000-2024) para construir métricas avanzadas como la valoración por partido, el rating defensivo o los estadísticos per game en todas las categorías. Los resultados se presentan mediante tablas dinámicas y un dashboard interactivo, todo dentro de un único archivo Excel.

---

## Estructura del Proyecto

```
KNICKS_LIMPIO.xlsx
│
├── KNICKS_DATASET                 # Datos crudos originales descargados de Kaggle (CSV embebido, 1.218 filas)
├── KNICKS_TABLA_BRUTO             # Dataset sin procesar con las 28 columnas originales de la NBA
├── KNICKS_TABLA_LIMPIA_20_to_24   # Datos limpios y enriquecidos para el período 2000-01 a 2023-24
├── EVOLUCIÓN_FRANQUICIA           # Resumen estadístico agregado por temporada (22 temporadas)
├── TABLAS_DINÁMICAS               # Tablas pivote con rankings, comparativas y estadísticas clave
└── DASHBOARD                      # Panel visual interactivo con gráficos
```

---

## Fuente de Datos

El dataset original fue obtenido de Kaggle:

> [Knicks 1951 - 2024](https://www.kaggle.com/datasets/kennetharias/knicks-1951-2024) - *Kenneth Arias*

Recoge las estadísticas oficiales de todos los jugadores que han formado parte de la plantilla de los New York Knicks desde la temporada 1951-52 hasta la 2023-24, tal y como las registra la NBA en su base de datos oficial.

---

## Descripción del Dataset

El dataset en crudo contiene 1.218 registros, uno por cada combinación jugador-temporada en la historia de la franquicia. Para este análisis se filtra el período 2000-01 a 2023-24, obteniendo 408 registros correspondientes a 219 jugadores únicos.

### Variables originales (28 columnas)

| Variable | Descripción |
|---|---|
| `PLAYER_ID` | Identificador único del jugador en la NBA |
| `SEASON_ID` | Temporada (formato YYYY-YY) |
| `LEAGUE_ID` | Identificador de la liga (00 = NBA) |
| `TEAM_ID` | Identificador del equipo |
| `TEAM_ABBREVIATION` | Abreviatura del equipo (NYK) |
| `PLAYER_AGE` | Edad del jugador durante esa temporada |
| `GP` | Partidos jugados (*Games Played*) |
| `GS` | Partidos como titular (*Games Started*) |
| `MIN` | Minutos totales jugados |
| `FGM` / `FGA` | Tiros de campo anotados / intentados |
| `FG_PCT` | Porcentaje de tiro de campo |
| `FG3M` / `FG3A` | Triples anotados / intentados |
| `FG3_PCT` | Porcentaje de tiro de tres puntos |
| `FTM` / `FTA` | Tiros libres anotados / intentados |
| `FT_PCT` | Porcentaje de tiro libre |
| `OREB` / `DREB` / `REB` | Rebotes ofensivos, defensivos y totales |
| `AST` | Asistencias totales |
| `STL` | Robos de balón (*Steals*) |
| `BLK` | Tapones (*Blocks*) |
| `TOV` | Pérdidas de balón (*Turnovers*) |
| `PF` | Faltas personales |
| `PTS` | Puntos totales |
| `PLAYER_NAME` | Nombre completo del jugador |

### Variables añadidas en la limpieza (43 columnas totales)

Durante el proceso de limpieza y enriquecimiento se añadieron métricas derivadas para facilitar comparaciones entre jugadores con distinto número de partidos disputados:

- `VALORATIONPG`: Valoración oficial de la NBA por partido, métrica compuesta que pondera positivamente puntos, rebotes, asistencias, robos y tapones, y penaliza los intentos fallados y las pérdidas.
- `DEFRTNGPG`: Rating defensivo por partido, basado en rebotes totales, tapones y robos.
- `PTSPG`, `REBPG`, `ASTPG`, `STLPG`, `BLKPG`, `TOVPG`, `PFPG`: Versiones por partido de cada estadístico principal.
- `PLAYER_SEASON`: Clave única que combina nombre del jugador y temporada, útil para identificar registros en tablas dinámicas.

### Cobertura temporal

El dataset limpio cubre 22 temporadas completas. Las temporadas 2018-19 y 2019-20 no están incluidas en el dataset original de Kaggle, por lo que no forman parte del análisis. Tampoco lo están las temporadas 2024-25 y 2025-26, especialmente relevantes dado que en esta última los Knicks conquistaron el campeonato, lo que convierte su incorporación en uno de los objetivos prioritarios del proyecto.

---

## Resultados y Conclusiones

### Rendimiento individual

Quizás el dato más sorprendente del análisis es que la mejor temporada individual en valoración por partido no pertenece a ninguna de las grandes estrellas de la franquicia, sino a David Lee en 2009-10 (23,81), por delante de Jalen Brunson en 2023-24 (23,74) y Julius Randle en 2020-21 (23,65). Lee, un ala-pívot que nunca fue considerado una estrella de primer nivel en Nueva York, tuvo una temporada extraordinaria en dobles-dobles antes de ser traspasado a Golden State, donde sí alcanzó mayor reconocimiento. Randle aparece dos veces entre las cinco mejores temporadas, lo que refleja su peso en la franquicia durante los años 2020. Carmelo Anthony es el máximo anotador histórico del período con 10.186 puntos, casi cuatro mil más que el segundo clasificado, Julius Randle (6.197). En cuanto a presencia, Kurt Thomas es el jugador que más partidos disputó con 439 encuentros, seguido de Carmelo Anthony (412) y David Lee (368).

### Defensa y rebote

Earl Barron registró la mejor temporada defensiva del período en 2012-13 con un rating de 19,00 por partido, siendo el único jugador en superar esa barrera. Por detrás, Marcus Camby es el más consistente defensivamente con las dos siguientes mejores temporadas, ambas por encima de 14, fundamentadas en el rebote y los tapones. En el cómputo global de rebotes totales, David Lee lidera con 3.529, seguido de Kurt Thomas con 3.481. En asistencias, Stephon Marbury encabeza el ranking histórico del período con 2.004, reflejo de los años en que fue el motor del juego de los Knicks en la primera parte de los 2000.

### Evolución del equipo

La franquicia ha experimentado un crecimiento sostenido en anotación a lo largo del período. La temporada 2022-23 fue la más prolífica con 9.514 puntos de equipo, impulsada por Randle (1.936 pts), Brunson (1.633 pts) y Barrett (1.431 pts), lo que refleja la consolidación de un núcleo competitivo tras años de reconstrucción. En contraste, la temporada 2011-12 fue la más floja en anotación (6.458 pts), consecuencia directa del lockout de la NBA de 2011, que redujo el calendario de 82 a 66 partidos.

El uso del triple ha crecido de forma exponencial a lo largo de todo el período: de 1.115 intentos en 2000-01 a 2.936 en 2023-24, prácticamente triplicando el volumen en poco más de dos décadas. Esta tendencia no es exclusiva de los Knicks, sino un reflejo de la transformación táctica global de la NBA, aunque el equipo tardó más que otras franquicias en adoptar plenamente el juego perimetral.

---

## Próximos Pasos

- Completar y enriquecer el Dashboard con visualizaciones interactivas por temporada y jugador.
- Incorporar datos de las temporadas no incluidas (2018-19, 2019-20, 2024-25 y 2025-26) para cerrar el análisis.
- Añadir métricas avanzadas adicionales como PER (Player Efficiency Rating), True Shooting % y Win Shares.
- Comparar la evolución de los Knicks frente a la media de la NBA en el mismo período.