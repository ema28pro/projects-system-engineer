# 2567101 – Descubriendo la Física

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Descubriendo la Física
* **Código de Curso:** 2567101
* **Nivel:** 1
* **Unidad Académica:** Facultad de Ingeniería – Instituto de Física (FCEN)
* **Área:** Ciencias Básicas de Ingeniería
* **Créditos Académicos:** 3
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Las Leyes de la Mecánica**
   * Conceptos de posición, desplazamiento, velocidad, aceleración y Sistema Internacional (SI).
   * Masa, inercia, principios de Newton, conservación de la cantidad de movimiento y colisiones.
   * Ley de gravitación universal y condiciones de equilibrio estático.
2. **Unidad 2: Termodinámica**
   * Concepto de trabajo y calor; presión atmosférica.
   * Leyes de la termodinámica: Ley Cero, Primera Ley (conservación de energía) y Segunda Ley (**Entropía y degradación energética**).
3. **Unidad 3: Electrodinámica**
   * Cargas eléctricas, campo eléctrico y potencial electrostático.
   * Corriente eléctrica, Ley de Ohm, circuitos eléctricos básicos en serie y paralelo.
   * Magnetismo, inducción electromagnética y Ley de Faraday.
4. **Unidad 4: Estructura de la Materia**
   * Modelos atómicos, enlaces químicos y estados de agregación.
   * Introducción a la física del estado sólido: conductores, aislantes y **semiconductores** (la base del transistor de silicio y la computación moderna).
5. **Unidad 5: Información y Telecomunicaciones**
   * Ondas electromagnéticas y espectro electromagnético.
   * Transmisión de señales, modulación (AM, FM), reflexión/refracción en fibra óptica.
   * De la física al bit: el principio físico del almacenamiento magnético, óptico y electrónico.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Simulador Computacional Multidisciplinar de Física (Mecánica, Termodinámica y Circuitos DC)
* **Problema a Resolver:** Comprender visualmente cómo las leyes de la física se traducen en modelos numéricos computacionales, sirviendo como base para simuladores industriales y videojuegos.
* **Correspondencia con el PDF:**
  * Unidades 1, 2 y 3: Cinemática newtoniana, equilibrio térmico / calorimetría y resolución de circuitos resistivos aplicando la Ley de Ohm y Leyes de Kirchhoff.
* **Requerimientos Funcionales:**
  1. **Módulo de Mecánica:** Simulación de colisiones elásticas e inelásticas en 1D con cálculo de momentum conservado.
  2. **Módulo de Termodinámica:** Simulador de mezcla de sustancias a diferentes temperaturas calculando la temperatura de equilibrio final ($Q_{ganado} + Q_{cedido} = 0$) y aumento de entropía $\Delta S$.
  3. **Módulo de Circuitos:** Solucionador interactivo de circuitos DC con resistencias en serie y paralelo, calculando voltajes de nodo y corrientes de malla.
* **Stack Tecnológico:** Python (NumPy, Matplotlib o Streamlit) o JavaScript con Canvas HTML5.
* **Valor en Entrevistas Técnicas:** Conecta la ciencia fundamental con el desarrollo de simuladores de software interactivos.

---

### Proyecto 2: Visualizador Interactivo de Telecomunicaciones: Ondas, Modulación y Propagación en Fibra Óptica
* **Problema a Resolver:** En redes y comunicaciones, los datos digitales viajan como ondas moduladas en medios físicos. Visualizar la física ondulatoria aclara el funcionamiento de Wi-Fi y fibra óptica.
* **Correspondencia con el PDF:**
  * Unidad 5: Ondas electromagnéticas, modulación analógica/digital (AM/FM/FSK), Ley de Snell y reflexión interna total en cables de fibra óptica.
* **Requerimientos Funcionales:**
  1. Generador de onda portadora y moduladora interactiva con control de amplitud y frecuencia.
  2. Demostración visual de la reflexión interna total en un núcleo de fibra óptica variando el índice de refracción del núcleo vs revestimiento.
* **Stack Tecnológico:** Python o Web (p5.js / HTML5 Canvas).
