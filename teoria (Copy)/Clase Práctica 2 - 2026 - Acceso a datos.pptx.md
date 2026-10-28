# Acceso a datos

Fundamentos de la Ciencia de Datos - Clase Práctica Nro. 2

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 187x51px, 187x50pt, ~73dpi, JPG, DEVICE_RGB, 32bpp>

Acceso a datos y análisis ¿Qué vamos a ver hoy?

● Parte“teórica” de la clase (15:30 a 16:00): ○ Un breve repaso de lo que vieron en la teoría ○ Tipos de datos más comunes para almacenamiento de data estructurada ○ La librería Pandas ● Parte práctica en Colab (16:00 a 17:00): ○ Lectura de archivos CSV ○ Pandas y uso general de la librería para análisis exploratorio de los datos ● Resuelvan el práctico en clase!

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Repasemos de qué hablamos cuando hablamos de

# Datos / Taxonomía

**Datos estructurados (structured)**

Los que podemos representar en tablas (filas y columnas), por ende en bases de datos relacionales (registros y campos) Ejemplos: financieros, sociales, comportamentales, …

**Datos no estructurados (unstructured)**

Los que no podemos representar en tablas Ejemplos: texto libre, imágenes, video, sonido. No vamos a trabajar con estos en el curso!

**Más info:**

sdfsdfsdf

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 380x296px, 379x295pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Repasemos de qué hablamos cuando hablamos de

# Datos / Muestra vs. población

**● Población**

(population): el grupo completo que queremos estudiar.

**● Muestra**

(sample): subconjunto de esa población, obtenido por muestreo.

**● Muestreo**

(sampling): proceso de selección de una muestra a partir de una población. = A ○ Muestreo“ representativo” quel que nos brinda un conjunto de muestras que sirven de ejemplo del comportamiento real de la población. ● Nuestros datos provienen siempre de una población - Siempre necesitamos contexto (metadata)

Nuestra muestra va a estar siempre dada, y va a venir en uno o más archivos (o en una base de datos).

**Tendremos poco control sobre el**

proceso de sampleo!

**Más info:**

sdfsdfsdf

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 459x174px, 458x173pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Repasemos de qué hablamos cuando hablamos de

# Datos / Observaciones

Ejemplo: housing.csv

**● Observación**

(individuo, a veces“sample” también) = cada elemento de la muestra. ○ Registro de una base de datos, fila de una tabla.

**● Cada observación tiene un conjunto de atributos**

