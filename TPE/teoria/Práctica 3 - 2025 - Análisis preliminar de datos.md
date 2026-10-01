# Análisis preliminar de datos

Fundamentos de la Ciencia de Datos - Clase Práctica Nro. 3

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 187x51px, 187x50pt, ~73dpi, JPG, DEVICE_RGB, 32bpp>

Librerías de Python para Data Science

# Numpy & Scipy

● Librería de Python para procesamiento eficiente de matrices y vectores ○ Basta de bucles para recorrerlas! → operaciones matriciales y vectoriales (“slicing”) ● Base de otras librerías (Pandas, Scipy, Scikit Learn, Matplotlib), incluidas las más populares para hacer machine learning!

● Brinda funciones para matemática, álgebra lineal, optimización, y estadísticas, entre otras áreas. ● En ciencia de datos, se usa para análisis de correlación, test estadísticos, y modelado. ● Complementa a NumPy, con herramientas más sofisticadas y especializadas para el procesamiento de datos.

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 227x102px, 227x102pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 204x102px, 204x102pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Algunas formas de

# Analizar nuestros datos

# analysis

• An

**álisis univariado: estudiar el comportamiento estadístico de una variable de manera**

aislada. ○ Medidas de tendencia central (media, mediana, moda) ○ Medidas de dispersión (varianza, desvío estándar) ○ Cuantiles (cuartiles, percentiles, deciles, rangos) ○ Estudio gráfico mediante histogramas.

• An

**álisis bivariado: estudiar la relación entre una variable y otra**

○ Correlación (de Pearson, de Spearman, de Kendall), prueba de chi-cuadrado. ○ Gráficos de dispersión ○ Tablas de contingencia (muestro la frecuencia de combinaciones de dos variables categóricas)

• An

**álisis multivariado: estudiar la relación entre múltiples variables**

**○**

(ya las veremos!!!)

Más info: Joel Grus,“Data Science from Scratch: First Principles with Python”. Ca pítulo 10.

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Análisis de los datos

# Análisis bivariado / Correlación

Correlación entre dos variables = dirección y fuerza de la relación entre variables

**Coeficiente de correlación de Pearson**

• Mi

de la correlación lineal e/ 2 variables.

• N

o te dice si dos variables tienen o no relación, sólamente te dice si la relación es lineal

• N

o confundir correlación con causalidad!

Más info: Pág. 99 del libro de Joel Grus.

En estos casos hay otras relaciones entre las variables que no se pueden capturar con Pearson → estudiar gráficamente

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 411x188px, 411x188pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 268x95px, 267x94pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Análisis de los datos

# Análisis bivariado / Scatter plot

Una buena herramienta para estudiar la relación entre dos variables

• Graficamos los valores de dos variables x, y en

un plano cartesiano, con un par ordenado (x, y) para cada muestra i del conjunto

• L

a forma en la que los puntos se distribuyen en el espacio nos da una idea general de la relación entre ambas variables

• Ojo que los problemas típicos se mantienen:

○ Pocas muestras? Malas conclusiones ○ Muchas muestras mal recolectadas? Malas conclusiones ○ Correlación no es causalidad

Más info: Pág. 99 del libro de Joel Grus.

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 420x311px, 419x311pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Análisis de los datos

# Análisis bivariado / Scatter plot

Una buena herramienta para estudiar la relación entre dos variables

• Graficamos los valores de dos variables x, y en

un plano cartesiano, con un par ordenado (x, y) para cada muestra i del conjunto

• L

a forma en la que los puntos se distribuyen en el espacio nos da una idea general de la relación entre ambas variables

• Ojo que los problemas típicos se mantienen:

○ Pocas muestras? Malas conclusiones ○ Muchas muestras mal recolectadas? Malas conclusiones ○ Correlación no es causalidad

Más info: Pág. 99 del libro de Joel Grus.

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 328x313px, 327x312pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Análisis de los datos

# Análisis bivariado / Scatter plot

Una buena herramienta para estudiar la relación entre dos variables

• Graficamos los valores de dos variables x, y en

un plano cartesiano, con un par ordenado (x, y) para cada muestra i del conjunto

• L

a forma en la que los puntos se distribuyen en el espacio nos da una idea general de la relación entre ambas variables

• Ojo que los problemas típicos se mantienen:

○ Pocas muestras? Malas conclusiones ○ Muchas muestras mal recolectadas? Malas conclusiones ○ Correlación no es causalidad

Más info: Pág. 99 del libro de Joel Grus.

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 328x326px, 327x326pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

\- ciencia datos-unicen- practica-3- python.ipynb

<image redacted: 960x415px, 960x415pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Acceso a datos y análisis (parte II) ¿Qué vimos hoy?

1\. Estudiamos un poco sobre análisis bivariado 2. Aprendimos a estudiar correlaciones en Python usando Pandas 3. Tenemos todo para empezar y terminar el práctico 3!

**Material adicional:**

● Pág. 40 (57 en el PDF) del libro de Skiena, hasta la 46 (63 en el PDF). Una introducción bien detallada sobre la correlación. ● Pág. 99 a 106 del libro de Joel Grus. Algunas curiosidades sobre la correlación. ● Un video introductorio al análisis exploratorio bivariado.

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>