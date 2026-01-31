# 📊 Predicción de Fuga de Clientes (Churn) – Regresión Logística

**Autor:** Felipe Santiago Goicolea Guerra  

![Machine Learning](https://img.shields.io/badge/Machine%20Learning-II-blue)
![Python](https://img.shields.io/badge/Python-3.9+-green)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Latest-orange)

Este repositorio contiene la **Actividad 1** del Magíster en Data Science (UDLA), **desarrollada íntegramente por mí** como parte del curso de Machine Learning.  
El proyecto aborda el problema de la deserción de clientes en telecomunicaciones utilizando **Regresión Logística**, comparando la complejidad de modelos polinomiales frente a la estabilidad y capacidad de generalización de modelos regularizados.

---

## 📋 Contexto del Negocio  

La identificación temprana de clientes con alta probabilidad de abandonar la empresa (*Churn*) es clave para optimizar las estrategias de retención y reducir pérdidas económicas.  
En este trabajo utilicé un dataset con información demográfica, de servicios contratados y de facturación para construir un modelo capaz de clasificar a los clientes según su riesgo de fuga.

---

## 🎯 Objetivos  

Los principales objetivos de esta actividad fueron:

- **Construir un pipeline robusto:** automatizar el preprocesamiento, escalado y modelado de los datos.
- **Ingeniería de características:** evaluar el impacto de transformaciones polinomiales de grado 2 sobre el desempeño del modelo.
- **Regularización:** optimizar hiperparámetros de regularización $L_1$ (Lasso) y $L_2$ (Ridge) mediante `GridSearchCV`.
- **Evaluación del modelo:** analizar el rendimiento considerando el desbalance de clases, utilizando métricas como Precision, Recall, F1-Score, ROC-AUC y PR-AUC.

---

## 🛠️ Metodología y Tecnologías  

### Stack Técnico  

- **Procesamiento de datos:** `Pandas`, `NumPy`.
- **Modelado:** `Scikit-Learn` (Pipelines, ColumnTransformer, StratifiedKFold).
- **Visualización:** `Matplotlib`, `Seaborn`.

### Flujo de Trabajo (Pipeline)  

1. **Limpieza de datos:** tratamiento de valores faltantes en `TotalCharges` y eliminación de variables irrelevantes como `customerID`.
2. **Codificación:** aplicación de `OneHotEncoder` para variables categóricas.
3. **Escalado:** uso de `StandardScaler` para asegurar una correcta convergencia del modelo de regresión logística.
4. **Expansión polinomial:** generación de interacciones entre variables numéricas.
5. **Validación:** validación cruzada con K-Fold estratificado para manejar el desbalance de la variable objetivo.

---

## 📊 Hallazgos y Resultados  

### Comparación de Modelos  

A partir de los experimentos realizados, se observó que:

- **Modelos polinomiales:** permiten capturar relaciones no lineales entre las variables, pero incrementan significativamente la dimensionalidad del problema, aumentando el riesgo de sobreajuste.
- **Regularización (parámetro $C$):** la aplicación de penalizaciones permitió controlar la magnitud de los coeficientes, logrando modelos más estables y con mejor capacidad de generalización en datos no vistos.

### Análisis del Trade-off Precision–Recall  

Del análisis crítico de resultados se concluyó que la métrica a priorizar depende del contexto del negocio:

- **Campañas de bajo costo (por ejemplo, emails):** es preferible priorizar el **Recall**, con el objetivo de detectar la mayor cantidad posible de clientes en riesgo de fuga.
- **Campañas de alto costo (por ejemplo, descuentos o beneficios económicos):** resulta más conveniente priorizar la **Precision**, evitando invertir recursos en clientes que no tenían intención de abandonar la empresa.

---

## ✅ Conclusión  

Este proyecto me permitió aplicar de forma práctica conceptos clave de machine learning, como pipelines, regularización, manejo de desbalance de clases y análisis de métricas más allá de la Accuracy.  
Los resultados muestran que, en problemas reales de negocio, la selección del modelo y de las métricas debe estar fuertemente alineada con los costos y objetivos estratégicos de la organización.
