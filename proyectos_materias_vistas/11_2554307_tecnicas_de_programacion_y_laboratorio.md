# 2554307 – Técnicas de Programación y Laboratorio

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Técnicas de Programación y Laboratorio
* **Código de Curso:** 2554307
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 4
* **Pre-requisitos:** Ninguno | **Co-requisitos:** 2554306 – Lógica y Representación II
* **Modalidad:** Virtual / Presencial
* **Lenguaje Oficial:** Java (deseable Python complementario)

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Introducción a los Lenguajes de Programación (4 semanas)**
   * Generalidades de los lenguajes; elección del lenguaje según el tipo de problema.
   * IDEs, frameworks y herramientas de construcción (Maven/Gradle).
   * Tipos primitivos, expresiones aritmético-lógicas, precedencia de operadores.
   * Colecciones de datos nativas del lenguaje (arreglos, matrices, listas, conjuntos, mapas).
   * Algoritmos de búsqueda, ordenamiento y recorrido en colecciones.
   * Manejo de strings, expresiones regulares (Regex) y conversión de tipos.
   * Recursión y estructuras de representación.
2. **Unidad 2: Paradigmas de Programación (2 semanas)**
   * Definición formal de paradigma y comparación técnica:
     * Paradigma Imperativo y Procedimental (procedimientos, funciones, efectos secundarios).
     * Paradigma Declarativo y Funcional (funciones puras, inmutabilidad, funciones de orden superior, streams/lambdas).
     * Paradigma Reactivo (asincronía, flujos de eventos).
     * Programación probabilística.
3. **Unidad 3: Paradigma Orientado a Objetos y Buenas Prácticas (3 semanas)**
   * Conceptos esenciales: Abstracción, Encapsulamiento, Herencia, Polimorfismo y Sobrecarga.
   * Clases abstractas, interfaces y modificador `static`.
   * Diagramación de Clases en UML.
   * **Principios SOLID** (Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion).
   * **Código Limpio (Clean Code)** y estándares de nombramiento.
   * Control de versiones colaborativo con Git y GitHub.
4. **Unidad 4: Archivos, Excepciones y Calidad de Software (3 semanas)**
   * Jerarquía de excepciones en Java (`checked` vs `unchecked`, bloques `try-catch-finally`, creación de excepciones personalizadas).
   * Gestión de archivos y serialización: lectura/escritura de formatos CSV y JSON (librerías como Gson o Jackson).
   * Generación de reportes en PDF (librerías como iText).
   * Construcción y empaquetado de librerías reutilizables (`.jar`).
   * Documentación estandarizada con **JavaDoc**.
   * Pruebas unitarias automatizadas con **JUnit**.
5. **Unidad 5: Desarrollo de Aplicaciones Web (3 semanas)**
   * Fundamentos de frontend: HTML5 semántico, maquetación con CSS3 y dinamismo con JavaScript nativo.
   * Integración con backend (API REST / Servlets) para consumo de datos.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Sistema Empresarial de Facturación y Nómina con Principios SOLID, JUnit y JavaDoc
* **Problema a Resolver:** En entornos corporativos Java, el código debe ser mantenible, extensible sin modificar código existente (Open/Closed), documentado rigurosamente y cubierto por pruebas unitarias automatizadas antes de pasar a integración continua.
* **Correspondencia con el PDF:**
  * Unidades 1, 3 y 4: POO avanzada en Java (interfaces, clases abstractas, polimorfismo), principios SOLID, jerarquía de excepciones personalizadas, persistencia en JSON/CSV, generación de facturas en PDF y testing con JUnit 5.
