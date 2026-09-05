# 2554842 – Sistemas Operativos y Laboratorio

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Sistemas Operativos y Laboratorio
* **Código de Curso:** 2554842
* **Nivel:** 8
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 4
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial
* **Libro Guía Oficial:** *Operating Systems: Three Easy Pieces (OSTEP)* (Remzi Arpaci-Dusseau & Andrea Arpaci-Dusseau - Wisconsin).

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Introducción a los Sistemas Operativos (1 semana)**
   * El sistema operativo como gestor de recursos y como máquina virtual extendida.
   * Arquitecturas de kernel: Monolítico, Microkernel, Híbrido.
   * Modos de ejecución de hardware: Modo Usuario (*User Mode*) vs Modo Kernel (*Kernel/Supervisor Mode*).
   * La interfaz de llamadas al sistema (**System Calls / Syscalls**) y manejo de interrupciones y excepciones por hardware.
2. **Unidad 2: Virtualización de Recursos: CPU (4 semanas)**
   * La abstracción de Proceso: espacio de direcciones, estados del proceso y Bloque de Control de Proceso (**PCB**).
   * Creación y control de procesos en UNIX: llamadas al sistema `fork()`, `exec()` y `wait()`.
   * El Cambio de Contexto (*Context Switch*).
   * Algoritmos de planificación de la CPU:
     * No expulsivos: FIFO, Shortest Job First (**SJF**).
     * Expulsivos: Shortest Time-to-Completion First (**STCF**), **Round Robin (RR)** con quantum de tiempo.
     * Planificación avanzada por prioridades dinámicas: **Cola de Retroalimentación Multinivel (MLFQ - Multi-Level Feedback Queue)**.
3. **Unidad 3: Virtualización de Recursos: Memoria (4 semanas)**
   * La abstracción del espacio de direcciones virtual.
   * Mecanismos de reubicación de memoria: registros Base y Límite, Segmentación de memoria.
   * **Paginación**: Marcos de página físicos (*frames*), páginas lógicas y Tablas de Páginas.
   * Aceleración del hardware: **TLB (Translation Lookaside Buffer)** y manejo de fallos de TLB.
   * Tablas de páginas multinivel para optimizar el consumo de memoria del kernel.
   * **Memoria Virtual y Paginación por Demanda**: Manejo del fallo de página (*Page Fault*).
   * Algoritmos de reemplazo de páginas: FIFO, Óptimo (MIN), **LRU (Least Recently Used)** y Algoritmo del Reloj (*Clock Algorithm* con bit de uso).
4. **Unidad 4: Concurrencia (4 semanas)**
   * Hilos de ejecución (*Threads*), memoria compartida y condiciones de carrera (*Race Conditions*).
   * Exclusión mutua y primitivas de sincronización:
     * Cerrojos (**Locks / Mutexes**) con soporte de hardware (instrucciones atómicas `test-and-set` y `compare-and-swap`).
     * Variables de Condición (`wait`, `signal`, `broadcast`).
     * **Semáforos de Dijkstra** (binarios y contadores).
   * Problemas clásicos de sincronización:
     * Productor-Consumidor con búfer acotado.
     * Lectores-Escritores.
     * La Cena de los Filósofos.
   * **Interbloqueos (Deadlocks)**: Las 4 condiciones necesarias de Coffman, prevención, detección y el **Algoritmo del Banquero de Dijkstra**.
5. **Unidad 5: Persistencia (3 semanas)**
   * Dispositivos de E/S: Discos duros magnéticos y Unidades de Estado Sólido (**SSD** con capa FTL y nivelación de desgaste).
   * Abstracción del Sistema de Archivos: archivos, directorios, descriptores de archivo y tablas de inodos (**inodes**).
   * Asignación de bloques en disco: continua, enlazada e indexada (inodos con bloques directos e indirectos).
   * Integridad y consistencia ante fallos (*Crash Consistency*): Recuperación con comprobadores de integridad (`fsck`) y **Sistemas de Archivos con Registro en Diario (Journaling File Systems)**.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Implementación de una Shell de Linux Propia (Custom Unix Shell) en C
