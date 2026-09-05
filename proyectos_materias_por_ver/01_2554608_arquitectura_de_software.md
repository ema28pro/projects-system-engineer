# 2554608 – Arquitectura de Software

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Arquitectura de Software
* **Código de Curso:** 2554608
* **Nivel:** 6
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Profesional / Ingeniería de Software
* **Créditos Académicos:** 3
* **Pre-requisitos:** 2554506 – Análisis y Diseño de Sistemas II
* **Modalidad:** Virtual / Presencial
* **Libros Guía Oficiales:** *Software Architecture in Practice* (Bass, Clements, Kazman - SEI), *Building Evolutionary Architectures* (Ford, Parsons, Kua).

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Fundamentos en Arquitecturas de Software (3 semanas)**
   * Definición de arquitectura de software; diferencia entre diseño y arquitectura.
   * Drivers arquitectónicos: Requerimientos Funcionales, Restricciones del Negocio y **Atributos de Calidad (Quality Attributes / FURPS+)**.
   * Especificación formal de Atributos de Calidad: Escenarios de Calidad (Fuente, Estímulo, Entorno, Artefacto, Respuesta y Medida de Respuesta).
   * **Tácticas Arquitectónicas** para disponibilidad, modificabilidad, desempeño, seguridad y testeabilidad.
2. **Unidad 2: Patrones Arquitectónicos (4 semanas)**
   * Patrones monolíticos y distribuidos:
     * Arquitectura en Capas (*Layered Architecture*).
     * Arquitectura Basada en Microservicios (*Microservices*).
     * Arquitectura Dirigida por Eventos (*Event-Driven Architecture - EDA*): Broker vs Mediator.
     * Arquitectura Hexagonal / Puertos y Adaptadores (*Ports & Adapters*).
     * Arquitectura de Tuberías y Filtros (*Pipes and Filters*).
     * Microkernel / Plugin Architecture.
3. **Unidad 3: Desarrollo de Software Basado en Arquitectura (3 semanas)**
   * Método de Diseño Guiado por Atributos (**ADD - Attribute-Driven Design**).
   * Documentación arquitectónica: **Modelo 4+1 Vistas de Kruchten** y el estándar moderno **C4 Model** (Context, Containers, Components, Code).
   * Evaluación de arquitecturas: Método **ATAM (Architecture Tradeoff Analysis Method)**.
   * Registros de Decisiones de Arquitectura (**ADR - Architectural Decision Records**).
4. **Unidad 4: Los Servicios Web en la Arquitectura (3 semanas)**
   * Estilos de comunicación entre servicios: síncrono (REST, gRPC, GraphQL) vs asíncrono (colas de mensajería AMQP, Kafka).
   * Patrones de integración: API Gateway, Backend for Frontend (BFF), Service Discovery y Circuit Breaker.
5. **Unidad 5: Aspectos de Seguridad en Arquitecturas de Software (3 semanas)**
   * Arquitectura Zero Trust, seguridad perimetral vs defensa en profundidad.
   * Autenticación y Autorización descentralizada: OAuth 2.0, OpenID Connect (OIDC) y JSON Web Tokens (JWT).
   * Protección de APIs: Rate Limiting, CORS, mTLS y secretos seguros.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Sistema de E-Commerce Distribuido Basado en Microservicios y Event-Driven Architecture (EDA)
* **Problema a Resolver:** Los sistemas monolíticos de comercio electrónico colapsan durante eventos de alta concurrencia (como Black Friday). Se requiere una arquitectura de microservicios resiliente, desacoplada por eventos y tolerante a fallos que procese órdenes de compra, reservas de stock y pasarelas de pago de forma asíncrona.
* **Correspondencia con el PDF:**
  * Unidades 2, 4 y 5: Patrón de microservicios, Event-Driven con Kafka/RabbitMQ, patrón Saga orquestado/coreografiado, API Gateway y Circuit Breaker.
