# Proyecto Final: Data Science — Estructuras Productivas Agrícolas y Ganaderas (1961-2023)

**Autora:** Lobo, Constanza Belén
**Carrera:** Data Science — Coderhouse

## Descripción

Este proyecto analiza la evolución de las estructuras productivas agrícolas y ganaderas a nivel global entre 1961 y 2023, utilizando datos históricos de FAOSTAT. Se exploran patrones de producción, transiciones estructurales entre países y su relación con el nivel de desarrollo económico, y se integra información climática para modelar la producción agrícola mediante distintos algoritmos de regresión.

## Hipótesis

Los países con menor desarrollo económico tienden a mantener estructuras agrícolas relativamente estables, mientras que las economías de mayores ingresos muestran mayor diversificación y cambios estructurales, impulsados por la demanda global y políticas de valor agregado.

## Objetivos

- Caracterizar tendencias temporales en la orientación productiva (agrícola vs. ganadera) de cada país.
- Comparar patrones productivos entre grupos de países según nivel de ingreso.
- Identificar transiciones estructurales (diversificación, consolidación, cambios de perfil).
- Integrar datos climáticos históricos y evaluar su relación con la producción.
- Construir y comparar modelos predictivos de producción agrícola normalizada.

## Estructura del proyecto

1. **Análisis exploratorio (FAOSTAT)**: limpieza y transformación del dataset (wide → long → wide), clasificación de productos en agrícolas/ganaderos, visualizaciones globales y por país, rankings, heatmaps y análisis de tendencias.
2. **Incorporación de datos climáticos**: integración de variables climáticas (NASA POWER) para el top 10 de países productores (China, India, Brasil, EE.UU., Rusia, Pakistán, Indonesia, Tailandia, Nigeria, México).
3. **Modelado predictivo**: comparación de cinco modelos de regresión (Lineal, Ridge, Random Forest, SVR, KNN) y optimización mediante GridSearchCV.

## Principales resultados

- Los países de menor desarrollo (Nigeria, Indonesia, Tailandia) mantienen estructuras agrícolas estables a lo largo del tiempo.
- Economías más desarrolladas (EE.UU., Alemania, Francia) muestran mayor diversificación y crecimiento de la proporción ganadera.
- Random Forest fue el modelo con mejor desempeño (R² ≈ 0.72), superando a los modelos lineales tras filtrar variables colineales.
- Se construyó un pipeline reproducible: selección de variables, escalado, entrenamiento, optimización y evaluación comparativa.

## Datos

Por su tamaño, el dataset principal no se incluye en este repositorio. Puede descargarse desde:
[FAOSTAT Crops and Livestock Data (Kaggle)](https://www.kaggle.com/datasets/vijayveersingh/faostat-crops-and-livestock-data)

Los datos climáticos provienen de [NASA POWER Data Access Viewer](https://power.larc.nasa.gov/data-access-viewer/).

## Tecnologías utilizadas

- Python (pandas, numpy)
- Visualización: matplotlib, seaborn
- Modelado: scikit-learn (Linear Regression, Ridge, Random Forest, SVR, KNN, GridSearchCV)
- Google Colab

## Cómo ejecutar

1. Descargar el dataset de FAOSTAT desde el enlace de Kaggle.
2. Abrir el notebook `ProyectoFinalDS_Lobo.ipynb` en Google Colab.
3. Montar Google Drive y ajustar las rutas de los archivos a tu propia estructura de carpetas.
4. Ejecutar las celdas en orden.
