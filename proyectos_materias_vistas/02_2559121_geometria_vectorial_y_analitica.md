# 2559121 – Geometría Vectorial y Analítica

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Geometría Vectorial y Analítica
* **Código de Curso:** 2559121
* **Unidad Académica:** Facultad de Ingeniería – Cursos de Servicios
* **Área:** Ciencias Básicas de Ingeniería
* **Créditos Académicos:** 4
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Sistemas de Ecuaciones Lineales y Álgebra Matricial**
   * Sistemas $2 \times 2$ y $3 \times 3$, interpretación geométrica (intersección de rectas y planos).
   * Método de reducción de Gauss y Gauss-Jordan.
   * Definición de $\mathbb{R}^n$, producto escalar de $n$-tuplas, ortogonalidad y combinaciones lineales.
2. **Unidad 2: La Función Determinante**
   * Definición, propiedades algebraicas y cálculo de determinantes.
   * Matriz inversa mediante la adjunta y Regla de Cramer.
3. **Unidad 3: Vectores Geométricos**
   * Magnitud, dirección, sentido y vectores equipolentes.
   * Suma geométrica (regla del paralelogramo y polígono) y multiplicación por un escalar.
4. **Unidad 4: Vectores Coordenados**
   * Componentes cartesianas en $\mathbb{R}^2$ y $\mathbb{R}^3$, cosenos directores y vector unitario.
5. **Unidad 5: Álgebra Vectorial**
   * Producto punto, proyección ortogonal y componente ortogonal.
   * Producto cruz (interpretación de área), producto mixto (volumen de paralelepípedos).
   * Ecuaciones vectoriales, paramétricas y simétricas de la recta en $\mathbb{R}^3$.
   * Ecuación vectorial, general y normal del plano en $\mathbb{R}^3$. Distancias punto-recta y punto-plano.
6. **Unidad 6: Vectores de la Física y Aplicaciones**
   * Fuerzas concurrentes, resultante, equilibrio estático, momento de una fuerza (torque) y trabajo mecánico como producto escalar.
7. **Unidad 7: Secciones Cónicas**
   * Circunferencia, parábola, elipse e hipérbola (ecuaciones canónicas y focales).
   * Traslación y rotación de ejes coordenados para eliminación del término mixto $Bxy$.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Mini-Motor Gráfico 3D Wireframe desde Cero (Sin Librerías 3D)
* **Problema a Resolver:** Los motores gráficos como Three.js o Unity abstraen toda la matemática espacial. Para un ingeniero de sistemas, comprender la proyección tridimensional sobre una pantalla bidimensional es el cimiento de la computación gráfica, CAD y visión por computador.
* **Correspondencia con el PDF:**
  * Unidad 4 y 5: Vectores en $\mathbb{R}^3$, proyecciones ortogonales y producto cruz para el cálculo de vectores normales de caras.
  * Unidad 1 y 2: Matrices de transformación geométrica (traslación, rotación con ángulos de Euler y escalado) y solución de sistemas de proyección de cámara.
* **Requerimientos Funcionales:**
  1. Cargar modelos en formato `.obj` básico (vértices y aristas).
  2. Implementar una cámara virtual definida por un punto de vista (*eye*), vector hacia dónde mira (*target*) y vector hacia arriba (*up vector*) usando producto cruz para construir la base ortonormal.
  3. Proyectar vértices del espacio tridimensional $\mathbb{R}^3$ al plano cartesiano $\mathbb{R}^2$ de la pantalla (proyección en perspectiva).
  4. Realizar *Back-face Culling*: calcular el vector normal a cada cara triangular usando el producto cruz $\vec{u} \times \vec{v}$ y omitir aquellas caras cuyo producto punto con el vector de visión sea negativo.
