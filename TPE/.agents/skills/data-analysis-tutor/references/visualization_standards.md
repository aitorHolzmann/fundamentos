# Estándar de Visualización de Datos de la Cátedra (UNICEN)

Esta guía condensa los principios teóricos y técnicos de la **Clase N° 5: Visualización de Datos**, fundamentales para resolver el Práctico 5 y responder las preguntas conceptuales de los exámenes.

---

## 1. Principio Fundamental: "Mostrar vs. Demostrar"

1. **Mostrar no es demostrar:** Una gráfica presenta evidencia visual intuitiva y reduce la carga cognitiva, pero **no constituye una prueba matemática ni estadística formal**.
2. **Honestidad Visual:** La estructura del gráfico debe reflejar la estructura de la realidad sin manipular escalas para exagerar o disimular diferencias.
3. **Inmutabilidad del Canvas en Matplotlib:** Al llamar a `plt.show()`, el canvas se cierra y se libera la memoria. Toda configuración (`title`, `xlabel`, `ylabel`, `legend`, límites de ejes) debe ejecutarse **antes** de `plt.show()`.

---

## 2. Catálogo de Gráficos por Tipo de Pregunta

### A. Scatter Plot (Gráfico de Dispersión)
- **Propósito:** Evaluar la relación entre dos variables cuantitativas continuas.
- **Regla de oro de la cátedra:** Debe tener **relación de aspecto 1:1 (cuadrado)**:
  ```python
  fig, ax = plt.subplots(figsize=(6, 6))  # Cuadrado
  ax.scatter(df['x'], df['y'], alpha=0.6)
  ax.set_aspect('equal', adjustable='box') # Si las escalas son directamente comparables
  ```
  *Motivo de examen:* Un gráfico rectangular altera artificialmente la percepción de la pendiente y la fuerza de la correlación.

### B. Boxplots y la Heurística de las Muescas (`notches`)
- **Propósito:** Comparar la distribución de una variable cuantitativa entre diferentes grupos categóricos.
- **Anatomía:**
  - Caja: Delimitada por $Q_1$ (25%) y $Q_3$ (75%). La longitud de la caja es el $IQR$.
  - Línea central: Mediana ($Q_2$).
  - Bigotes: Extensión hasta el dato más alejado dentro de $1.5 \times IQR$. Puntos aislados exteriores son outliers.
- **Heurística de las Muescas (`notch=True`):**
  ```python
  sns.boxplot(data=df, x='categoria', y='valor', notch=True)
  ```
  *Regla de decisión:* La muesca representa aproximadamente el intervalo de confianza del 95% para la mediana. Si las muescas de dos cajas se solapan, existe alta probabilidad de que la diferencia de medianas no sea estadísticamente significativa bajo un test formal (T-test o Wilcoxon).

### C. Histogramas y el Ajuste de "Bins"
- **Propósito:** Estudiar la silueta y distribución univariada de una variable continua.
- **Riesgo del sub-muestreo:** Pocos bins (ej. 5) suavizan la distribución y pueden esconder patrones críticos como la **trimodalidad** (ejemplo visto en Boston Housing).
- **Práctica recomendada:** Iterar el parámetro `bins` (o usar la regla de Freedman-Diaconis / Sturges) hasta que la forma represente adecuadamente los datos.

### D. Gráficos de Barras: Orden y "Color Focus"
- **Propósito:** Comparar cantidades o frecuencias entre categorías discretas.
- **Reglas de diseño cognitivo:**
  1. **Ordenar por magnitud:** Las barras deben ordenarse de mayor a menor para permitir una lectura inmediata del ranking.
  2. **Color Focus:** Usar colores neutros (gris claro) para las categorías de contexto y un color llamativo (ej. celeste o azul) para la categoría de interés (ej. Argentina).
  3. **Rotación de Ticks:** Aplicar `plt.xticks(rotation=45, ha='right')` si los nombres de categorías son largos, evitando el solapamiento.

### E. Series Temporales (Líneas) e Hitos Contextuales
- **Propósito:** Seguir la evolución secuencial a lo largo del tiempo.
- **Contextualización con `plt.axvline()`:** Explicar quiebres y volatilidad mediante líneas verticales discontinuas que marquen hitos históricos o eventos conocidos (ej. crisis, cambios de política, pandemia).

---

## 3. Checklist Obligatorio para Todo Gráfico

Antes de dar por finalizada una celda gráfica, verificar:
- [ ] ¿Tiene `plt.title()` informativo que describa la hipótesis o hallazgo?
- [ ] ¿Están presentes `plt.xlabel()` y `plt.ylabel()` con sus unidades de medida explícitas?
- [ ] ¿El rango del eje Y es honesto? (No comenzar en 60 si el rango posible es de 0 a 100, evitando crear falsas diferencias abismales).
- [ ] En gráficos de barras, ¿están ordenadas por valor y se evita el exceso de colores saturados sin justificación?
- [ ] En dispersión, ¿el gráfico es cuadrado para no sesgar la pendiente visual?
- [ ] ¿La interpretación redactada responde a la capa *"So What?"* en lugar de limitarse a describir la imagen?

