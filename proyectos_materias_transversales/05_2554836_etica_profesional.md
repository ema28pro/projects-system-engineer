# 2554836 – Ética Profesional

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Ética Profesional
* **Código de Curso:** 2554836
* **Nivel:** 8 / Profesional Terminal
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Formación Socio-Humanística y Profesional
* **Créditos Académicos:** 2
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial
* **Marcos Reguladores:** Código de Ética de la Ingeniería en Colombia (Ley 842 de 2003 / COPNIA), Código de Ética y Práctica Profesional de la ACM/IEEE-CS.

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Eje 1: Ética y Ética Profesional**
   * Moralidad, ética y deontología profesional.
   * Responsabilidad social y técnica del ingeniero de sistemas ante la sociedad y el medio ambiente.
   * Los Códigos de Ética formales: **Ley 842 de 2003** (régimen disciplinario y ejercicio legal de la profesión en Colombia) y el **Código de Ética de ACM / IEEE**.
2. **Eje 2: Lo Legítimo vs lo Legal**
   * La distinción entre cumplimiento legal y legitimidad moral.
   * Imperativos categóricos kantianos y dilemas éticos morales en el ejercicio profesional.
   * La objeción de conciencia y la denuncia de irregularidades (*Whistleblowing*).
3. **Eje 3: Avance Tecnológico vs Ética Profesional (Dilemas Contemporáneos)**
   * Sesgos algorítmicos y discriminación automatizada en Inteligencia Artificial y Machine Learning.
   * Privacidad, consentimiento informado y explotación masiva de datos personales (vigilancia corporativa y estatal).
   * Ciberseguridad ofensiva, divulgación responsable de vulnerabilidades (*Responsible Disclosure*) y hacking ético.
   * Armas autónomas letales, desinformación sintética (Deepfakes) y propiedad intelectual en modelos fundacionales.
4. **Eje 4: Investigación y Análisis de Dilemas Morales en Ingeniería**
   * Metodologías estructuradas para el análisis y toma de decisiones éticas ante dilemas de software.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Framework de Auditoría de Sesgos Algorítmicos y Equidad (*Fairness in AI*)
* **Problema a Resolver:** Los modelos de Machine Learning utilizados para aprobar créditos bancarios o seleccionar personal reproducen y amplifican sesgos raciales, socioeconómicos y de género preexistentes en los datos de entrenamiento.
* **Correspondencia con el PDF:**
  * Ejes 1 y 3: Ética aplicada al avance tecnológico, responsabilidad profesional según el código ACM/IEEE y justicia algorítmica.
* **Requerimientos Funcionales:**
  1. Tomar un dataset con atributos protegidos (género, etnia, edad, ej. *Adult Census* o *German Credit Data*).
  2. Implementar métricas cuantitativas de equidad algorítmica:
     * *Demographic Parity* (Paridad Demográfica).
     * *Equalized Odds* (Igualdad de Oportunidades / Tasa de Falsos Positivos uniforme).
     * *Disparate Impact Ratio*.
  3. Aplicar técnicas de mitigación de sesgo (preprocesamiento con reponderación o postprocesamiento de umbrales calibrados).
  4. Generar un **Informe de Impacto Ético y Auditoría Algorítmica** que dictamine formalmente si el modelo es apto para producción bajo principios éticos.
* **Stack Tecnológico:** Python, Fairlearn / AIF360, Scikit-learn, Matplotlib.
* **Valor en Entrevistas Técnicas:** Esencial para roles de IA Responsable (*Responsible AI Specialist*), Machine Learning Engineer y Data Scientist Senior.

---

### Proyecto 2: Dictamen Pericial Técnico y Ético sobre un Desastre de Software Histórico
* **Problema a Resolver:** Analizar desde la perspectiva de la Ley 842 de 2003 (COPNIA) y el código ACM/IEEE la cadena de decisiones que provocó un desastre por negligencia técnica (ej. Therac-25, Boeing 737 MAX MCAS, o la crisis del software de correos del Reino Unido Horizon de Fujitsu).
* **Correspondencia con el PDF:**
  * Ejes 1, 2 y 4: Régimen de faltas contra la ética profesional, presiones organizacionales vs código de honor y responsabilidad penal/civil del ingeniero.
* **Entregables Concretos:**
  1. Reconstrucción técnica del bug o falla arquitectónica causante del incidente.
  2. Identificación de los artículos específicos de la **Ley 842 de 2003** y principios de la **ACM/IEEE** que fueron violados por los líderes y desarrolladores.
  3. Protocolo de contingencia ética (*Ethical Escalation Protocol*): Qué debió hacer un ingeniero ante presiones de la gerencia para desplegar software no probado.
* **Formato:** Dictamen pericial estructurado en PDF.
