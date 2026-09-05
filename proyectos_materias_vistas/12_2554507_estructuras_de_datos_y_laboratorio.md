# 2554507 – Estructuras de Datos y Laboratorio

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Estructuras de Datos y Laboratorio
* **Código de Curso:** 2554507
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 4
* **Pre-requisitos:** 2554402 – Lógica y Representación III | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial
* **Libros Guía:** *Fundamentos de Bases de Datos* (Korth), *Foundations of Multidimensional and Metric Data Structures* (Hannan Samet), *El Arte de Programar Ordenadores Vol. 3* (Knuth).

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **UNIDAD 1: Archivos y Métodos de Acceso Unidimensional (8 semanas)**
   * Dispositivos de almacenamiento secundario y acceso directo (DASD: pistas, sectores, cilindros, bloques).
   * Gestión de archivos en sistemas operativos: FAT, NTFS, RAID (0, 1, 5, 10), arquitecturas HDFS/Hadoop.
   * Procesamiento en línea (*online*) vs por lotes (*batch*).
   * Registros de longitud fija y longitud variable (delimitadores, longitud prefijada).
   * Métodos de indización: **ISAM** (Indexed Sequential Access Method).
   * Métodos de acceso directo por **Hashing**: Hashing estático, Hashing dinámico lineal, extendido y **Hashing extensible**.
   * Árboles $m$-vías, **Árboles B** y **Árboles B+** (indización de memoria secundaria, nodos hoja enlazados).
   * Árboles Trie, árboles doblemente encadenados y archivos de anillo.
   * Índices secundarios: multilistas e **índices invertidos** para motores de búsqueda.
   * Estructuras de datos para serialización (JSON, XML, Bitmaps) y bases de datos NoSQL.
2. **UNIDAD 2: Algoritmos de Ordenamiento (4 semanas)**
   * Comparación de ordenamientos internos: inserción, intercambio, selección, mezcla (Merge), distribución (Radix/Bucket).
   * **Ordenamiento Externo por Mezcla Multi-vía (External $K$-Way Merge Sort)** para volúmenes de datos que exceden la memoria RAM.
3. **UNIDAD 3: Archivos y Métodos de Acceso Multidimensional (4 semanas)**
   * Métodos de acceso puntual (PAM): **Árbol KD**, KD Adaptativo, **Árboles Quad (QuadTrees)** y Quad de regiones.
   * PAM en memoria secundaria: **Grid File**.
   * Estructuras jerárquicas: Árbol KDB, Árboles HB.
   * Métodos de acceso espacial (SAM): **Árboles R (R-Trees)**, **Árboles R*** y variantes (VAM-split R).

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Motor de Base de Datos Basado en Disco con Árbol B+ y Hashing Extensible
* **Problema a Resolver:** Los motores relacionales reales (MySQL InnoDB, SQLite, PostgreSQL) almacenan páginas binarias de disco organizadas en Árboles B+ para mantener consultas ordenadas en tiempo logarítmico con un mínimo de operaciones I/O en disco.
* **Correspondencia con el PDF:**
  * Unidad 1: Registros de longitud fija/variable, páginas de disco, Árbol B+ persistente en archivo y Hashing dinámico extensible.
* **Requerimientos Funcionales:**
  1. Diseñar un `FileManager` que simule bloques/páginas de disco de 4096 bytes en un archivo binario `.dat`.
  2. Implementar un **Árbol B+ persistente** donde los nodos internos contienen llaves y punteros a números de bloque de disco, y los nodos hoja forman una lista doblemente enlazada para recorridos de rango secuenciales eficientes (`SELECT * WHERE id BETWEEN 100 AND 500`).
  3. Soporte para inserción con división de nodos (*split*) hacia arriba y borrado con redistribución/fusión (*merge*).
  4. Implementar un módulo alternativo de **Hashing Extensible** con directorio de profundidad global y bloques de datos con profundidad local que se duplican dinámicamente cuando hay desbordamiento.
  5. Mini-CLI para ejecutar comandos `INSERT`, `SEARCH`, `DELETE` y `RANGE_SCAN`.
* **Stack Tecnológico:** C++, Rust, C o Java (usando `RandomAccessFile` y `ByteBuffer`).
* **Valor en Entrevistas Técnicas:** Es uno de los proyectos de sistemas más avanzados e impresionantes que puede tener un estudiante, demostrando comprensión absoluta de bajo nivel sobre almacenamiento en bases de datos.

---

### Proyecto 2: Motor de Consultas Espaciales y Geográficas mediante Árbol R (R-Tree) o QuadTree
* **Problema a Resolver:** En aplicaciones de movilidad y logística (como Uber o Google Maps), encontrar todos los vehículos o locales dentro de un área rectangular o buscar el objeto más cercano requiere indexación multidimensional eficiente (Bounding Boxes).
* **Correspondencia con el PDF:**
  * Unidad 3: Métodos de acceso espacial (SAM), Árboles R con rectángulos mínimos envolventes (MBR - *Minimum Bounding Rectangles*), división de nodos y QuadTrees.
* **Requerimientos Funcionales:**
  1. Ingesta de 50,000 coordenadas geográficas reales (latitud, longitud, metadata).
  2. Construcción de un **Árbol R** con cálculo de MBRs para cada nodo hoja e intermedio.
  3. Algoritmo de división de nodos cuadrático (*Quadratic Split*) al superar la capacidad máxima de la página $M$.
  4. Ejecución de consultas espaciales:
     * *Window Query*: retornar todos los puntos contenidos dentro de un rectángulo de consulta.
     * *$k$-Nearest Neighbors ($k$-NN)*: encontrar los $k$ puntos más cercanos a una coordenada dada usando poda de distancias mínimas.
  5. Visualización interactiva en navegador (renderizando los MBRs sobre un mapa con Leaflet o Mapbox).
* **Stack Tecnológico:** Python, Java o TypeScript.
* **Valor en Entrevistas Técnicas:** Demuestra dominio de indexación espacial para GIS, motores de juegos y procesamiento de datos geográficos.

---

### Proyecto 3: Clasificador Externo de Archivos Masivos (External K-Way Merge Sort)
* **Problema a Resolver:** Ordenar un archivo plano de 5 GB en una máquina con una restricción estricta de memoria RAM de 64 MB sin que el sistema colapse por falta de memoria (*OutOfMemoryError*).
* **Correspondencia con el PDF:**
  * Unidad 2: Ordenamiento externo por mezcla multi-vía, gestión de buffers de lectura/escritura y árboles de perdedores / Min-Heaps en memoria.
* **Requerimientos Funcionales:**
  1. Fase 1 (Generación de *Runs*): leer bloques de tamaño fijo que quepan en la RAM permitida, ordenarlos en memoria con QuickSort y escribirlos como archivos temporales ordenados en disco.
  2. Fase 2 (Mezcla Multi-vía): abrir flujos concurrentes de $K$ archivos temporales y mezclarlos hacia el archivo final de salida usando un **Min-Heap** de $K$ elementos en memoria.
  3. Registro detallado de métricas: número de lecturas/escrituras en disco (I/O operations), tiempo total y espacio temporal utilizado.
* **Stack Tecnológico:** C++, Java o Python.
