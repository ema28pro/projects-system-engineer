# 2554609 – Bases de Datos y Laboratorio

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Bases de Datos y Laboratorio
* **Código de Curso:** 2554609
* **Nivel:** 6
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 4
* **Pre-requisitos:** 2554507 – Estructuras de Datos y Laboratorio
* **Modalidad:** Virtual / Presencial
* **Libros Guía Oficiales:** *Fundamentals of Database Systems* (Elmasri & Navathe), *Database System Concepts* (Silberschatz, Korth, Sudarshan).

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Introducción a los Sistemas de Gestión de Bases de Datos**
   * Bases de datos relacionales y el auge del Big Data.
   * Arquitectura de 3 niveles ANSI/SPARC; características y componentes internos de un SGBD.
   * Aspectos legales y regulatorios del manejo de datos (Habeas Data, Ley 1581 de Colombia, GDPR).
2. **Unidad 1: Bases de Datos Relacionales y Álgebra Relacional**
   * El modelo relacional formal: relaciones, tuplas, dominios, claves primarias, foráneas y candidatas.
   * Álgebra relacional: selección ($\sigma$), proyección ($\pi$), unión ($\cup$), diferencia ($-$), producto cartesiano ($\times$), join ($\bowtie$) y división ($\div$).
   * Lenguaje SQL estándar: DDL (`CREATE`, `ALTER`, `DROP`), DML (`SELECT`, `INSERT`, `UPDATE`, `DELETE`), agregaciones, subconsultas correlacionadas, funciones de ventana (*Window Functions*) y CTEs (`WITH`).
3. **Unidad 2: Diseño Conceptual y Normalización**
   * Metodología de diseño de BD: del requerimiento al modelo relacional.
   * Modelo Entidad-Relación (E/R) y E/R Extendido (especialización/generalización, categorías).
   * Mapeo del modelo E/R a tablas relacionales.
   * **Teoría de Dependencias Funcionales (DF):** axiomas de Armstrong, clausura de dependencias y clausura de atributos ($X^+$).
   * **Formas Normales:** 1FN, 2FN, 3FN y Forma Normal de Boyce-Codd (BCNF). Descomposición que preserva dependencias y sin pérdida de información (*Lossless Join*).
4. **Unidad 3: Diseño Físico y Optimización de Consultas**
   * Almacenamiento en disco: bloques, páginas, registros, tablas organizadas por montón (*heap*), secuenciales y clúster.
   * Estructuras de indexación: índices primarios, secundarios, B-Tree, Hash y Bitmap.
   * **Optimización heurística/algebraica de consultas:** transformación de árboles relacionales (empuje de selecciones y proyecciones hacia las hojas).
   * **Optimización basada en costos:** planes de ejecución con `EXPLAIN ANALYZE` (Seq Scan, Index Scan, Bitmap Index Scan, Nested Loop, Hash Join, Merge Join).
   * Transacciones y propiedades ACID: control de concurrencia (bloqueo en dos fases - 2PL, MVCC) y niveles de aislamiento (Read Committed, Repeatable Read, Serializable).
5. **Unidad 4: Grandes Volúmenes de Datos y Bodegas de Datos**
   * Modelado dimensional para Business Intelligence (BI): esquemas en Estrella (*Star Schema*) y Copo de Nieve (*Snowflake*), tablas de hechos y tablas de dimensiones.
   * Procesamiento analítico (OLAP vs OLTP).
   * Creación de tablas, particiones y buckets en **Apache Hive** / Big Data Storage.
6. **Unidad 5: Nuevas Tendencias en Bases de Datos (NoSQL)**
   * Limitaciones del modelo relacional frente a escalabilidad horizontal (Teorema CAP).
   * Familias NoSQL: Documentales (MongoDB), Clave-Valor (Redis), Columnar Ancha (Cassandra/HBase) y Grafos (Neo4j).

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Sistema Hospitalario Completo: Modelado E/R Extendido, Normalización BCNF y Optimización SQL
* **Problema a Resolver:** Modelar la operación completa de una red hospitalaria (pacientes, citas, historiales clínicos, médicos especialistas, pabellones y recetas) garantizando cero redundancia de datos mediante normalización matemática y tiempos de respuesta sub-segundo en millones de filas.
* **Correspondencia con el PDF:**
  * Unidades 1, 2 y 3: Modelo E/R Extendido, algoritmo formal de descomposición en BCNF preservando dependencias, SQL avanzado (Window Functions, CTEs recursivas, Triggers, Procedimientos Almacenados) y optimización con `EXPLAIN`.
