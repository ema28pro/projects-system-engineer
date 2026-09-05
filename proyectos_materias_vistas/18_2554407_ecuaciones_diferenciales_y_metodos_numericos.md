# 2554407 – Ecuaciones Diferenciales y Métodos Numéricos

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Ecuaciones Diferenciales y Métodos Numéricos
* **Código de Curso:** 2554407
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 3
* **Pre-requisitos:** 2559221 – Álgebra Lineal y 2559231 – Cálculo Integral | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Solución de Sistemas Lineales y Descomposición de Matrices (2.5 semanas)**
   * Métodos directos vs métodos iterativos.
   * **Descomposición LU** (factorización $A = LU$), método de Doolittle / Crout y factorización de Cholesky ($A = L L^T$).
   * Técnicas iterativas estacionarias: **Método de Jacobi** y **Método de Gauss-Seidel** (criterios de convergencia por diagonal dominante).
   * Condicionamiento de matrices y número de condición ($\kappa(A)$).
2. **Unidad 2: Diferenciación e Integración Numéricas (2 semanas)**
   * Fórmulas de diferenciación numérica por diferencias finitas: hacia adelante, hacia atrás y centradas de orden $O(h^2)$.
   * Extrapolación de Richardson.
   * Integración numérica compuesta: **Regla del Trapecio**, **Regla de Simpson 1/3** y **Regla de Simpson 3/8** con estimación del error de truncamiento.
3. **Unidad 3: Ecuaciones Diferenciales de Primer Orden y Modelación (3 semanas)**
   * Definición, clasificación (orden, grado, linealidad) y problemas de valor inicial (PVI).
   * Métodos analíticos: separación de variables, ecuaciones diferenciales exactas y factor integrante, ecuaciones lineales de primer orden.
   * Modelos matemáticos aplicados: ley de enfriamiento de Newton, modelos de crecimiento logístico poblacional y problemas de mezclas en tanques interconectados.
4. **Unidad 4: Ecuaciones Diferenciales de Orden Superior y Modelación (3.5 semanas)**
   * EDOs lineales de segundo orden homogéneas con coeficientes constantes (raíces reales distintas, raíces dobles y raíces complejas conjugadas).
   * EDOs no homogéneas: método de coeficientes indeterminados y método de variación de parámetros.
   * Modelos mecánicos y eléctricos: oscilador armónico simple, sistema masa-resorte con amortiguamiento (subamortiguado, críticamente amortiguado y sobreamortiguado), movimiento forzado y fenómeno de **resonancia**.
5. **Unidad 5: Sistemas de Ecuaciones Diferenciales de Primer Orden (2.5 semanas)**
   * Sistemas lineales homogéneos en forma matricial: $\vec{x}'(t) = A \vec{x}(t)$.
   * Solución mediante autovalores y autovectores.
   * Análisis cualitativo en el plano de fase: clasificación de puntos de equilibrio (nodos estables/inestables, puntos de silla, centros, focos espirales).
6. **Unidad 6: Soluciones Numéricas de Ecuaciones Diferenciales (2.5 semanas)**
   * Formulación del problema de valor inicial numérico.
   * **Método de Euler** explícito y análisis de error local $O(h^2)$ y global $O(h)$.
   * Método de Euler Mejorado (**Método de Heun** / predictor-corrector).
   * **Método de Runge-Kutta de Cuarto Orden (RK4)**: formulación matemática, deducción de pesos $k_1, k_2, k_3, k_4$ y precisión $O(h^4)$.
   * Sistemas de EDOs acopladas resueltos con RK4 y análisis de estabilidad numérica.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Laboratorio Interactivo de Algoritmos Numéricos (LU, Jacobi, Gauss-Seidel, Simpson y Richardson)
* **Problema a Resolver:** Construir una librería de cálculo científico modular que resuelva sistemas de ecuaciones lineales e integración compuesta, reportando formalmente el número de iteraciones, error relativo y convergencia.
* **Correspondencia con el PDF:**
  * Unidades 1 y 2: Factorización LU, métodos iterativos de Jacobi y Gauss-Seidel con normas matriciales de error, y cuadratura numérica con Simpson 1/3 y Simpson 3/8.
* **Requerimientos Funcionales:**
  1. Factorización $A = LU$ con pivoteo parcial para resolver $Ax = b$.
  2. Implementación de Jacobi y Gauss-Seidel con control de parada estricto: $\frac{||x^{(k+1)} - x^{(k)}||}{||x^{(k+1)}||} < \text{tol}$.
  3. Módulo de cuadratura: regla del Trapecio y Simpson 1/3 compuesta con cálculo analítico del error de truncamiento $E_t = -\frac{(b-a)h^4}{180}f^{(4)}(\xi)$.
  4. Extrapolación de Richardson para duplicar el orden de convergencia de derivadas numéricas.
  5. Visualizador de la matriz de convergencia y curvas de error vs número de iteraciones.
* **Stack Tecnológico:** Python (NumPy puro para vectorización, Matplotlib o Streamlit).
* **Valor en Entrevistas Técnicas:** Demuestra fundamentos sólidos de computación científica de alto rendimiento y estabilidad de punto flotante.

---

### Proyecto 2: Simulador Epidemiológico Dinámico (Modelo SIR / SEIR) resuelto con RK4
* **Problema a Resolver:** Modelar la propagación de una enfermedad infecciosa en una población mediante un sistema de ecuaciones diferenciales no lineales acopladas (Susceptibles, Expuestos, Infectados, Recuperados) y resolverlo mediante integración numérica de alta precisión.
* **Correspondencia con el PDF:**
  * Unidades 3, 5 y 6: Ecuaciones diferenciales aplicadas, sistemas no lineales de primer orden y método de Runge-Kutta de 4to orden (RK4).
* **Requerimientos Funcionales:**
  1. Definir el sistema de EDOs acopladas:
     $$\frac{dS}{dt} = -\frac{\beta S I}{N}, \quad \frac{dI}{dt} = \frac{\beta S I}{N} - \gamma I, \quad \frac{dR}{dt} = \gamma I$$
  2. Implementar el integrador **RK4 para sistemas multivariados** desde cero.
  3. Permitir simular intervenciones: uso de vacunas (reducción de $S$), aislamiento social (reducción de la tasa de contagio $\beta$) y capacidad de camas UCI (umbral crítico sobre $I(t)$).
  4. Calcular el número reproductivo básico $R_0 = \frac{\beta}{\gamma}$ y determinar analítica y numéricamente si la epidemia colapsará o generará un pico descontrolado.
* **Stack Tecnológico:** Python (NumPy, Matplotlib) o JavaScript interactivo.
* **Valor en Entrevistas Técnicas:** Demuestra capacidad para traducir problemas científicos del mundo real a modelos matemáticos computacionales robustos.

---

### Proyecto 3: Simulador de Resonancia y Plano de Fase de Osciladores Mecánicos y Circuitos RLC
* **Problema a Resolver:** En ingeniería, comprender el fenómeno de resonancia (cuando la frecuencia forzadora coincide con la natural, amplificando las oscilaciones hasta el colapso estructural, como en el famoso puente de Tacoma Narrows) y visualizar la estabilidad en el plano de fase.
* **Correspondencia con el PDF:**
  * Unidades 4 y 5: EDOs de segundo orden, sistemas amortiguados y forzados ($m x'' + c x' + k x = F_0 \cos(\omega t)$), soluciones complementaria y particular, resonancia y retratos de fase.
* **Requerimientos Funcionales:**
  1. Resolver analíticamente la ecuación característica clasificando el régimen: subamortiguado, críticamente amortiguado o sobreamortiguado.
  2. Animar el movimiento oscilatorio con control deslizante de la frecuencia forzadora $\omega$ para observar visualmente la curva de resonancia espectral.
  3. Renderizar el **Retrato de Fase ($x$ vs $x'$)** mostrando trayectorias cerradas (centros conservativos) vs espirales convergentes hacia el atractor de equilibrio.
* **Stack Tecnológico:** Python (SciPy / SymPy para cálculo analítico, Matplotlib interactivo).