* **Problema a Resolver:** Comprender exactamente cómo el sistema operativo crea procesos, redirige descriptores de archivo estándar y maneja tuberías (*pipes*) programando una consola de comandos tipo `bash` desde cero.
* **Correspondencia con el PDF:**
  * Unidades 1 y 2: Llamadas al sistema del kernel UNIX (`fork`, `execvp`, `waitpid`, `pipe`, `dup2`, `open`, `close`, `kill`), señales de software y gestión del PCB.
* **Requerimientos Funcionales:**
  1. Bucle de ejecución REPL que imprime un prompt personalizado y parsea comandos con argumentos variables.
  2. Ejecución de comandos del sistema buscando binarios en el `PATH` mediante `fork()` y `execvp()`.
  3. Soporte para comandos internos (*built-ins*): `cd`, `pwd`, `exit`, `history`.
  4. Redirección de entrada y salida estándar usando `dup2()`: `comando > archivo.txt`, `comando < entrada.txt`, `comando >> append.txt`.
  5. Implementación de **Tuberías (*Pipes*) inter-procesos**: encadenar múltiples comandos mediante `pipe()` (ej. `ls -l | grep txt | wc -l`).
  6. Ejecución en segundo plano: soporte para el operador `&` evitando la creación de procesos zombies mediante recolección con `waitpid(WNOHANG)`.
  7. Manejo de señales: capturar `Ctrl+C` (`SIGINT`) para que cancele el proceso hijo en ejecución sin cerrar la shell principal.
* **Stack Tecnológico:** Lenguaje C (estándar POSIX), compilador GCC, entorno Linux / WSL.
* **Valor en Entrevistas Técnicas:** Es el proyecto de cabecera más respetado en sistemas operativos, demostrando dominio de memoria en C, punteros y llamadas al kernel.

---

### Proyecto 2: Simulador del Planificador MLFQ y Algoritmos de Reemplazo de Páginas (LRU / Clock)
* **Problema a Resolver:** Visualizar y comparar empíricamente el comportamiento de los dos mecanismos más complejos de virtualización del SO: la cola de retroalimentación multinivel (CPU) y la paginación por demanda (Memoria RAM).
* **Correspondencia con el PDF:**
  * Unidades 2 y 3: Planificador MLFQ (con reglas de prioridad, asignación de quantum y envejecimiento/boost prioritario para evitar inanición) y simulador de memoria virtual con fallos de página.
* **Requerimientos Funcionales:**
  1. **Módulo MLFQ:** Configuración de $N$ colas con diferentes quantums de tiempo, degradación de prioridad cuando un proceso consume su tiempo de CPU y *Priority Boost* periódico. Simular procesos interactivos (I/O bound) vs intensivos de CPU (CPU bound) y reportar tiempos de respuesta y retorno.
  2. **Módulo de Paginación de Memoria:** Generar trazas de acceso a memoria y comparar el número de fallos de página (*Page Faults*) entre FIFO, Óptimo, LRU y Algoritmo del Reloj (*Clock Algorithm*).
  3. Gráficas interactivas que muestren el diagrama de Gantt de la CPU y la tasa de aciertos de la memoria RAM.
* **Stack Tecnológico:** C++ o Python con Matplotlib / Interfaz web.
* **Valor en Entrevistas Técnicas:** Demuestra entendimiento cuantitativo de la gestión interna de recursos en el kernel.

---

### Proyecto 3: Servidor de Chat Concurrente Multihilo Seguro sin Condiciones de Carrera
* **Problema a Resolver:** Administrar múltiples clientes concurrentes accediendo a recursos compartidos en memoria (salas de chat, balances de cuentas) garantizando exclusión mutua estricta con semáforos y locks sin caer en interbloqueos (*deadlocks*).
* **Correspondencia con el PDF:**
  * Unidad 4: Hilos POSIX (`pthread`), mutexes, variables de condición, semáforos contadores y prevención de condiciones de Coffman.
* **Requerimientos Funcionales:**
  1. Servidor en C o Rust escuchando conexiones TCP concurrentes mediante un pool de hilos de trabajo (*Thread Pool*).
  2. Implementar un búfer circular compartido de mensajes aplicando el patrón **Productor-Consumidor** sincronizado con 2 semáforos y 1 mutex.
  3. Demostrar la detección de *Deadlocks* implementando una rutina de verificación de ciclos en el grafo de asignación de recursos o el Algoritmo del Banquero.
* **Stack Tecnológico:** C (`pthreads`) o Rust.
