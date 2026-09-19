**Fundamentos de la Ciencia de Datos**

**Cursada 2026**

**Práctico 4: Acceso a datos y análisis (parte III)**

1\.​Implementar una solución en Python que permita realizar un análisis exploratorio del conjunto de datos“movies.csv”de Kaggle, que contiene datos descargados usando BeautifulSoup de IMBD. El código debe: a.​Descargar los datos desde https://ignaciorlando.github.io/datasets/data-science/movies.csv. b.​Leer los datos del archivo. c.​Realizar un análisis preliminar de valores nulos. Discutir qué acciones correctivas se creen pertinentes para resolver la presencia de estos valores. d.​Preprocesar la columna GENRE. ¿Cuál es el mejor mecanismo para hacerlo? Justificar. e.​Existe el preconcepto de que las mejores películas según el público son las que han logrado mejores recaudaciones. ¿Qué podés decirnos de esta hipótesis, considerando los datos disponibles? Justificar. f.​Un grupo de expertos en cine asegura que hay una tendencia en los últimos años a producir películas y series de una duración mayor. ¿Es cierto esto? Justificar. g.​Plantear tres hipótesis adicionales vinculando pares de variables. Explorar los datos para reunir evidencia para confirmarlas o descartarlas. Resumir las observaciones realizadas. 2.​Implementar una solución en Python que permita realizar un análisis exploratorio del conjunto de datos“food.zip”de Kaggle, que contiene datos de una encuesta a 126 estudiantes acerca de preferencias de alimentación. El código debe: a.​Descargar los datos desde https://ignaciorlando.github.io/datasets/data-science/food.zip b.​Descomprimir el archivo .zip c.​Documentar el contenido de las columnas del archivo. d.​Identificar valores nulos. ¿Qué acciones correctivas se sugieren? ¿Son necesarias? Justificar. e.​Preprocesar la columna comfort\_food, para identificar cuáles son las comidas más sugeridas. f.​Plantear tres hipótesis adicionales vinculando pares de variables. Explorar los datos para reunir evidencia para confirmarlas o descartarlas. Resumir las observaciones realizadas.

A continuación incluimos algunos ejercicios tipo parcial para que puedan hacer con papel y lápiz para prepararse mejor para el examen.

Ejercicio 1

Se dispone de un conjunto obtenido mediante web scraping de Glassdoor, con 672 ofertas laborales y las siguientes variables:

Job Title, Salary Estimate, Job Description, Rating, Company Name, Location, Headquarters, Size, Founded, Type of ownership, Industry, Sector, Revenue y Competitors, index.

Al explorar los datos se obtuvieron los siguientes resultados:

| Variable Competitors =           | Valores potencialmente faltantes 501 213 |
|----------------------------------|------------------------------------------|
| Revenue =                        |                                          |
| Non-Applicable Revenue =         | Unknown / 27                             |
| Founded = -1 Industry = Sector = | 118 71 71                                |

Size ="-1"

17 Size ="Unknown"

31 Headquarters ="-1"

Además:

●​Si se considera la columna index, no se detectan filas duplicadas. ●​Si se elimina index, aparecen 13 filas exactamente duplicadas. ●​Job Title tiene 172 valores diferentes.

●​455 títulos contienen exactamente la expresión Data Scientist, pero 519 contienen la palabra scientist, ignorando mayúsculas y minúsculas. ●​Industry tiene 57 categorías. De ellas, 43 aparecen menos de diez veces. ●​Salary Estimate contiene valores como $137K-$171K (Glassdoor est.).

●​Company Name contiene valores como Healthfirst\\n3.1.

Resolver:

a)​Un estudiante propone reemplazar simultáneamente todos los valores -1, Unknown y Unknown / Non-Applicable por NaN. ¿Es una estrategia correcta? ¿Qué situaciones imagina que Unknown y Non-Applicable pueden representar? Indique qué análisis realizaría antes de decidir el reemplazo de cada columna.

