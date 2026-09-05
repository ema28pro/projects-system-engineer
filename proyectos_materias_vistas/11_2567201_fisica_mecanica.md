# 2567201 – Física Mecánica

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Física Mecánica
* **Código de Curso:** 2567201
* **Unidad Académica:** Facultad de Ingeniería – Cursos de Servicios
* **Área:** Ciencias Básicas de Ingeniería
* **Créditos Académicos:** 4
* **Pre-requisitos:** 2559121 – Geometría Vectorial y Analítica | **Co-requisitos:** 2559131 – Cálculo Diferencial
* **Modalidad:** Virtual / Presencial

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Cinemática (La descripción matemática del movimiento)**
   * Medición, unidades y vectores cinemáticos (posición, velocidad y aceleración en función del tiempo).
   * Movimiento en una dimensión: aceleración constante, caída libre.
   * Movimiento en dos dimensiones: movimiento de proyectiles (tiro parabólico).
   * Movimiento circular uniforme (MCU) y acelerado (MCUA), aceleración centrípeta y tangencial.
2. **Unidad 2: Dinámica (Leyes del movimiento y Trabajo)**
   * Primera, segunda y tercera ley de Newton.
   * Diagramas de cuerpo libre (DCL), fuerzas de fricción estática y cinética, planos inclinados y poleas.
   * Dinámica del movimiento circular (fuerza centrípeta).
   * Concepto de trabajo efectuado por fuerzas constantes y variables, producto escalar $\vec{F} \cdot \Delta \vec{r}$.
3. **Unidad 3: Energía y Momento Lineal**
   * Energía cinética y Teorema del Trabajo y la Energía.
   * Fuerzas conservativas y disipativas; energía potencial gravitacional y elástica.
   * Principio de conservación de la energía mecánica.
   * Cantidad de movimiento lineal (momentum), impulso y conservación del momentum.
   * Colisiones elásticas e inelásticas en una y dos dimensiones.
4. **Unidad 4: Dinámica Rotacional de Cuerpos Rígidos y Movimiento Armónico Simple (MAS)**
   * Cinemática de rotación, momento de inercia y Teorema de los Ejes Paralelos (Steiner).
   * Torque (momento de torsión $\vec{\tau} = \vec{r} \times \vec{F}$) y segunda ley de Newton para la rotación ($\tau = I \alpha$).
   * Conservación del momento angular.
   * Movimiento Armónico Simple: oscilador masa-resorte, péndulo simple y péndulo físico.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Motor Físico 2D de Partículas y Colisiones (Physics Engine)
* **Problema a Resolver:** Diseñar desde cero el bucle de simulación temporal e integración de ecuaciones newtonianas para partículas con masa, gravedad y detección de colisiones elásticas e inelásticas.
* **Correspondencia con el PDF:**
  * Unidades 1, 2 y 3: Cinemática vectorial, leyes de Newton, conservación del momentum lineal e impulso en colisiones 2D.
* **Requerimientos Funcionales:**
  1. Integrador temporal (Euler Semi-implícito o Verlet) para actualizar $\vec{v}(t + \Delta t)$ y $\vec{r}(t + \Delta t)$.
  2. Manejo de fuerzas concurrentes: gravedad, viento y fuerzas de fricción viscosa con el aire ($F_d = -b v$).
  3. Detección continua de colisiones entre círculos y contra paredes rectangulares.
  4. Resolución de colisiones basada en impulso, conservando el momento lineal y aplicando un coeficiente de restitución $e \in [0, 1]$ (elástico vs inelástico).
  5. Panel interactivo que monitorea en tiempo real la conservación de la energía cinética total del sistema.
* **Stack Tecnológico:** JavaScript / Canvas puro o Python con Pygame.
* **Valor en Entrevistas Técnicas:** Demuestra entendimiento de arquitectura de motores de videojuegos, simulación computacional de sistemas continuos y estabilidad numérica en bucles de renderizado.

---

### Proyecto 2: Simulador Balístico con Resistencia del Aire Cuadrática y Viento Vectorial
* **Problema a Resolver:** En la cinemática ideal sin fricción, el tiro parabólico es una parábola analítica simétrica. En la realidad física, el arrastre aerodinámico es proporcional al cuadrado de la velocidad ($F_d = \frac{1}{2} \rho C_d A v^2$), convirtiendo las ecuaciones en un sistema acoplado no lineal que exige solución numérica.
* **Correspondencia con el PDF:**
  * Unidad 1 y 2: Cinemática en 2D, descomposición vectorial de fuerzas, ecuaciones diferenciales de movimiento newtoniano.
* **Requerimientos Funcionales:**
  1. Configuración de parámetros: ángulo de disparo, velocidad inicial, masa del proyectil, densidad del aire, área frontal y vector de velocidad del viento.
  2. Integración numérica paso a paso comparando la trayectoria ideal teórica vs la trayectoria aerodinámica real.
  3. Cálculo automático del alcance horizontal máximo, tiempo de vuelo y ángulo óptimo de tiro (que con fricción ya no es $45^\circ$).
  4. Gráfica comparativa superpuesta con telemetría de energía disipada por calor.
* **Stack Tecnológico:** Python (NumPy, Matplotlib o Streamlit).
* **Valor en Entrevistas Técnicas:** Conexión de física teórica con modelado matemático computacional y métodos numéricos de integración.

---

### Proyecto 3: Simulador de Péndulo Doble Caótico y Análisis de Conservación Energética
* **Problema a Resolver:** Un péndulo doble es el ejemplo prototípico del caos determinista: pequeñas variaciones en las condiciones iniciales generan trayectorias radicalmente divergentes gobernadas por la mecánica lagrangiana/rotacional.
* **Correspondencia con el PDF:**
  * Unidad 4: Dinámica rotacional, momento de inercia, conservación de energía mecánica y oscilaciones complejas.
* **Requerimientos Funcionales:**
  1. Formular las ecuaciones de movimiento para dos masas articuladas con longitudes $l_1, l_2$ y masas $m_1, m_2$.
  2. Resolver numéricamente el sistema mediante el método de Runge-Kutta de 4to orden (RK4).
  3. Dibujar la traza del extremo inferior creando atractores visuales en el plano.
  4. Monitorear la suma de energía cinética $T$ y potencial $V$ para verificar que el error de integración no viole el principio de conservación de la energía.
* **Stack Tecnológico:** Python (Matplotlib Animation / Pygame) o Web Canvas.
