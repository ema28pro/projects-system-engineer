# 2554506 – Análisis y Diseño de Sistemas II

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Análisis y Diseño de Sistemas II
* **Código de Curso:** 2554506
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Profesional / Ingeniería de Software
* **Créditos Académicos:** 3
* **Pre-requisitos:** 2554403 – Análisis y Diseño de Sistemas I | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial
* **Libros Guía:** *Diseño Ágil con TDD*, *Design Patterns: Elements of Reusable Object-Oriented Software* (GoF), *Applying UML and Patterns* (Craig Larman).

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Diagnóstico, Scrum y Proyecto (2 semanas)**
   * Marco de trabajo ágil SCRUM: roles (Product Owner, Scrum Master, Developers), eventos (Sprint Planning, Daily, Review, Retrospective) y artefactos (Product Backlog, Sprint Backlog, Incremento).
   * Definición de Terminado (*Definition of Done - DoD*) y Definición de Listo (*DoR*).
   * Estimación con *Planning Poker*, Story Points y gráficos de avance (*Burndown charts*).
2. **Unidad 2: Modelo de Análisis (2 semanas)**
   * Diagramas de Robustez (Análisis BCE: *Boundary, Control, Entity*).
   * Realización preliminar de casos de uso mediante diagramas de interacción y secuencia preliminares.
   * Transición fluida del "¿qué hace el sistema?" al "¿cómo se estructura internamente?".
3. **Unidad 3: Introducción al Diseño Arquitectural (2 semanas)**
   * Concepto de Arquitectura de Software y drivers arquitectónicos (Atributos de Calidad / FURPS+).
   * Estilos y patrones arquitectónicos: Arquitectura por Capas (*Layered*), MVC, **Arquitectura Hexagonal (Puertos y Adaptadores)**, Arquitectura Limpia (*Clean Architecture*) y Microservicios.
   * Documentación arquitectónica bajo el **Modelo 4+1 Vistas de Kruchten** y el modelo moderno **C4 (Contexto, Contenedores, Componentes, Código)**.
4. **Unidad 4: Principios Básicos de Diseño (3 semanas)**
   * Repaso y profundización de los **Principios SOLID**.
   * **Patrones GRASP (General Responsibility Assignment Software Patterns)**:
     * Creador, Experto en Información, Bajo Acoplamiento, Alta Cohesión.
     * Controlador, Polimorfismo, Indirección, Fabricación Pura (*Pure Fabrication*) y Variaciones Protegidas.
5. **Unidad 5: Patrones de Diseño y Antipatrones (5 semanas)**
   * **Patrones Creacionales GoF:** Singleton, Factory Method, Abstract Factory, Builder, Prototype.
   * **Patrones Estructurales GoF:** Adapter, Bridge, Composite, Decorator, Facade, Proxy.
   * **Patrones de Comportamiento GoF:** Strategy, Observer, Command, State, Template Method, Chain of Responsibility.
   * Estudio de **Antipatrones de Diseño y Arquitectura**: *God Object (Blob)*, *Spaghetti Code*, *Lava Flow*, *Golden Hammer*, *Poltergeists*.
6. **Unidad 6: Calidad en el Diseño de Software (2 semanas)**
   * Métricas de diseño: Acoplamiento Aferente ($Ca$) y Eferente ($Ce$), Inestabilidad ($I$), Complejidad Ciclomática de McCabe.
   * Refactorización y olores de código (*Code Smells*).
   * **Diseño guiado por pruebas (TDD - Test-Driven Development)**: Ciclo *Red-Green-Refactor*.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Sistema Empresarial con Arquitectura Hexagonal y Catálogo de Patrones GoF
* **Problema a Resolver:** En sistemas productivos a escala, mezclar lógica de negocio con frameworks web o bases de datos produce software rígido y frágil. La Arquitectura Hexagonal aísla el núcleo de dominio haciéndolo 100% independiente de tecnologías externas.
* **Correspondencia con el PDF:**
  * Unidades 2, 3, 4 y 5: Robustez BCE, Arquitectura Hexagonal (puertos de entrada/salida y adaptadores), principios GRASP y patrones GoF (Strategy, Factory, Observer, Adapter, Decorator).