* **Requerimientos Funcionales y Técnicos:**
  1. **Servicios independientes con Base de Datos propia (*Database-per-Service*):**
     * `Order-Service`: Gestión de órdenes (PostgreSQL).
     * `Inventory-Service`: Control de stock con transacciones optimistas (Redis/PostgreSQL).
     * `Payment-Service`: Procesamiento y simulación de transacciones con pasarelas.
     * `Notification-Service`: Consumo de eventos y envío de correos asíncronos.
  2. **Broker de Eventos:** Apache Kafka o RabbitMQ para emitir y consumir eventos (`OrderCreated`, `StockReserved`, `PaymentFailed`).
  3. **Tolerancia a fallos:** Implementar el patrón **Circuit Breaker** (Resilience4j) para evitar caídas en cascada si la pasarela de pagos se degrada.
  4. **API Gateway:** Enrutamiento centralizado, autenticación JWT unificada y limitación de tasa (*Rate Limiting*).
  5. **Trazabilidad Distribuida:** Correlación de trazas de extremo a extremo mediante OpenTelemetry / Zipkin.
* **Stack Tecnológico:** Java (Spring Boot / Spring Cloud) o TypeScript (NestJS), Apache Kafka, PostgreSQL, Redis, Docker Compose.
* **Valor en Entrevistas Técnicas:** Demuestra dominio de sistemas distribuidos a gran escala, consistencia eventual y patrones de integración empresariales.

---

### Proyecto 2: Expediente Completo de Evaluación y Documentación Arquitectónica (ADD + ATAM + C4 Model + ADRs)
* **Problema a Resolver:** Las organizaciones pierden millones al elegir arquitecturas sin justificación técnica formal o al carecer de documentación clara que guíe a decenas de desarrolladores.
* **Correspondencia con el PDF:**
  * Unidades 1, 3 y 5: Escenarios de Atributos de Calidad, diseño ADD, evaluación ATAM para identificar puntos de sensibilidad y *trade-offs*, y diagramación C4 completa.
* **Entregables Concretos:**
  1. **6 Escenarios de Atributos de Calidad Formales:** Latencia en p99 < 200 ms, Disponibilidad 99.95%, Resiliencia ante caídas de nodos, etc.
  2. **Diagramas C4 Model Interactivos (en Structurizr o PlantUML):** Contexto, Contenedores y Componentes.
  3. **Matriz de Tácticas Arquitectónicas:** Relación directa entre táctica elegida (ej. *Heartbeat*, *Active Redundancy*, *Defer Binding*) y el escenario que mitiga.
  4. **Evaluación ATAM Documentada:** Identificación de riesgos, *non-risks*, puntos de sensibilidad y compromisos (*trade-offs*, ej. rendimiento vs consistencia).
  5. **5 ADRs (Architectural Decision Records):** En formato MADR documentando decisiones críticas (ej. Adopción de GraphQL vs REST, Event Sourcing vs CRUD).
* **Herramientas:** Structurizr / PlantUML, Markdown, Draw.io.
* **Valor en Entrevistas Técnicas:** Proyecto insignia para aspirantes a Arquitecto de Software Junior / Tech Lead.

---

### Proyecto 3: API Gateway & Service Mesh Ligero con Políticas de Seguridad Zero-Trust
* **Problema a Resolver:** Proteger una malla de microservicios internos garantizando que ninguna llamada sea anónima y aplicando políticas de autorización basadas en roles y alcances (*scopes*).
* **Correspondencia con el PDF:**
  * Unidades 4 y 5: Servicios web, API Gateways, OAuth 2.0 / JWT y arquitectura de seguridad Zero Trust.
* **Requerimientos Funcionales:**
  1. Servidor de Autorización OAuth 2.0 / OIDC (Keycloak o implementación con Spring Security).
  2. Gateway que valida tokens JWT criptográficamente sin consultar la base de datos en cada petición.
  3. Middleware de Rate Limiting por IP/Usuario implementado con algoritmo *Token Bucket* en Redis.
  4. Encriptación mTLS entre microservicios internos.
* **Stack Tecnológico:** Go o Node.js / Spring Cloud Gateway, Keycloak, Redis, Docker.
