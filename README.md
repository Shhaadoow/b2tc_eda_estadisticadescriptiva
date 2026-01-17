1. Definición del Análisis Exploratorio de Datos (EDA)
El Análisis Exploratorio de Datos (EDA) es un enfoque para entender un dataset antes de modelar o concluir, resumiendo sus características principales mediante estadística descriptiva y visualizaciones. Siguiendo la propuesta de John Tukey, el EDA se basa en “mirar primero” los datos para descubrir patrones, errores, rarezas y preguntas que los propios datos sugieren antes de aplicar modelos formales.

Importancia
Evita decisiones ciegas: un modelo puede aprender información incorrecta si los datos están sucios.
Detecta inconsistencias: valores imposibles, fechas mal interpretadas o texto con ruido.
Encuentra señales: distribuciones sesgadas, valores atípicos y relaciones entre variables.
Ejemplos del propósito
Si la variable budget contiene muchos valores 0 (que en cine suelen representar datos no registrados), el EDA permite detectarlo antes de calcular promedios engañosos.
Si release_date está almacenada como texto, el EDA obliga a convertirla a formato fecha para analizar tendencias temporales.
2. Objetivos del EDA
Comprender la estructura del dataset: tamaño, columnas, tipos de datos y valores únicos.
Evaluar la calidad de los datos: valores nulos, vacíos, duplicados, inconsistencias y outliers.
Resumir el comportamiento de las variables mediante medidas de tendencia central y dispersión.
Explorar hipótesis iniciales, como la relación entre presupuesto e ingresos.
Preparar los datos para análisis o modelado posterior.
3. Fases del EDA (flujo general)
Flujo general típico
Carga y vista general de los datos (head, info, diccionario de datos).
Limpieza de datos (Data Cleaning) ← fase crítica.
Análisis univariable.
Análisis bivariable o multivariable.
Conclusiones y dataset final listo.
3.1 Limpieza de Datos: procesos clave
Nota: Un valor nulo no siempre se representa como NaN. En datasets reales puede aparecer como cadenas vacías (""), "N/A", "null" o incluso como 0 en columnas numéricas.

(1) Detección y manejo de valores faltantes
Descripción:
Se identifican valores faltantes reales (NaN) y valores faltantes implícitos (vacíos o ceros con significado de desconocido).

Estrategias:

Eliminación de registros cuando la ausencia es mínima.
Imputación:
Numéricos: media o mediana.
Texto o categóricos: moda o valor "Unknown".
Temporales: imputación por grupos (por ejemplo, por año o idioma).
Ejemplo:
En películas, un budget = 0 suele indicar que el dato no fue registrado, no que el costo haya sido cero.

(2) Eliminación de duplicados
Descripción:
Se detectan filas o identificadores repetidos.

Importancia:
Los duplicados inflan conteos y distorsionan promedios, correlaciones y rankings.

(3) Corrección de tipos de datos
Objetivo:
Garantizar coherencia en los tipos de datos:

Fechas como datetime.
Números como tipos numéricos.
Booleanos como valores lógicos.
(4) Normalización y limpieza de texto
Acciones comunes:

Eliminación de espacios innecesarios.
Normalización de mayúsculas y minúsculas.
Unificación de valores vacíos a NaN.
Esto evita duplicaciones semánticas como "Action" y " action ".

(5) Manejo de valores atípicos (outliers)
Método aplicado:
Regla del Rango Intercuartílico (IQR).

Opciones de tratamiento:

Conservar valores atípicos (EDA descriptivo).
Limitar valores extremos (winsorización).
Excluir valores erróneos.
(6) Renombrado de columnas
Buenas prácticas:

Uso de snake_case.
Nombres cortos y consistentes.
Eliminación de espacios y caracteres especiales.
4. Herramientas del EDA
4.1 Estadística descriptiva
Tendencia central: media, mediana y moda.
Dispersión: desviación estándar, varianza, IQR y rangos.
4.2 Visualizaciones
runtime_hist runtime_box corr_matrix budget_vs_revenue
5. Caso práctico con IA – Dataset Movies
Fase 1: Resumen y Limpieza (Vista General)
Evidencia del uso de IA
Para la fase de limpieza de datos se utilizó una herramienta de inteligencia artificial (Julius AI o Gemini), la cual permitió identificar valores faltantes explícitos e implícitos, registros duplicados, errores en los tipos de datos y valores atípicos mediante el método del rango intercuartílico (IQR).
El uso de IA facilitó una depuración más eficiente del dataset antes del análisis exploratorio.

Carga y resumen general
Separador del archivo: ;
Tamaño original: 99 filas × 28 columnas
Tipos de datos: 19 object, 5 int, 2 bool, 2 float
Limpieza de datos aplicada
Valores faltantes detectados en columnas como belongs_to_collection, budget, revenue, homepage y tagline.
Se eliminó un registro duplicado con id = 102051.
Se corrigió el tipo de dato de release_date a formato fecha.
Se normalizó texto eliminando espacios y unificando valores vacíos.
Se identificaron outliers mediante la regla IQR.
Se revisó la estandarización de nombres de columnas.
6. Análisis Univariable – Runtime
La variable runtime fue seleccionada por ser numérica, interpretable y presentar valores extremos.

Resumen estadístico:

Número de registros: 94
Mediana: ~99 minutos
Q1: ~85.5 | Q3: ~111.5
Outliers detectados: 10
La mayoría de las películas se concentra entre 90 y 110 minutos, con una cola derecha correspondiente a producciones de mayor duración.

7. Análisis Bivariable – Budget vs Revenue
Se analizaron películas con valores disponibles de presupuesto e ingresos.

Registros válidos: 9
Correlación de Pearson estimada: ~0.96
Existe una relación positiva fuerte entre presupuesto e ingresos, aunque el tamaño reducido de la muestra limita conclusiones definitivas.

Referencias
Hoaglin, D. C. (2003). John W. Tukey and data analysis. Statistical Science, 18(3).
Matplotlib. (2025). matplotlib.pyplot.boxplot. Matplotlib documentation.
NIST/SEMATECH. (n.d.). What are outliers in the data? e-Handbook of Statistical Methods.
pandas. (2025). pandas.DataFrame.describe. pandas documentation.
pandas. (2025). Working with missing data. pandas documentation.
pandas. (2025). pandas.DataFrame.drop_duplicates. pandas documentation.
pandas. (2025). pandas.to_datetime. pandas documentation.
scikit-learn. (2025). SimpleImputer. scikit-learn documentation.
Tukey, J. W. (1977). Exploratory Data Analysis. Addison-Wesley.
