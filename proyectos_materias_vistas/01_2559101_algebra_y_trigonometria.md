# 2559101 – Álgebra y Trigonometría

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Álgebra y Trigonometría
* **Código de Curso:** 2559101
* **Unidad Académica:** Facultad de Ingeniería – Cursos de Servicios
* **Área:** Ciencias Básicas de Ingeniería
* **Créditos Académicos:** 3
* **Nivel:** 1
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial

---

## 2. Ejes Temáticos y Saberes Oficiales (según Microcurrículo)
1. **Unidad 1: Elementos de Aritmética y Sistemas Numéricos**
   * Razones, proporciones y proporcionalidad.
   * Sistemas numéricos y propiedades algebraicas de los números reales.
   * Progresiones aritméticas y geométricas (término general y sumatorias).
2. **Unidad 2: Potenciación, Radicación y Racionalización**
   * Leyes de exponentes enteros y racionales.
   * Radicales, simplificación y técnicas de racionalización de denominadores (monomios y binomios).
3. **Unidad 3: Polinomios y Ecuaciones Polinómicas**
   * Operaciones polinómicas, productos notables y técnicas avanzadas de factorización.
   * Teorema del Binomio de Newton y construcción del Triángulo de Pascal.
   * Ecuación cuadrática, discriminante y análisis de raíces.
   * Polinomios de grado superior: Algoritmo de división sintética, Teorema del Residuo, Teorema del Factor, Teorema de los Ceros Racionales y Regla de los Signos de Descartes.
4. **Unidad 4: Fracciones Algebraicas y Descomposición en Fracciones Parciales**
   * Simplificación y operaciones con fracciones racionales.
   * Descomposición en fracciones parciales (factores lineales y cuadráticos irreducibles, repetidos y no repetidos).
5. **Unidad 5: Funciones Exponenciales y Logarítmicas**
   * Propiedades de la función exponencial, modelos de crecimiento y decaimiento poblacional/radiactivo.
   * Logaritmos, cambios de base y propiedades algebraicas.
   * Resolución de ecuaciones exponenciales y logarítmicas.
6. **Unidad 6: Trigonometría, Resolución de Triángulos e Identidades**
   * Medición angular (grados sexagesimales y radianes), funciones circulares en el círculo unitario.
   * Trigonometría del triángulo rectángulo y resolución de triángulos oblicuángulos (Ley de Senos y Ley de Cosenos).
   * Verificación de identidades trigonométricas fundamentales, suma/resta y ángulo doble.
   * Resolución de ecuaciones trigonométricas en intervalos reales.
7. **Unidad 7: Números Complejos y Plano Complejo**
   * Forma estándar $z = a + bi$, conjugado y módulo.
   * Representación geométrica en el plano de Argand.
   * Forma polar y trigonométrica $z = r(\cos\theta + i\sin\theta)$.
   * Teorema de De Moivre para potencias y cálculo de las $n$-raíces en el plano complejo.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Motor Simbólico CAS Lite (Parser Polinómico, División Sintética y Fracciones Parciales)
* **Problema a Resolver:** En semestres posteriores (Cálculo Integral, Ecuaciones Diferenciales y Señales), descomponer expresiones racionales en fracciones parciales o hallar raíces exactas de polinomios de orden superior es indispensable. Construir un motor algebraico simbólico desde cero enseña manipulación de Árboles de Sintaxis Abstracta (AST), gramáticas y algoritmia algebraica exacta sin números flotantes imprecisos.
* **Correspondencia con el PDF:**
  * Unidad 3: Polinomios, división sintética, Teorema de Ceros Racionales y Teorema del Factor.
  * Unidad 4: Descomposición de fracciones racionales en factores lineales y cuadráticos irreducibles.
* **Requerimientos Funcionales:**
  1. Tokenizador y Parser matemático para cadenas como `(3x^3 - 2x^2 + 5)/(x^2 - 1)`.
  2. Implementar la división sintética automática dados los coeficientes y el divisor $(x - c)$.
  3. Búsqueda de todas las posibles raíces racionales usando el Teorema de Descartes y evaluación en divisores de $p/q$.
  4. Algoritmo de Descomposición en Fracciones Parciales que plantee el sistema lineal de coeficientes indeterminados y entregue la suma de términos simplificados.
  5. CLI interactivo con soporte de salida en texto formateado y notación LaTeX.
