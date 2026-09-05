# 2554402 – Lógica y Representación III

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Lógica y Representación III
* **Código de Curso:** 2554402
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 4
* **Pre-requisitos:** 2554306 – Lógica y Representación II y 2554308 – Teoría de la Probabilidad y Colas
* **Modalidad:** Virtual / Presencial
* **Libro Guía Oficial:** *Mining of Massive Datasets* (Leskovec, Rajaraman, Ullman - Stanford/Cambridge)

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Introducción a Big Data y Algoritmos Probabilísticos**
   * Nuevas métricas más allá de tiempo y espacio: nivel de error esperado, falsos positivos/negativos, costo de comunicación y sesgo algorítmico.
   * Estimación de la probabilidad de fallar de un algoritmo aleatorizado (cotas de Markov y Chebyshev).
   * Funciones de Hash teóricas y universales; hashing en la práctica.
2. **Data Streams (Flujos de Datos Masivos en Tiempo Real)**
   * El modelo de flujo de datos (streams): memoria extremadamente limitada frente a flujos infinitos.
   * **Filtros de Bloom (*Bloom Filters*)**: verificación probabilística de pertenencia en memoria compacta sin falsos negativos.
   * Técnicas de muestreo en streams: Muestreo de Reservorio (*Reservoir Sampling*).
   * Algoritmos de conteo en streams: Algoritmo de Flajolet-Martin para contar elementos distintos.
   * Estimación de momentos estadísticos: Algoritmo Alon-Matias-Szegedy (AMS).
   * **Algoritmo DGIM (Datar-Gionis-Indyk-Motwani)**: estimación del número de bits 1 en ventanas deslizantes recientes.
3. **Procesando Grafos de Gran Tamaño**
   * Cadenas de Markov y distribución estacionaria.
   * **Algoritmo PageRank**: cálculo de relevancia web, problema de *dead ends* (callejones sin salida) y *spider traps* (trampas de araña) resueltos mediante teletransportación (factor de amortiguamiento $\beta$).
   * Caminatas aleatorias (*Random Walk*).
   * Solución aleatoria del problema 2-SAT con Random Walks.
4. **MapReduce y Paralelismo**
   * Paradigma MapReduce: funciones `Map` y `Reduce`, particionamiento y ordenamiento (*Shuffle & Sort*).
   * Algoritmos usando MapReduce: conteo de palabras, multiplicación de matrices masivas, cálculo de aristas en grafos.
   * Análisis de costos y complejidad en entornos distribuidos.
5. **Búsqueda del Vecino Más Próximo y Documentos Similares**
   * Medidas de distancia: Distancia Jaccard, Coseno, Euclídea y Hamming.
   * *Shingling*: descomposición de texto en $k$-shingles.
   * **Minhashing**: preservación de la similitud de Jaccard mediante permutaciones de hash.
   * **Locality-Sensitive Hashing (LSH)**: particionamiento en bandas para encontrar pares candidatos de alta similitud en tiempo subcuadrático.
6. **Programación Dinámica Aplicada a Datos Masivos**
   * El problema del alineamiento de secuencias (Needleman-Wunsch / Smith-Waterman) aplicado a bioinformática y comparación masiva de cadenas.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Motor de Detección de Plagio y Documentos Similares a Escala (Shingling + MinHash + LSH)
* **Problema a Resolver:** En una colección de 500,000 artículos o repositorios de código, una comparación par a par requeriría $O(n^2) \approx 1.25 \times 10^{11}$ comparaciones (computacionalmente inviable). Utilizando LSH, es posible aislar documentos con similitud Jaccard $\ge 0.8$ en segundos.
* **Correspondencia con el PDF:**
  * Búsqueda del vecino más próximo, $k$-shingles, matrices de firmas de MinHash y Locality-Sensitive Hashing dividido en $b$ bandas y $r$ filas.
* **Requerimientos Funcionales:**
  1. Extracción de $k$-shingles (tokens de $k$ palabras consecutivas) y hash de tokens.
  2. Construcción de la matriz de firmas de MinHash usando $m$ funciones hash lineales $h_i(x) = (a_i x + b_i) \pmod p$.
  3. Particionamiento LSH en $b$ bandas de $r$ filas ($m = b \times r$) con inserción en tablas hash de colisiones.
  4. Generación de pares candidatos y cálculo de la similitud Jaccard real únicamente sobre los candidatos.
  5. Reporte de precisión, falsos positivos y falsos negativos en función del umbral teórico $s \approx (1/b)^{1/r}$.
* **Stack Tecnológico:** Python (NumPy vectorizado o PySpark).
* **Valor en Entrevistas Técnicas:** Proyecto insignia para ingenieros de datos y roles en motores de búsqueda, sistemas de recomendación y ciberseguridad.

---

### Proyecto 2: Procesador de Stream de Eventos en Tiempo Real (Bloom Filter + DGIM + Flajolet-Martin)
* **Problema a Resolver:** En una red corporativa o plataforma social de alto tráfico (millones de requests/segundo), no se puede persistir cada evento para responder preguntas como "¿esta IP es maliciosa?" o "¿cuántos usuarios únicos nos visitaron en la última hora?".
* **Correspondencia con el PDF:**
  * Data Streams: Filtro de Bloom, algoritmo Flajolet-Martin de elementos distintos y algoritmo DGIM sobre ventanas deslizantes.
* **Requerimientos Funcionales:**
  1. Generador de flujo continuo de datos mediante sockets o eventos simulados.
  2. Implementar un **Filtro de Bloom** con $k$ funciones hash óptimas ($k = \frac{m}{n}\ln 2$) para bloquear dominios/IPs maliciosas en memoria RAM mínima ($< 1$ MB).
  3. Implementar el **Algoritmo DGIM** para responder consultas sobre el número de eventos de un tipo ocurridos en los últimos $N$ instantes de tiempo con un factor de error $\le 50\%$.
  4. Implementar **Flajolet-Martin** contando los ceros iniciales de los hashes para estimar la cardinalidad de usuarios distintos.
  5. Dashboard de métricas en consola o web que compare la estimación probabilística vs el valor exacto en tiempo real.
* **Stack Tecnológico:** Python (o Go / Rust) con visualización en terminal (Rich / Textual) o Streamlit.
* **Valor en Entrevistas Técnicas:** Demuestra cómo resolver problemas donde el tamaño de los datos excede la capacidad de memoria RAM.

---

### Proyecto 3: Mini-Google: Motor de Cálculo PageRank Distribuido con MapReduce
* **Problema a Resolver:** Calcular la autoridad de millones de páginas web en un grafo masivo con callejones sin salida y trampas de bucle.
* **Correspondencia con el PDF:**
  * Procesando grafos de gran tamaño: Cadenas de Markov, distribución estacionaria, teletransportación de PageRank y MapReduce.
* **Requerimientos Funcionales:**
  1. Crawler o generador de grafos de enlaces web sintéticos (100,000+ páginas).
  2. Implementar el cálculo iterativo de PageRank formulado bajo el modelo **MapReduce**:
     * Fase Map: distribuir la probabilidad de una página entre sus enlaces salientes.
     * Fase Reduce: sumar los aportes de las páginas entrantes y aplicar la teletransportación estocástica ($1-\beta$).
  3. Manejo de *Dead Ends* (páginas sin enlaces de salida) redistribuyendo su peso a todo el grafo.
  4. Monitorear la convergencia hasta que $|v_{t+1} - v_t| < \epsilon$.
* **Stack Tecnológico:** Python con librería `mrjob` o PySpark.
