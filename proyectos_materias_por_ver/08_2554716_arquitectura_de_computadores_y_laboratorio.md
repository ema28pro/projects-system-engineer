# 2554716 – Arquitectura de Computadores y Laboratorio

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Arquitectura de Computadores y Laboratorio
* **Código de Curso:** 2554716
* **Nivel:** 7
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 4
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial
* **Libro Guía Oficial:** *Computer Organization and Design: The Hardware/Software Interface* (Patterson & Hennessy - RISC-V / MIPS Edition).

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **UNIDAD 0 y 1: Representación de Datos y Álgebra Booleana (3 semanas)**
   * Representación binaria de datos a bajo nivel: enteros sin signo, complemento a 2 y desbordamiento (*overflow*).
   * Representación en punto flotante bajo el estándar internacional **IEEE 754** (precisión simple de 32 bits y doble de 64 bits: bit de signo, exponente sesgado y mantisa/fracción).
   * Álgebra de Boole y simplificación de circuitos con compuertas lógicas primitivas.
2. **UNIDAD 2: Componentes Digitales Combinacionales (1 semana)**
   * Decodificadores, codificadores con prioridad y multiplexores ($N \to 1$).
   * Circuitos aritméticos: Semisumador, sumador completo (*Full Adder*), sumador con propagación de acarreo (*Ripple-Carry*) y sumador con acarreo anticipado (*Carry-Lookahead*).
   * Diseño de una **Unidad Aritmético-Lógica (ALU)** de 32 bits con operaciones `AND`, `OR`, `ADD`, `SUB`, `SLT` y bandera de Cero (*Zero flag*).
3. **UNIDAD 3: Componentes Digitales Secuenciales y Almacenamiento (1.5 semanas)**
   * Elementos biestables: Latches SR y Flip-Flops tipo D activados por flanco de reloj (*clock edge*).
   * Registros de almacenamiento, registros de desplazamiento y contadores síncronos.
   * Banco de Registros (**Register File**) con 2 puertos de lectura y 1 de escritura.
   * Memorias estáticas (SRAM) y dinámicas (DRAM).
4. **UNIDAD 4: El Lenguaje de la Máquina (ISA) (3 semanas)**
   * Arquitectura de Conjunto de Instrucciones (**ISA**): Filosofía RISC vs CISC.
   * El repertorio de instrucciones **RISC-V o MIPS**:
     * Instrucciones tipo R (aritmético-lógicas entre registros).
     * Instrucciones tipo I (inmediatos y cargas de memoria `lw`).
     * Instrucciones tipo S/B (almacenamiento en memoria `sw` y saltos condicionales `beq`, `bne`).
     * Instrucciones tipo U/J (saltos incondicionales y llamadas a funciones `jal`, `jalr`).
   * Convenciones de registro y manejo de la pila (*Stack Pointer* `sp`, *Frame Pointer* `fp`, preservación de registros).
   * Traducción manual y compilación de código C a lenguaje ensamblador.
5. **UNIDAD 5: Evaluación del Rendimiento de un Computador (1.5 semanas)**
   * Métrica central del rendimiento de la CPU: $Tiempo_{CPU} = IC \times CPI \times \tau$.
   * Conteo de Instrucciones ($IC$), Ciclos por Instrucción ($CPI$) y frecuencia de reloj.
   * Benchmarks estandarizados (SPEC CPU) y la **Ley de Amdahl** para aceleración por paralelismo.
6. **UNIDAD 6: Procesador Monociclo y Segmentado (Pipelined) (2 semanas)**
   * Diseño del camino de datos (**Datapath**) monociclo: búsqueda de instrucción (*Instruction Fetch*), decodificación, ejecución en la ALU, acceso a memoria y escritura de registros (*Write-back*).
   * Unidad de Control combinacional (generación de señales: `RegWrite`, `ALUSrc`, `MemRead`, `MemWrite`, `Branch`).
   * Procesador segmentado de 5 etapas (**Pipeline**): IF, ID, EX, MEM, WB.
   * Riesgos en el pipeline y sus soluciones:
     * Riesgos Estructurales: separación de memorias de instrucciones y datos (Arquitectura Harvard).
     * Riesgos de Datos: **Adelantamiento (*Forwarding / Bypassing*)** y detección de riesgos con detención (*Stall / Bubble*).
     * Riesgos de Control: predicción estática y dinámica de saltos.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Emulador Funcional de un Procesador RISC-V de 32 Bits (RV32I) en C++ o Python
