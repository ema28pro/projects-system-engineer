# 2554902 – Proyecto Integrador II (Área Electiva / Capstone)

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Proyecto Integrador II - Área Electiva
* **Código de Curso:** 2554902
* **Nivel:** 8
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Proyectos / Integración Profesional Terminal
* **Créditos Académicos:** 2
* **Pre-requisitos:** 2554700 – Proyecto Integrador I
* **Modalidad:** Virtual / Presencial
* **Metodología Oficial:** Desarrollo Capstone de ciclo completo, articulación con líneas de profundización/electivas (IA, Ciberseguridad, Redes, Cloud, Software Empresarial), validación empírica en entorno real y sustentación pública ante jurados de la Facultad de Ingeniería.

---

## 2. Ejes Temáticos y Fases del Proyecto Capstone (según PDF)
1. **Fase 1: Formalización de la Propuesta Avanzada (Semanas 1 a 2)**
   * Acta de inicio y definición de roles en el equipo de desarrollo.
   * Delimitación del problema tecnológico complejo y justificación de la articulación con el área electiva seleccionada.
   * Planificación detallada del cronograma de sprints y criterios de aceptación formal.
2. **Fase 2: Arquitectura del Sistema y Primer Prototipo Operativo (Semanas 3 a 5 - Seguimiento #1)**
   * Diseño arquitectónico de alto nivel (Diagramas C4, modelo de datos, infraestructura cloud).
   * Configuración de la plataforma de desarrollo: repositorio GitHub con políticas de ramas protegidas, pipelines CI/CD y despliegue del entorno base.
   * Demostración en vivo del primer prototipo operativo funcional.
3. **Fase 3: Desarrollo Incremental y Módulos Avanzados (Semanas 6 a 9 - Seguimiento #2)**
   * Construcción de los algoritmos especializados del área electiva (modelos predictivos de ML, protocolos criptográficos, microservicios distribuidos o módulos de bajo nivel).
   * Integración de servicios y pruebas de integración continuas.
4. **Fase 4: Validación Empírica y Aseguramiento de Calidad (Semanas 10 a 13 - Seguimiento #3)**
   * Ejecución del plan de pruebas: pruebas unitarias, E2E, pruebas de carga con k6 y escaneos de seguridad.
   * Pruebas de campo o validación formal con usuarios reales / datos del mundo real.
5. **Fase 5: Despliegue en Producción, Informe Final y Sustentación (Semanas 14 a 16 - Seguimiento #4)**
   * Despliegue en producción con monitoreo y observabilidad activados.
   * Redacción del Informe Final de Ingeniería de acuerdo a estándares profesionales y sustentación formal ante jurados docentes.

---

## 3. Proyectos de Portafolio Recomendados (por Línea Electiva)

### Opción A (Línea Inteligencia Artificial / Datos): Plataforma de Detección Temprana de Fraude Transaccional en Tiempo Real
* **Problema a Resolver:** Las instituciones bancarias necesitan clasificar millones de transacciones por segundo detectando patrones fraudulentos con modelos de Machine Learning en milisegundos y con explicabilidad inmediata.
* **Articulación de Materias:** Modelos y Simulación I & II + Arquitectura de Software + Bases de Datos + Calidad de Software.
* **Requerimientos Funcionales y Técnicos:**
  1. Pipeline de streaming con Apache Kafka ingiriendo eventos de transacciones sintéticas.
  2. Servicio de inferencia en tiempo real en FastAPI / Docker ejecutando un ensamble de modelos (XGBoost + Red Neuronal) optimizado en ONNX Runtime.
  3. Módulo de explicabilidad generando valores SHAP para justificar ante el analista bancario por qué se bloqueó una transacción.
  4. Base de datos relacional (PostgreSQL) para auditoría transaccional y Redis para control de velocidad de transferencias por usuario.
  5. Dashboard web interactivo para analistas de riesgo con mapas de calor y alertas sonoras en tiempo real.
* **Stack Tecnológico:** Python, FastAPI, XGBoost, ONNX, Apache Kafka, PostgreSQL, Docker, React.

---

### Opción B (Línea Ciberseguridad / Redes): Sistema de Detección de Intrusos y Monitoreo de Amenazas Perimetrales (SIEM Ligero)
* **Problema a Resolver:** Centralizar y correlacionar logs de red y eventos de servidores para identificar ataques en curso (fuerza bruta, escaneos de puertos, inyecciones SQL) y bloquear IPs atacantes automáticamente en el firewall.
* **Articulación de Materias:** Comunicaciones I & II + Sistemas Operativos + Gestión de Proyectos + Calidad de Software.
* **Requerimientos Funcionales y Técnicos:**
  1. Agentes de monitoreo ligeros desplegados en servidores que capturan logs de autenticación y tráfico de red en crudo.
  2. Motor de correlación de eventos en Go o Python que detecta patrones anómalos en ventanas deslizantes de tiempo.
  3. Automatización de respuesta (*SOAR*): ejecutar llamadas automáticas a `iptables` / Cloudflare API para bloquear temporalmente las IPs maliciosas detectadas.
  4. Panel web seguro con autenticación multifactor (MFA) que muestra el mapa de amenazas y métricas de seguridad perimetral.
* **Stack Tecnológico:** Go, Python, Elasticsearch / OpenSearch, Linux `nftables`, Docker, Vue.js.

---

### Opción C (Línea Ingeniería de Software / Cloud): Plataforma SaaS Multitenant con Arquitectura Hexagonal y CI/CD
* **Problema a Resolver:** Construir una plataforma de software como servicio (SaaS) completa para clínicas o empresas logísticas que aísle los datos de cada cliente (*Multi-tenancy*), escale automáticamente y esté respaldada por una cobertura de pruebas total.
* **Articulación de Materias:** Arquitectura de Software + Bases de Datos + Calidad de Software + DevOps.
* **Requerimientos Funcionales y Técnicos:**
  1. Backend bajo Arquitectura Hexagonal estricta con aislamiento de base de datos por tenant (*Schema-per-Tenant* en PostgreSQL).
  2. Autenticación y gestión de roles con OAuth2 / JWT.
  3. Suite de pruebas automatizadas completa: unitarias (JUnit/Jest), de API (Postman/Supertest) y E2E (Playwright) ejecutadas en GitHub Actions con Quality Gates.
  4. Aprovisionamiento automático en la nube con Terraform y despliegue continuo en clúster Kubernetes.
* **Stack Tecnológico:** Java (Spring Boot) o TypeScript (NestJS), PostgreSQL, Docker, Kubernetes, Terraform, React.
