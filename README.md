# Telecom X – Parte 2: Predicción de Cancelación de Clientes (Churn)


## 1. Resumen del Proyecto

Este repositorio contiene el desarrollo de un proyecto de Machine Learning para predecir la cancelación de clientes (churn) en la empresa ficticia de telecomunicaciones "Telecom X". El objetivo es construir un pipeline completo, desde el preprocesamiento de datos hasta el entrenamiento, evaluación e interpretación de modelos de clasificación, con el fin de identificar proactivamente a los clientes con mayor probabilidad de abandonar el servicio.


## 2. Problema de Negocio

La cancelación de clientes es uno de los problemas más críticos para las empresas de servicios por suscripción como Telecom X. Adquirir un nuevo cliente es significativamente más costoso que retener a uno existente. Este proyecto aborda la necesidad de reducir la pérdida de ingresos y mejorar la lealtad del cliente mediante la creación de un sistema de alerta temprana basado en datos. El modelo predictivo servirá como base para diseñar y dirigir estrategias de retención efectivas.


## 3. Conjunto de Datos

Se utilizó el conjunto de datos `Telco Customer Churn`, que contiene información demográfica de los clientes, los servicios que han contratado, y su estado actual (si cancelaron o no).

- **Fuente:** IBM Sample Data Sets, comúnmente encontrado en plataformas como Kaggle.
- **Características:** 7043 observaciones y 21 variables, incluyendo:
  - `gender`, `SeniorCitizen`, `Partner`, `Dependents` (Datos demográficos)
  - `tenure`, `Contract`, `PaymentMethod`, `MonthlyCharges`, `TotalCharges` (Información de la cuenta)
  - `PhoneService`, `MultipleLines`, `InternetService`, `OnlineSecurity`, etc. (Servicios contratados)
  - `Churn` (Variable objetivo)


## 4. Metodología

El proyecto siguió un pipeline estructurado de Machine Learning:

1.  **Preprocesamiento de Datos:**
    - Limpieza y corrección de tipos de datos.
    - Manejo de valores faltantes.
    - Codificación de variables categóricas mediante One-Hot Encoding.
    - Balanceo de clases utilizando la técnica SMOTE para corregir el desequilibrio en la variable objetivo.
    - Estandarización de variables numéricas con `StandardScaler` para preparar los datos para modelos sensibles a la escala.

2.  **Análisis Exploratorio de Datos (EDA):**
    - Visualización de la distribución de las variables.
    - Análisis de correlación para identificar las relaciones iniciales entre las características y la variable `Churn`.

3.  **Modelado:**
    - Se entrenaron y compararon dos modelos de clasificación:
      - **Regresión Logística:** Como un modelo base robusto, interpretable y sensible a la escala de los datos.
      - **Árbol de Decisión:** Como un modelo no lineal que no requiere estandarización.

4.  **Evaluación de Modelos:**
    - Se evaluaron los modelos utilizando una matriz de confusión y métricas clave como Exactitud, Precisión, F1-Score y, de forma prioritaria, el **Recall**, para maximizar la detección de clientes que realmente van a cancelar.

5.  **Análisis de Importancia de Variables:**
    - Se interpretaron los resultados para identificar los factores más influyentes en la predicción, utilizando los coeficientes de la Regresión Logística y la importancia de características del Árbol de Decisión.


## 5. Resultados Clave

- El modelo de **Regresión Logística** fue seleccionado como el de mejor rendimiento, logrando un **Recall del 84.2%** en el conjunto de prueba. Esto significa que es capaz de identificar correctamente a 84 de cada 100 clientes que están a punto de cancelar.

- Los **principales factores que impulsan la cancelación** de clientes son:
  1.  **Tipo de Contrato:** Tener un contrato `Mes a Mes` es el predictor más fuerte de churn.
  2.  **Antigüedad (Tenure):** Los clientes con pocos meses de servicio son mucho más propensos a cancelar.
  3.  **Cargos Mensuales:** Facturas mensuales elevadas se correlacionan con un mayor riesgo de churn.
  4.  **Servicio de Internet:** Contratar `Fibra Óptica` está asociado a una mayor tasa de cancelación, sugiriendo posibles problemas de precio o calidad.


## 6. Tecnologías Utilizadas

- **Python**
- **Pandas:** Para manipulación y análisis de datos.
- **Scikit-learn:** Para el preprocesamiento, modelado y evaluación.
- **Imbalanced-learn:** Para técnicas de remuestreo como SMOTE.
- **Matplotlib & Seaborn:** Para la visualización de datos.
- **Jupyter:** Como entorno de desarrollo interactivo.
