# 2554207 – Matemáticas Discretas I

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Matemáticas Discretas I
* **Código de Curso:** 2554207
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 3
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad I: Lógica Proposicional y Cuantificacional (8 semanas)**
   * Proposiciones, operadores lógicos, tablas de verdad, tautologías, contradicciones y contingencias.
   * Leyes de equivalencia lógica (De Morgan, absorción, distribución, condicional).
   * Formas normales disyuntiva y conjuntiva (FND, FNC).
   * Lógica de predicados, cuantificadores universal ($\forall$) y existencial ($\exists$), negación de cuantificadores.
   * Reglas de inferencia lógica (Modus Ponens, Modus Tollens, Silogismos, Resolución).
   * Métodos formales de demostración: demostración directa, por contraposición, reducción al absurdo (contradicción) y por casos.
2. **Unidad II: Conjuntos y Relaciones (3 semanas)**
   * Álgebra de conjuntos, subconjuntos, operaciones (unión, intersección, diferencia simétrica, complemento) y producto cartesiano.
   * Relaciones binarias sobre conjuntos: definición, matrices booleanas de adyacencia y digrafos de relaciones.
   * Propiedades de las relaciones: reflexiva, irreflexiva, simétrica, antisimétrica, asimétrica y transitiva.
   * Clausuras de relaciones: reflexiva, simétrica y clausura transitiva (Algoritmo de Warshall).
   * Relaciones de equivalencia, clases de equivalencia y particiones de un conjunto.
   * Relaciones de orden parcial (posets), elementos maximales/minimales, cotas superiores/inferiores, diagramas de Hasse y Retículas (*lattices*).
3. **Unidad III: Álgebra Booleana y Sistemas Numéricos (3 semanas)**
   * Postulados de Huntington y definición formal de Álgebra de Boole.
   * Funciones booleanas, minitérminos, maxitérminos y formas canónicas (Suma de Productos y Producto de Sumas).
   * Minimización algebraica y mapas de Karnaugh para simplificación de circuitos.
   * Sistemas de numeración: binario, octal, hexadecimal, conversión entre bases.
   * Representación de números enteros con signo (signo y magnitud, complemento a 1, complemento a 2) y aritmética binaria.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Evaluador Simbólico de Lógica Proposicional y Verificador Formal de Argumentos
* **Problema a Resolver:** En verificación formal de software, los ingenieros deben validar si una especificación lógica es consistente o si un argumento formal es válido sin cometer errores humanos.
* **Correspondencia con el PDF:**
  * Unidad I: Tablas de verdad, operadores lógicos, reglas de inferencia, equivalencias de De Morgan y el principio de resolución lógica.
* **Requerimientos Funcionales:**
  1. Parser de expresiones proposicionales con sintaxis estándar: `(P & Q) -> (R | ~P)`.
  2. Generación automática y formateada de tablas de verdad completas con evaluación paso a paso por subexpresiones.
  3. Clasificación formal: Tautología, Contradicción o Contingencia.
  4. Módulo de Verificación de Argumentos: el usuario introduce premisas $P_1, P_2, \dots, P_k$ y una conclusión $C$; el motor determina si el razonamiento es formalmente válido mediante tablas o reducción al absurdo (método de resolución).
  5. Conversor a Formas Normales: transformar cualquier proposición a Forma Normal Conjuntiva (FNC) y Forma Normal Disyuntiva (FND).
* **Stack Tecnológico:** Python (con librería `lark` o parser manual) o TypeScript con interfaz web interactiva.
* **Valor en Entrevistas Técnicas:** Demuestra diseño de compiladores preliminares, árboles lógicos y base matemática para verificación de sistemas críticos.

---

### Proyecto 2: Analizador Computacional de Relaciones Binarias, Clausuras y Diagramas de Hasse
* **Problema a Resolver:** Modelar jerarquías de permisos (Role-Based Access Control - RBAC), dependencias de tareas o relaciones de orden requiere verificar propiedades matemáticas y calcular clausuras transitivas eficientemente.
* **Correspondencia con el PDF:**
  * Unidad II: Relaciones binarias, propiedades de orden/equivalencia, algoritmo de Warshall, diagramas de Hasse y retículas.
* **Requerimientos Funcionales:**
  1. Ingreso de un conjunto finito $A$ y un conjunto de pares ordenados $R \subseteq A \times A$.
  2. Detección algorítmica de propiedades: reflexividad, simetría, antisimetría y transitividad utilizando operaciones matriciales booleanas.
  3. Implementación del **Algoritmo de Warshall** para calcular la clausura transitiva $R^+$ en tiempo $O(n^3)$.
  4. Si es relación de equivalencia: generar el conjunto cociente $A / R$ (partición en clases de equivalencia).
  5. Si es conjunto parcialmente ordenado (poset): calcular elementos maximales, minimales, supremo, ínfimo y renderizar el **Diagrama de Hasse** eliminando aristas redundantes y bucles reflexivos.
* **Stack Tecnológico:** Python (NetworkX, Matplotlib, NumPy) o Web (vis.js / D3.js).
* **Valor en Entrevistas Técnicas:** Conecta teoría abstracta de conjuntos con modelado de ontologías, sistemas de bases de datos relacionales y grafos de precedencia.

---

### Proyecto 3: Optimizador de Circuitos Booleanos y Convertidor Aritmético de Complemento a Dos
* **Problema a Resolver:** Diseñar un simulador que ayude a comprender cómo la CPU almacena enteros negativos y cómo las compuertas lógicas pueden simplificarse mediante álgebra de Boole.
* **Correspondencia con el PDF:**
  * Unidad III: Álgebra booleana, formas canónicas, mapas de Karnaugh de 2 a 4 variables y representación en complemento a 2.
* **Requerimientos Funcionales:**
  1. Convertidor de números entre bases (base 2, 8, 10, 16) y cálculo paso a paso de representación en punto fijo y Complemento a Dos con $N$ bits (detectando condiciones de desbordamiento/overflow).
  2. Simplificador booleano: dada una tabla de verdad o minitérminos, generar el Mapa de Karnaugh correspondiente, agrupar las potencias de 2 y retornar la función mínima en Suma de Productos (SOP).
* **Stack Tecnológico:** Python o JavaScript.