* **Stack Tecnológico:** Python (Pygame nativo / Canvas Tkinter) o TypeScript con HTML5 Canvas puro (sin WebGL ni Three.js).
* **Estructura Sugerida:**
  ```text
  wireframe-3d-engine/
  ├── src/
  │   ├── math/
  │   │   ├── Vector3.py       # Suma, producto punto, cruz, norma, proyecciones
  │   │   └── Matrix4x4.py     # Matrices de rotación, traslación y proyección
  │   ├── camera/
  │   │   └── Camera.py        # Base ortonormal de vista
  │   ├── geometry/
  │   │   └── Mesh.py          # Parser OBJ y lista de vértices/caras
  │   └── renderer/
  │       └── Engine.py        # Pipeline de renderizado en Canvas
  └── main.py
  ```
* **Valor en Entrevistas Técnicas:** Demuestra dominio directo de matemática espacial, álgebra vectorial sin dependencias de terceros y fundamentos de renderizado gráfico.

---

### Proyecto 2: Analizador, Clasificador y Graficador de Cónicas Generales con Rotación de Ejes
* **Problema a Resolver:** Determinar la naturaleza de una ecuación cuadrática general de segundo grado $Ax^2 + Bxy + Cy^2 + Dx + Ey + F = 0$ requiere eliminar el término mixto $Bxy$ calculando el ángulo de rotación $\cot(2\theta) = \frac{A - C}{B}$, aplicar transformaciones y clasificar la cónica (incluso si es degenerada).
* **Correspondencia con el PDF:**
  * Unidad 7: Ecuaciones canónicas de la elipse, parábola, hipérbola y circunferencia.
  * Unidad 1 y 7: Traslación y rotación de coordenadas mediante matrices de rotación ortogonales.
* **Requerimientos Funcionales:**
  1. Ingesta de coeficientes $[A, B, C, D, E, F]$ ingresados por el usuario.
  2. Cálculo del invariante discriminante $\Delta = B^2 - 4AC$ para clasificar el tipo de cónica (elipse si $\Delta < 0$, parábola si $\Delta = 0$, hipérbola si $\Delta > 0$).
  3. Cálculo automático del ángulo de rotación $\theta$ y generación de las nuevas variables rotadas $x', y'$.
  4. Completación de cuadrados para encontrar el centro/vértice traslados $(h, k)$.
  5. Graficación interactiva que muestre simultáneamente el sistema de coordenadas original $(x, y)$, el sistema rotado $(x', y')$, la curva cónica, los focos, vértices y directrices/asíntotas.
* **Stack Tecnológico:** Python (NumPy, Matplotlib, Streamlit o PyQt).
* **Valor en Entrevistas Técnicas:** Demuestra capacidad para trasladar deducciones analíticas formales de geometría analítica a algoritmos robustos de software matemático.

---

### Proyecto 3: Simulador de Equilibrio Estático y Momento de Fuerzas (Torque) en Estructuras 3D
* **Problema a Resolver:** En simulaciones físicas y robótica, es indispensable calcular el equilibrio de un cuerpo rígido sujeto a múltiples fuerzas en el espacio ($\sum \vec{F} = \vec{0}$ y $\sum \vec{\tau} = \sum (\vec{r} \times \vec{F}) = \vec{0}$).
* **Correspondencia con el PDF:**
  * Unidad 5 y 6: Producto cruz para momento de fuerza $\vec{\tau} = \vec{r} \times \vec{F}$, producto punto para cálculo de trabajo $W = \vec{F} \cdot \vec{d}$, sistemas lineales con Gauss-Jordan.
* **Requerimientos Funcionales:**
  1. Definir nodos espaciales y vectores de fuerza aplicados con magnitud y cosenos directores.
  2. Construir automáticamente la matriz del sistema de ecuaciones resultante de las condiciones de equilibrio.
  3. Resolver el sistema para encontrar fuerzas de reacción en apoyos fijos o articulaciones.
  4. Exportar el diagrama vectorial con representación visual de las tensiones y pares torsores.
* **Stack Tecnológico:** Python (NumPy, Matplotlib 3D).
