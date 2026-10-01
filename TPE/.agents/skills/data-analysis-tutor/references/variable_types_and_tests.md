# Guía Teórica: Clasificación de Variables y Selección de Técnicas Estadísticas

Esta guía sintetiza los conceptos de la cátedra de **Fundamentos del Análisis de Datos (UNICEN)** sobre el nivel de medición de variables y las técnicas bivariadas y multivariadas aplicables.

---

## 1. Niveles de Medición de Variables

Antes de ejecutar cualquier cálculo en Python, es obligatorio clasificar cada columna en una de estas categorías:

### A. Variables Cualitativas (Categóricas)
Representan atributos o cualidades no numéricas.
- **Nominales:** No admiten un orden natural. La única operación matemática válida es el conteo de frecuencias (moda, proporciones).
  - *Ejemplos:* País de origen, género cinematográfico (`GENRE`), tipo de contenido (`type`: Movie vs TV Show), presencia de río (`chas` booleano).
- **Ordinales:** Poseen un orden intrínseco o jerarquía, pero la distancia entre categorías consecutivas **no es necesariamente igual ni medible**.
  - *Ejemplos:* Año de cursada (1°, 2°, 3°), tamaño de empresa (`Size`: Small, Medium, Large), nivel de satisfacción (Bajo, Medio, Alto).
  - *Advertencia de parcial:* Asignar números 1, 2, 3... a una ordinal introduce el supuesto arbitrario de que la distancia entre 1 y 2 es idéntica a la de 2 y 3.

### B. Variables Cuantitativas (Numéricas)
Representan cantidades numéricas medibles donde las distancias y operaciones aritméticas tienen significado real.
- **Discretas:** Valores enteros aislados surgidos de un proceso de conteo. No admiten valores intermedios.
  - *Ejemplos:* Número de hijos, cantidad de votos (`VOTES`), temporadas de una serie, cantidad de palabras en una descripción.
- **Continuas:** Valores reales dentro de un intervalo continuo, surgidos de un proceso de medición.
  - *Ejemplos:* Altura, peso, salario, recaudación de taquilla (`Gross`), duración en minutos (`RunTime`).

---

## 2. Matriz de Cruce Bivariado (La Regla de Oro de la Cátedra)

| Variable X | Variable Y | Herramienta Estadística | Gráfico Recomendado | Supuestos y Advertencias Críticas |
| :--- | :--- | :--- | :--- | :--- |
| **Cuantitativa Continua** | **Cuantitativa Continua** | Coeficiente de Pearson ($r$) | Scatter Plot (Aspecto 1:1) | Solo mide **asociación lineal**. Sensible a outliers. Si la relación es monótona no lineal o muy asimétrica, usar **Spearman**. |
| **Cuantitativa** | **Ordinal** | Coeficiente de Spearman ($\rho$) o Kendall ($\tau$) | Scatter Plot con jittering / Boxplot por nivel ordinal | **Prohibido usar Pearson**. Spearman compara el orden de los rangos, no las magnitudes directas. |
| **Ordinal** | **Ordinal** | Coeficiente de Spearman o Kendall | Heatmap de tabla de contingencia de rangos | Respeta el orden de categorías sin asumir distancias lineales. |
| **Cualitativa** | **Cualitativa** | Test de Chi-cuadrado ($\chi^2$) + Tablas de Contingencia | Gráfico de barras agrupadas o apiladas (100%) | Compara frecuencias observadas vs esperadas bajo independencia. No usar gráficos de dispersión. |
| **Cuantitativa** | **Cualitativa** | Comparación de medianas/medias (T-test, Mann-Whitney, ANOVA, Kruskal-Wallis) | Boxplots comparativos (con `notch=True`) | Las muescas (`notches`) muestran el IC del 95% de la mediana: solapamiento sugiere medianas estadísticamente similares. |

---

## 3. Coeficientes de Correlación: Pearson vs Spearman

### Coeficiente de Pearson ($r$)
$$r = \frac{\sum (x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum (x_i - \bar{x})^2 \sum (y_i - \bar{y})^2}}$$

- Rango: $[-1, 1]$.
- **Indeterminación ($0/0$):** Ocurre si una de las variables tiene varianza cero (todos los valores idénticos en la muestra).
- **Limitaciones graves:**
  1. No detecta relaciones no lineales (ej. parábolas, ciclos). Un $r \approx 0$ no implica independencia, solo ausencia de relación lineal.
  2. Altamente sensible a valores atípicos (un solo outlier extremo puede inflar o destruir la correlación).
  3. No aplicable a variables ordinales.

### Coeficiente de Spearman ($\rho$)
Calcula la correlación de Pearson sobre los **rangos** de las observaciones ($R(x_i), R(y_i)$).
- Evalúa si la relación es **monótona** (cuando una variable aumenta, la otra tiende a aumentar o disminuir, sin importar si es en línea recta).
- **Mucho más robusto ante outliers** y asimetrías severas (como distribuciones de ingresos o taquilla `Gross`).
- Es la herramienta correcta para cruzar variables cuantitativas con ordinales.

---

## 4. Correlación vs. Causalidad y Variables Confusoras

1. **"Correlación no implica causalidad":** Una correlación estadística fuerte puede deberse a:
   - Coincidencia / Correlación espuria (ej. consumo de té en India vs velocidad de caballos).
   - Causalidad inversa.
   - Presencia de una tercera variable oculta o de confusión (ej. año, inflación, tamaño de la muestra).
2. **Techos artificiales y datos censurados:**
   - Detectar si los datos están truncados en un valor máximo o mínimo (ej. precios fijos en \$50k en Boston Housing). Si no se limpian o separan antes, falsean el coeficiente de correlación.

