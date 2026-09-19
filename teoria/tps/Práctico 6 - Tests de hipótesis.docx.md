**Fundamentos de la Ciencia de Datos**

**Cursada 2026**

**Práctico 6: Tests de hipótesis**

disponible en: 1.​Utilizando el conjunto de datos “Life expectancy”, https://raw.githubusercontent.com/ignaciorlando/duia-ml-datasets/ master/LifeExpectancyWHO/Life Expectancy Data.csv: a.​Realizar todo el preprocesamiento necesario sobre todas las columnas. b.​Comprobar gráfica y estadísticamente si los países desarrollados tienen un producto per cápita mayor al de los en vías de desarrollo. Seleccionar el mejor test en función del objetivo y el cumplimiento de los supuestos. c.​Comprobar gráfica y estadísticamente si los países en vías de desarrollo gastan un menor porcentaje de su producto bruto en salud que los países desarrollados. Seleccionar el mejor test en función del objetivo y el cumplimiento de los supuestos. d.​Comprobar gráfica y estadísticamente si los países en vías de desarrollo tienen una expectativa de vida menor a los desarrollados. e.​¿Hay una relación entre la combinación de las variables producto per cápita y porcentaje del producto per cápita invertido en salud y la expectativa de vida? Seleccionar la mejor estrategia para aproximar esta conclusión. disponible en 2.​Utilizando el conjunto de datos “Life expectancy”, https://ignaciorlando.github.io/datasets/data-science/Life-Expect

ancy-Data-Updated.csv y cuya descripción está disponible en el sitio de Kaggle:

a.​Plantear al menos 6 hipótesis bivariadas y probarlas utilizando alguna metodología gráfica y un test de hipótesis. Validar previamente los supuestos. b.​Agrupar los países por continente y establecer hipótesis según los resultados obtenidos y validarlas estadísticamente empleando los test que mejor se ajusten. disponible en 3.​Utilizando el conjunto de datos“Health and sleep statistics”, https://www.kaggle.com/datasets/hanaksoy/health-and-sleep-statistics a.​Evaluar si hay una diferencia significativa en la calidad del sueño entre hombres y mujeres. b.​Examinar si el nivel de actividad física (alta vs. baja) afecta significativamente la calidad del sueño. c.​Comparar la cantidad de pasos diarios entre personas con hábitos alimenticios saludables y no saludables. d.​Plantear nuevas hipótesis y verificarlas usando herramientas vistas en la materia.

A continuación incluimos algunos ejercicios tipo parcial para que puedan hacer con papel y lápiz para prepararse mejor para el examen.

Ejercicio 1:

Para cada situación:

1\.​Identifique la variable respuesta y la variable que define los grupos. 2.​Determine si las muestras son independientes o relacionadas. 3.​Formule hipótesis nula y alternativa. 4.​Seleccione el test más apropiado. 5.​Indique sus supuestos y cómo los verificaría. 6.​Proponga una visualización complementaria.

**Situación Información disponible**

| A Se desea diferente de 100     | determinar si la duración media de las películas de una plataforma es minutos.                                        |
|---------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| B Se compara la aproximadamente | presión arterial entre dos grupos independientes. Los datos son normales, pero las varianzas son diferentes.          |
| C Se mide la intervención.      | calidad del sueño de las mismas 35 personas antes y después de una Las diferencias no siguen una distribución normal. |
| D Se compara el normales y las  | ancho del sépalo entre tres especies de iris. Los residuos son varianzas homogéneas.                                  |
| E Se compara distribuciones     | una escala ordinal de satisfacción entre cuatro servicios. Las son asimétricas.                                       |
| F Se desea categoría de         | evaluar si la presencia de trastornos del sueño está asociada con la índice de masa corporal.                         |

Ejercicio 2:

La calidad del sueño se registra mediante una escala entera de 1 a 10. Se desea determinar si existen diferencias entre hombres y mujeres. Suponga que se obtuvieron los siguientes resultados:

**Grupo nn Media Mediana RIC**

Mujeres 188 7.21 7 2

Hombres 187 6.94 7 2

Shapiro-Wilk, mujeres: W=0.903, p\<0.001 Shapiro-Wilk, hombres: W=0.917, p\<0.001

Mann-Whitney U, bilateral: U=15940, p=0.032

Responda:

1\.​Explique por qué la naturaleza de la escala debe considerarse al elegir el test. 2.​Formule H0 y H1 para el test utilizado. 3.​Interprete el resultado estadístico. 4.​¿Puede concluirse directamente que las medianas poblacionales son diferentes? Indique qué condición adicional permitiría esa interpretación. 5.​Analice la diferencia entre significancia estadística y relevancia práctica en este caso.

6\.​Un estudiante propone repetir el test con alternative=" porque la greater" media de las mujeres es mayor. Evalúe esa decisión. 7.​Proponga una visualización que muestre la distribución completa y no solamente las medias.

Ejercicio 3:

Un programa de ocho semanas busca mejorar la calidad del sueño. Se estudian 28 personas, medidas antes y después de la intervención.

| Momento              | Media     | Desvío |
|----------------------|-----------|--------|
| Antes                | 6,4       | 1,3    |
| Después              | 7,1       | 1,2    |
| Diferencia después − | antes 0,7 | 1,19   |

Shapiro-Wilk de las diferencias: W=0.961, p=0.238 Test t apareado: t=3.12, p=0.0043 IC 95% de la diferencia: \[0.23, 1.17\]

Responda:

1\.​Explique por qué las dos muestras no son independientes. 2.​Formule H0H\_0 y H1H\_1. 3.​¿Sobre qué valores debe comprobarse el supuesto de normalidad? 4.​Justifique la prueba utilizada. 5.​Interprete conjuntamente el p-valor y el intervalo de confianza. 6.​¿Qué significa el signo positivo de la diferencia? 7.​Explique por qué un test t para muestras independientes desperdiciaría información. 8.​¿Es posible atribuir causalmente el cambio a la intervención si no existió un grupo de control? 9.​Indique qué prueba utilizaría si las diferencias fueran fuertemente asimétricas.