# 2554700 – Proyecto Integrador I

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Proyecto Integrador I
* **Código de Curso:** 2554700
* **Nivel:** 6
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Proyectos / Integración Profesional
* **Créditos Académicos:** 2
* **Pre-requisitos:** Cumplimiento de créditos de ciclo básico
* **Modalidad:** Virtual / Presencial
* **Metodología Oficial:** Aprendizaje Basado en Proyectos (ABP), seguimiento incremental por hitos y evaluación formal con rúbricas de ingeniería.

---

## 2. Ejes Temáticos y Fases del Proyecto (según PDF)
1. **Fase 1: Constitución y Formalización de la Propuesta (Semanas 1 a 2)**
   * Acta de inicio y compromiso del equipo de trabajo.
   * Identificación del problema real de ingeniería (contexto social, institucional o empresarial).
   * Delimitación del alcance, objetivos generales y específicos medibles.
   * Formalización del documento de propuesta técnico-económica y viabilidad.
2. **Fase 2: Diagnóstico, Elicitación y Requisitos (Semanas 3 a 5 - Seguimiento #1)**
   * Levantamiento exhaustivo de requerimientos funcionales y no funcionales.
   * Definición del marco ágil de trabajo (Scrum/Kanban), tablero de control de tareas y definición de terminado (*DoD*).
   * Prototipado inicial de interfaces de usuario de alta fidelidad.
3. **Fase 3: Diseño de Arquitectura y Primer Incremento Funcional (Semanas 6 a 9 - Seguimiento #2)**
   * Diseño arquitectónico formal del sistema (diagramas C4, modelo de base de datos relacional/NoSQL).
   * Configuración de la infraestructura de desarrollo: repositorio GitHub con ramas protegidas, pipeline CI preliminar y entornos en Docker.
   * Entrega del **MVP (Producto Mínimo Viable)** con la funcionalidad nuclear operativa.
4. **Fase 4: Desarrollo Incremental y Aseguramiento de Calidad (Semanas 10 a 13 - Seguimiento #3)**
   * Construcción de los módulos secundarios y de integración externa.
   * Pruebas automatizadas (unitarias e integración) y corrección de deuda técnica.
5. **Fase 5: Despliegue, Validación y Cierre (Semanas 14 a 16 - Seguimiento #4 e Informe Final)**
   * Despliegue del producto en un entorno de producción accesible (Cloud / Servidor real).
   * Validación con usuarios finales o pruebas de aceptación.
   * Redacción del informe final de ingeniería y sustentación pública ante docentes evaluadores.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Sistema Integral de Gestión Comunitaria y Respaldo de Emergencias Locales (Full-Stack Integrado)
* **Problema a Resolver:** Las juntas de acción comunal o brigadas de emergencia en zonas vulnerables carecen de software accesible para censar habitantes, registrar personas en condición de vulnerabilidad y coordinar alertas tempranas georreferenciadas sin depender de servicios pagos.
* **Correspondencia con el PDF:**
  * Todas las fases del curso: Formulación formal, requerimientos con usuarios reales, arquitectura hexagonal desacoplada, desarrollo ágil en sprints y despliegue público en la nube.
* **Requerimientos Funcionales y Técnicos:**
  1. **Frontend:** Aplicación Web Progresiva (PWA) responsiva para funcionar en móviles con soporte offline básico.
  2. **Backend:** API RESTful robusta bajo arquitectura limpia (Node.js/Express, Spring Boot o FastAPI) con autenticación JWT basada en roles (`Administrador`, `Brigadista`, `Ciudadano`).
  3. **Base de Datos Espacial:** PostgreSQL con extensión **PostGIS** para registrar ubicaciones geográficas de alertas y albergues.
  4. **Mapa Interactivo:** Visualización en tiempo real de incidentes con Leaflet/OpenStreetMap.
  5. **Notificaciones en Tiempo Real:** WebSockets para alertar a brigadistas cuando se reporta una emergencia cercana.
  6. **Infraestructura:** Despliegue completo en la nube (Render, Railway, AWS o GCP) orquestado con Docker y con pipeline de GitHub Actions que ejecute pruebas automáticas antes de desplegar.
* **Entregables:** Repositorio GitHub con tags de versiones (`v0.1-mvp`, `v1.0-final`), enlace a demo funcional en vivo y documento final PDF estructurado.
* **Valor en Entrevistas Técnicas:** Demuestra capacidad probada de llevar un producto de software desde una idea en papel hasta un despliegue productivo real con impacto social.

---

### Proyecto 2: Plataforma Académica de Préstamos y Trazabilidad de Dispositivos de Laboratorio
* **Problema a Resolver:** En universidades, el control de inventario de osciloscopios, sensores y tarjetas embebidas se gestiona en hojas de cálculo desactualizadas, generando pérdidas de equipos y conflictos de horarios entre estudiantes y profesores.
* **Requerimientos Funcionales:**
  1. Catálogo con escaneo de códigos de barra / QR para agilizar el check-in y check-out de equipos.
  2. Sistema de reservas con control de solapamiento horario y penalizaciones automáticas por entregas tardías.
  3. Módulo de auditoría que registra cada cambio de estado del equipo en base de datos.
  4. Dashboard analítico con tasas de utilización por laboratorio y alertas de mantenimiento preventivo.
* **Stack Tecnológico:** React / Vue.js, Python (FastAPI), PostgreSQL, Docker.