* **Requerimientos Funcionales y Técnicos:**
  1. Caso de negocio: Sistema de Pasarela de Pagos y Facturación Electrónica Multi-proveedor.
  2. **Arquitectura Hexagonal:**
     * `Domain Core`: Entidades puras y reglas de negocio sin ninguna anotación de frameworks (independiente de Spring o bases de datos).
     * `Ports`: Interfaces Java/TypeScript que definen operaciones entrantes (`PagoUseCase`) y salientes (`GuardarPagoPort`, `NotificarUsuarioPort`).
     * `Adapters`: Implementaciones concretas: controladores REST, persistencia en PostgreSQL con JPA/Hibernate, y adaptadores externos para PayPal y Stripe (aplicando el patrón **Adapter**).
  3. **Patrones GoF implementados:**
     * **Strategy:** Selección dinámica del algoritmo de cálculo de impuestos y recargos según el país.
     * **Factory Method:** Instanciación desacoplada de la pasarela de pagos correspondiente.
     * **Observer:** Publicación de eventos de dominio (`PagoAprobadoEvent`) para desencadenar el envío de correo y la actualización de stock en tiempo real.
     * **Decorator:** Enriquecimiento de facturas con seguros adicionales o cargos de envío sin modificar la clase base.
  4. Cobertura de pruebas unitarias al dominio usando mocks (Mockito) para los puertos salientes.
* **Stack Tecnológico:** Java (Spring Boot) o TypeScript (NestJS) o C# (.NET Core), PostgreSQL, Docker.
* **Estructura Sugerida:**
  ```text
  hexagonal-payment-engine/
  ├── domain/
  │   ├── model/           # Pago, Factura, Moneda
  │   └── service/         # ProcesarPagoService (Pure Logic)
  ├── application/
  │   └── ports/
  │       ├── in/          # ProcesarPagoUseCase
  │       └── out/         # TransaccionRepositoryPort, NotificadorPort
  └── infrastructure/
      ├── adapters/
      │   ├── in/web/      # PagoRestController
      │   └── out/
      │       ├── persistence/ # JpaPagoRepositoryAdapter
      │       └── external/    # StripeGatewayAdapter, PaypalAdapter
      └── config/          # Bean Injections
  ```
* **Valor en Entrevistas Técnicas:** Es el estándar de oro que buscan las empresas líderes de software para contratar ingenieros Backend / Full-Stack.

---

### Proyecto 2: Documento Formal de Arquitectura de Software (SAD) con C4 Model y Matriz de Atributos de Calidad
* **Problema a Resolver:** Documentar de manera inequívoca la arquitectura de un sistema complejo para equipos de desarrollo, líderes de infraestructura y stakeholders de negocio.
* **Correspondencia con el PDF:**
  * Unidades 1 y 3: Modelo 4+1 vistas, diagramación C4 model, definición de escenarios de atributos de calidad (disponibilidad, latencia, seguridad) y justificación de decisiones arquitecturales (ADR - *Architectural Decision Records*).
* **Entregables Concretos del Proyecto:**
  1. **Diagramas C4 Model completos:**
     * Nivel 1 (Contexto del Sistema): actores, límites del sistema y dependencias externas.
     * Nivel 2 (Contenedores): aplicaciones web, móviles, microservicios, bases de datos y colas de mensajería con sus protocolos de comunicación (HTTPS, gRPC, AMQP).
     * Nivel 3 (Componentes): descomposición interna de los contenedores críticos.
  2. **Escenarios de Atributos de Calidad:** 5 escenarios formalmente especificados (Estímulo, Fuente, Entorno, Artefacto, Respuesta, Medida de Respuesta).
  3. **3 Registros de Decisiones de Arquitectura (ADRs):** Justificación técnica documentada de decisiones (ej. "¿Por qué elegir PostgreSQL sobre MongoDB?", "¿Por qué usar mensajería asíncrona con RabbitMQ?").
* **Herramientas:** Structurizr / PlantUML / C4-PlantUML, Markdown.
* **Valor en Entrevistas Técnicas:** Demuestra madurez y visión holística de Arquitectura de Software para aspirar a roles de Tech Lead o Software Architect.
