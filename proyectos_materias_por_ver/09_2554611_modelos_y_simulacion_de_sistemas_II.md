# 2554611 – Modelos y Simulación de Sistemas II (Machine Learning & Modelado Matemático Avanzado)

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Modelos y Simulación de Sistemas II
* **Código de Curso:** 2554611
* **Nivel:** 7
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 4
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial
* **Libros Guía Oficiales:** *Pattern Recognition and Machine Learning* (Christopher Bishop), *The Elements of Statistical Learning* (Hastie, Tibshirani, Friedman).

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Introducción al Aprendizaje de Máquina (3 semanas)**
   * Taxonomía: Aprendizaje Supervisado, No Supervisado y por Refuerzo.
   * Definición formal de funciones de pérdida: Error Cuadrático Medio (MSE) y Entropía Cruzada Binaria / Categórica (*Cross-Entropy*).
   * Optimización matemática: Descenso de Gradiente, Descenso de Gradiente Estocástico (SGD) y optimizadores modernos con momento (Adam, RMSprop).
2. **Unidad 2: Métodos Paramétricos y No Paramétricos (5 semanas)**
   * Métodos lineales de clasificación: **Regresión Logística** (función sigmoide, frontera de decisión) y Análisis Discriminante Lineal (LDA).
   * Clasificador Bayesiano Ingenuo (**Naive Bayes**): modelos Gaussiano, Multinomial y Bernoulli.
   * Algoritmos basados en árboles: **Árboles de Decisión (CART)**, criterios de división por ganancia de información (Entropía de Shannon) e impureza de Gini.
   * Métodos de Ensamble (*Ensemble Learning*):
     * *Bagging*: **Bosques Aleatorios (Random Forests)** y estimación Out-of-Bag (OOB).
     * *Boosting*: AdaBoost, Gradient Boosting y algoritmos de alto rendimiento (**XGBoost / LightGBM**).
   * Algoritmo de los **$k$-Vecinos más Cercanos ($k$-NN)** y selección de métricas de distancia.
3. **Unidad 3: Redes Neuronales Artificiales (2 semanas)**
   * El modelo biológico y el Perceptrón simple de Rosenblatt.
   * **Perceptrón Multicapa (MLP)** y funciones de activación no lineales: Sigmoide, Tanh, ReLU y Leaky ReLU.
   * El algoritmo de **Retropropagación del Error (*Backpropagation*)**: deducción matemática con la regla de la cadena de cálculo multivariable para la actualización de pesos sinápticos y sesgos (*biases*).
4. **Unidad 4: Máquinas de Vectores de Soporte (SVM) (2 semanas)**
   * Clasificación lineal con margen máximo: vectores de soporte y distancia al hiperplano separador.
   * Formulación matemática: problema de optimización cuadrática primal y dual mediante **Multiplicadores de Lagrange** (condiciones KKT).
   * Clasificación con margen suave (parámetro de regularización $C$ y variables de holgura $\xi_i$).
   * El **Truco del Kernel (*Kernel Trick*)** para problemas no linealmente separables: Kernel Polinomial, Kernel Sigmoide y Kernel de Base Radial Gaussiana (**RBF**).
5. **Unidad 5: Sobreajuste y Reducción de Dimensión (2 semanas)**
   * El dilema Sesgo-Varianza (*Bias-Variance Tradeoff*).
   * Técnicas de regularización matemática: Regularización $L_1$ (**Lasso** - selección de variables) y Regularización $L_2$ (**Ridge** - contracción de coeficientes).
   * Reducción de dimensionalidad no supervisada: **Análisis de Componentes Principales (PCA)** mediante autovalores y autovectores de la matriz de covarianza.
   * Estrategias de validación estadística: Validación cruzada estratificada $k$-Fold, curvas de aprendizaje y curvas de validación.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Implementación desde Cero (from scratch) de Algoritmos Nucleares de Machine Learning
* **Problema a Resolver:** En la industria, cualquiera puede importar `sklearn.ensemble.RandomForestClassifier` en dos líneas de código sin comprender cómo funciona. Implementar los algoritmos matemáticos desde cero con álgebra lineal pura vectorizada demuestra una competencia técnica de nivel Senior.
* **Correspondencia con el PDF:**
  * Unidades 1, 2, 3 y 4: Regresión Logística con descenso de gradiente, Árbol de Decisión CART con cálculo de Gini, Red Neuronal MLP con Backpropagation matricial y SVM lineal.
* **Requerimientos Funcionales:**
  1. **Regresión Logística Vectorizada:** Implementar la función de coste de entropía cruzada con regularización $L_2$ y optimización por gradiente en NumPy.
  2. **Árbol de Decisión CART:** Implementar recursivamente la búsqueda del mejor umbral de división que minimice la impureza de Gini y métodos de poda (*pruning*).
  3. **Red Neuronal MLP desde Cero:**
     * Capas densas arbitrarias ($[d_{in}, h_1, h_2, d_{out}]$).
     * Forward pass con activaciones ReLU y Softmax.
     * Backward pass computando gradientes matriciales $\frac{\partial L}{\partial W^{[l]}}$ y $\frac{\partial L}{\partial b^{[l]}}$ sin librerías de autodiferenciación.
  4. **Benchmark Comparativo:** Entrenar tus implementaciones artesanales vs Scikit-Learn sobre datasets estándar (ej. Breast Cancer, MNIST dígitos) demostrando que alcanzan métricas de precisión idénticas ($> 95\%$).
* **Stack Tecnológico:** Python 3, NumPy puro vectorizado, Matplotlib (sin Scikit-Learn ni PyTorch para el core de los modelos).
* **Valor en Entrevistas Técnicas:** Es la prueba técnica más respetada en entrevistas de Machine Learning y Data Science cuantitativa.

---

### Proyecto 2: Sistema Predictivo de Diagnóstico Clínico Multiclase con XGBoost, SVM y Explicabilidad SHAP
* **Problema a Resolver:** En el sector de la salud, no basta con predecir una patología con alta precisión; el modelo debe ser explicable (*Explainable AI - XAI*) para que los médicos entiendan qué variables clínicas justifican el diagnóstico.
* **Correspondencia con el PDF:**
  * Unidades 2, 4 y 5: Optimización de hiperparámetros con validación cruzada $k$-Fold, comparación rigurosa entre SVM (con kernel RBF) y XGBoost, y análisis de importancia de características con valores SHAP.
* **Requerimientos Funcionales:**
  1. Preprocesamiento robusto de datos clínicos con valores faltantes, escalado robusto y balanceo de clases (SMOTE).
  2. Búsqueda bayesiana de hiperparámetros (*Bayesian Optimization*) para SVM y Gradient Boosting.
  3. Evaluación completa: Curvas ROC-AUC multiclase, curvas Precision-Recall y matrices de confusión calibradas.
  4. Módulo de Explicabilidad con **SHAP (SHapley Additive exPlanations)**: Gráficos *Summary Plot* globales y *Force Plot* locales para casos individuales de pacientes.
  5. Despliegue de una interfaz interactiva donde el médico ingresa parámetros clínicos y recibe el diagnóstico con su desglose explicable.
* **Stack Tecnológico:** Python, XGBoost, Scikit-learn, SHAP, Streamlit.
* **Valor en Entrevistas Técnicas:** Combina modelado predictivo de vanguardia con ética, interpretabilidad y aplicación real en la industria.
