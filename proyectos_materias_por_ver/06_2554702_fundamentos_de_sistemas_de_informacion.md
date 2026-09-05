# 2554702 – Fundamentos de Sistemas de Información

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Fundamentos de Sistemas de Información
* **Código de Curso:** 2554702
* **Nivel:** 7
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Profesional / Sistemas de Información y Gestión
* **Créditos Académicos:** 3
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial
* **Libros Guía Oficiales:** *Management Information Systems* (Laudon & Laudon), *COBIT 2019 Framework: Introduction and Methodology* (ISACA), *ISO/IEC 27001 Information Security Management*.

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Generalidades de los Sistemas de Información (SI)**
   * Definición, componentes estructurales (hardware, software, datos, personas, procesos).
   * Tipologías y niveles organizacionales de los SI:
     * Nivel Operativo: Sistemas de Procesamiento de Transacciones (**TPS**).
     * Nivel Táctico: Sistemas de Información Gerencial (**MIS**) y Sistemas de Soporte a Decisiones (**DSS**).
     * Nivel Estratégico: Sistemas de Información Ejecutiva (**EIS**).
   * Sistemas Empresariales Integrados: **ERP** (Enterprise Resource Planning), **CRM** (Customer Relationship Management) y **SCM** (Supply Chain Management).
   * Los SI en la estrategia competitiva: Cadena de Valor de Porter y fuerzas competitivas.
2. **Unidad 2: Transformación Digital**
   * Concepto y dimensiones de la Transformación Digital en las organizaciones.
   * Modelos de madurez digital y rediseño de procesos.
   * Tecnologías habilitadoras: Computación en la Nube (IaaS, PaaS, SaaS), Automatización Robótica de Procesos (**RPA**), Inteligencia Artificial y Big Data aplicados al negocio.
   * Gestión del cambio organizacional frente a la digitalización.
3. **Unidad 3: Planeación Estratégica de Tecnologías de Información (PETI)**
   * Metodología PETI: alineación de la estrategia de negocio con la estrategia de TI.
   * Diagnóstico de la situación actual (As-Is) y formulación de la arquitectura objetivo (To-Be).
   * Portafolio de proyectos de TI y priorización por impacto/retorno de inversión (ROI).
   * Marcos de Gobierno y Gestión de TI: **COBIT 2019** (objetivos de gobierno y gestión) e **ITIL 4** (Sistema de Valor del Servicio).
4. **Unidad 4: Gestión de Riesgos de los Sistemas de Información**
   * Identificación, clasificación y valoración de activos de información.
   * Análisis y evaluación de amenazas y vulnerabilidades (metodologías MAGERIT / ISO 31000).
   * Norma internacional **ISO/IEC 27001** (Sistemas de Gestión de Seguridad de la Información - SGSI): Anexo A (controles de seguridad).
   * Planes de Tratamiento de Riesgo (mitigar, transferir, aceptar, evitar).
   * Continuidad del Negocio: Plan de Continuidad del Negocio (**BCP**) y Plan de Recuperación ante Desastres (**DRP**), cálculo de RTO (Recovery Time Objective) y RPO (Recovery Point Objective).

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Plan Estratégico de Tecnologías de Información (PETI) y Matriz de Gobierno COBIT para una PyME
* **Problema a Resolver:** La mayoría de empresas medianas invierten en tecnología de forma desarticulada sin alineación con las metas del negocio, acumulando silos de información y software redundante.
* **Correspondencia con el PDF:**
  * Unidades 1, 2 y 3: Análisis de sistemas TPS/ERP existentes, diagnóstico de madurez digital, plan PETI a 3 años y cascada de metas COBIT 2019.
* **Entregables Concretos:**
  1. **Diagnóstico Estratégico Integral:** Análisis de la cadena de valor de la empresa y evaluación de madurez digital actual.
  2. **Cascada de Metas COBIT 2019:** Mapeo de los Objetivos de Negocio $\to$ Objetivos de Alineación de TI $\to$ Objetivos de Gobierno y Gestión prioritarios (ej. APO12 Gestión del Riesgo, BAI03 Gestión de Soluciones).
  3. **Mapa de Ruta (Roadmap) PETI To-Be:** Portafolio de 5 proyectos de TI estratégicos cronometrados a 36 meses con presupuesto estimado, KPIs de seguimiento y cálculo preliminar de ROI/TCO.
  4. **Propuesta de Arquitectura de Aplicaciones:** Integración del ERP central con canales de comercio electrónico y CRM.
* **Herramientas:** Plantillas COBIT 2019, Diagramas de flujo de procesos, Markdown/Word ejecutivo.
* **Valor en Entrevistas Técnicas:** Demuestra visión estratégica corporativa para roles de Consultor de TI, Business Analyst y Oficial de Transformación Digital.

---

### Proyecto 2: Sistema de Gestión de Seguridad de la Información (SGSI ISO 27001) y Plan BCP/DRP
* **Problema a Resolver:** Diseñar formalmente la gestión de riesgos de ciberseguridad y el plan de recuperación ante desastres para una empresa de servicios financieros o de salud que maneja datos sensibles.
* **Correspondencia con el PDF:**
  * Unidad 4: Inventario y valoración de activos, matriz de riesgos cualitativa/cuantitativa, controles del Anexo A de ISO 27001 y formulación de BCP/DRP con métricas RTO/RPO.
* **Entregables Concretos:**
  1. **Matriz de Gestión de Riesgos:** Inventario de activos de información (bases de datos, servidores cloud, endpoints, personal), asignación de probabilidad e impacto (matriz $5 \times 5$) y cálculo de riesgo inherente vs residual tras controles.
  2. **Declaración de Aplicabilidad (SoA):** Selección y justificación de 20 controles clave de la norma ISO/IEC 27001 (control de accesos, criptografía, seguridad en operaciones, copias de seguridad).
  3. **Plan DRP Formal:** Protocolo técnico paso a paso ante contingencias críticas (ej. ataque de Ransomware o caída del Data Center principal), definiendo un RTO $\le 2$ horas y un RPO $\le 15$ minutos mediante respaldos automatizados.
* **Herramientas:** Hojas de cálculo de riesgo, diagramas de topología de respaldo, documentación formal.
* **Valor en Entrevistas Técnicas:** Clave para aspirantes a Oficial de Seguridad de la Información (CISO Junior), Consultor de Seguridad y Auditor de TI.
