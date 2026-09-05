# 2554306 – Lógica y Representación II

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Lógica y Representación II
* **Código de Curso:** 2554306
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 3
* **Pre-requisitos:** 2554208 – Lógica y Representación I | **Co-requisitos:** 2554303 – Matemáticas Discretas II
* **Modalidad:** Virtual / Presencial
* **Lenguaje Oficial:** Python

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Pilas y Colas (3 semanas)**
   * Pilas (LIFO): operaciones `push`, `pop`, `peek/top`. Pilas con listas ligadas y algoritmos con $N$-Pilas en arreglos compartidos.
   * Colas (FIFO): Colas No Circulares (CNC), Colas Circulares (CC), operaciones básicas y colas con listas ligadas.
   * Algoritmos de un arreglo con dos colas y un arreglo con $N$-Colas.
2. **Unidad 2: Análisis de Algoritmos (3 semanas)**
   * Costo computacional temporal y espacial.
   * Notación asintótica: Big-O ($O$), Big-Omega ($\Omega$) y Big-Theta ($\Theta$).
   * Mejor caso, caso promedio y peor caso.
   * Análisis formal de algoritmos iterativos y de estructuras de datos.
3. **Unidad 3: Recursión y Divide y Vencerás (3 semanas)**
   * Recursión directa e indirecta; transformación de iterativo a recursivo.
   * Análisis de complejidad de algoritmos recursivos mediante relaciones de recurrencia y el **Teorema Maestro**.
   * Algoritmos de ordenamiento eficientes: **MergeSort** ($O(n \log n)$) y **QuickSort** ($O(n \log n)$ promedio).
   * Algoritmos de selección de orden estadístico: **QuickSelect** y **Median-of-Medians (MomSelect)** ($O(n)$ en el peor caso).
   * Multiplicación rápida de enteros (Algoritmo de Karatsuba).
4. **Unidad 4: Árboles y Grafos (3 semanas)**
   * Grafos: representación por listas y matrices de adyacencia.
   * Algoritmo de Fleury para ciclos de Euler.
   * Recorridos BFS (*Breadth-First Search*) y DFS (*Depth-First Search*) para caminos sin ponderación.
   * Caminos mínimos con ponderación: **Algoritmo de Dijkstra** y **Algoritmo de Floyd-Warshall**.
   * Árboles enraizados, ordenados, $m$-arios e isomórficos. Árbol de expansión mínima: **Prim** y **Kruskal**.
   * Árbol de Búsqueda Binaria (BST) y árboles balanceados: **Árbol AVL** (rotaciones simples y dobles).
   * Estructura de datos **Heap / Montículo** binario (Min-Heap, Max-Heap) y ordenamiento **HeapSort**.
5. **Unidad 5: Programación Dinámica (2 semanas)**
   * Subestructura óptima y superposición de subproblemas. Memoización vs Tabulación.
   * Solución de problemas clásicos: Problema de la Mochila (0/1 Knapsack), Corte de Varillas y Subsecuencia Común Más Larga (LCS).
6. **Unidad 6: Teoría de NP-Completitud (2 semanas)**
   * Clases de complejidad P, NP, NP-Completo y NP-Hard. El problema P vs NP.
   * Reducciones polinomiales: 3-SAT, Ciclos Hamiltonianos, Conjunto Independiente y Cobertura de Vértices (*Vertex Cover*).

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Simulador de Enrutamiento y Navegación GPS (Dijkstra, Floyd-Warshall y Prim)
* **Problema a Resolver:** Encontrar rutas óptimas en redes urbanas de transporte con diferentes criterios (menor distancia, menor costo de peajes o menor tiempo con tráfico) y diseñar la red de interconexión de menor coste de tendido eléctrico o fibra óptica.
* **Correspondencia con el PDF:**
  * Unidad 4: Grafos ponderados, Dijkstra con Heap de prioridad, Floyd-Warshall para todas las distancias entre pares y Prim/Kruskal para árbol de expansión mínima.
* **Requerimientos Funcionales:**
  1. Cargar redes viales representadas como grafos dirigidos y ponderados (nodos = intersecciones, aristas = vías con pesos).
  2. Implementar **Dijkstra** utilizando una cola de prioridad basada en un **Min-Heap** binario propio para garantizar complejidad $O((V + E) \log V)$.
  3. Implementar **Floyd-Warshall** ($O(V^3)$) para generar la matriz de distancias mínimas globales entre todos los puntos del mapa.
  4. Algoritmo de **Prim o Kruskal** para calcular el tendido de costo mínimo que conecte todos los nodos sin ciclos.
  5. Interfaz gráfica interactiva que permita agregar nodos, aristas con pesos y visualizar el camino resaltado.
* **Stack Tecnológico:** Python (NetworkX para visualización, Pygame o Tkinter) o TypeScript (Canvas/Vis.js).
* **Valor en Entrevistas Técnicas:** Es la pregunta de entrevista número uno de grandes tecnológicas (FAANG) para evaluar grafos y montículos.

---

### Proyecto 2: Árbol AVL y Banco de Pruebas Comparativo con BST y Heaps
* **Problema a Resolver:** Demostrar cómo un árbol de búsqueda binario convencional se degrada a una lista enlazada $O(n)$ ante entradas ordenadas, mientras que un Árbol AVL mantiene balance estricto garantizando operaciones en tiempo $O(\log n)$.
* **Correspondencia con el PDF:**
  * Unidad 2 y 4: BST, Árbol AVL con rotaciones (LL, RR, LR, RL), Max-Heap, HeapSort y análisis asintótico de operaciones.
* **Requerimientos Funcionales:**
  1. Implementar la clase `ArbolAVL` desde cero con factores de equilibrio calculados y rotaciones automáticas tras cada inserción y eliminación.
  2. Implementar la clase `MaxHeap` con operaciones `insertar`, `extraer_max` y `heapify` para el algoritmo `HeapSort`.
  3. Visualizador de la jerarquía del árbol en consola o interfaz gráfica en tiempo real.
  4. Módulo de benchmarking: insertar 100,000 elementos ordenados consecutivamente en un BST estándar vs AVL, midiendo tiempos de búsqueda para corroborar el peor caso $O(n)$ vs $O(\log n)$.
* **Stack Tecnológico:** Python o C++.
* **Valor en Entrevistas Técnicas:** Demuestra maestría en estructuras de datos autorebalanceables y punteros/referencias.

---

### Proyecto 3: Optimizador de Recursos mediante Programación Dinámica y Comparador NP
* **Problema a Resolver:** Comparar la explosión combinatoria de algoritmos de fuerza bruta $O(2^n)$ contra soluciones polinomiales de Programación Dinámica en problemas de optimización empresarial (ej. empaquetamiento de servidores o asignación de presupuesto).
* **Correspondencia con el PDF:**
  * Unidades 3, 5 y 6: Recursión, divide y vencerás, programación dinámica (Knapsack 0/1, LCS) y teoría NP-Completa (reducción a Subset-Sum).
* **Requerimientos Funcionales:**
  1. Solucionador del Problema de la Mochila 0/1: implementación por recursión ingenua, memoización (top-down) y matriz de tabulación (bottom-up), reconstruyendo los ítems seleccionados.
  2. Medidor del límite en que la fuerza bruta se vuelve intratable ($n > 30$) mientras la programación dinámica se ejecuta en milisegundos.
  3. Documento anexo que demuestre formalmente la reducción polinomial de un problema NP-completo visto en clase.
* **Stack Tecnológico:** Python.
