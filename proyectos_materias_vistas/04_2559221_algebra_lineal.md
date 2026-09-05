# 2559221 – Álgebra Lineal

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Álgebra Lineal
* **Código de Curso:** 2559221
* **Unidad Académica:** Facultad de Ingeniería – Cursos de Servicios
* **Área:** Ciencias Básicas de Ingeniería
* **Créditos Académicos:** 4
* **Pre-requisitos:** 2559121 – Geometría Vectorial y Analítica | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Espacios Vectoriales**
   * Espacios y subespacios vectoriales reales.
   * Combinaciones lineales, espacio generado (*span*).
   * Dependencia e independencia lineal.
   * Base y dimensión de un espacio vectorial; coordenadas relativas a una base.
2. **Unidad 2: Ortogonalidad**
   * Espacios con producto interno, norma y distancia inducida.
   * Conjuntos ortogonales y ortonormales.
   * Proceso de ortonormalización de Gram-Schmidt.
   * Complementos ortogonales y teorema de proyección.
   * Aproximación por mínimos cuadrados y ajuste lineal matricial ($A^T A \hat{x} = A^T b$).
3. **Unidad 3: Transformaciones Lineales**
   * Definición, propiedades, núcleo (kernel) e imagen de una transformación lineal.
   * Teorema de la dimensión (Rango-Nulidad).
   * Matriz asociada a una transformación lineal respecto a bases canónicas y arbitrarias.
   * Matrices de cambio de base (semejanza de matrices).
4. **Unidad 4: Valores y Vectores Propios**
   * Polinomio característico, autovalores (eigenvalues) y autovectores (eigenvectors).
   * Espacios propios y multiplicidad algebraica vs geométrica.
   * Diagonalización de matrices cuadradas ($A = P D P^{-1}$).
   * Matrices simétricas y diagonalización ortogonal ($A = P D P^T$).
   * Formas cuadráticas, clasificación (definida positiva, negativa, indefinida) y aplicaciones.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Compresor de Imágenes y Reductor de Dimensionalidad usando Descomposición Espectral y SVD
* **Problema a Resolver:** La comprensión y manipulación de datos a gran escala (imágenes, audios, matrices de correlación) requiere condensar la información reteniendo los autovalores predominantes. 
* **Correspondencia con el PDF:**
  * Unidad 4: Valores y vectores propios, matrices simétricas, diagonalización ortogonal y descomposición en valores singulares ($A = U \Sigma V^T$).
* **Requerimientos Funcionales:**
  1. Cargar imágenes monocromáticas o por canales RGB como matrices numéricas $A_{m \times n}$.
  2. Calcular la matriz de covarianza simétrica $A A^T$ y encontrar sus autovalores y autovectores mediante algoritmos numéricos (método de las potencias o QR).
  3. Reconstruir aproximaciones de bajo rango: $A_k = \sum_{i=1}^k \sigma_i u_i v_i^T$, permitiendo al usuario variar $k$ (número de componentes principales).
  4. Graficar la curva de energía espectral acumulada (varianza explicada por los primeros $k$ autovalores) y métricas de error MSE/PSNR de la compresión.
* **Stack Tecnológico:** Python (NumPy vectorizado, Matplotlib, OpenCV/Pillow).
* **Valor en Entrevistas Técnicas:** Es el proyecto fundacional por excelencia para roles en Machine Learning, Data Science y Visión por Computador.

---

### Proyecto 2: Motor de Ajuste de Modelos por Mínimos Cuadrados y Ortogonalización de Gram-Schmidt
* **Problema a Resolver:** Cuando los sistemas lineales son sobredeterminados ($Ax = b$ sin solución exacta), la mejor aproximación matemática proviene de proyectar ortogonalmente el vector $b$ sobre el subespacio columna de $A$.
* **Correspondencia con el PDF:**
  * Unidad 1 y 2: Bases ortonormales, proceso de Gram-Schmidt, proyecciones ortogonales y solución de sistemas normales $A^T A \hat{x} = A^T b$.
* **Requerimientos Funcionales:**
  1. Implementar el algoritmo de Gram-Schmidt clásico y modificado (para estabilidad numérica) para descomponer $A = QR$.
  2. Ajustar curvas polinomiales de grado $m$ a nubes de datos dispersos mediante la solución de ecuaciones normales y mediante la factorización QR ($R \hat{x} = Q^T b$).
  3. Comparar la estabilidad numérica entre resolver $A^T A$ (condicionamiento al cuadrado) vs la descomposición QR directa.
  4. Interfaz interactiva donde se dibujan puntos en un plano cartesiano y se recalcula instantáneamente la regresión matricial.
* **Stack Tecnológico:** Python (NumPy) o C++ con visualización gráfica.
* **Valor en Entrevistas Técnicas:** Demuestra entendimiento de álgebra lineal numérica, estabilidad de punto flotante y teoría de proyecciones en espacios de Hilbert.

---

### Proyecto 3: Visualizador Geométrico Interactivo de Transformaciones Lineales en 2D y 3D
* **Problema a Resolver:** Las transformaciones lineales son la base de los gráficos por computador, la robótica y la visión artificial. Visualizar cómo una matriz $2 \times 2$ deforma el espacio, altera el determinante (área orientada) y preserva los autovectores es fundamental.
* **Correspondencia con el PDF:**
  * Unidad 3 y 4: Matriz de transformación, cambio de base, núcleo, imagen y vectores invariantes (autovectores).
* **Requerimientos Funcionales:**
  1. Cuadrícula interactiva 2D que muestra los vectores base canónicos $\hat{i}, \hat{j}$.
  2. El usuario introduce valores de una matriz $M = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$.
  3. Animar la transformación continua del espacio, mostrando cómo el círculo unitario se transforma en una elipse cuyos semiejes son los autovectores escalados por sus autovalores.
  4. Mostrar el determinante como la razón de cambio de área y resaltar si la matriz no es invertible (colapso a una recta o al origen).
* **Stack Tecnológico:** TypeScript con HTML5 Canvas o Python con librería Manim.
