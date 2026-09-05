# 2517450 – Cátedra de Formación Ciudadana y Constitucional

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Cátedra de Formación Ciudadana y Constitucional
* **Código de Curso:** 2517450
* **Nivel:** 2 / Transversal
* **Unidad Académica:** Facultad de Derecho y Ciencias Políticas
* **Área:** Formación Socio-Humanística
* **Créditos Académicos:** 2
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Eje 1: La Construcción de Ciudadanía(s) y el Estado Social de Derecho**
   * Concepto de ciudadanía crítica frente a la visión tradicional puramente jurídica.
   * Principios estructurales del Estado Social de Derecho en Colombia (dignidad humana, solidaridad, prevalencia del interés general).
   * La Constitución Política de 1991 como pacto de paz e inclusión social.
2. **Eje 2: Derechos Fundamentales, Colectivos y del Medio Ambiente**
   * Carta de derechos fundamentales (vida, igualdad, intimidad, libertad de expresión, debido proceso).
   * Derechos económicos, sociales y culturales (DESC) y derechos colectivos.
   * El derecho a la privacidad digital y protección de datos personales en el entorno tecnológico.
3. **Eje 3: Mecanismos Constitucionales de Protección Ciudadana y Participación**
   * Mecanismos de protección de derechos: **Acción de Tutela**, **Derecho de Petición (Art. 23)**, Acción Popular, Acción de Grupo y Hábeas Corpus.
   * Mecanismos de participación democrática: Voto, plebiscito, referendo, consulta popular, cabildo abierto e iniciativa popular normativa.
4. **Eje 4: Cultura de Paz, Memoria Histórica y Resolución de Conflictos**
   * Conflicto armado en Colombia, justicia transicional y construcción de memoria histórica.
   * Métodos alternativos de solución de conflictos (MASC: conciliación, mediación, arbitraje).

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Plataforma Web Cívica "DefiendeTusDerechos" (Generador Legaltech de Tutelas y Derechos de Petición)
* **Problema a Resolver:** Millones de ciudadanos colombianos no pueden acceder oportunamente a la justicia o a servicios de salud vitales por desconocimiento técnico de cómo redactar un Derecho de Petición o una Acción de Tutela.
* **Correspondencia con el PDF:**
  * Ejes 2 y 3: Derechos fundamentales (salud, educación, petición), Acción de Tutela y Derecho de Petición con sustento jurídico de la Constitución de 1991.
* **Requerimientos Funcionales:**
  1. Asistente interactivo tipo cuestionario que guía al ciudadano para tipificar su caso (ej. negación de medicamentos por EPS, falta de respuesta de una entidad pública, vulneración al debido proceso).
  2. Generación automática del documento formal en formato PDF descargable, incluyendo fundamentos jurídicos, jurisprudencia aplicable de la Corte Constitucional y solicitud formal de medidas cautelares.
  3. Guía interactiva paso a paso sobre cómo y dónde radicar el documento electrónica o presencialmente.
* **Stack Tecnológico:** TypeScript / React o Python (FastAPI/ReportLab).
* **Valor en Entrevistas Técnicas:** Un proyecto ejemplar de tecnología cívica (**CivicTech / LegalTech**) que demuestra impacto social directo.

---

### Proyecto 2: Observatorio Ciudadano de Transparencia y Contratación Pública (Datos Abiertos Colombia)
* **Problema a Resolver:** Fiscalizar el gasto público y promover el control ciudadano mediante la analítica de datos abiertos de contratación estatal (SECOP II).
* **Correspondencia con el PDF:**
  * Ejes 1 y 3: Control social de la gestión pública, veedurías ciudadanas y derecho al acceso a la información pública.
* **Requerimientos Funcionales:**
  1. Consumir la API oficial de Datos Abiertos de Colombia (`datos.gov.co` / Socrata API) sobre contratos estatales.
  2. Dashboard interactivo que filtra por entidad territorial, cuantía, contratista y modalidad de selección (licitación vs contratación directa).
  3. Detección automática de posibles alertas tempranas (ej. contratos con único proponente en vísperas electorales).
* **Stack Tecnológico:** Python (Pandas, Plotly / Dash) o React con gráficos interactivos.
