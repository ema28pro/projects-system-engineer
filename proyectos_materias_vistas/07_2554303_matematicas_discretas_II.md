# 2554303 – Matemáticas Discretas II

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Matemáticas Discretas II
* **Código de Curso:** 2554303
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 3
* **Pre-requisitos:** 2554207 – Matemáticas Discretas I | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Aritmética Entera (2 semanas)**
   * Divisibilidad, algoritmo de la división euclidiana.
   * Máximo Común Divisor (MCD) y Mínimo Común Múltiplo (MCM).
   * Algoritmo de Euclides estándar y Algoritmo de Euclides Extendido (identidad de Bézout).
   * Números primos, criba de Eratóstenes y Teorema Fundamental de la Aritmética.
   * Ecuaciones diofánticas lineales ($ax + by = c$).
2. **Unidad 2: Aritmética Modular (6 semanas)**
   * Relación de congruencia y propiedades algebraicas en $\mathbb{Z}_m$.
   * Aritmética en $\mathbb{Z}_m$ (suma, resta, multiplicación).
   * Inversos multiplicativos modulares.
   * Ecuaciones de congruencia lineales y sistemas de congruencias mediante el Teorema Chino del Resto (TCR).
   * Pequeño Teorema de Fermat y Teorema de Euler (función $\phi$ de Euler).
   * Exponenciación modular rápida.
3. **Unidad 3: Técnicas de Conteo (2 semanas)**
   * Principio de adición y multiplicación.
   * Principio del Palomar (Casillas de Dirichlet).
   * Permutaciones y combinaciones con y sin repetición.
   * Teorema del Binomio y coeficientes binomiales.
   * Principio de inclusión-exclusión generalizado.
4. **Unidad 4: Inducción Matemática (2 semanas)**
   * Principio del Buen Orden.
   * Inducción matemática simple y fuerte para demostrar propiedades de algoritmos y fórmulas cerradas.
5. **Unidad 5: Teoría de Grafos (2 semanas)**
   * Caminos, circuitos eulerianos y hamiltonianos.
   * Grafos planos y Teorema de Kuratowski.
   * Coloreo de grafos y número cromático (Teorema de los 4 colores).
   * Árboles y propiedades de conectividad.
6. **Unidad 6: Criptografía (1.5 semanas)**
   * Criptografía clásica: cifrado César, cifrado Afín y cifrado por sustitución.
   * Criptografía moderna de clave pública: Criptosistema RSA (generación de claves, cifrado, descifrado) e intercambio de claves Diffie-Hellman.
7. **Unidad 7: Teoría de la Codificación (0.5 semanas)**
   * Códigos de bloque, distancia de Hamming, detección y corrección de errores (códigos de paridad y Hamming).

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Implementación Completa del Criptosistema RSA y Diffie-Hellman desde Cero
* **Problema a Resolver:** La seguridad de internet (HTTPS, SSH, firmas digitales) se basa en la dificultad del problema de factorización entera y logaritmo discreto. Implementar RSA desde los fundamentos de la teoría de números es el pináculo de las matemáticas discretas aplicadas.
* **Correspondencia con el PDF:**
  * Unidades 1, 2 y 6: Primos, test de primalidad (Miller-Rabin), algoritmo de Euclides extendido para inversos modulares, exponenciación modular rápida, función $\phi$ de Euler y criptografía asimétrica RSA.
* **Requerimientos Funcionales:**
  1. Generador de números primos grandes utilizando el test probabilístico de primalidad de Miller-Rabin.
  2. Implementación del **Algoritmo de Euclides Extendido** para calcular el inverso modular $d = e^{-1} \pmod{\phi(n)}$.
  3. Algoritmo de **Exponenciación Modular Rápida** ($O(\log b)$) para cifrado $c = m^e \pmod n$ y descifrado $m = c^d \pmod n$.
  4. Protocolo de intercambio de llaves **Diffie-Hellman** demostrando la creación de un secreto compartido sobre un canal público.
  5. CLI interactivo con soporte para cifrar y descifrar archivos de texto plano o generar pares de llaves pública/privada exportables.
* **Stack Tecnológico:** Python (sin usar librerías criptográficas de alto nivel como `cryptography`; solo aritmética entera pura de precisión arbitraria) o Rust / C++.
* **Valor en Entrevistas Técnicas:** Demuestra fundamentos sólidos de seguridad informática, criptografía moderna y teoría de números aplicada.

---

### Proyecto 2: Solucionador de Sistemas de Congruencias mediante Teorema Chino del Resto y Ecuaciones Diofánticas
* **Problema a Resolver:** El Teorema Chino del Resto permite resolver problemas de sincronización cíclica de procesos periódicos, computación distribuida de alta velocidad con aritmética modular (RNS - Residue Number System) y puzles matemáticos.
* **Correspondencia con el PDF:**
  * Unidades 1 y 2: Ecuaciones diofánticas lineales, congruencias lineales y Teorema Chino del Resto.
* **Requerimientos Funcionales:**
  1. Resolver sistemas de congruencias de la forma $x \equiv a_i \pmod{m_i}$ verificando que los módulos sean coprimos dos a dos.
  2. Resolver ecuaciones diofánticas $ax + by = c$, calculando el $\gcd(a, b)$ y verificando la condición de existencia de soluciones enteras ($c \mid \gcd(a, b)$).
  3. Visualización interactiva del paso a paso matemático para fines educativos.
* **Stack Tecnológico:** Python.
* **Valor en Entrevistas Técnicas:** Dominio de algoritmos algebraicos exactos y estructuras matemáticas discretas.

---

### Proyecto 3: Simulador de Códigos Detectores y Correctores de Errores (Hamming(7,4))
* **Problema a Resolver:** En transmisiones de red o lectura de memoria RAM (ECC), los bits se corrompen debido a ruido electromagnético. Los códigos de bloque basados en distancia de Hamming permiten detectar y corregir automáticamente bits alterados.
* **Correspondencia con el PDF:**
  * Unidad 7: Distancia de Hamming, bits de paridad, matrices generadoras y matrices de paridad en códigos de bloque lineales.
* **Requerimientos Funcionales:**
  1. Codificar paquetes de datos de 4 bits en palabras de código de 7 bits insertando 3 bits de paridad (Código Hamming(7,4)).
  2. Simulador de canal con ruido: inyectar aleatoriamente 1 bit de error en el mensaje transmitido.
  3. Decodificador que calcula el vector síndrome $S = H \cdot r^T$, identifica la posición exacta del bit corrupto, lo corrige automáticamente y recupera el mensaje original.
* **Stack Tecnológico:** Python o C.
