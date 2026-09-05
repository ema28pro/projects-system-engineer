# 2554308 – Teoría de la Probabilidad y Colas

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Teoría de la Probabilidad y Colas
* **Código de Curso:** 2554308
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 3
* **Pre-requisitos:** Ninguno | **Co-requisitos:** 2559231 – Cálculo Integral
* **Modalidad:** Virtual / Presencial

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Estadística Descriptiva (2 semanas)**
   * Tipos de datos y escalas de medición; tablas de frecuencias para variables discretas y continuas.
   * Medidas de tendencia central (media, mediana, moda), dispersión (varianza, desviación estándar, rango intercuartílico) y localización (percentiles).
   * Técnicas gráficas de exploración de datos: histogramas, diagramas de caja (*boxplots*), dispersión y diagramas de Pareto.
2. **Unidad 2: Fundamentos de Probabilidad (2 semanas)**
   * Espacios muestrales, eventos y axiomas de Kolmogorov.
   * Probabilidad condicional, independencia de eventos, regla multiplicativa y Ley de Probabilidad Total.
   * **Teorema de Bayes** y actualización de probabilidades a priori y a posteriori.
3. **Unidad 3: Variables Aleatorias Discretas (2 semanas)**
   * Función de masa de probabilidad (FMP) y función de distribución acumulada (FDA).
   * Valor esperado (media $\mu$), varianza ($\sigma^2$) y propiedades.
   * Modelos de probabilidad discretos: Bernoulli, Binomial, Geométrica, Hipergeométrica y **Proceso y Distribución de Poisson**.
4. **Unidad 4: Variables Aleatorias Continuas (2 semanas)**
   * Función de densidad de probabilidad (FDP) y FDA continua.
   * Modelos continuos: Distribución Uniforme, **Distribución Exponencial** (propiedad de falta de memoria), **Distribución Normal** (estandarización $Z$), y Distribución Gamma.
5. **Unidad 5: Distribuciones Conjuntas (2 semanas)**
   * Variables aleatorias bivariadas (discretas y continuas), distribuciones conjuntas y marginales.
   * Covarianza, coeficiente de correlación de Pearson e independencia estocástica.
6. **Unidad 6: Distribución Muestral y Estimación Puntual (2 semanas)**
   * Muestra aleatoria, estimadores puntuales y propiedades (insesgadez, consistencia y eficiencia).
   * **Teorema del Límite Central (TLC)** y distribución de la media muestral.
7. **Unidad 7: Estimación por Intervalos y Pruebas de Hipótesis (2 semanas)**
   * Intervalos de confianza para la media y proporción (distribuciones $Z$ y $t$-Student).
   * Pruebas de hipótesis estadísticas: hipótesis nula ($H_0$) y alternativa ($H_1$), errores tipo I ($\alpha$) y tipo II ($\beta$), cálculo del $p$-valor.
8. **Unidad 8: Teoría de Colas (2 semanas)**
   * Procesos estocásticos de nacimiento y muerte.
   * Elementos de los sistemas de líneas de espera y notación de Kendall ($A/B/c/K/m/Z$).
   * Modelos analíticos de colas: **$M/M/1$** (un servidor, capacidad infinita) y **$M/M/c$** (múltiples servidores en paralelo).
   * Fórmulas analíticas de Little: Factor de utilización $\rho$, número medio de clientes en el sistema ($L$) y en la cola ($L_q$), tiempos medios de espera en el sistema ($W$) y en la cola ($W_q$).

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Simulador de Eventos Discretos de Líneas de Espera ($M/M/c/K$) y Comparador Analítico
* **Problema a Resolver:** Los arquitectos de sistemas en la nube necesitan dimensionar cuántas instancias de servidor aprovisionar para atender peticiones web sin que los tiempos de respuesta se degraden ni se incurra en costos excesivos por servidores ociosos.
* **Correspondencia con el PDF:**
  * Unidades 3, 4 y 8: Procesos de Poisson (llegadas), distribución exponencial (tiempos de servicio con falta de memoria), fórmulas de Little y modelos de colas $M/M/1$ y $M/M/c$.
