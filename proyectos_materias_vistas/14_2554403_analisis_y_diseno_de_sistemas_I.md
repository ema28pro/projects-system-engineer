# 2554403 – Análisis y Diseño de Sistemas I

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Análisis y Diseño de Sistemas I
* **Código de Curso:** 2554403
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Profesional / Ingeniería de Software
* **Créditos Académicos:** 3
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Ingeniería de Software (2 semanas)**
   * Historia y evolución del software; la "crisis del software".
   * Conceptos fundamentales de procesos de software (prescriptivos, iterativos, ágiles).
   * Enfoques generales de metodologías de desarrollo y tendencias modernas.
   * Introducción al modelado conceptual y su importancia en ingeniería.
2. **Unidad 2: Modelado de Procesos de Negocio (4 semanas)**
   * Fundamentos de procesos de negocio y notación **BPMN (Business Process Model and Notation)**.
   * Elementos BPMN: eventos (inicio, intermedio, fin), actividades/tareas, compuertas (exclusivas, paralelas, inclusivas), flujos de secuencia y de mensaje, carriles (*lanes*) y piscinas (*pools*).
   * Modelado de procesos "As-Is" (estado actual) y "To-Be" (estado futuro optimizado).
3. **Unidad 3: Definición del Proyecto (1 semana)**
   * Identificación de problemas y oportunidades de mejora tecnológica.
   * Estudio de viabilidad técnica, operativa y económica.
   * Definición de objetivos, alcance inicial y Acta de Constitución del Proyecto (*Project Charter*).
4. **Unidad 4: Ingeniería de Requisitos (4.5 semanas)**
   * Elicitación de requisitos: técnicas (entrevistas, observación, encuestas, talleres).
   * Análisis, clasificación, negociación y gestión de requisitos.
   * **Unidad 4.1: Aproximaciones Ágiles (2 semanas)**
     * Historias de Usuario (User Stories), criterios INVEST, épicas y temas.
     * Criterios de aceptación bajo formato BDD / Gherkin (*Given-When-Then*).
     * Backlog del producto y priorización (MoSCoW, valor de negocio).
   * **Unidad 4.2: Aproximaciones Tradicionales (2.5 semanas)**
     * Documento formal de Especificación de Requisitos de Software según el estándar **IEEE 830**.
     * Requisitos funcionales (RF) y no funcionales (RNF: rendimiento, seguridad, usabilidad, confiabilidad).
     * Modelado de **Casos de Uso en UML**: diagramas de casos de uso, relaciones `<<include>>`, `<<extend>>` y generalización.
     * Especificación textual detallada de casos de uso (flujo principal, flujos alternos y de excepción).
5. **Unidad 5: Introducción al Diseño del Sistema (2.5 semanas)**
   * Modelado dinámico con **Diagramas de Actividades en UML**.
   * Modelado estático preliminar: **Diagrama de Clases del Dominio (Modelo Conceptual)** con atributos y multiplicidades.
   * Trazabilidad de requisitos hacia artefactos de análisis y diseño.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Expediente Profesional de Ingeniería de Requisitos (SRS IEEE 830 + BPMN + Prototipo UI/UX)
* **Problema a Resolver:** En la industria del software, más del 50% de los proyectos fracasan no por fallas de código, sino por requerimientos ambiguos, mal elicitados o sin trazabilidad. Un expediente de requisitos formal para un cliente real o simulado demuestra profesionalismo de nivel Senior/Analista Funcional.
* **Correspondencia con el PDF:**
  * Unidades 2, 3 y 4.2: Modelado BPMN de procesos del negocio, estudio de viabilidad, SRS IEEE 830 completo con casos de uso UML especificados y prototipado UI/UX.
* **Entregables Concretos del Proyecto:**
  1. **Diagrama BPMN:** Modelado completo en Camunda o Bizagi del proceso de negocio (ej. "Sistema de Telemedicina y Despacho de Medicamentos" o "Gestión de Admisiones Universitarias"), mostrando los carriles del paciente, médico, farmacéutico y sistema.
  2. **Documento SRS IEEE 830 estructurado:**
     * Introducción, propósito, alcance y perspectiva del producto.
     * Catálogo exhaustivo de Requisitos Funcionales (RF01 a RF25) y Requisitos No Funcionales (RNF01 a RNF10 bajo norma ISO/IEC 25010).
     * Matriz de trazabilidad cruzada (Objetivo de negocio $\leftrightarrow$ RF $\leftrightarrow$ Caso de Uso $\leftrightarrow$ Pantalla).
  3. **Modelado UML:** Diagrama general de Casos de Uso con relaciones `<<include>>` y `<<extend>>`, y plantillas descriptivas detalladas para los casos de uso críticos.
  4. **Prototipo Interactivo en Figma:** Wireframes de media fidelidad vinculados directamente con los identificadores de cada requisito.
* **Herramientas:** Camunda Modeler, Visual Paradigm / Enterprise Architect / PlantUML, Figma, Markdown / Word.
* **Valor en Entrevistas Técnicas:** Esencial para roles de Product Owner, Business Analyst (BA) e Ingeniero de Software que deba justificar decisiones ante stakeholders.

---

### Proyecto 2: Backlog Ágil BDD y Modelo Conceptual del Dominio de una Fintech
* **Problema a Resolver:** Los equipos ágiles modernos articulan requerimientos mediante Historias de Usuario con especificaciones ejecutables (BDD) que los desarrolladores y testers pueden automatizar directamente.
* **Correspondencia con el PDF:**
  * Unidades 4.1 y 5: Historias de usuario ágiles con INVEST, BDD (Gherkin), diagramas de actividades y modelo de clases del dominio.
* **Entregables Concretos del Proyecto:**
  1. **Backlog en Jira / GitHub Projects:** 15+ Historias de Usuario organizadas en épicas (ej. Autenticación Biométrica, Transferencias Interbancarias, Gestión de Tarjetas Virtuales).
  2. **Criterios de Aceptación Gherkin:** Escritos en lenguaje formal (*Given, When, Then*) listos para pruebas con Cucumber.
  3. **Diagrama de Actividades UML:** Flujo detallado de decisiones y caminos concurrentes para el procesamiento de transacciones financieras.
  4. **Modelo Conceptual de Clases (Dominio):** Diagrama UML que define entidades del negocio (`Cuenta`, `Cliente`, `Transacción`, `Balance`), cardinalidades estrictas y reglas de negocio, sin incluir detalles tecnológicos de bases de datos.
* **Herramientas:** Jira / GitHub Projects, PlantUML / Mermaid, Gherkin syntax.
* **Valor en Entrevistas Técnicas:** Demuestra dominio de metodologías ágiles reales, modelado de dominio limpio y criterios de aceptación sin ambigüedades.
