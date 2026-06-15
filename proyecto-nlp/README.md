# Proyecto Final: Data Science III — NLP sobre Reseñas de E-Commerce

**Autora:** Lobo, Constanza Belén
**Carrera:** Data Science — Coderhouse

## Descripción

Este proyecto aplica técnicas de Procesamiento de Lenguaje Natural (NLP) sobre el dataset *Women's E-Commerce Clothing Reviews*, que contiene reseñas reales de clientas de un e-commerce de ropa femenina. El objetivo es analizar el texto de las reseñas para predecir si una clienta recomienda o no un producto, descubrir los temas principales de insatisfacción y segmentar el comportamiento por departamento, categoría de producto y grupo de edad.

## Objetivos

- Realizar un análisis exploratorio del dataset (ratings, edades, categorías de producto, longitud de reseñas).
- Preprocesar el texto (limpieza, tokenización, lematización y eliminación de stopwords, preservando negaciones relevantes para el análisis de sentimiento).
- Construir modelos de clasificación para predecir la recomendación (`Recommended IND`) a partir del texto.
- Aplicar Topic Modeling (LDA) para identificar los principales temas de insatisfacción en reseñas negativas.
- Segmentar resultados por departamento, clase de producto y grupo de edad.
- Implementar y ajustar una red neuronal con PyTorch como alternativa a los modelos clásicos.

## Estructura del proyecto

1. **EDA**: limpieza inicial, distribución de ratings, edades, categorías de producto y longitud de reseñas.
2. **Preprocesamiento NLP**: lowercasing, eliminación de puntuación, tokenización y lematización con spaCy, preservando negaciones (`not`, `no`, `never`).
3. **Modelo baseline (TF-IDF + Regresión Logística)**: clasificación con unigramas, análisis de palabras clave y errores (falsos positivos), y re-evaluación con unigramas + bigramas.
4. **LDA Topic Modeling**: identificación automática de temas en reseñas negativas y su relación con la tasa de recomendación.
5. **Segmentación**: tasa de recomendación por departamento, clase de producto, edad y cruce de tópicos con departamentos.
6. **Red Neuronal con PyTorch**: clasificación con manejo de desbalance de clases (pesos), múltiples iteraciones de ajuste de hiperparámetros (normalización, learning rate, dropout) y early stopping.

## Principales resultados

| Modelo | Accuracy | Macro F1 | Recall clase 0 (no recomienda) |
|---|---|---|---|
| Regresión Logística (unigramas) | 90.0% | 0.81 | 0.61 |
| Regresión Logística (uni + bigramas) | 90.0% | 0.81 | 0.58 |
| Red Neuronal PyTorch (LayerNorm, v3 final) | 89.0% | 0.83 | 0.80 |

- La Regresión Logística logra mayor accuracy general, pero con menor capacidad de detectar reseñas negativas (clase minoritaria).
- La red neuronal con LayerNorm (en lugar de BatchNorm, más adecuado para vectores TF-IDF dispersos) logra un mejor balance entre clases, priorizando el recall de la clase negativa, clave para detectar insatisfacción real de clientas.
- El ajuste de hiperparámetros de la red neuronal requirió varias iteraciones: configuraciones con BatchNorm sufrieron colapso de clases o sobreajuste, resueltos al pasar a LayerNorm con dropout 0.3 y learning rate 0.001.

## Datos

El dataset se descarga automáticamente desde KaggleHub:
[Women's E-Commerce Clothing Reviews (Kaggle)](https://www.kaggle.com/datasets/nicapotato/womens-ecommerce-clothing-reviews)

## Tecnologías utilizadas

- Python (pandas, numpy)
- NLP: spaCy (tokenización, lematización, stopwords)
- Visualización: matplotlib, seaborn
- Modelado clásico: scikit-learn (TF-IDF, Regresión Logística, LDA)
- Deep Learning: PyTorch (red neuronal con manejo de desbalance de clases)
- Google Colab

## Cómo ejecutar

1. Abrir el notebook `ProyectoFinalDSIII_Lobo.ipynb` en Google Colab.
2. Ejecutar las celdas en orden; el dataset se descarga automáticamente vía `kagglehub`.
3. La celda de spaCy instala el modelo `en_core_web_sm` automáticamente.
