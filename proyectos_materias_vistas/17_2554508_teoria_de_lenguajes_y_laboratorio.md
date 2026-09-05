# 2554508 – Teoría de Lenguajes y Laboratorio

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Teoría de Lenguajes y Laboratorio
* **Código de Curso:** 2554508
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 4
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Autómatas**
   * Alfabetos, cadenas, lenguajes y operaciones sobre lenguajes (concatenación, estrella de Kleene).
   * Autómatas Finitos Deterministas (DFA): funciones de transición, estados de aceptación.
   * Autómatas Finitos No Deterministas (NFA) y NFA con transiciones vacías (NFA-$\epsilon$).
   * Algoritmo de construcción de subconjuntos para conversión de NFA a DFA.
   * Algoritmos de minimización de estados en DFAs (Algoritmo de partición / Hopcroft).
   * Expresiones regulares y el **Algoritmo de Thompson** (conversión de regex a NFA-$\epsilon$).
   * Autómatas de Pila (*Pushdown Automata - PDA*) para reconocimiento de lenguajes libres de contexto.
2. **Unidad 2: Gramáticas**
   * Definición formal de gramática ($V_N, V_T, P, S$) y Clasificación de la Jerarquía de Chomsky (Tipo 0 a Tipo 3).
   * Gramáticas regulares y su equivalencia con autómatas finitos.
   * Gramáticas Libres de Contexto (GLC): derivaciones por izquierda, derivaciones por derecha y árboles de análisis sintáctico (*parse trees*).
   * Ambigüedad en gramáticas y transformación para eliminación de ambigüedad.
   * Formas normales de Chomsky y Greibach.
   * Gramáticas de traducción y esquemas de traducción dirigida por la sintaxis (SDTS).
3. **Unidad 3: Reconocimiento Descendente (Top-Down Parsing)**
   * Cálculo de conjuntos **Primero (*First*)** y **Siguiente (*Follow*)**.
   * Gramáticas y tablas de análisis **LL(1)**.
   * Transformaciones de gramáticas: eliminación de recursión por izquierda (directa e indirecta) y factorización por izquierda.
   * Implementación de un **Analizador Sintáctico Descendente Recursivo** sin retroceso.
4. **Unidad 4: Reconocimiento Ascendente (Bottom-Up Parsing)**
   * Mecanismo de desplazamiento y reducción (*Shift-Reduce parsing*).
   * Colección de elementos canónicos y autómatas **LR(0)**.
   * Construcción de tablas de análisis sintáctico **SLR(1)**.
   * Elementos y tablas **LR(1)** canónicas y **LALR(1)**.
   * Resolución de conflictos Desplazamiento-Reducción (*Shift-Reduce*) y Reducción-Reducción (*Reduce-Reduce*).
   * Uso de herramientas generadoras de analizadores léxicos y sintácticos (Lex/Flex, Yacc/Bison o ANTLR).

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Compilador e Intérprete Completo de un Lenguaje Específico (DSL / Toy Language)
* **Problema a Resolver:** Comprender a fondo cómo un archivo de texto con código fuente se convierte en instrucciones ejecutables en memoria mediante las fases de análisis léxico, análisis sintáctico, validación semántica y generación de código o evaluación.
* **Correspondencia con el PDF:**
  * Unidades 1, 2, 3 y 4: Tokens con expresiones regulares, gramática libre de contexto formal en EBNF, parser descendente recursivo / tabla LL(1) o LALR, construcción del AST y evaluación dirigida por sintaxis.
* **Requerimientos Funcionales:**
  1. Diseñar la gramática formal para un lenguaje que soporte: variables, tipos (números, booleanos, cadenas), estructuras de control (`if/else`, `while`), funciones con parámetros y retorno.
  2. **Lexer (Analizador Léxico):** tokenizador que ignore espacios en blanco y comentarios, reportando número de línea y columna ante caracteres ilegales.
  3. **Parser (Analizador Sintáctico):** construcción del Árbol de Sintaxis Abstracta (AST) eliminando ambigüedades en la precedencia de operadores mediante análisis descendente recursivo.
  4. **Analizador Semántico:** verificación de ámbito de variables (*scope*) y comprobación estricta de tipos.
  5. **Evaluador/Intérprete:** recorrer el AST ejecutando el programa con su propio entorno de variables (*Environment / Symbol Table*).
* **Stack Tecnológico:** Python, Java o TypeScript (implementado de forma artesanal o con apoyo de ANTLR4).
* **Valor en Entrevistas Técnicas:** Es la cúspide de la ingeniería de software fundacional. Demuestra recursión profunda, manejo de árboles, patrones Visitor e intérpretes de ejecución.

---

### Proyecto 2: Motor de Expresiones Regulares desde Cero (Regex-to-DFA Engine)
* **Problema a Resolver:** Las utilidades como `grep` o los validadores de regex ejecutan autómatas finitos. Construir la cadena de transformación completa desde el texto del patrón regex hasta la ejecución en tiempo lineal demuestra el dominio absoluto de la computación teórica.
* **Correspondencia con el PDF:**
  * Unidad 1: Expresiones regulares, Algoritmo de Thompson (Regex $\to$ NFA-$\epsilon$), Algoritmo de Construcción de Subconjuntos (NFA $\to$ DFA) y Algoritmo de Minimización de Hopcroft.
* **Requerimientos Funcionales:**
  1. Parser del patrón regex con soporte para concatenación, unión (`|`) y cerradura de Kleene (`*`), además de paréntesis para agrupación.
  2. Conversión a NFA-$\epsilon$ mediante el **Algoritmo de Thompson**.
  3. Conversión de NFA a DFA determinista mediante cálculo de $\epsilon$-clausuras y subconjuntos.
  4. Minimización del DFA reduciendo el número de estados al autómata canónico mínimo.
  5. Motor de matching que evalúa si una cadena dada es aceptada en tiempo $O(|cadena|)$, sin retrocesos exponenciales (*catastrophic backtracking*).
* **Stack Tecnológico:** Python, C++ o Rust.
* **Valor en Entrevistas Técnicas:** Distingue inmediatamente a un candidato en roles de infraestructura de software, lenguajes de programación y herramientas de desarrollo.

---

### Proyecto 3: Calculador de Conjuntos Primero/Siguiente y Generador de Tablas LL(1) / SLR(1)
* **Problema a Resolver:** Automatizar el proceso manual que realizan los estudiantes y compiladores para determinar si una gramática dada es apta para análisis sintáctico determinista sin conflictos.
* **Correspondencia con el PDF:**
  * Unidades 2, 3 y 4: Gramáticas libres de contexto, cálculo de First y Follow, detección de recursión por izquierda y construcción de tablas LL(1) y SLR(1).
* **Requerimientos Funcionales:**
  1. Ingesta de producciones de una gramática libre de contexto en formato texto.
  2. Detección y eliminación automática de recursión directa por la izquierda.
  3. Cálculo algorítmico recursivo de los conjuntos $Primero(\alpha)$ y $Siguiente(A)$.
  4. Generación y visualización de la tabla de análisis sintáctico predictivo LL(1), alertando si la gramática no es LL(1) por conflictos en celdas.
* **Stack Tecnológico:** Python o Web interactiva.
