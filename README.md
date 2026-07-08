# Detección Evolutiva de Patrones en Series Temporales — Metaheurística P3

Proyecto desarrollado para la asignatura de **Metaheurística**.

Este proyecto implementa un algoritmo evolutivo en Python para detectar patrones repetidos en series temporales a partir de archivos CSV.

El objetivo es identificar ventanas representativas dentro de una señal, buscar patrones similares y visualizar las regiones detectadas mediante gráficas.

---

## Descripción

El proyecto trabaja con series temporales cargadas desde un archivo CSV.

A partir de la primera columna numérica válida, se normalizan los datos y se aplica un algoritmo evolutivo basado en ventanas.

Cada individuo representa un conjunto de ventanas temporales:

```txt
[(inicio_1, fin_1), (inicio_2, fin_2), ..., (inicio_n, fin_n)]
```

La calidad de cada individuo se evalúa teniendo en cuenta la cobertura de la serie y la existencia de patrones similares dentro de la señal.

Además, el sistema incluye detección de regiones planas mediante baja desviación estándar.

---

## Funcionalidades

* Carga de series temporales desde archivos CSV.
* Selección automática de la primera columna numérica válida.
* Eliminación de valores NaN.
* Normalización min-max de los datos.
* Generación de población inicial aleatoria.
* Representación de individuos mediante ventanas temporales.
* Evaluación de soluciones mediante función de fitness.
* Selección por torneo.
* Cruce de individuos mediante punto único.
* Mutación por desplazamiento de ventanas.
* Búsqueda de patrones similares mediante correlación.
* Soporte para múltiples tamaños de ventana.
* Detección de patrones planos.
* Ejecución configurable por línea de comandos.
* Visualización de la serie temporal original.
* Visualización de patrones detectados sobre la serie.

---

## Algoritmo implementado

### Algoritmo evolutivo

El algoritmo evolutivo genera una población de individuos, donde cada individuo contiene una o varias ventanas de la serie temporal.

Durante cada generación se aplican las siguientes fases:

* evaluación de fitness,
* selección por torneo,
* cruce de punto único,
* mutación por desplazamiento,
* reemplazo de población,
* selección del mejor individuo final.

### Detección de patrones similares

Una vez obtenidas las mejores ventanas, el sistema busca regiones similares en la serie utilizando correlación.

### Detección de patrones planos

También se detectan segmentos de la serie con baja variación, identificando regiones planas mediante la desviación estándar de ventanas consecutivas.

---

## Estructura del proyecto

```txt
Practica3-MH/
├── main.py
├── algorithm.py
├── preprocessing.py
├── visualization.py
└── data/
```

---

## Tecnologías utilizadas

* Python
* NumPy
* Pandas
* Matplotlib
* fastdtw
* joblib

---

## Ejecución

Instala las dependencias principales:

```bash
pip install numpy pandas matplotlib fastdtw joblib
```

Ejecuta el programa indicando un archivo CSV:

```bash
python main.py ruta/al/archivo.csv
```

Ejemplo con parámetros personalizados:

```bash
python main.py datos.csv --generations 100 --population_size 20 --window_length 50 --n_windows 3
```

También se pueden usar varios tamaños de ventana:

```bash
python main.py datos.csv --window_sizes 30,50,100 --generations 100 --population_size 20 --n_windows 3
```

---

## Parámetros disponibles

| Parámetro           | Descripción                                       | Valor por defecto |
| ------------------- | ------------------------------------------------- | ----------------- |
| `csv_file`          | Ruta al archivo CSV con la serie temporal         | Obligatorio       |
| `--generations`     | Número de generaciones del algoritmo evolutivo    | `100`             |
| `--population_size` | Tamaño de la población                            | `20`              |
| `--window_length`   | Longitud de ventana cuando se usa un único tamaño | `50`              |
| `--n_windows`       | Número de ventanas por individuo                  | `3`               |
| `--window_sizes`    | Lista de tamaños de ventana separados por comas   | `None`            |

---

## Resultados generados

El programa muestra por consola las ventanas base encontradas y los patrones similares detectados.

Además, genera visualizaciones como:

* serie temporal normalizada,
* patrones detectados resaltados sobre la serie,
* regiones similares agrupadas visualmente,
* patrones planos detectados.

---

## Objetivo académico

El proyecto permite estudiar el uso de algoritmos evolutivos aplicados a series temporales, analizando:

* representación de soluciones mediante ventanas,
* diseño de una función de fitness,
* búsqueda de patrones repetidos,
* influencia del tamaño de ventana,
* uso de correlación para medir similitud,
* detección de regiones planas,
* visualización de resultados,
* aplicación de metaheurísticas a datos secuenciales.

---

## Estado del proyecto

Proyecto académico funcional para experimentación con detección de patrones en series temporales mediante algoritmos evolutivos.

---

## Autores

* Daniel Grande Rubio — [@Dani93414](https://github.com/Dani93414)
* Carlos de la Torre Frías — [@CarlosDT191](https://github.com/CarlosDT191)
* Manuel Eddy Ruiz Rivera — [@i12rurim](https://github.com/i12rurim)
