# 2559131 – Cálculo Diferencial

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Cálculo Diferencial
* **Código de Curso:** 2559131
* **Unidad Académica:** Facultad de Ingeniería – Instituto de Matemáticas (FCEN)
* **Área:** Ciencias Básicas de Ingeniería
* **Créditos Académicos:** 4
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Pre-cálculo y Fundamentos de Funciones**
   * Números reales, desigualdades, intervalos, inecuaciones y valor absoluto.
   * Sistema cartesiano, línea recta, funciones (dominio, rango, tipos de funciones).
   * Operaciones, desplazamientos, alargamientos y compresiones.
2. **Límites de Funciones y Continuidad**
   * Noción intuitiva y formal de límite ($\epsilon-\delta$).
   * Límites laterales, límites infinitos y al infinito; asíntotas verticales y horizontales.
   * Continuidad de funciones y Teorema del Valor Intermedio (TVI).
3. **La Derivada**
   * Razón de cambio promedio e instantánea, definición formal de derivada como límite del cociente de diferencias.
   * Interpretación geométrica (pendiente de la recta tangente) y física (velocidad instantánea).
   * Reglas de derivación: constante, potencia, suma, producto, cociente y regla de la cadena.
   * Derivación implícita y derivadas de orden superior.
4. **Aplicaciones de la Derivada**
   * Razones de cambio relacionadas en problemas de ingeniería.
   * Aproximaciones lineales y diferenciales.
   * Valores extremos (máximos y mínimos locales y absolutos), Teorema de Rolle y Teorema del Valor Medio.
   * Criterio de la primera derivada (crecimiento/decrecimiento) y de la segunda derivada (concavidad y puntos de inflexión).
   * Problemas de optimización aplicada y análisis completo para el trazado de curvas.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Motor Interactivo de Optimización y Visualizador de Descenso de Gradiente (1D y 2D)
* **Problema a Resolver:** En inteligencia artificial y machine learning, los modelos ajustan sus parámetros encontrando el mínimo de una función de pérdida mediante derivadas sucesivas. Conectar el cálculo diferencial con el descenso de gradiente es el puente clave entre las matemáticas puras y la ingeniería de software moderna.
* **Correspondencia con el PDF:**
  * Puntos críticos, derivadas de primer y segundo orden, concavidad y optimización analítica vs numérica.
* **Requerimientos Funcionales:**
  1. Permitir al usuario ingresar una función objetivo $f(x)$ (o $f(x, y)$) diferenciable.
  2. Implementar el algoritmo de descenso de gradiente: $x_{k+1} = x_k - \alpha f'(x_k)$ donde la derivada se calcula tanto analíticamente (reglas de derivación) como por aproximación de diferencias finitas.
  3. Visualizar en tiempo real el paso a paso del descenso, comparando la tasa de aprendizaje $\alpha$ y detectando mínimos locales, puntos de silla o divergencia cuando $\alpha$ es excesivo.
  4. Analizar la segunda derivada $f''(x)$ en el punto convergido para confirmar formalmente el criterio de convexidad/concavidad (mínimo local si $f''(x) > 0$).
* **Stack Tecnológico:** Python (NumPy, Matplotlib / Plotly, Streamlit o Web interactiva en Vue/React con Math.js).
* **Valor en Entrevistas Técnicas:** Conecta directamente los conceptos de cálculo de primer semestre con los fundamentos de optimización de algoritmos de Machine Learning y Deep Learning.

---

### Proyecto 2: Motor de Diferenciación Simbólica y Análisis de Curvas (Parser AST)
* **Problema a Resolver:** Construir un programa que no solo evalúe números, sino que manipule expresiones matemáticas formalmente, aplicando recursivamente la regla de la cadena, del producto y del cociente sobre un Árbol de Sintaxis Abstracta (AST).
* **Correspondencia con el PDF:**
  * Reglas formales de derivación, cálculo de asíntotas, puntos de inflexión y raíces del Teorema del Valor Intermedio.
* **Requerimientos Funcionales:**
  1. Parser que recibe una expresión matemática en texto (ej. `x^3 - 3*x + 1` o `sin(2*x)/(x+1)`).
  2. Construir un árbol de operaciones binarias y unarias.
  3. Implementar un método recursivo `diferenciar(nodo, variable)` que retorne el árbol simplificado de la derivada $f'(x)$ y $f''(x)$.
  4. Algoritmo de bisección o Newton-Raphson guiado por el Teorema del Valor Intermedio para localizar raíces y puntos críticos ($f'(x) = 0$).
  5. Graficar automáticamente la función con sus rectas tangentes interactivas, asíntotas verticales/horizontales y puntos de inflexión marcados.
* **Stack Tecnológico:** Python o TypeScript/JavaScript.
* **Valor en Entrevistas Técnicas:** Demuestra diseño de compiladores básicos, recursión profunda, estructuras de datos en árbol y rigor matemático.

---

### Proyecto 3: Simulador de Problemas de Razones de Cambio Relacionadas en Tiempo Real
* **Problema a Resolver:** Modelar visual y computacionalmente problemas dinámicos clásicos (vaciado cónico de agua, sombra de un poste con peatón en movimiento, radar de tráfico con vectores de posición) donde varias variables cambian con respecto al tiempo $t$.
* **Correspondencia con el PDF:**
  * Razones de cambio relacionadas y derivación implícita con respecto a la variable temporal $t$.
* **Requerimientos Funcionales:**
  1. Simulación física interactiva parametrizable (altura de tanque cónico, caudal de entrada/salida $dV/dt$).
  2. Cálculo numérico y analítico simultáneo de la velocidad a la que varía el nivel del agua $dh/dt$ en cualquier instante.
  3. Comparador entre la derivada teórica instantánea y la tasa de cambio promedio $\frac{\Delta h}{\Delta t}$ para ilustrar la convergencia del límite cuando $\Delta t \to 0$.
* **Stack Tecnológico:** JavaScript (Canvas API / p5.js) o Python con Pygame.
