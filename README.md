# 🧠 Workshop – Análisis de Sensibilidad de Hiperparámetros  
### Proyecto Integrador: AVSI (Visión Artificial de Apilamiento de Pañales)

## 📌 Descripción General

Este repositorio contiene el desarrollo completo del **Workshop de Optimización de Hiperparámetros**, aplicado al modelo de **visión por computador** del proyecto **AVSI**, cuyo objetivo es inspeccionar de forma automática el **apilamiento de pañales en línea de producción**, optimizando tanto la **precisión del modelo (mAP ≥ 0.7, IoU > 0.5)** como la **velocidad de inferencia (>30 FPS)**.

El análisis de sensibilidad permite identificar **qué hiperparámetros son críticos** para el rendimiento del modelo y cuáles tienen **bajo impacto**, con el fin de **optimizar el entrenamiento y la robustez** del sistema de IA industrial.

---

## 🧩 Contenido del Repositorio

| Archivo / Carpeta | Descripción |
|--------------------|-------------|
| `Narvaez_analisis_sensibilidad.ipynb` | Notebook principal del workshop. Contiene la búsqueda de hiperparámetros, análisis de sensibilidad, ranking de importancia y visualizaciones. |
| `VC_ResNet_18_Rev_2.ipynb` | Notebook base del proyecto AVSI con la arquitectura de ResNet-18 y pipeline de entrenamiento previo. |
| `figures_workshop/` | Carpeta donde se guardan los gráficos de salida: `partial_dependence.png`, `importance.png`, `interaction_*.png`. |
| `workshop_outputs/` | Contiene los resultados numéricos de la optimización: `search_results.csv`, `sensibilidad_table.csv`, `importance_table.csv`. |
| `Narvaez_reporte_optimizacion.pdf` | Plantilla del reporte final (2–3 páginas) con la estructura solicitada para entrega académica. |
| `README.md` | Este documento. |

---

## ⚙️ Tecnologías Utilizadas

- **Python 3.10+**
- **PyTorch / TensorFlow** (para el modelo AVSI)
- **Scikit-learn** (búsqueda y análisis)
- **Matplotlib / Pandas / NumPy**
- **ReportLab** (para generar reporte PDF)
- **ResNet-18 (Transfer Learning)** como base del modelo CNN

---

## 🧠 Metodología de Trabajo

### 1. Configuración Base  
Se documentaron los hiperparámetros actuales del modelo AVSI, incluyendo `learning_rate`, `batch_size`, `dropout_rate`, `optimizer`, `num_layers` y `num_neurons`.

### 2. Búsqueda Aleatoria  
Se ejecutó una búsqueda **RandomizedSearchCV** con validación cruzada (cv=3) sobre el dataset de entrenamiento del proyecto, evaluando 50 combinaciones de hiperparámetros.

### 3. Análisis de Sensibilidad  
Se generaron **Partial Dependence Plots (PDP)** para cada hiperparámetro, clasificándolos en:
- 🔴 Crítico  
- 🟠 Moderado  
- 🟢 Bajo  

### 4. Ranking de Importancia  
Mediante un **RandomForestRegressor meta-modelo**, se determinó el impacto porcentual de cada hiperparámetro sobre el rendimiento.

### 5. Interacciones  
Se analizaron las **interacciones sinérgicas o antagónicas** entre los 3 parámetros más influyentes mediante **heatmaps**.

### 6. Plan de Acción  
Se elaboró un plan en tres fases:
- **Fase 1:** Ajustes inmediatos (alta ganancia, bajo riesgo)  
- **Fase 2:** Refinamiento adicional (interacciones complejas)  
- **Fase 3:** Parámetros estables (mantener valores actuales)

---

## 📈 Resultados Esperados

| Indicador | Valor Actual | Valor Óptimo | Mejora (%) |
|------------|--------------|---------------|-------------|
| mAP | ≥ 0.70 | 0.74 | +5.7 % |
| IoU | > 0.50 | 0.54 | +8 % |
| FPS | > 30 | 32 FPS | +6 % |

> *Resultados estimados con base en el análisis de sensibilidad y ajustes sugeridos.*

---

## 📊 Visualizaciones Clave

- **Partial Dependence Plot (PDP):** Sensibilidad de cada hiperparámetro.  
- **Gráfico de Importancia:** Ranking de impacto porcentual.  
- **Heatmaps de Interacciones:** Efecto combinado entre hiperparámetros críticos.

Ejemplo:
