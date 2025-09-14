
# Análisis interactivo del *Wine Dataset* (PCA, LDA, t‑SNE, UMAP)
# Marcelo Carmona S- Paula Alvarez V.
Aplicación **Streamlit** para explorar el dataset de vinos (*Wine*) mediante técnicas de reducción de dimensionalidad (PCA, LDA, t‑SNE y UMAP), además de evaluación supervisada con k‑NN y no supervisada con k‑means. La app incluye visualizaciones interactivas con **Plotly** y utilidades para preprocesamiento (escalado, partición train/test y verificación de valores faltantes).

> Este README se basa en el script `entero.py`, que implementa las secciones, controles y métricas descritas a continuación. 

---

## 📦 Dataset
- Se utiliza el **Wine dataset** provisto por `scikit-learn` a través de `sklearn.datasets.load_wine`.
- Es un conjunto clásico de clasificación con medidas fisicoquímicas de vinos y una etiqueta de clase (tres variedades). 
- En la app, los datos se estandarizan con `StandardScaler` antes de aplicar las distintas técnicas de reducción/visualización.

> Nota: El script carga el dataset directamente desde `scikit-learn` (no requiere descarga manual) mediante `load_wine()`.

---

## 🧰 Funcionalidades principales
1. **Carga, inspección y preprocesamiento**
   - Vista de las primeras filas del dataset y reporte de valores faltantes.
   - Gráfico de **missingness** con `missingno.bar`.
   - **Estandarización** de características con `StandardScaler`.
   - **Partición** en entrenamiento/prueba con `train_test_split` (estratificado).

2. **Reducción de dimensionalidad y visualización**
   - **PCA**: curva de varianza explicada (scree plot), resumen tabular y proyección 2D coloreada por clase.
   - **LDA**: proyección 2D en el espacio discriminante y proporción de varianza explicada por LD1/LD2.
   - **t‑SNE**: proyección 2D con controles interactivos de *perplexity* y *learning rate*.
   - **UMAP**: proyección 2D con controles de `n_neighbors` y `min_dist`.

3. **Evaluación y comparación**
   - **Métrica supervisada**: Entrenamiento de **k‑NN** sobre datos reducidos con PCA (2D) y reporte de *accuracy* en test.
   - **Métricas no supervisadas** con **k‑means**: `silhouette_score`, `adjusted_rand_score (ARI)` y `normalized_mutual_info_score (NMI)` más visualización de clusters.

---

## ✅ Requisitos
Asegúrate de contar con **Python 3.9+** (recomendado) y crear un entorno virtual. Paquetes principales usados por la app:

```txt
streamlit
pandas
numpy
scikit-learn
plotly
matplotlib
missingno
umap-learn
```

> Dependiendo de tu entorno, puede requerirse instalar `pip install -U scikit-learn plotly missingno umap-learn streamlit`.

---

