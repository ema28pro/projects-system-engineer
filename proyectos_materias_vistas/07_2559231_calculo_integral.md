# 2559231 – Cálculo Integral

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Cálculo Integral
* **Código de Curso:** 2559231
* **Unidad Académica:** Facultad de Ingeniería – Cursos de Servicios
* **Área:** Ciencias Básicas de Ingeniería
* **Créditos Académicos:** 4
* **Pre-requisitos:** 2559131 – Cálculo Diferencial | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Función Primitiva o Antiderivada. Métodos de Integración**
   * Antiderivada e integral indefinida.
   * Integración por sustitución simple, integración por partes.
   * Integrales trigonométricas y sustitución trigonométrica.
   * Integración de funciones racionales por fracciones parciales.
2. **Unidad 2: La Integral Definida. Teoremas Fundamentales del Cálculo**
   * Notación sigma, particiones de un intervalo y Sumas de Riemann (izquierda, derecha, punto medio).
   * Definición formal de la integral definida como límite de sumas de Riemann.
   * Propiedades de la integral definida.
   * Primer y Segundo Teorema Fundamental del Cálculo.
   * Integrales impropias (límites infinitos y discontinuidades infinitas).
3. **Unidad 3: Aplicaciones de la Integral Definida**
   * Área de regiones planas entre curvas.
   * Volúmenes de sólidos de revolución: Método de los discos, arandelas y cascarones cilíndricos.
   * Longitud de arco de una curva plana y área de superficies de revolución.
   * Aplicaciones en física e ingeniería: trabajo mecánico, fuerza y presión hidrostática, centros de masa y centroides.
4. **Unidad 4: Sucesiones y Series**
   * Sucesiones infinitas, límites y convergencia.
   * Series infinitas, sumas parciales, series geométricas y series telescópicas.
   * Criterios de convergencia: Criterio de la integral, de comparación directa, comparación en el límite, prueba de la razón (d'Alembert), prueba de la raíz (Cauchy) y series alternadas (Leibniz).
   * Series de potencias, radio e intervalo de convergencia.
   * Series de Taylor y Maclaurin, aproximación polinomial de funciones y residuo de Lagrange.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Visualizador 3D Interactivo de Sólidos de Revolución (Discos, Arandelas y Cascarones)
* **Problema a Resolver:** Comprender geométricamente cómo una función rotada sobre un eje genera un volumen tridimensional es uno de los mayores desafíos visuales de la ingeniería. Un software interactivo 3D que modele los discos infinitesimales resuelve esta necesidad de forma pedagógica y técnica.
* **Correspondencia con el PDF:**
  * Unidad 2 y 3: Sumas de Riemann aplicadas a volúmenes, integración definida y sólidos de revolución (métodos de discos, arandelas y cascarones cilíndricos).
* **Requerimientos Funcionales:**
  1. Interfaz donde el usuario introduce $f(x)$ (y opcionalmente $g(x)$ para arandelas), límites $[a, b]$ y eje de rotación ($y = k$ o $x = h$).
  2. Renderizar la superficie de revolución en 3D interactivo (rotación, zoom).
  3. Control deslizante de particiones $n$: mostrar el sólido compuesto por $n$ cilindros discretos (aproximación de Riemann) y animar cómo al aumentar $n \to \infty$ la aproximación converge al volumen continuo calculado por la integral definida.
  4. Comparador de métodos: mostrar la formulación por discos vs cascarones con sus fórmulas matemáticas explícitas.
* **Stack Tecnológico:** Three.js / WebGL con TypeScript/JavaScript, o Python con Plotly/VPython.
* **Valor en Entrevistas Técnicas:** Demuestra capacidades avanzadas de renderizado tridimensional, algoritmia espacial y aplicación rigurosa del cálculo integral.

---

### Proyecto 2: Suite Numérica y Analítica de Cuadratura e Integrales Impropias
* **Problema a Resolver:** En simulación física y ciencia de datos, la mayoría de integrales no tienen primitiva elemental (ej. distribución Gaussiana $\int e^{-x^2} dx$). Se requiere un motor que evalúe integrales impropias y converja con tolerancias estrictas de error.
* **Correspondencia con el PDF:**
  * Unidad 1 y 2: Métodos de integración numérica de Riemann, integrales impropias de primera y segunda especie.
* **Requerimientos Funcionales:**
  1. Implementar Sumas de Riemann (izquierda, derecha, punto medio, trapecio) y Cuadratura de Gauss-Legendre.
  2. Detección automática de discontinuidades interiores (asíntotas) para dividir el intervalo según la definición formal de integrales impropias.
  3. Evaluación de límites superiores infinitos mediante cambio de variable o truncamiento adaptativo con control de error $\epsilon < 10^{-7}$.
  4. Tabla comparativa de velocidad de convergencia en función del número de evaluaciones de la función.
* **Stack Tecnológico:** Python (NumPy, SciPy para benchmark, Matplotlib) o C++.
* **Valor en Entrevistas Técnicas:** Demuestra comprensión del cómputo numérico de alta precisión y manejo riguroso de singularidades matemáticas.

---

### Proyecto 3: Calculador y Comparador de Convergencia de Series de Taylor y Maclaurin
* **Problema a Resolver:** Las unidades de procesamiento gráfico (GPU) y librerías matemáticas calculan funciones trigonométricas y exponenciales mediante aproximaciones de polinomios de Taylor.
* **Correspondencia con el PDF:**
  * Unidad 4: Series de potencias, radio de convergencia, series de Taylor/Maclaurin y cota de error del residuo de Lagrange.
* **Requerimientos Funcionales:**
  1. Generar los polinomios de Taylor $P_n(x)$ para $\sin(x)$, $\cos(x)$, $e^x$, $\ln(1+x)$, $\arctan(x)$ hasta el grado $n$ configurado.
  2. Graficar simultáneamente la función real y los polinomios sucesivos $P_1, P_2, P_5, P_{10}$, ilustrando visualmente el radio de convergencia.
  3. Calcular la cota superior del error mediante el residuo de Lagrange $|R_n(x)| \le \frac{M}{(n+1)!}|x-c|^{n+1}$ y contrastarlo contra el error computacional de punto flotante real.
* **Stack Tecnológico:** Python (SymPy, Matplotlib) o aplicación Web interactiva.