* **Requerimientos Funcionales:**
  1. Configuración de parámetros del sistema: tasa media de llegada $\lambda$, tasa media de atención por servidor $\mu$, número de servidores concurrentes $c$ y capacidad máxima de cola $K$ (detección de paquetes descartados / *dropped packets*).
  2. Implementar un **Simulador de Eventos Discretos (DES)** desde cero (usando una cola de prioridad de eventos en el tiempo: eventos `Llegada` y `Salida`).
  3. Cálculo de métricas empíricas de la simulación: $L, L_q, W, W_q$, probabilidad de encontrar el sistema vacío $P_0$ y porcentaje de utilización de cada servidor.
  4. Módulo de validación cruzada: contrastar los resultados de la simulación con las fórmulas analíticas teóricas de Kendall para verificar la convergencia del simulador.
  5. Dashboard interactivo con gráficas de evolución temporal de la cola y análisis de costos económicos ($Costo_{servidores} + Costo_{espera}$).
* **Stack Tecnológico:** Python (librería `simpy` o desde cero con `heapq`, visualización con Streamlit o Matplotlib).
* **Valor en Entrevistas Técnicas:** Conecta la probabilidad teórica con la ingeniería de rendimiento (*Performance Engineering*), dimensionamiento de servidores y arquitecturas cloud.

---

### Proyecto 2: Clasificador Bayesiano de Spam / Fraude desde Cero con Validación de Intervalos
* **Problema a Resolver:** En ciberseguridad, filtrar mensajes fraudulentos o correos spam en tiempo real se basa en aplicar el Teorema de Bayes sobre las probabilidades condicionales de palabras clave.
* **Correspondencia con el PDF:**
  * Unidades 1, 2 y 7: Axiomas de probabilidad, probabilidad condicional, Teorema de Bayes, suavizado de Laplace e intervalos de confianza para la tasa de acierto del modelo.
* **Requerimientos Funcionales:**
  1. Ingesta y preprocesamiento de un dataset de mensajes clasificados (Spam / Ham).
  2. Cálculo de probabilidades a priori $P(Spam)$ y verosimilitudes condicionales $P(palabra_i | Spam)$ aplicando el suavizado de Laplace para palabras no observadas en el entrenamiento.
  3. Clasificación de nuevos mensajes aplicando el logaritmo de la regla de Bayes para evitar el subdesbordamiento de punto flotante (*underflow*).
  4. Matriz de confusión completa (Verdaderos Positivos, Falsos Positivos, etc.) y cálculo del intervalo de confianza al 95% para la precisión y recall mediante aproximación normal.
* **Stack Tecnológico:** Python puro (sin usar librerías de ML como Scikit-Learn; solo matemáticas nativas).
* **Valor en Entrevistas Técnicas:** Demuestra que entiendes la fundamentación probabilística detrás del Machine Learning supervisado y no solo cómo llamar a librerías prefabricadas.

---

### Proyecto 3: Simulador Monte Carlo del Teorema del Límite Central y Ley de los Grandes Números
* **Problema a Resolver:** Demostrar de forma visual y computacional por qué la distribución normal emerge espontáneamente al sumar variables aleatorias independientes de cualquier otra distribución (Uniforme, Exponencial, Poisson o Bernoulli).
* **Correspondencia con el PDF:**
  * Unidades 3, 4 y 6: Generación de variables aleatorias mediante el método de transformación inversa, cálculo de medias muestrales y demostración empírica del Teorema del Límite Central.
* **Requerimientos Funcionales:**
  1. El usuario selecciona una distribución base asimétrica o discontinua (ej. Exponencial con $\lambda = 2$ o Bernoulli con $p = 0.1$).
  2. Extraer $M = 10,000$ muestras de tamaño $N \in [2, 5, 15, 50, 100]$.
  3. Graficar en tiempo real el histograma de las medias muestrales superpuesto con la curva teórica Gaussiana $N(\mu, \sigma^2/N)$, demostrando la normalización a medida que $N$ crece.
  4. Prueba formal de bondad de ajuste para cuantificar la normalidad.
* **Stack Tecnológico:** Python (NumPy, SciPy, Seaborn) o Web (Plotly.js).
