# 2554408 – Métodos Estadísticos

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Métodos Estadísticos
* **Código de Curso:** 2554408
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 3
* **Pre-requisitos:** 2554308 – Teoría de la Probabilidad y Colas | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial
* **Libros Guía:** *Applied Linear Statistical Models* (Kutner, Nachtsheim, Neter), *Time Series Analysis and Its Applications* (Shumway, Stoffer).

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Modelos de Regresión Lineal Simple (MRLS)**
   * Formulación del modelo: $Y_i = \beta_0 + \beta_1 X_i + \epsilon_i$.
   * Estimación de parámetros por el método de Mínimos Cuadrados Ordinarios (MCO).
   * Propiedades de los estimadores bajo los supuestos del Teorema de Gauss-Markov.
   * Inferencia estadística sobre $\beta_0$ y $\beta_1$ (pruebas $t$ e intervalos de confianza).
   * Intervalos de confianza para la respuesta media e intervalos de predicción para nuevas observaciones.
   * Tabla de Análisis de Varianza (ANOVA en regresión) y descomposición de sumas de cuadrados ($SST = SSR + SSE$).
   * Coeficiente de determinación ($R^2$) y coeficiente de correlación ($r$).
   * Diagnóstico de supuestos sobre los residuales: normalidad (Shapiro-Wilk / Q-Q plot), homocedasticidad (Breusch-Pagan) e independencia.
2. **Unidad 2: Modelos de Regresión Lineal Múltiple (MRLM)**
   * Formulación matricial: $Y = X\beta + \epsilon$.
   * Estimador matricial $\hat{\beta} = (X^T X)^{-1} X^T Y$ y matriz de varianzas-covarianzas.
   * Coeficiente de determinación múltiple y $R^2$ ajustado ($R^2_{adj}$).
   * Métodos de selección y refinamiento de variables: *Stepwise*, *Forward Selection* y *Backward Elimination*.
   * Detección de **Multicolinealidad** mediante el Factor de Inflación de la Varianza (**VIF**).
   * Análisis de observaciones atípicas e influyentes: residuales estandarizados, residuales studentizados, puntos de apalancamiento (*Leverage* / matriz sombrero $H$) y **Distancia de Cook**.
3. **Unidad 3: Modelos de Análisis de Varianza (ANOVA)**
   * Diseño de experimentos completamente aleatorizado de un solo factor (ANOVA unifactorial).
   * Pruebas de hipótesis para la igualdad de medias de $k$ tratamientos ($F$-test).
   * Diseños en Bloques Completos al Azar (DBCA).
   * Métodos de comparación múltiple *post-hoc*: Prueba HSD de Tukey y método de Scheffé.
   * Validación formal de supuestos de normalidad y homocedasticidad (prueba de Levene).
4. **Unidad 4: Series de Tiempo**
   * Componentes de una serie temporal: tendencia, estacionalidad, componente cíclico y variación irregular/aleatoria.
   * Métodos de descomposición clásica (aditiva y multiplicativa).
   * Técnicas de suavizamiento: Promedios Móviles y **Suavizamiento Exponencial Simple y Doble (Método de Holt-Winters)**.
   * Noción de estacionariedad (prueba de Dickey-Fuller aumentada) y función de autocorrelación (ACF) y autocorrelación parcial (PACF).
   * Introducción a modelos autorregresivos y de medias móviles (**AR, MA y ARIMA**).

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Plataforma Web Automatizada de A/B Testing con Diagnóstico ANOVA y Pruebas Post-Hoc
* **Problema a Resolver:** Las empresas digitales evalúan continuamente cambios en productos (diseños web, algoritmos de recomendación, flujos de checkout) mediante experimentos A/B/n. Se requiere una herramienta que no solo calcule medias, sino que valide formalmente supuestos estadísticos y ajuste comparaciones múltiples para evitar falsos descubrimientos.
* **Correspondencia con el PDF:**
  * Unidad 3: ANOVA unifactorial, prueba $F$, verificación de normalidad y homocedasticidad con Levene, y comparaciones múltiples con Tukey HSD.