¿Aplicaría la misma decisión en Competitors, Founded, Size y Revenue? Justifique separadamente. b)​¿Eliminaría la columna index? ¿En qué circunstancias podría ser útil conservarla? Al eliminarla aparecen duplicados. ¿Por qué? ¿Eliminaría automáticamente las 13 filas repetidas? ¿Qué variables utilizaría para determinar si se trata de una duplicación del scraping o de dos publicaciones legítimas de una misma oferta? c)​Para cada una de las tres estrategias de preprocesamiento propuestas para trabajar la columna Job Title, determine qué información conserva, qué información pierde, para qué pregunta de análisis sería apropiada, y qué falsos positivos o negativos podría generar. Explique también cómo trataría títulos que podrían pertenecer a más de un grupo. ●​Reemplazar cualquier título que contenga scientist por Data Scientist.

●​Crear una variable binaria is\_datascientist.

●​Construir una nueva variable categórica con grupos como Data Scientist, Data Engineer, Machine Learning Engineer, Analyst y Other. d)​Para modelar si un trabajo es remoto, un analista de datos propone generar is\_remote a partir de la columna Job Title. ¿Considera adecuada la variable construida? Si la respuesta es negativa, proponga una definición alternativa; si no, justifique. Tener en cuenta que se obtuvieron las siguientes cantidades de registros que contienen la palabra remote:

**Columna examinada Registros**

| Job Title       | 4   |
|-----------------|-----|
| Location        | 6   |
| Job Description | 63  |

e)​Proponga una transformación de Salary Estimate que genere: ●​minimum\_salary; ●​maximum\_salary; ●​average\_salary; ●​salary\_source.

Explique:

1\.​Qué operaciones de texto necesitaría. 2.​Por qué conviene conservar los extremos del intervalo y no solamente su promedio. 3.​Qué haría con valores que no respondan al formato esperado. 4.​Cómo verificaría que la transformación no produjo salarios imposibles.

f)​Size y Revenue contienen intervalos ordenados.

Compare estas estrategias:

●​Números consecutivos: 1, 2, 3… ●​Límite inferior del intervalo. ●​Límite superior. ●​Punto medio. ●​Conservar la variable como categoría ordinal.

¿Utilizaría la misma estrategia para ambas variables? Explique qué supuestos sobre las distancias entre categorías introduce cada alternativa.

g)​Un estudiante propone aplicar one-hot encoding directamente sobre las 57 industrias. Otro agrupa como Other todas las categorías con menos de diez observaciones. 1.​Compare las ventajas y limitaciones de ambas propuestas. 2.​¿Por qué la categoría Other podría terminar reuniendo industrias muy diferentes? 3.​¿Considera justificable utilizar un umbral fijo de diez observaciones? 4.​¿Cambiaría su decisión si el objetivo fuera describir el mercado en lugar de construir un modelo? 5.​Proponga una tercera estrategia que conserve más información sin crear 57 columnas.​

h)​Formule una hipótesis relacionada con el salario de las ofertas. Indique: ●​Variables originales necesarias. ●​Variables derivadas que construiría. ●​Tratamiento de faltantes. ●​Codificaciones seleccionadas. ●​Posibles sesgos del conjunto obtenido mediante scraping.

Ejercicio 2

El conjunto movies.csv contiene 9999 registros y nueve variables:

MOVIES, YEAR, GENRE, RATING, ONE-LINE, STARS, VOTES, RunTime y Gross.

Al contabilizar valores faltantes, se obtuvieron estos resultados

| Variable | Valores faltantes |
|----------|-------------------|
| YEAR     | 644               |
| GENRE    | 80                |
| RATING   | 1820              |
| VOTES    | 1820              |
| RunTime  | 2958              |
| Gross    | 9539              |

Además:

●​Hay 431 filas exactamente duplicadas. ●​Existen 6817 títulos diferentes. ●​GENRE presenta 510 combinaciones textuales, pero sólo 27 géneros individuales. ●​Gross está disponible en 460 registros. ●​Todos los registros con recaudación disponible corresponden a entradas de año puntual, no a series representadas mediante intervalos. ●​RunTime varía entre 1 y 853 minutos. ●​YEAR contiene formatos como (2021), (2010–2022), (2021– ), (2019 TV Movie) y (I) (2019). ●​La correlación entre RATING y Gross en los 460 casos disponibles es aproximadamente 0,19. ●​La correlación de Spearman entre VOTES y Gross es aproximadamente 0,80.

a. Compare las siguientes estrategias para tratar valores faltantes en la variable Gross:

1\.​Eliminar los registros sin recaudación. 2.​Eliminar la columna. 3.​Imputar con la media o mediana. 4.​Conservar los faltantes y restringir a 460 observaciones sólo los análisis que necesiten recaudación.

Seleccione una estrategia y justifique por qué resulta más apropiada. Analice especialmente:

●​El porcentaje de faltantes. ●​El probable mecanismo que genera la ausencia. ●​La diferencia entre películas y series. ●​La población a la que podrían generalizarse las conclusiones.

b. Para el tratamiento de filas duplicadas:

1\.​¿Eliminarías las 431 filas repetidas? 2.​¿Consideraría duplicados todos los registros que compartan MOVIES? 3.​Explique por qué dos obras distintas podrían tener el mismo título. 4.​Proponga una clave más adecuada para investigar duplicados. 5.​¿Qué información faltaría para identificar inequívocamente una obra?

c. Se desea responder tres preguntas diferentes:

1\.​¿Cuántas obras incluyen el género comedia? 2.​¿Cuáles son los géneros más frecuentes? 3.​¿Cómo se relaciona cada género con la puntuación?

Para cada pregunta, seleccione entre las siguientes estrategias:

●​Conservar únicamente el primer género. ●​Buscar palabras dentro de la cadena original. ●​Separar la columna y aplicar explode (). ●​Construir una columna booleana por género.

Explique por qué la mejor representación puede cambiar según la pregunta. Analice también qué ocurre con la unidad de observación después de aplicar explode().

d. VOTES contiene valores como 885,805 y Gross valores como $75.47M.

1\.​Proponga una secuencia de transformación para convertir ambas columnas en variables numéricas. 2.​¿Por qué no alcanzaría con eliminar todos los caracteres no numéricos? 3.​¿Cómo comprobaría que todos los valores de Gross utilizan la misma unidad? 4.​¿Qué haría con formatos inesperados? 5.​Explique por qué debería conservarse una copia de las columnas originales.

e. Diseñe una transformación que tome la variable YEAR y permita generar:

●​start\_year; ●​end\_year; ●​is\_ongoing; ●​content\_format, distinguiendo cuando sea posible películas, series y especiales.

Explique qué haría con valores como (I), (2019 TV Movie) y (2021– ). ¿Es preferible descartar los formatos irregulares o conservarlos con información parcial?

f. Al observar una correlación de Pearson r = 0,19, un estudiante concluye que“Las películas que más recaudan no son las que más gustan”. Evalúe la conclusión considerando:

●​La cantidad de registros utilizados. ●​El patrón de faltantes en Gross. ●​La forma probablemente asimétrica de la recaudación. ●​La diferencia entre Pearson y Spearman. ●​El posible efecto del año, género y cantidad de votos. ●​La diferencia entre puntuación del público, popularidad y calidad.

Indique qué transformaciones, gráficos y análisis adicionales realizaría antes de aceptar o rechazar la hipótesis.

g. Se desea evaluar la afirmación:“En los últimos años se producen contenidos cada vez más largos”. Pro ponga un análisis adecuado. Su respuesta debe explicar:

1\.​Por qué no conviene mezclar directamente películas y series. 2.​Qué representa probablemente RunTime en cada caso. 3.​Qué año utilizaría para contenidos con un intervalo. 4.​Cómo trataría las duraciones extremas. 5.​Si utilizaría medias, medianas o ambas. 6.​Qué gráfico permitiría estudiar la tendencia. 7.​Por qué un cambio en la composición del catálogo podría confundirse con un cambio real en la duración.