* **Problema a Resolver:** Comprender exactamente el ciclo de instrucción de la CPU (*Fetch-Decode-Execute*) programando un emulador por software que cargue un binario compilado y lo ejecute instrucción por instrucción actualizando el Program Counter (PC), los registros y la memoria RAM.
* **Correspondencia con el PDF:**
  * Unidades 1, 4 y 6: Decodificación binaria de formatos R, I, S, B, U, J de RISC-V, emulación de la ALU, banco de 32 registros, memoria virtual y ejecución paso a paso.
* **Requerimientos Funcionales:**
  1. Diseñar las estructuras para el estado de la CPU: `uint32_t pc`, `uint32_t registers[32]` (con `x0` siempre en 0) y un arreglo de memoria `uint8_t memory[MEMORY_SIZE]`.
  2. Implementar el ciclo de instrucción:
     * **Fetch:** Leer palabra de 32 bits apuntada por el PC.
     * **Decode:** Extraer campos `opcode`, `rd`, `funct3`, `rs1`, `rs2`, `funct7` y extender el signo de los inmediatos según el tipo de instrucción.
     * **Execute:** Ejecutar operaciones aritméticas (`add`, `sub`, `sll`, `slt`), inmediatas (`addi`, `andi`), saltos condicionales (`beq`, `bne`, `blt`), saltos incondicionales (`jal`, `jalr`) y acceso a memoria (`lw`, `sw`).
  3. Cargar programas escritos en C y ensamblados con la toolchain oficial de GCC para RISC-V (ej. cálculo de la serie de Fibonacci o multiplicación de matrices).
  4. Visualizador en terminal que imprima el estado de los registros tras cada ciclo y las instrucciones desensambladas en tiempo real.
* **Stack Tecnológico:** C++17 o Python 3.
* **Valor en Entrevistas Técnicas:** Es el proyecto cumbre para roles en firmware, sistemas embebidos, ingeniería de compiladores y bajo nivel.

---

### Proyecto 2: Diseño y Simulación de un Procesador Monociclo MIPS en Logisim / Digital
* **Problema a Resolver:** Diseñar físicamente a nivel de compuertas y bloques lógicos el camino de datos y la unidad de control que ejecute un repertorio básico de instrucciones.
* **Correspondencia con el PDF:**
  * Unidades 2, 3 y 6: ALU de 32 bits, banco de registros con multiplexores y decodificadores, memoria de instrucciones/datos y unidad de control monociclo.
* **Requerimientos Funcionales:**
  1. Construir la **ALU de 32 bits** modular combinando 32 ALUs de 1 bit con acarreo en cascada.
  2. Construir el **Banco de Registros (Register File)** de 32 registros $\times$ 32 bits con habilitador de escritura `RegWrite`.
  3. Integrar el Datapath conectando el PC, sumadores de incremento ($PC+4$) y de salto relativo, multiplexores de selección de operandos y la memoria RAM.
  4. Diseñar la **Unidad de Control Principal** (ROM o matriz de compuertas) que decodifica el código de operación y activa las líneas de control correctas.
  5. Cargar un microcódigo de prueba en la memoria de instrucciones y demostrar la ejecución autónoma de un bucle de suma en el circuito animado.
* **Herramientas:** Digital (de HNeemann) o Logisim Evolution.
* **Valor en Entrevistas Técnicas:** Demuestra entendimiento de hardware digital y de cómo el software interactúa con la electrónica subyacente.