* **Stack Tecnológico:** Python o TypeScript (sin usar librerías simbólicas como SymPy o MathJS; implementado desde las estructuras de datos fundamentales).
* **Estructura Sugerida:**
  ```text
  cas-lite-engine/
  ├── src/
  │   ├── ast/
  │   │   ├── Expression.py      # Nodos del árbol sintáctico (Suma, Mult, Potencia)
  │   │   └── Polynomial.py      # Estructura de polinomio y coeficientes
  │   ├── parser/
  │   │   ├── Lexer.py           # Tokens numéricos, variables y operadores
  │   │   └── Parser.py          # Shunting-Yard o Recursive Descent
  │   ├── solvers/
  │   │   ├── SyntheticDivision.py # División sintética y residuo
  │   │   ├── RationalRoots.py     # Ceros racionales y factorización
  │   │   └── PartialFractions.py  # Descomposición en fracciones parciales
  │   └── cli.py
  └── tests/
      └── test_solvers.py
  ```
* **Valor en Entrevistas Técnicas:** Demuestra habilidades de diseño de compiladores/intérpretes básicos, comprensión profunda de manipulación simbólica y rigor en estructuras algorítmicas.

---

### Proyecto 2: Visualizador Interactivo del Plano Complejo de Argand y Generador Fractal de Julia/Mandelbrot
* **Problema a Resolver:** Los números complejos son la piedra angular del procesamiento de señales (FFT), computación cuántica y gráficos por computador. Desarrollar un sistema visual que grafique vectores complejos, aplique potencias con De Moivre y compute fractales de conjuntos de Julia explora directamente la convergencia en el plano complejo.
* **Correspondencia con el PDF:**
  * Unidad 7: Álgebra de complejos, forma binómica, forma polar ($r, \theta$), plano de Argand, potencias y raíces $n$-ésimas con el Teorema de De Moivre.
* **Requerimientos Funcionales:**
  1. Módulo aritmético complejo con conversión bidireccional inmediata: forma estándar ($a + bi$) $\leftrightarrow$ polar ($r \angle \theta$).
  2. Calculadora geométrica en el plano de Argand que dibuje las $n$ raíces complejas de un número, mostrando su polígono regular inscrito en la circunferencia de radio $\sqrt[n]{r}$.
  3. Renderizador de alta velocidad en Canvas para iterar la función cuadrática compleja $z_{k+1} = z_k^2 + c$ generando los conjuntos de Mandelbrot y Julia.
  4. Controles interactivos para zoom, paneo continuo y variación del parámetro complejo $c$ en tiempo real.
* **Stack Tecnológico:** Rust con WebAssembly o TypeScript con HTML5 Canvas / WebGL.
* **Valor en Entrevistas Técnicas:** Demuestra dominio de aritmética compleja, optimización de renderizado píxel a píxel y traslación directa de teoría matemática pura a software interactivo.

---

### Proyecto 3: Sistema de Triangulación, Geoposicionamiento y Simulación de Navegación 2D/3D
* **Problema a Resolver:** La robótica móvil, el posicionamiento satelital (GPS) y la visión artificial dependen críticamente de la trigonometría para estimar la posición de un agente u objeto a partir de distancias o ángulos medidos con sensores ruidosos.
* **Correspondencia con el PDF:**
  * Unidad 6: Trigonometría de triángulo rectángulo, identidades angulares, Ley de Senos y Ley de Cosenos en triángulos oblicuángulos.
* **Requerimientos Funcionales:**
  1. Modelar un entorno con balizas/antenas fijas cuyas coordenadas en el plano son conocidas.
  2. Implementar algoritmos de triangulación (basados en ángulos de azimut medidos) y trilateración (basados en distancias con Ley de Cosenos).
  3. Resolver automáticamente las ambigüedades geométricas de intersección de señales circulares.
  4. Dashboard interactivo con graficación de vectores de línea de vista, error de medición estimado y trayectoria estimada del robot/embarcación.
* **Stack Tecnológico:** Python (NumPy, Matplotlib o Dash/Plotly) o JavaScript/Canvas.
* **Valor en Entrevistas Técnicas:** Ejemplifica cómo la trigonometría analítica fundamental se convierte en soluciones para IoT, robótica autónoma y sistemas embebidos de navegación.
