%%writefile README.md
# 🏦 Sistema de Predicción de Riesgo de Crédito (Credit Default Risk)

![Python](https://img.shields.io/badge/Python-3.9%2B-blue)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit_Learn-orange)
![FastAPI](https://img.shields.io/badge/Framework-FastAPI-009688)
![Streamlit](https://img.shields.io/badge/Frontend-Streamlit-FF4B4B)

## 📋 Descripción del Proyecto
Este proyecto es una solución integral de Machine Learning diseñada para ayudar a instituciones financieras a evaluar el riesgo de impago (default) de solicitantes de crédito.

El sistema utiliza una arquitectura modular basada en la metodología **CRISP-DM** (Cross Industry Standard Process for Data Mining) para estructurar el flujo de trabajo desde la preparación de datos hasta el despliegue en producción.

## 🚀 Funcionalidades Principales
1.  **Integración de Datos Compleja:** Fusiona datos demográficos (`application`), historial de pagos de cuotas (`installments`) y comportamiento en burós de crédito externos (`bureau`).
2.  **Ingeniería de Características:** Genera variables agregadas inteligentes (ej. promedio de días de atraso, deuda total externa) para mejorar la predicción.
3.  **Modelo Robusto:** Utiliza un **Random Forest Classifier** optimizado para clases desbalanceadas.
4.  **API REST:** Microservicio construido con **FastAPI** para realizar inferencias en tiempo real.
5.  **Dashboard Interactivo:** Interfaz de usuario construida con **Streamlit** para visualización de riesgo y toma de decisiones.

 # 👣 Paso a Paso: Metodología Aplicada

El desarrollo del proyecto siguió 5 fases secuenciales lógicas (CRISP-DM):

1.  **Entendimiento de Datos:** Se exploraron las tablas `application`, `bureau` e `installments`, detectando desbalance de clases.
2.  **Preparación de Datos:** Se creó `feature_engineering.py` para generar variables agregadas (ej. promedios de atrasos) y unir las tablas.
3.  **Modelado:** Se entrenó un **Random Forest** con `class_weight='balanced'` dentro de un Pipeline.
4.  **Evaluación:** Se validó con métricas AUC-ROC y Matriz de Confusión, priorizando la detección de morosos.
5.  **Despliegue:** Se implementó una API (FastAPI) y un Dashboard (Streamlit).

---

## 💡 Conclusión y Recomendación

Tras la evaluación del prototipo, se presentan las siguientes conclusiones para el negocio:

1.  **Viabilidad Técnica:** La arquitectura de microservicios permite escalar y mantener el código fácilmente.
2.  **Capacidad Predictiva:** El modelo es capaz de distinguir patrones de riesgo basándose en el comportamiento histórico de pagos.
3.  **Valor:** La API y el Dashboard facilitan el uso de IA por parte de los ejecutivos sin conocimientos técnicos.

**Veredicto:** Se recomienda la adopción de esta metodología para reducir la exposición al riesgo financiero.

## 📂 Estructura del Proyecto (Microservicios)

El código está organizado siguiendo buenas prácticas de ingeniería de software:

```text
/proyecto_riesgo_credito
│
├── /01_data_understanding   # Análisis Exploratorio de Datos (EDA) y Notebooks.
│   └── eda_analisis.ipynb
│
├── /02_data_preparation     # Scripts de limpieza e ingeniería de features.
│   └── feature_engineering.py
│
├── /03_modeling             # Scripts de entrenamiento y persistencia del modelo.
│   └── train_model.py
│
├── /04_evaluation           # Scripts para generar métricas y gráficos de rendimiento.
│   └── evaluate_model.py
│
├── /05_deployment           # Código fuente de la API y el Dashboard.
│   ├── app.py
│   └── dashboard.py
│
├── /artifacts               # Artefactos generados (Modelo .joblib, Scalers, Features).
├── /data                    # Archivos fuente en formato Parquet.
├── /reports                 # Reportes generados (Matriz de Confusión, Curva ROC).
├── requirements.txt         # Dependencias del proyecto.
└── README.md                # Documentación.
