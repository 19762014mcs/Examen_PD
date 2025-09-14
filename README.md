
# Análisis interactivo del *Wine Dataset* (PCA, LDA, t‑SNE, UMAP)

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

## 🚀 Ejecución
1. **Clona** el repositorio o copia `entero.py` a una carpeta de trabajo.
2. Crea y activa un **entorno virtual** (opcional pero recomendado):
   ```bash
   python -m venv .venv
   # Windows
   .venv\\Scripts\\activate
   # macOS / Linux
   source .venv/bin/activate
   ```
3. **Instala** dependencias:
   ```bash
   pip install -U streamlit pandas numpy scikit-learn plotly matplotlib missingno umap-learn
   ```
4. **Inicia** la app de Streamlit:
   ```bash
   streamlit run entero.py
   ```
5. Abre el **navegador** y visita la URL local que muestra Streamlit (por defecto: `http://localhost:8501`).

---

## 🖱️ Uso rápido (qué encontrarás en la app)
- **1. Carga y preprocesamiento**: vista del dataset, gráfico de valores faltantes, tabla estandarizada y detalles de la partición train/test.
- **2. Métodos de reducción**: controles deslizantes para PCA (selección de componentes), t‑SNE (perplexity y learning rate) y UMAP (`n_neighbors` y `min_dist`).
- **3. Evaluación y comparación**: sliders para `test_size` y `k` en k‑NN, métricas de rendimiento y visualizaciones interactivas.

> La app utiliza `st.cache_data` para acelerar recomputaciones cuando no cambian los parámetros.

---

## 🧪 Archivos y estructura
- `entero.py`: Script principal de Streamlit con toda la lógica de carga, preprocesamiento, visualización y evaluación.

---

## 🛠️ Consejos y solución de problemas
- Si `KMeans(n_init='auto')` genera advertencias en ciertas versiones, prueba fijar `n_init=10` o actualizar `scikit-learn`.
- Para que t‑SNE/UMAP sean reproducibles, el script fija `random_state=42` en los componentes que lo permiten.
- Si el navegador no abre automáticamente, copia/pega la URL que imprime Streamlit en la terminal.

---

## 📄 Licencia
Define aquí la licencia de tu proyecto (por ejemplo, MIT, Apache‑2.0) o elimínalo si no aplica.

---

## 🙌 Créditos
- Dataset: `sklearn.datasets.load_wine` (conjunto clásico de clasificación de vinos).
- Librerías: Streamlit, scikit‑learn, Plotly, Matplotlib, Missingno y UMAP.
