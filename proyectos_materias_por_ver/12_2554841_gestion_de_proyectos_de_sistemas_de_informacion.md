# 2554841 – Gestión de Proyectos de Sistemas de Información

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Gestión de Proyectos de Sistemas de Información
* **Código de Curso:** 2554841
* **Nivel:** 8
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Profesional / Gestión de Proyectos
* **Créditos Académicos:** 3
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial
* **Libros Guía Oficiales:** *A Guide to the Project Management Body of Knowledge (PMBOK Guide 7th ed.)* (PMI), *The Phoenix Project* (Gene Kim), *The DevOps Handbook* (Kim, Humble, Debois, Willis).

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Fundamentos para la Gestión de Proyectos de Software y Equipos**
   * Definición de proyecto de software frente a operaciones continuas.
   * El ciclo de vida de los proyectos: enfoques predictivos (en cascada), adaptativos (ágiles) e híbridos.
   * Habilidades interpersonales y liderazgo: resolución de conflictos, conformación y maduración de equipos (Modelo de Tuckman: Forming, Storming, Norming, Performing).
2. **Unidad 2: Planificación de Proyectos de Software**
   * Gestión del Alcance: Estructura de Desglose del Trabajo (**EDT / WBS**) y diccionario de la EDT.
   * Estimación de esfuerzo, tiempo y costos:
     * Modelos algorítmicos paramétricos: **COCOMO II** (Constructive Cost Model) y Puntos de Función.
     * Estimación ágil: *Planning Poker*, Story Points y velocidad del equipo.
   * Gestión del Cronograma: Diagramas de red de actividades (PDM), Diagramas de Gantt y **Método de la Ruta Crítica (CPM / PERT)** con cálculo de holguras.
   * Gestión de Riesgos del Proyecto: Matriz cualitativa y cuantitativa de riesgos (Riesgos técnicos, organizacionales y externos) y planes de contingencia.
3. **Unidad 3: Proceso de Cierre y Entrega de Proyectos**
   * Criterios de aceptación formal y entrega del producto.
   * Transición del proyecto a la operación y gestión del cambio organizacional (ADKAR).
   * Evaluación de desempeño del proyecto y recopilación del documento de **Lecciones Aprendidas**.
4. **Unidad 4: Gestión de Proyectos de Software con Cultura DevOps**
   * El movimiento DevOps: principios de las Tres Vías (Pensamiento Sistémico, Amplificación de Bucles de Retroalimentación y Cultura de Experimentación Continua).
   * Integración Continua (**CI**) y Entrega / Despliegue Continuo (**CD**).
   * Automatización de pipelines: compilación, ejecución de pruebas, análisis de seguridad y empaquetado de artefactos.
5. **Unidad 5: Conceptos Avanzados para la Gestión y Métricas DevOps**
   * Medición de desempeño de entrega de software: **Las 4 Métricas DORA**:
     * *Deployment Frequency* (Frecuencia de Despliegue).
     * *Lead Time for Changes* (Tiempo de Entrega de Cambios).
     * *Change Failure Rate* (Tasa de Falla en Cambios).
     * *Time to Restore Service / MTTR* (Tiempo Medio de Recuperación).
   * Monitoreo continuo y prácticas de *Site Reliability Engineering* (SRE): Acuerdos de Nivel de Servicio (SLA), Objetivos de Nivel de Servicio (SLO) y Presupuestos de Error (*Error Budgets*).
6. **Unidad 6: Aprovisionamiento de Infraestructura en Proyectos de Software**
   * **Infraestructura como Código (IaC)**: principios, idempotencia y herramientas (**Terraform** y **Ansible**).
   * Orquestación de contenedores y gestión de entornos estandarizados (Desarrollo, Staging, Producción).

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Plan de Dirección de Proyecto Completo (PMBOK 7 / Híbrido) con Estimación COCOMO II y CPM
* **Problema a Resolver:** Defender ante un comité de inversiones la viabilidad económica, cronograma, riesgos y estimación de costos de un sistema de información a gran escala antes de escribir la primera línea de código.
* **Correspondencia con el PDF:**
  * Unidades 1, 2 y 3: WBS formal, estimación formal con COCOMO II contrastada contra Story Points, cálculo de Ruta Crítica (CPM), curva S de costos y matriz de riesgos del proyecto.
* **Entregables Concretos:**
  1. **Acta de Constitución del Proyecto (Project Charter):** Justificación del caso de negocio, patrocinadores y restricciones.
  2. **EDT / WBS de 4 niveles:** Con su respectivo Diccionario de la EDT detallando paquetes de trabajo.
  3. **Estudio de Estimación Formal:**
     * Modelo COCOMO II: cálculo de líneas de código fuente (SLOC), multiplicadores de costo (complejidad, experiencia del personal) y cálculo de Person-Months ($PM$).
     * Estimación ágil con Story Points y cálculo de sprints requeridos según la velocidad histórica.
  4. **Diagrama de Red y Ruta Crítica (CPM):** Identificación de holguras libres y totales, determinando la duración mínima del proyecto.
  5. **Matriz de Riesgos con Estrategias de Mitigación:** 10 riesgos evaluados por severidad y plan de contingencia financiero.
* **Herramientas:** Microsoft Project / GanttProject, Hojas de cálculo, Markdown profesional.
* **Valor en Entrevistas Técnicas:** Esencial para aspirantes a **Project Manager (PMP/CAPM)**, Scrum Master, Product Owner y Consultor de TI.

---

### Proyecto 2: Pipeline Completo de CI/CD con Infraestructura como Código (Terraform) y Métricas DORA
* **Problema a Resolver:** Los equipos de ingeniería pierden días desplegando manualmente software en servidores que se desconfiguran con el tiempo (*Configuration Drift*). Se requiere un pipeline automatizado que provisione infraestructura en la nube con código y despliegue la aplicación automáticamente.
* **Correspondencia con el PDF:**
  * Unidades 4, 5 y 6: Cultura DevOps, automatización CI/CD con GitHub Actions, provisionamiento con Terraform (IaC), contenedorización en Docker y cálculo de métricas DORA.
* **Requerimientos Funcionales y Técnicos:**
  1. **Infraestructura como Código (Terraform):** Scripts modulares de Terraform que provisionan una máquina virtual / clúster en la nube (AWS, DigitalOcean o Azure) con sus reglas de firewall y red.
  2. **Pipeline de Integración Continua (GitHub Actions):** En cada `push`, compilar código, ejecutar suite de tests automatizados y empaquetar imagen de Docker en un Container Registry.
  3. **Pipeline de Despliegue Continuo (CD):** Desplegar automáticamente el contenedor en el entorno de producción sin tiempo de inactividad (*Zero-Downtime Deployment* con rolling update).
  4. **Dashboard de Métricas DORA:** Script que consulte la API de GitHub para calcular automáticamente el *Lead Time for Changes* y la frecuencia de despliegues semanales.
* **Stack Tecnológico:** Terraform, GitHub Actions, Docker, AWS / DigitalOcean, Bash.
* **Valor en Entrevistas Técnicas:** El proyecto estrella que buscan los reclutadores para contratar ingenieros **DevOps**, **Cloud Engineers** y **SRE**.
