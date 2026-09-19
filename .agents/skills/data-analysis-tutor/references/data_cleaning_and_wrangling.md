# Guía Técnica: Limpieza y Preprocesamiento Crítico de Datos

Esta guía detalla los criterios exigidos en la cátedra para el tratamiento riguroso de valores faltantes, duplicados, tipos de datos y transformaciones de texto en Pandas.

---

## 1. Tratamiento de Valores Faltantes (Nulos)

**Regla de oro:** Nunca borrar filas ni imputar con la media a ciegas sin antes auditar el origen y mecanismo de la ausencia.

### Diagnóstico de Nulos:
1. **Porcentaje de nulos por columna:**
   ```python
   null_pct = df.isnull().mean() * 100
   print(null_pct[null_pct > 0].sort_values(ascending=False))
   ```
2. **Clasificación del mecanismo de falta:**
   - **MCAR (Missing Completely at Random):** La ausencia es puro azar; no depende de ninguna variable observada ni oculta.
   - **MAR (Missing at Random):** La ausencia depende de otra variable conocida (ej. `Gross` ausente en series de TV porque no tienen taquilla cinematográfica).
   - **MNAR (Missing Not at Random):** La ausencia depende del propio valor de la variable (ej. salarios altos o bajos que el encuestado prefiere ocultar).

### Estrategias de Decisión:
- **Conservar faltantes y filtrar por subset analítico:** Si una variable tiene un porcentaje alto de nulos (ej. `Gross` con >90% de nulos en IMDB), **no se borra la columna entera ni se eliminan todas las filas del dataset**. Se conserva el dataset completo y, únicamente para los análisis que involucren taquilla, se filtra `df.dropna(subset=['Gross'])`, explicitando la población reducida a la que aplican las conclusiones.
- **Imputación con media/mediana:** Solo admisible si el porcentaje de nulos es muy bajo (<5%), la distribución es unimodal y se conoce el mecanismo. Para variables asimétricas o con outliers, preferir siempre la **mediana**.

---

## 2. Detección de Duplicados: Claves Compuestas

**Regla de oro:** Dos filas con el mismo título o nombre no implican necesariamente un duplicado erróneo de scraping.

### Distinción Crítica:
- **Duplicado técnico (scraping repetido):** Todas las características sustantivas coinciden exactamente debido a una consulta redundante al sitio web.
- **Entidades homónimas legítimas:** 
  - Remakes o películas distintas con el mismo nombre estrenadas en diferentes años (ej. *The Lion King* en 1994 vs 2019).
  - Múltiples vacantes laborales de una misma empresa publicadas en distintas fechas o sucursales.

### Protocolo en Pandas:
1. Inspeccionar duplicados exactos:
   ```python
   duplicados_completos = df[df.duplicated(keep=False)]
   ```
2. Si existe una columna artificial como `index` o `id_scraping`, eliminarla temporalmente para verificar si las filas restantes son idénticas:
   ```python
   cols_sin_id = [c for c in df.columns if c != 'index']
   duplicados_sin_id = df[df.duplicated(subset=cols_sin_id, keep=False)]
   ```
3. Definir una **clave candidata compuesta** para verificar unicidad real:
   - En películas: `['MOVIES', 'YEAR', 'RunTime']`.
   - En empleos: `['Job Title', 'Company Name', 'Location']`.

---

## 3. Transformación de Texto Heterogéneo y Expresiones Regulares

### Casos Típicos de la Cátedra:
1. **Limpieza de votos y monedas con comas y símbolos:**
   ```python
   # Convertir "885,805" a entero
   df['VOTES'] = df['VOTES'].astype(str).str.replace(',', '').astype(float)
   ```
2. **Manejo de unidades compuestas (ej. taquilla en millones `$75.47M`):**
   ```python
   # Verificar unidades antes de convertir
   def parse_gross(val):
       if pd.isna(val):
           return np.nan
       val = str(val).replace('$', '').strip()
       if val.endswith('M'):
           return float(val[:-1]) * 1_000_000
       elif val.endswith('K'):
           return float(val[:-1]) * 1_000
       return float(val)
   ```
3. **Extracción con Regex (`str.extract`):**
   - Siempre verificar qué porcentaje de registros coincide con el patrón y qué se hace con los formatos irregulares (ej. `(2021– )` para series activas).

---

## 4. Columnas Multivalor y el Peligro de `.explode()`

Cuando una celda contiene listas o valores separados por comas (ej. géneros cinematográficos `"Action, Comedy, Sci-Fi"`):

1. **La técnica `.explode()`:**
   ```python
   df['genre_list'] = df['GENRE'].str.split(', ')
   df_exploded = df.explode('genre_list')
   ```
2. **Advertencia metodológica fundamental (Pregunta típica de parcial):**
   - **Cambio de la unidad muestral:** Al aplicar `.explode()`, la unidad de observación pasa de ser *"una película"* a *"una asociación película-género"*.
   - Una película con 3 géneros figurará 3 veces. Si calculamos el promedio global de votos o recaudación sobre el dataframe explotado, estaremos ponderando con triple peso a las películas multigénero frente a las de género único.

---

## 5. Detección y Tratamiento de Outliers (Regla de Tukey)

- **Rango Intercuartílico ($IQR$):**
  $$IQR = Q_3 - Q_1$$
  - Límite inferior: $Q_1 - 1.5 \times IQR$
  - Límite superior: $Q_3 + 1.5 \times IQR$
- **Valores extremos:**
  - No eliminar automáticamente los outliers; primero determinar si son errores de medición (ej. duración de película de 1 minuto o 800 minutos) o registros reales legítimos (ej. un blockbuster que recaudó 10 veces más que la media).

