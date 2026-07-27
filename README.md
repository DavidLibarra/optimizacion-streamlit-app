# Proyecto Final de Optimización — App Interactiva en Streamlit

Aplicación web interactiva construida con **Streamlit** que implementa y visualiza **18 algoritmos clásicos de optimización numérica**, tanto univariados (una variable) como multivariados (múltiples variables). Permite seleccionar una función objetivo, ajustar los parámetros de cada algoritmo, ejecutarlo y ver el resultado mediante gráficas, tablas de iteraciones y (en varios métodos) animaciones del proceso de búsqueda.

## Algoritmos incluidos

**Métodos univariados (búsqueda de línea / una variable):**
- Búsqueda Exhaustiva (`busqueda_exhaustiva.py`)
- Fase de Acotamiento (`fase_acotamiento.py`)
- Eliminación de Regiones (`region_elimination.py`)
- Intervalos por la Mitad (`intervalos_mitad.py`)
- Fibonacci Search (`fibonacci_search.py`)
- Golden Section Search (`golden_section_search.py`)
- Newton-Raphson (`newton_raphson.py`)
- Bisección (`metodo_biseccion.py`)
- Secante (`metodo_secante.py`)

**Métodos multivariados (basados en gradiente y búsqueda directa):**
- Búsqueda Unidireccional (`unidirectional_search.py`)
- Nelder-Mead Simplex (`nelder_mead.py`)
- Hooke-Jeeves (`hooke_jeeves.py`)
- Random Walk / Caminata Aleatoria (`random_walk.py`)
- Hill Climbing (`hill_climbing.py`)
- Recocido Simulado / Simulated Annealing (`simulated_annealing.py`)
- Método de Cauchy / Descenso más Pronunciado (`cauchy_method.py`)
- Método de Newton (`newton_method.py`)
- Gradiente Conjugado (`conjugate_gradient.py`)

`main.py` es el punto de entrada de la aplicación: define las funciones objetivo disponibles (univariadas y multivariadas), la navegación lateral y enruta a cada módulo `show_*` según el algoritmo seleccionado.

## Requisitos

```bash
pip install -r requirements.txt
```

Algunos módulos (`metodo_biseccion.py`, `metodo_secante.py`, `newton_raphson.py`) intentan generar las animaciones con **ImageMagick** primero, y si no está instalado en el sistema, usan **Pillow** automáticamente como respaldo. No es obligatorio instalar ImageMagick, pero si lo tienes, las animaciones se generan más rápido:

- **Windows/Mac:** [descarga ImageMagick](https://imagemagick.org/script/download.php)
- **Linux:** `sudo apt-get install imagemagick`

## Uso

```bash
streamlit run main.py
```

Esto abrirá la aplicación en tu navegador (por defecto en `http://localhost:8501`). Desde el menú lateral puedes navegar entre la página principal, el contexto teórico de la materia, y cada uno de los 18 algoritmos.

## Estructura del proyecto

```
.
├── main.py                      # Punto de entrada, navegación y funciones objetivo
├── busqueda_exhaustiva.py
├── fase_acotamiento.py
├── region_elimination.py
├── intervalos_mitad.py
├── fibonacci_search.py
├── golden_section_search.py
├── newton_raphson.py
├── metodo_biseccion.py
├── metodo_secante.py
├── unidirectional_search.py
├── nelder_mead.py
├── hooke_jeeves.py
├── random_walk.py
├── hill_climbing.py
├── simulated_annealing.py
├── cauchy_method.py
├── newton_method.py
├── conjugate_gradient.py
├── requirements.txt
└── animations/                  # Se genera automáticamente al correr algunos métodos (no versionada)
```

## Nota sobre las animaciones

Varios módulos generan GIFs animados que muestran el proceso iterativo del algoritmo paso a paso. Estos GIFs **se generan dinámicamente** en tiempo de ejecución (algunos en un archivo temporal, otros en una carpeta local `animations/` que se crea automáticamente) y no forman parte del código fuente — por eso no están incluidos ni versionados en este repositorio.

## Funciones objetivo disponibles

La app incluye un conjunto de funciones de prueba predefinidas, tanto univariadas (`Función 1`–`4`, `Función Lata`, `Función Caja`) como multivariadas (`Rastrigin`, `Ackley`, entre otras), cada una con su expresión en LaTeX, dominio sugerido y —cuando aplica— gradiente analítico para los métodos que lo requieren (Cauchy, Gradiente Conjugado, Newton).

## Tecnologías

- Python
- Streamlit
- NumPy
- Matplotlib (incluye `matplotlib.animation`)
- Pandas
- Pillow (para exportar animaciones a GIF)

## Licencia

MIT.
