# 🚌 SF Transit Real-Time Analytics & ML Prediction System

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/downloads/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13+-336791.svg)](https://www.postgresql.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.28+-FF4B4B.svg)](https://streamlit.io/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3+-F7931E.svg)](https://scikit-learn.org/)

Sistema completo de análisis y predicción de tránsito en tiempo real para San Francisco Bay Area.

## 🎯 Características

- ✅ Monitoreo de ~1,140 vehículos en tiempo real
- ✅ Modelo Random Forest con 90% de precisión (R² = 0.9044)
- ✅ Predicción de ETA y sistema de alertas
- ✅ Dashboard interactivo con Streamlit

## 📊 Resultados

**Métricas del Sistema:**
- Precisión: R² = 90.44%
- Error: ±4.67 km/h
- Datos: 19,150+ registros procesados

**Comparación de Modelos ML:**

| Modelo | RMSE (km/h) | MAE (km/h) | R² Score | Hiperparámetros Clave |
|--------|-------------|------------|----------|----------------------|
| **Random Forest** ⭐ | **4.67** | **2.61** | **0.9044** | n_estimators=100, max_depth=15 |
| Lasso | 4.89 | 3.18 | 0.8952 | alpha=0.1 |
| Linear Regression | 4.90 | 3.19 | 0.8945 | - |
| Ridge | 4.91 | 3.20 | 0.8943 | alpha=1.0 |
| Decision Tree | 4.92 | 2.77 | 0.8938 | max_depth=10, min_samples_split=20 |
| Gradient Boosting | 4.96 | 2.81 | 0.8919 | n_estimators=100, learning_rate=0.1 |

## 🚀 Uso Rápido

```bash
# 1. Recolectar datos
python 01_data_ingestion_511.py

# 2. Análisis y ML
python 02_exploratory_analysis.py
python 03_data_preprocessing.py
python 04_train_models.py

# 3. Dashboard
streamlit run 07_advanced_dashboard.py
## 📁 Estructura del Proyecto

San-Francisco-transit/ ├── 01_data_ingestion_511.py # Ingesta de datos API 511.org ├── 02_exploratory_analysis.py # Análisis exploratorio (EDA) ├── 03_data_preprocessing.py # Feature engineering (25+ features) ├── 04_train_models.py # Entrenamiento ML (6 modelos) ├── 06_eta_and_alerts.py # Sistema de ETA y alertas ├── 07_advanced_dashboard.py # Dashboard Streamlit avanzado ├── data/processed/ # Datasets procesados ├── models/ # Modelos entrenados (.pkl) ├── plots/ # Visualizaciones ├── requirements.txt └── README.md

## 🔬 Metodología

### Cálculo de Velocidades (Haversine)
La API 511.org **NO proporciona velocidades**, solo coordenadas GPS. Calculamos velocidades usando la fórmula de Haversine para distancias esféricas.

### Feature Engineering
**25+ features creados:**
- **Temporales:** hour, day_of_week, is_weekend, is_rush_hour
- **Geográficos:** distance_to_center, zone, is_in_downtown
- **Movimiento:** acceleration, heading_change, is_stopped
- **Agregados:** avg_speed_vehicle, std_speed_vehicle, max_speed_vehicle

## 🎨 Dashboard Interactivo

**4 tabs principales:**

1. **Monitoreo General** - Panel de alertas y mapa en tiempo real
2. **Calculadora de ETA** - Predicción de tiempo de llegada
3. **Comparador de Rutas** - Análisis comparativo de rutas
4. **Rastreador de Vehículos** - Seguimiento individual con historial

## 🛠️ Tecnologías

- Python 3.9+, PostgreSQL 13+
- scikit-learn, Pandas, NumPy
- Streamlit, Plotly
- API 511.org (GTFS-Realtime)

## 📦 Instalación

```bash
git clone https://github.com/FNarvaezmo/San-Francisco-transit.git
cd San-Francisco-transit
python3 -m venv env_data
source env_data/bin/activate
pip install -r requirements.txt
💡 Casos de Uso
Pasajeros: Predecir tiempos de llegada reales
Agencias: Detectar congestiones y optimizar rutas
Planificación urbana: Analizar patrones de tráfico
Apps de navegación: Integrar predicciones ML
🚧 Mejoras Futuras
 Deployment en cloud (AWS/Heroku)
 API REST con FastAPI
 Sistema de notificaciones
 Modelo LSTM para series temporales
 App móvil
 Docker containerization
👥 Autores
Francisco Narvaez M
GitHub: @FNarvaezmo

Karen Gómez
Contribuciones al análisis y desarrollo

📄 Licencia
MIT License
Agradecimientos
511.org - API de datos en tiempo real
Streamlit - Plataforma de visualización
scikit-learn - Herramientas ML
Versión: 1.0.0
Fecha: 2025-11-12 EOF


