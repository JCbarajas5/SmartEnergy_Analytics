# ⚡ Smart Energy Analytics: Un Modelo de Decisión para Programas de Eficiencia Energética mediante Machine Learning
### Predicción, Detección de Anomalías y Segmentación de Hogares sobre Datos de Smart Meters, Segmentación y Detección de Anomalías en Consumo Energético Residencial para Programas de Eficiencia Energética

---

## 📌 Descripción del proyecto

Este proyecto desarrolla una solución de Machine Learning orientada a la toma de decisiones para una distribuidora de energía eléctrica que desea lanzar un **programa de eficiencia energética focalizado**.

A partir de datos reales de consumo de **5,567 hogares en Londres** (Smart Meters, 2011–2014), el equipo construye un sistema de análisis tipo consultoría que responde a la siguiente pregunta de negocio:

> **¿A cuáles de mis clientes debo contactar primero, y con qué oferta?**

La solución combina tres enfoques complementarios de Machine Learning para entregar recomendaciones accionables, no solo predicciones técnicas.

---

## 🎯 Objetivo

Desarrollar un pipeline completo de Machine Learning que permita a una distribuidora de energía:

1. **Predecir** el consumo energético diario por hogar para los próximos días
2. **Detectar** hogares con patrones de consumo anómalos que podrían beneficiarse de una auditoría energética
3. **Segmentar** la base de clientes en perfiles de consumo para personalizar tarifas, ofertas e intervenciones

---

## 📦 Dataset

| Campo | Detalle |
|---|---|
| **Fuente** | [Smart Meters in London — Kaggle](https://www.kaggle.com/datasets/jeanmidev/smart-meters-in-london) |
| **Origen** | UK Power Networks (London Data Store) |
| **Hogares** | 5,567 |
| **Período** | Noviembre 2011 — Febrero 2014 |
| **Granularidad** | Lecturas cada 30 minutos por hogar |
| **Variables adicionales** | Clima diario (DarkSky API), grupo socioeconómico (ACORN), tipo de tarifa (Estándar / ToU) |

---

## 🔬 Alcance técnico

El proyecto cubre las siguientes etapas:

### 1. Preparación de datos
- Consolidación de múltiples fuentes (consumo, clima, metadatos de hogares)
- Limpieza y tratamiento de valores faltantes
- Filtrado de hogares con cobertura temporal insuficiente
- Análisis Exploratorio de Datos (EDA)

### 2. Feature Engineering
- Variables temporales: hora, día de semana, mes, estación
- Variables climáticas: temperatura media, Heating Degree Days (HDD), humedad
- Lag features por hogar: consumo hace 1 día, 7 días
- Rolling averages: promedio móvil 7 y 30 días por hogar
- Perfil agregado por hogar para segmentación

### 3. Modelado
Se aplican al menos dos algoritmos de Machine Learning con justificación técnica:

| Modelo | Tipo | Objetivo |
|---|---|---|
| Random Forest / XGBoost | Regresión | Predicción de consumo diario |
| Isolation Forest | Detección de anomalías | Identificar hogares con consumo inusual |
| K-Means + PCA | Clustering | Segmentación de hogares por perfil de consumo |

### 4. Evaluación
- Comparación de modelos con métricas adecuadas (MAE, RMSE, Silhouette Score)
- Validación con train/test split y cross-validation
- Análisis de overfitting/underfitting
- Identificación de limitaciones

### 5. Interpretación y toma de decisiones
- Traducción de resultados técnicos a recomendaciones accionables
- Estimación del ahorro potencial en kWh y valor económico
- Priorización de hogares para intervención

### 6. Visualización ejecutiva
- Dashboard interactivo (Streamlit) para usuario no técnico
- Predicción de consumo próximos 7 días
- Alertas de anomalías por hogar
- Mapa de segmentos de clientes

---

## 📁 Estructura del repositorio

```
├── README.md
├── data/
│   └── (instrucciones de descarga — dataset no incluido por tamaño)
├── notebooks/
│   ├── 01_eda_preparacion.ipynb        ← Limpieza, EDA, selección de variables
│   ├── 02_modelo_regresion.ipynb       ← Predicción de consumo
│   ├── 03_modelo_anomalias.ipynb       ← Detección de anomalías
│   └── 04_modelo_clustering.ipynb      ← Segmentación de hogares
├── dashboard/
│   └── app.py                          ← Dashboard Streamlit
├── reports/
│   └── reporte_consultoria.pdf         ← Reporte ejecutivo final
└── requirements.txt
```

---

## 👥 Equipo y roles

| Integrante | Rol | Responsabilidad principal |
|---|---|---|
| TBD | Data Engineer | Carga, limpieza y preparación del pipeline de datos |
| TBD | Data Analyst | EDA, visualizaciones y análisis de patrones |
| TBD | ML Engineer | Modelos, evaluación y comparación |
| TBD | Business Analyst | Interpretación, reporte ejecutivo y narrativa |

> Cada integrante trabaja en su rama individual (`feature/nombre-integrante`) e integra cambios a `main` vía Pull Request.

---

## 🚀 Cómo reproducir el proyecto

### 1. Clonar el repositorio
```bash
git clone https://github.com/<usuario>/<repositorio>.git
cd <repositorio>
```

### 2. Instalar dependencias
```bash
pip install -r requirements.txt
```

### 3. Descargar el dataset
```python
import kagglehub
path = kagglehub.dataset_download("jeanmidev/smart-meters-in-london")
print("Path:", path)
```

### 4. Ejecutar notebooks en orden
```
notebooks/01 → 02 → 03 → 04
```

### 5. Correr el dashboard
```bash
streamlit run dashboard/app.py
```

---

## 🛠️ Stack tecnológico

- **Lenguaje:** Python 3.10+
- **Manipulación de datos:** pandas, numpy
- **Visualización:** matplotlib, seaborn
- **Machine Learning:** scikit-learn, xgboost
- **Dashboard:** Streamlit
- **Entorno de desarrollo:** Google Colab / Jupyter Notebook
- **Control de versiones:** Git / GitHub

---

## 📊 Criterios de evaluación

Este proyecto es desarrollado como entregable final del curso de Machine Learning y es evaluado sobre los siguientes criterios: planteamiento del problema, preparación de datos, modelado, evaluación, interpretación, código, comunicación y dashboard.

---

*Proyecto Final — Curso de Machine Learning*
