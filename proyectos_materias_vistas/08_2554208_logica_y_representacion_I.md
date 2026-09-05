# 2554208 – Lógica y Representación I

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Lógica y Representación I
* **Código de Curso:** 2554208
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 3
* **Pre-requisitos:** Ninguno | **Co-requisitos:** 2554207 – Matemáticas Discretas I
* **Modalidad:** Virtual / Presencial
* **Lenguaje Oficial de Referencia:** Python

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Algoritmos Secuenciales (2 semanas)**
   * Problemas y tipos de soluciones; etapas del proceso de desarrollo de software.
   * Algoritmos, programas y productos de software.
   * Entradas, proceso y salida de un algoritmo.
   * Elementos del algoritmo: variables, tipos de datos primitivos, operadores y expresiones aritmético-lógicas.
   * Pruebas de escritorio y casos de prueba formales.
   * Implementación de algoritmos secuenciales en Python.
2. **Unidad 2: Introducción a la Programación Orientada a Objetos (2 semanas)**
   * El paradigma orientado a objetos, abstracción y encapsulamiento.
   * Clases, objetos, atributos de estado y métodos de comportamiento.
   * Tipos de métodos: constructores (`__init__`), analizadores/accesores (`getters`), modificadores (`setters`).
3. **Unidad 3: Estructuras de Control Selectivas (2 semanas)**
   * Condicionales simples (`if`), dobles (`if-else`) y anidados (`elif`).
   * Validación de reglas de negocio y ramas de decisión.
4. **Unidad 4: Estructuras de Control Repetitivas (3 semanas)**
   * Variables contadoras, acumuladoras y banderas centinelas.
   * Ciclos basados en condición (`while` / Mientras-Haga).
   * Ciclos basados en contador/colección (`for` / Para-Haga).
5. **Unidad 5: Estructuras de Datos Estáticas – Arreglos Unidimensionales (3 semanas)**
   * Listas/arreglos unidimensionales: almacenamiento, indexación y mutabilidad.
   * Algoritmos de ordenamiento clásicos: Burbuja (*Bubble Sort*), Selección (*Selection Sort*) e Inserción (*Insertion Sort*).
   * Algoritmos de búsqueda: Búsqueda lineal ($O(n)$) y búsqueda binaria ($O(\log n)$ en arreglos ordenados).
6. **Unidad 6: Estructuras de Datos Estáticas – Arreglos Bidimensionales (2 semanas)**
   * Matrices: declaración, indexación, recorrido por filas y recorrido por columnas.
   * Operaciones con matrices: traspuesta, suma matricial, simetría y aplicaciones tabulares.
7. **Unidad 7: Persistencia de Datos con Archivos (2 semanas)**
   * Entrada y salida de datos a almacenamiento secundario.
   * Modos de apertura de archivos (`r`, `w`, `a`), lectura línea a línea y escritura bufferizada.
   * Serialización y almacenamiento de arreglos en archivos planos (CSV y texto).

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Sistema de Gestión de Notas y Rendimiento Académico con Persistencia Plana
* **Problema a Resolver:** Administrar las calificaciones de estudiantes por materias, cortes y créditos mediante estructuras matriciales, persistiendo la información de forma segura en disco sin bases de datos externas.
* **Correspondencia con el PDF:**
  * Unidades 1, 2, 3, 4, 5 y 7: Clases `Estudiante` y `Materia`, condicionales para estados de aprobación, ciclos de cálculo ponderado, ordenamiento de estudiantes por promedio (Burbuja o Inserción) y persistencia en archivos CSV.
* **Requerimientos Funcionales:**
  1. Ingesta de datos de estudiantes con validación de entradas numéricas (notas entre 0.0 y 5.0).
  2. Almacenar estudiantes en un arreglo unidimensional de objetos y las notas en matrices bidimensionales.
  3. Cálculo automático de promedios ponderados, notas mínimas requeridas para el último corte y determinación de estudiantes en cuadro de honor o prueba académica.
  4. Ordenar la lista de estudiantes por promedio descendente usando **Selection Sort** o **Insertion Sort** implementado manualmente.
  5. Búsqueda rápida de estudiantes por documento de identidad mediante **Búsqueda Binaria**.
  6. Guardar y cargar el estado completo del curso en archivos planos estructurados `.csv`.
* **Stack Tecnológico:** Python 3 puro (sin librerías externas como Pandas).
* **Estructura Sugerida:**
  ```text
  academic-grade-system/
  ├── src/
  │   ├── models/
  │   │   ├── Estudiante.py
  │   │   └── Calificacion.py
  │   ├── services/
  │   │   ├── GestorAcademico.py
  │   │   ├── AlgoritmosOrdenamiento.py
  │   │   └── PersistenciaCSV.py
  │   └── ui/
  │       └── MenuConsola.py
  ├── data/
  │   └── estudiantes.csv
  └── main.py
  ```
* **Valor en Entrevistas Técnicas:** Demuestra dominio impecable de los fundamentos de programación limpia, algoritmos de ordenamiento manuales y POO básica.

---

### Proyecto 2: Simulador y Motor del Juego "Batalla Naval" (Matrices 2D y POO)
* **Problema a Resolver:** Implementar un juego interactivo de estrategia en consola donde dos tableros matriciales interactúan bajo reglas de turnos, barcos de distintas dimensiones, detección de disparos y guardado de partidas.
* **Correspondencia con el PDF:**
  * Unidades 2, 4, 6 y 7: Clases de POO (`Tablero`, `Barco`, `Partida`), manipulación profunda de arreglos bidimensionales (acceso fila/columna, colocación vertical/horizontal) y persistencia del estado en disco.
* **Requerimientos Funcionales:**
  1. Tableros de $10 \times 10$ representados como matrices bidimensionales.
  2. Colocación aleatoria y manual de barcos de 1, 2, 3 y 4 casillas sin solapamiento ni desbordamiento de límites.
  3. Mecánica de disparo: coordenadas fila-columna, verificación de "Agua", "Tocado" o "Hundido".
  4. Algoritmo de Inteligencia Artificial básica para el rival de la computadora (modo caza tras un impacto exitoso explorando celdas adyacentes).
  5. Opción de "Guardar Partida" en archivo de texto plano para reanudar el juego posteriormente.
* **Stack Tecnológico:** Python 3.
* **Valor en Entrevistas Técnicas:** Demuestra control de flujo, modelado de estados mediante matrices y código estructurado modular.

---

### Proyecto 3: Benchmark Interactivo de Algoritmos de Ordenamiento y Búsqueda
* **Problema a Resolver:** Visualizar y medir empíricamente cuántas comparaciones e intercambios realizan los tres algoritmos clásicos de primer semestre (Burbuja, Selección e Inserción) sobre arreglos de diferentes tamaños.
* **Correspondencia con el PDF:**
  * Unidad 5: Ordenamiento por burbuja, selección, inserción, búsqueda lineal y binaria.
* **Requerimientos Funcionales:**
  1. Generar listas aleatorias, ya ordenadas e inversamente ordenadas de tamaño $N \in [10, 100, 1000, 5000]$.
  2. Contabilizar número exacto de operaciones elementales (comparaciones y swaps) y tiempo de CPU transcurrido.
  3. Demostrar empíricamente la diferencia entre búsqueda secuencial ($O(n)$) y búsqueda binaria ($O(\log n)$) tras ordenar.
  4. Exportar reporte tabular a consola y a archivo `.txt`.
* **Stack Tecnológico:** Python.