(descriptores, características, variables, features) asociados. ○ Campos de cada registro, columnas de una tabla. ● Cada atributo tiene un tipo de dato asociado: ○ Cualitativo (categórico) ■ Ordinal: si puedo establecer una relación de orden \<“2do año”) 1er año” entre dos valores (“ inglés”) ■ Nominal: si no hay orden (“argentino”,“ ○ Cuantitativo (numérico) ■ Continuo:“se puede dividir” altura”) (“ ■ Discreto:“no se puede dividir” nro. hijos”) (“ ● Y las binarias?

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 351x183px, 350x183pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 236x148px, 235x147pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Repasemos de qué hablamos cuando hablamos de

# Datos / Matriz de diseño

**El conjunto de observaciones y sus vectores de características asociados**

suele representarse en una matriz de diseño

2\) lantas atio? erficie (en m m de frente Nro de p Sup Tiene p Casa 1 150 1 20 2

Casa 2 22 0 5 1

Casa 3 76 0 21 1

Casa 4 98 1 35 2

… … … …

150 1 20 2

22 0 5 1 : 76 0 21 1

98 1 35 2

… … … …

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 52x43px, 52x43pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 22x32px, 21x31pt, ~74dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 30x25px, 30x25pt, ~73dpi, JPG, DEVICE_RGB, 32bpp>

Ahora sí - Hablemos de

# Almacenamiento de datos

**Algunos de los formatos de archivo más utilizados para almacenar y compartir**

**datos**

**.csv**

Texto plano con separadores de columnas (ej. comas) y

**.txt**

separados de línea (ej. saltos de línea \\n)

**.dat**

Ocupan más espacio, pero los puedo abrir hasta en Excel!

**.pkl**

Archivos con compresión que permiten hacer persistencia

**.mat**

de objetos (incluyendo tablas) Necesito rutinas especiales para abrirlos, pero pesan bastante menos .db

**.xlsx**

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Ahora sí - Hablemos de

# Almacenamiento de datos

**Algunos de los formatos de archivo más utilizados para almacenar y compartir**

**datos**

**.csv**

Texto plano con separadores de columnas (ej. comas) y

**.txt**

separados de línea (ej. saltos de línea \\n)

**.dat**

Ocupan más espacio, pero los puedo abrir hasta en Excel!

**.pkl**

Archivos con compresión que permiten hacer persistencia

**.mat**

de objetos (incluyendo tablas) Necesito rutinas especiales para abrirlos, pero pesan bastante menos .db

**.xlsx**

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Almacenamiento de datos

# Los archivos TXT

**● El clásico archivo de texto del bloc de notas**

● No hay formato ni estructura ● Son fáciles de leer y escribir desde el código, pero es difícil extraer su estructura. ● Son compatibles universalmente (no necesito un software especializado para leerlos). ● No son eficientes si manejo un volumen grande de datos. ● Atención a la codificación! ○ UTF-8 vs. ASCII - Las famosas tildes rotas ● No usen TXT para guardar datos estructurados! Usen otros formatos

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 294x220px, 293x220pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 233x236px, 233x236pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 86x86px, 85x85pt, ~73dpi, JPG, DEVICE_RGB, 32bpp>

Almacenamiento de datos

# Los archivos CSV

**● CSV = Comma Separated Value = Archivo**

separado por comas. ● Cada campo está separado por una coma. ● Se usa el \\n para indicar cambios de registro. ● Normalmente incluyen una primera fila para el header (cabecera, nombre de los atributos) ● Se puede abrir en software de hoja de cálculo sin problemas. ● Que se llame CSV no implica que sí o sí use comas para separarlos ○ ¿Qué pasa si usamos“,” de decimales? → Usemos“;” ○ Si no usan comas, avisen!

**Header**

**Registro**

**Podés ver acá cómo abrir un archivo CSV en**

como separador

**Excel, en Numbers y en LibreOffice**

para separar (un readme)

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 460x259px, 460x258pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Almacenamiento de datos

# Los archivos XLSX

**● XLSX = Archivo de datos de Excel**

(a partir de Excel 2007, antes era XLS). ● Es un archivo binario (no es texto plano) ● Internamente, es un archivo .zip formado por varios archivos internos: ○ Varios XML explicando la estructura de los datos y del archivo, el formato para mostrarlo, etc. ○ Un archivo con los datos crudos. ● Permite almacenar hasta 1M de registros, con 16.000 columnas. ● Recomendado para compartir datos con gente que no es experta, porque es fácil de abrir con herramientas de cálculo comunes. ● No es buena idea compartir datos crudos en este formato.

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 192x192px, 192x192pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Almacenamiento de datos

# Los archivos PKL

**● PKL = Archivo pickle**

(sí, como las verduritas encurtidas!). ● Es un archivo binario (no es texto plano) que se usa para serializar objetos de Python ○ Serializar un objeto = guardar una copia exacta del estado de un objeto, tal como estaba en RAM en ese momento ● Puedo guardar lo que se me ocurra, manteniendo la estructura original del objeto, y permitiéndome operar con él como estaba. e puedo meter cualquier ● No es seguro contra datos maliciosos-T cosa adentro sin que te des cuenta (pickle envenenado!) ● Hay que usarlos con cuidado, y para casos bien específicos ○ Checkpoints en pipelines de procesamiento de datos ○ Cosas que son extremadamente grandes como para bajar en archivos no binarios.

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 142x199px, 142x199pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 101x110px, 101x109pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Librerías de Python para Data Science

# Pandas

● Librería open source de Python para hacer análisis y manipulación de datos ● Tiene estructuras propias para facilitar el trabajo con datos (DataFrame, Series, …) “ ○ Como trabajar con una BD, pero con código imperativo” ● Permite leer archivos que vienen en distintos formatos (CSV, XLSX, SQL, etc.) ● Tiene muchas herramientas para limpieza y transformación de los datos, para fusionarlos, agruparlos, indexarlos rápidamente, e incluso visualizarlos (aunque con otras herramientas). ● Es la librería que más vamos a usar en el curso!

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 198x80px, 197x80pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 327x184px, 327x184pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

\- ciencia datos-unicen- practica-2- python.ipynb

<image redacted: 960x415px, 960x415pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Librerías de Python para Data Science

# Pandas / DataFrames y Series

**● DataFrame → estructura de datos bidimensional**

○ Una especie de tabla/hoja de cálculo. ○ Facilita bastante manipular y analizar datos estructurados ■ Operaciones vectorizadas → Procesa rapidísimo todo lo que le pidamos ■ Indexa los datos → Podemos hacer búsquedas muy eficientes

**● Serie → estructura de datos unidimensional**

○ Secuencia ordenada de datos ○ El equivalente a una columna o una lista ○ DataFrame =“ de Series arreglo”

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 284x371px, 284x371pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

\- ciencia datos-unicen- practica-2- python.ipynb

<image redacted: 960x415px, 960x415pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Miremos un poco los datos

# Boston

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 421x397px, 421x396pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

<image redacted: 488x325px, 487x325pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>

Acceso a datos y análisis (parte I) ¿Qué vimos hoy?

1\. Repasamos lo que van a ver el jueves en la teoría! 2. Los tipos de datos más comunes para compartir data estructurada 3. ¿Cómo usar Python para leer este tipo de archivos? 4. ¿Cómo usar Pandas para hacer análisis exploratorio del contenido de estos archivos?

**Material adicional:**

● ¿Qué es un DataFrame? Un video cortito yendo más al hueso. ● Curso de Pandas desde cero (7 videos). ● Curso de Python con Pandas desde cero (11 videos) ● Capítulo 4 del libro de Nathan George.

<image redacted: 960x541px, 960x541pt, ~72dpi, JPG, DEVICE_RGB, 32bpp>