* **Requerimientos Funcionales:**
  1. Modelo de dominio jerárquico: `Empleado` (abstracto), `EmpleadoTiempoCompleto`, `EmpleadoPorHoras`, `Contratista`.
  2. Implementación de interfaces segregadas: `Calculable`, `Exportable`, `Auditable`.
  3. Módulo de procesamiento de nómina usando Streams y Lambdas de Java (paradigma funcional) para filtrar, mapear totales y calcular retenciones fiscales.
  4. Persistencia en archivos JSON usando Jackson o Gson, implementando un patrón repositorio desacoplado mediante inversión de dependencias.
  5. Generador de desprendibles de pago en formato PDF utilizando la librería `OpenPDF` o `iText`.
  6. Suite completa de pruebas unitarias con **JUnit 5** cubriendo casos borde (sueldos negativos, formatos corruptos) con cobertura superior al 85%.
  7. Documentación completa del proyecto generada con JavaDoc en formato HTML.
* **Stack Tecnológico:** Java 17+, Maven, JUnit 5, Jackson, OpenPDF/iText.
* **Estructura Sugerida:**
  ```text
  payroll-solid-system/
  ├── pom.xml
  ├── src/
  │   ├── main/java/com/udea/payroll/
  │   │   ├── model/         # Empleados, Contratos, Deducciones
  │   │   ├── service/       # LiquidacionService, ImpuestosService
  │   │   ├── repository/    # JsonEmpleadoRepository
  │   │   ├── exporter/      # PdfExporter, CsvExporter
  │   │   └── exception/     # PayrollBusinessException
  │   └── test/java/com/udea/payroll/
  │       └── service/       # LiquidacionServiceTest.java
  └── docs/javadoc/
  ```
* **Valor en Entrevistas Técnicas:** Demuestra dominio corporativo de Java estándar, buenas prácticas de ingeniería, TDD básico y madurez arquitectónica.

---

### Proyecto 2: Comparador Multi-paradigma de Solución de Problemas (Imperativo vs Funcional vs Reactivo)
* **Problema a Resolver:** Explicar y contrastar la eficiencia, legibilidad y concurrencia al resolver un mismo problema complejo (ej. procesamiento masivo de transacciones sospechosas de fraude bancario) bajo diferentes paradigmas de programación.
* **Correspondencia con el PDF:**
  * Unidad 2: Estudio comparativo de paradigmas: imperativo con ciclos y estados mutables, funcional puro con inmutabilidad y streams paralelos, y reactivo con flujos asíncronos.
* **Requerimientos Funcionales:**
  1. Procesamiento de 1 millón de transacciones sintéticas.
  2. Implementación 1 (Imperativa): bucles `for`, arreglos mutables y variables de acumulación.
  3. Implementación 2 (Funcional): Java Streams API / Lambdas / `CompletableFuture`, funciones puras sin efectos secundarios.
  4. Implementación 3 (Reactiva): Project Reactor (`Flux` / `Mono`) o RxJava con manejo de contrapresión (*backpressure*).
  5. Benchmark comparativo que reporte tiempo de CPU, uso de memoria RAM y legibilidad de código.
* **Stack Tecnológico:** Java 17+ (Project Reactor).
* **Valor en Entrevistas Técnicas:** Diferenciador de alto nivel: la mayoría de juniors solo conocen código imperativo; demostrar dominio funcional y reactivo destaca de inmediato.

---

### Proyecto 3: Aplicación Web Interactiva de Gestión con Frontend JS y Backend Java
* **Problema a Resolver:** Construir una solución extremo a extremo (full-stack) conectando una interfaz web responsiva construida desde cero con un backend en Java.
* **Correspondencia con el PDF:**
  * Unidad 4 y 5: Entrada/salida HTTP, parsing de JSON, maquetación HTML5, estilos CSS3 y JavaScript moderno con `fetch`.
* **Requerimientos Funcionales:**
  1. Frontend en HTML5 semántico con diseño responsivo CSS3 (sin frameworks pesados) y manipulación del DOM con JavaScript.
  2. Backend ligero en Java (HTTP Server nativo de Java o Spring Boot mínimo) exponiendo endpoints REST (`GET`, `POST`, `DELETE`).
  3. Validaciones de formularios en el cliente mediante expresiones regulares (Regex) y validación cruzada en el servidor.
* **Stack Tecnológico:** Java, JavaScript (ES6+), HTML5, CSS3.
