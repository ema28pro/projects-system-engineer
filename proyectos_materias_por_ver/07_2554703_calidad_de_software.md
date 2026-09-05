# 2554703 – Calidad de Software

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Calidad de Software
* **Código de Curso:** 2554703
* **Nivel:** 7
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Profesional / Ingeniería de Software
* **Créditos Académicos:** 3
* **Pre-requisitos:** 2554506 – Análisis y Diseño de Sistemas II
* **Modalidad:** Virtual / Presencial
* **Libros Guía Oficiales:** *Foundations of Software Testing* (ISTQB / Rex Black), *Software Quality Engineering* (Jeff Tian), *Continuous Delivery* (Humble & Farley).

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Fundamentos de Calidad de Software (3 semanas)**
   * Definiciones formales de calidad; evolución histórica (inspección $\to$ control estadístico $\to$ aseguramiento $\to$ gestión total de calidad).
   * El Costo de la Calidad (**CoQ - Cost of Quality**): Costos de conformidad (prevención y evaluación) vs Costos de no conformidad (fallas internas y fallas externas).
   * Modelos de calidad del producto de software: Estándar **ISO/IEC 25010 (SQuaRE)** y sus 8 características de calidad (Adecuación funcional, Eficiencia de desempeño, Compatibilidad, Usabilidad, Confiabilidad, Seguridad, Mantenibilidad y Portabilidad).
2. **Unidad 2: Referentes para la Adopción de Prácticas de Calidad (3 semanas)**
   * Modelos de madurez y mejora de procesos: **CMMI-DEV** (niveles de madurez 1 a 5).
   * Estándares de ciclo de vida del software: **ISO/IEC 12207** e ISO 9001 aplicado a software.
   * Metodologías ágiles y su enfoque hacia la calidad intrínseca (Scrum, Kanban, XP).
3. **Unidad 3: Implementación del Proceso de Aseguramiento de Calidad (SQA) (4 semanas)**
   * Plan de Aseguramiento de Calidad de Software (**Plan SQA**): roles, actividades y auditorías de proceso.
   * Técnicas de revisión estática: Revisiones formales (*Formal Inspections* de Fagan), revisiones técnicas estructuradas y *Code Reviews* colaborativos.
   * Análisis estático de código: Detección de vulnerabilidades, olores de código (*Code Smells*), deuda técnica y complejidad ciclomática con **SonarQube / SonarCloud**.
   * Definición de puertas de calidad (**Quality Gates**).
4. **Unidad 4: Fundamentación en Pruebas de Software (3 semanas)**
   * Principios universales de las pruebas (el glosario y estándar **ISTQB**).
   * Niveles de prueba: Pruebas Unitarias, Pruebas de Integración, Pruebas de Sistema y Pruebas de Aceptación (UAT).
   * Tipos de prueba: Funcionales, No funcionales (rendimiento, carga, estrés, seguridad) y Pruebas de Regresión.
   * Técnicas de diseño de pruebas de **Caja Negra**:
     * Partición de Equivalencia (EP).
     * Análisis de Valores Límite (BVA).
     * Tablas de Decisión y Transición de Estados.
   * Técnicas de diseño de pruebas de **Caja Blanca**: Cobertura de sentencias, cobertura de ramas/decisiones y cobertura de caminos básicos (complejidad ciclomática de McCabe).
5. **Unidad 5: Prácticas de Automatización de Pruebas (3 semanas)**
   * La Pirámide de Automatización de Pruebas (Mike Cohn).
   * Automatización de pruebas de interfaz gráfica (E2E) con **Playwright** o **Cypress**.
   * Automatización de pruebas de APIs REST con **Postman / Newman** o **REST Assured**.
   * Pruebas de carga y estrés de rendimiento con **k6** o **Apache JMeter**.
   * Integración de pruebas continuas en pipelines de **CI/CD** (GitHub Actions).

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Framework de Automatización de Pruebas E2E y API en Pipeline CI/CD con Quality Gates
* **Problema a Resolver:** Las pruebas manuales retrasan los despliegues de software y dejan escapar bugs críticos a producción. Se requiere una suite de pruebas totalmente automatizada que valide tanto las APIs backend como los flujos de usuario en el frontend, bloqueando despliegues si la cobertura o la calidad bajan.
* **Correspondencia con el PDF:**
  * Unidades 3, 4 y 5: Diseño de pruebas de caja negra (EP y BVA), automatización E2E con Playwright/Cypress, pruebas de API REST, análisis estático con SonarCloud y ejecución automática en GitHub Actions.
* **Requerimientos Funcionales y Técnicos:**
  1. Tomar una aplicación real o de muestra (ej. Sistema de Gestión de Tareas o E-Commerce).
  2. **Pruebas de API Automatizadas:** Suite de 20+ tests en Postman/Newman o TypeScript/Supertest validando códigos de estado, esquemas JSON, tiempos de respuesta y autenticación JWT.
  3. **Pruebas E2E de Frontend:** Suite en **Playwright** implementando el patrón de diseño **Page Object Model (POM)** para flujos críticos (Login, Registro, Creación de Ítem, Validación de límites de formulario).
  4. **Análisis Estático con SonarCloud:** Configurar análisis en cada Pull Request verificando 0 vulnerabilidades de seguridad (*Security Hotspots*) y cobertura de pruebas $> 80\%$.
  5. **Pipeline GitHub Actions (`ci.yml`):**
     * Paso 1: Linting y compilación.
     * Paso 2: Análisis SonarCloud (Quality Gate).
     * Paso 3: Ejecución de pruebas de API y E2E headless con generación de reporte HTML de evidencias (screenshots y videos de fallos).
* **Stack Tecnológico:** TypeScript, Playwright, Newman, SonarCloud, GitHub Actions.
* **Valor en Entrevistas Técnicas:** Proyecto insignia para roles de **QA Automation Engineer**, **Software Development Engineer in Test (SDET)** y Desarrollador Full-Stack con cultura de calidad.

---

### Proyecto 2: Laboratorio de Pruebas de Carga y Rendimiento con k6 y Monitoreo Grafana
* **Problema a Resolver:** Determinar el punto de quiebre (*Breaking Point*) de una API REST antes del lanzamiento oficial, identificando cuellos de botella en la base de datos o saturación de memoria.
* **Correspondencia con el PDF:**
  * Unidades 1 y 5: Atributos ISO/IEC 25010 de eficiencia de desempeño, pruebas de carga (*Load Testing*), estrés (*Stress Testing*) y picos (*Spike Testing*) con métricas p95/p99.
* **Requerimientos Funcionales:**
  1. Diseñar scripts de prueba en **k6** simulando 100, 500 y 2,000 usuarios virtuales concurrentes (VUs) con curvas de subida (*ramp-up*) y bajada.
  2. Definir umbrales estrictos de aceptación (*Thresholds*): `http_req_duration p(95) < 300ms` y `http_req_failed < 1%`.
  3. Exportar telemetría en tiempo real hacia InfluxDB y visualizar métricas en un dashboard interactivo de **Grafana**.
  4. Diagnosticar qué endpoint falló primero y proponer la optimización arquitectónica (ej. indexación de base de datos o adición de caché en Redis).
* **Stack Tecnológico:** k6 (JavaScript), InfluxDB, Grafana, Docker.
* **Valor en Entrevistas Técnicas:** Demuestra conocimientos avanzados de ingeniería de rendimiento y resiliencia no funcional.