* **Requerimientos Funcionales:**
  1. Ingesta de datos de experimentación con $k \ge 2$ variantes del producto.
  2. Pruebas automáticas de verificación de supuestos:
     * Normalidad de los residuos mediante la prueba de Shapiro-Wilk y gráfico Q-Q.
     * Homocedasticidad mediante la prueba de Levene. Si no se cumple, aplicar alternativa de Welch.
  3. Ejecución de la tabla ANOVA reportando Sumas de Cuadrados, Grados de Libertad, Estadístico $F$ y $p$-valor.
  4. Si hay diferencias significativas ($p < 0.05$): ejecutar automáticamente la prueba de Tukey HSD reportando intervalos de confianza corregidos para cada par de variantes.
  5. Conclusión en lenguaje de negocio claro: "¿Cuál variante fue la ganadora y con qué certeza estadística?".
* **Stack Tecnológico:** Python (SciPy, Statsmodels, Pandas, Streamlit o FastAPI + React).
* **Valor en Entrevistas Técnicas:** Es el proyecto más demandado para roles de Data Analyst, Product Analyst y Data Scientist en startups y grandes tecnológicas.

---

### Proyecto 2: Suite de Modelado Econométrico Predictivo con Diagnóstico Riguroso de Residuos
* **Problema a Resolver:** En la industria, muchos modelos predictivos fallan en producción porque se ignora la multicolinealidad entre variables y la violación de supuestos de Gauss-Markov.
* **Correspondencia con el PDF:**
  * Unidades 1 y 2: Regresión Lineal Simple y Múltiple en forma matricial, cálculo de VIF, selección Stepwise, análisis de influencia con Distancia de Cook y gráficos diagnósticos.
* **Requerimientos Funcionales:**
  1. Cargar un dataset multivariado del mundo real (ej. predicción de precios de vivienda, consumo de combustible o rendimiento de ventas).
  2. Implementar la estimación matricial MCO $\hat{\beta} = (X^T X)^{-1} X^T Y$ y contrastarla contra librerías estándar.
  3. Calcular el VIF para cada variable independiente y filtrar variables con multicolinealidad severa ($VIF > 10$).
  4. Algoritmo de selección automática de variables por eliminación regresiva (*Backward Elimination*) basado en significancia del $p$-valor.
  5. Panel diagnóstico de 4 gráficos esenciales:
     * Residuos vs Valores Ajustados (detección de no-linealidad y heterocedasticidad).
     * Normal Q-Q Plot (normalidad).
     * Scale-Location Plot (homocedasticidad).
     * Residuos vs Leverage con líneas de contorno de Distancia de Cook (identificación de outliers influyentes).
* **Stack Tecnológico:** Python (Statsmodels, Pandas, Seaborn, Matplotlib).
* **Valor en Entrevistas Técnicas:** Demuestra madurez econométrica y capacidad de construir modelos explicables y estadísticamente válidos.

---

### Proyecto 3: Pronosticador de Series de Tiempo con Descomposición y Suavizamiento Holt-Winters
* **Problema a Resolver:** Predecir la demanda de inventario o el tráfico de red para los próximos 30 días descomponiendo patrones estacionales y tendencias históricas.
* **Correspondencia con el PDF:**
  * Unidad 4: Series de tiempo, descomposición aditiva/multiplicativa, suavizamiento exponencial Holt-Winters y métricas de pronóstico (MAPE, RMSE).
* **Requerimientos Funcionales:**
  1. Ingesta de datos temporales (diarios o mensuales).
  2. Descomposición automática en 3 componentes: Tendencia, Estacionalidad y Ruido Residual.
  3. Implementar el modelo de **Suavizamiento Exponencial Triple (Holt-Winters)** con optimización de los hiperparámetros $\alpha, \beta, \gamma$.
  4. Generación de pronóstico a horizonte $H$ con bandas de incertidumbre (intervalos de predicción al 95%).
* **Stack Tecnológico:** Python (Statsmodels, Plotly).
