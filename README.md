# Análisis Exploratorio de Datos (EDA) – Dataset Movies 🎬📊

Este repositorio documenta el desarrollo de un **Análisis Exploratorio de Datos (EDA)** aplicado a un dataset de películas, con énfasis en la **limpieza de datos**, el uso de **estadística descriptiva**, **visualización** y el **apoyo de herramientas de Inteligencia Artificial**.

---

## 📌 1. Definición del Análisis Exploratorio de Datos (EDA)

El **Análisis Exploratorio de Datos (EDA)** es un enfoque para entender un dataset antes de modelar o concluir, resumiendo sus características principales mediante **estadística descriptiva** y **visualizaciones**.  
Siguiendo la propuesta de **John Tukey**, el EDA se basa en “mirar primero” los datos para descubrir patrones, errores, rarezas y preguntas que los propios datos sugieren antes de aplicar modelos formales.

### Importancia

- Evita decisiones ciegas: un modelo puede aprender información incorrecta si los datos están sucios.
- Detecta inconsistencias: valores imposibles, fechas mal interpretadas o texto con ruido.
- Encuentra señales: distribuciones sesgadas, valores atípicos y relaciones entre variables.

### Ejemplos del propósito

- Si la variable **budget** contiene muchos valores 0 (que en cine suelen representar datos no registrados), el EDA permite detectarlo antes de calcular promedios engañosos.
- Si **release_date** está almacenada como texto, el EDA obliga a convertirla a formato fecha para analizar tendencias temporales.

---

## 🎯 2. Objetivos del EDA

- Comprender la estructura del dataset (tamaño, columnas, tipos de datos).
- Evaluar la calidad de los datos (nulos, duplicados, inconsistencias y outliers).
- Resumir el comportamiento de las variables mediante medidas estadísticas.
- Explorar hipótesis iniciales (ej. presupuesto vs ingresos).
- Preparar los datos para análisis o modelado posterior.

---

## 🔄 3. Fases del EDA

1. Carga y vista general de los datos.
2. **Limpieza de datos (fase crítica).**
3. Análisis univariable.
4. Análisis bivariable/multivariable.
5. Conclusiones y dataset final listo.

---

## 🧹 3.1 Limpieza de Datos

> **Nota:** Un valor nulo no siempre se representa como `NaN`. En datasets reales puede aparecer como `""`, `"N/A"`, `"null"` o incluso como `0`.

### (1) Valores faltantes
- Identificación de valores faltantes reales e implícitos.
- Estrategias:
  - Eliminación de registros.
  - Imputación:
    - Numéricos: media o mediana.
    - Texto: moda o `"Unknown"`.
    - Temporales: imputación por grupos.

**Ejemplo:**  
En películas, un **budget = 0** suele indicar dato no registrado.

---

### (2) Eliminación de duplicados
- Detección de filas o identificadores repetidos.
- Evita distorsión de conteos, promedios y correlaciones.

---

### (3) Corrección de tipos de datos
- Fechas → `datetime`
- Números → tipos numéricos
- Booleanos → valores lógicos

---

### (4) Limpieza de texto
- Eliminación de espacios innecesarios.
- Normalización de mayúsculas/minúsculas.
- Unificación de valores vacíos a `NaN`.

---

### (5) Manejo de outliers
- Método aplicado: **Rango Intercuartílico (IQR)**.
- Opciones:
  - Conservar (EDA).
  - Limitar valores extremos.
  - Excluir valores erróneos.

---

### (6) Renombrado de columnas
- Uso de `snake_case`.
- Nombres cortos y consistentes.
- Sin espacios ni caracteres especiales.

---

## 📊 4. Herramientas del EDA

### Estadística descriptiva
- Tendencia central: media, mediana, moda.
- Dispersión: desviación estándar, varianza, IQR, rangos.

### Visualización
- Histogramas.
- Boxplots.
- Gráficos de dispersión.
- Matrices de correlación.

---

## 🤖 5. Caso Práctico con IA – Dataset Movies

### Fase 1: Resumen y Limpieza (Principal)

#### Evidencia del uso de IA
Para la limpieza de datos se utilizó una herramienta de **Inteligencia Artificial (Julius AI / Gemini)**, la cual permitió identificar valores faltantes explícitos e implícitos, registros duplicados, errores en los tipos de datos y valores atípicos mediante el método IQR.  
El uso de IA facilitó una depuración más eficiente del dataset antes del análisis exploratorio.

#### Resumen del dataset
- Separador: `;`
- Tamaño original: **99 filas × 28 columnas**
- Tipos de datos: 19 `object`, 5 `int`, 2 `bool`, 2 `float`

---

## 📈 6. Análisis Univariable – Runtime

- Registros analizados: 94
- Mediana: ~99 minutos
- Rango intercuartílico: 85.5 – 111.5
- Outliers detectados: 10

La mayoría de las películas se concentra entre 90 y 110 minutos, con una cola derecha correspondiente a producciones de mayor duración.

---

## 🔗 7. Análisis Bivariable – Budget vs Revenue

- Registros con datos válidos: 9
- Correlación de Pearson estimada: ~0.96

Existe una relación positiva fuerte entre presupuesto e ingresos, aunque el tamaño reducido de la muestra limita conclusiones definitivas.

---

## 📂 8. Archivos Generados

<img width="915" height="766" alt="corr_matrix" src="https://github.com/user-attachments/assets/f505ccb7-373f-4294-ade8-f2d9998a0ce6" />

<img width="884" height="721" alt="budget_vs_revenue" src="https://github.com/user-attachments/assets/bebd435f-04e2-4321-9854-f7e9820f10c3" />

<img width="912" height="692" alt="runtime_box" src="https://github.com/user-attachments/assets/591690ba-ae0c-48d7-8ad5-def62f8e0bef" />

<img width="898" height="721" alt="runtime_hist" src="https://github.com/user-attachments/assets/142fedea-8fad-4d2d-b7ac-f6564fc3b325" />

---

## 📚 Referencias

- Hoaglin, D. C. (2003). *John W. Tukey and data analysis*. Statistical Science, 18(3).
- Matplotlib. (2025). *matplotlib.pyplot.boxplot*. Matplotlib documentation.
- NIST/SEMATECH. (n.d.). *What are outliers in the data?*
- pandas. (2025). *pandas.DataFrame.describe*.
- pandas. (2025). *Working with missing data*.
- scikit-learn. (2025). *SimpleImputer*.
- Tukey, J. W. (1977). *Exploratory Data Analysis*. Addison-Wesley.