* **Requerimientos Funcionales y Técnicos:**
  1. Diseño del diagrama E/R Extendido con herencia de roles (`Médico`, `Enfermero`, `Administrativo` heredan de `Persona`).
  2. Demostración formal paso a paso de la normalización del esquema desde 1FN hasta 3FN/BCNF usando cálculo de clausura de dependencias $X^+$.
  3. Creación del esquema en PostgreSQL con restricciones estrictas de integridad referencial (`ON DELETE RESTRICT/CASCADE`, `CHECK`, dominios personalizados).
  4. Generación sintética de **2 millones de registros** de pruebas.
  5. Consultas complejas de analítica:
     * Tiempos de espera promedio por especialidad usando `AVG() OVER (PARTITION BY especialidad_id)`.
     * Detección de posibles fraudes en prescripciones de medicamentos con CTEs correlacionadas.
  6. **Laboratorio de Optimización:** Comparar una consulta sin indexar (Seq Scan de 3.5 segundos) vs una consulta optimizada con Índices Parciales B-Tree e índices compuestos (Index Scan en 8 ms), documentando el análisis de costos del planificador.
* **Stack Tecnológico:** PostgreSQL 15+, Docker, pgAdmin, Python (script generador con Faker).
* **Valor en Entrevistas Técnicas:** Demuestra que sabes diseñar bases de datos con fundamento teórico formal y que dominas el tuning de rendimiento en SQL de nivel productivo.

---

### Proyecto 2: Data Warehouse para E-Commerce con Esquema en Estrella y Consultas OLAP
* **Problema a Resolver:** Los sistemas transaccionales (OLTP) se degradan si se ejecutan reportes analíticos pesados sobre ellos. Diseñar una Bodega de Datos (Data Warehouse) con proceso ETL permite analizar tendencias de ventas multianuales de forma instantánea.
* **Correspondencia con el PDF:**
  * Unidad 4: Data Warehouses, esquemas estrella/copo de nieve, tablas de hechos (`Fact_Sales`), tablas de dimensiones (`Dim_Time`, `Dim_Product`, `Dim_Customer`, `Dim_Store`) y consultas agregadas OLAP.
* **Requerimientos Funcionales:**
  1. Diseñar el pipeline ETL (Extract, Transform, Load) que extrae datos de la BD transaccional relacional, limpia inconsistencias y carga el Data Warehouse.
  2. Implementar dimensiones lentamente cambiantes (SCD Tipo 2: histórico de cambios de domicilio del cliente).
  3. Consultas analíticas multidimensionales usando `ROLLUP`, `CUBE` y `GROUPING SETS`.
  4. Conectar un dashboard interactivo de Business Intelligence (Power BI, Metabase o Grafana).
* **Stack Tecnológico:** PostgreSQL / ClickHouse / Apache Hive, Python (Pandas para ETL) y Metabase.
* **Valor en Entrevistas Técnicas:** Fundamental para aspirantes a Data Engineer y Database Administrator (DBA).

---

### Proyecto 3: Arquitectura de Persistencia Políglota (PostgreSQL + MongoDB + Redis + Neo4j)
* **Problema a Resolver:** En sistemas modernos, ninguna base de datos es óptima para todos los casos de uso: los datos financieros requieren ACID (Postgres), el catálogo requiere esquemas dinámicos (Mongo), la sesión requiere microsegundos (Redis) y las recomendaciones requieren relaciones complejas (Neo4j).
* **Correspondencia con el PDF:**
  * Unidades 1 y 5: Comparación relacional vs NoSQL documental, clave-valor y grafos; consistencia vs disponibilidad (Teorema CAP).
* **Requerimientos Funcionales:**
  1. Construir una aplicación unificada donde:
     * **PostgreSQL:** Gestiona usuarios, balances y compras (integridad transaccional ACID estricta).
     * **MongoDB:** Almacena el catálogo de productos con atributos variables no estructurados.
     * **Redis:** Caché de sesión de usuario y carrito de compras volátil con expiración TTL.
     * **Neo4j:** Grafo de amigos y recomendaciones (*"usuarios que compraron esto también compraron..."*).
  2. Implementar sincronización desacoplada mediante Change Data Capture (CDC) o eventos.
* **Stack Tecnológico:** PostgreSQL, MongoDB, Redis, Neo4j, Docker Compose, Node.js o Python.
