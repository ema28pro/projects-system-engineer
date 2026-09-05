# 2554509 – Modelos y Simulación de Sistemas I (MLOps & Ciclo de Vida Predictivo)

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Modelos y Simulación de Sistemas I
* **Código de Curso:** 2554509
* **Nivel:** 6
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 3
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial
* **Enfoque Principal del Curso:** Ingeniería de Machine Learning en Producción (**MLOps**), empaquetado, exposición de servicios de inferencia, re-entrenamiento automatizado y monitoreo de deriva de modelos (*Drift*).

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Unidad 1: Implementación de Modelos Predictivos**
   * Metodología del ciclo de vida del aprendizaje automático.
   * Ingesta, validación y preparación de datos; preprocesamiento estructurado (*Pipelines* de Scikit-Learn).
   * Entrenamiento y ajuste de hiperparámetros de modelos de regresión y clasificación.
   * Métricas de desempeño en inferencia: precisión, recall, F1-score, ROC-AUC, RMSE, MAE.
   * Registro y control de experimentos: seguimiento de parámetros y métricas.
2. **Unidad 2: Encapsulación de Modelos Predictivos**
   * Serialización y versionado de modelos: Pickle, Joblib y formatos estandarizados independientes (**ONNX - Open Neural Network Exchange**).
   * Empaquetado en artefactos de software reproducibles.
   * Contenedorización de entornos de inferencia mediante **Docker**.
   * Gestión de dependencias estrictas y prevención del "Dependency Hell" en entornos de producción.
3. **Unidad 3: Exposición de Servicios Predictivos y de Re-entrenamiento**
   * Creación de APIs de inferencia de baja latencia con **FastAPI**.
   * Inferencia en tiempo real (petición/respuesta) vs inferencia por lotes (*Batch Prediction*).
   * Arquitectura de re-entrenamiento desacoplada: procesamiento de tareas en segundo plano usando colas asíncronas (**Celery + Redis**).
   * Validación rigurosa de contratos de datos de entrada mediante esquemas **Pydantic**.
4. **Unidad 4: Monitoreo y Gestión del Modelo en Producción**
   * Concepto de degradación de modelos en el tiempo:
     * **Data Drift (Deriva de Datos):** cambios en la distribución estadística de las variables predictoras ($P(X)$).
     * **Concept Drift (Deriva de Concepto):** cambios en la relación matemática entre las variables y el objetivo ($P(Y|X)$).
   * Detección estadística de deriva: pruebas de Kolmogorov-Smirnov, divergencia Kullback-Leibler y Population Stability Index (PSI).
   * Métricas operativas de la API: latencia p95/p99, tasa de errores HTTP y consumo de recursos CPU/RAM.
   * Estrategias de despliegue de modelos: despliegue Canary (*Canary Deployment*) y pruebas Shadow (*Shadow Testing*).

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Plataforma End-to-End de MLOps: Inferencia con FastAPI, Re-entrenamiento con Celery y Monitoreo de Data Drift
* **Problema a Resolver:** En la industria, el 85% de los modelos de Machine Learning nunca llegan a producción o fallan en silencio cuando los datos del mundo real cambian. Se necesita una plataforma completa de ingeniería de MLOps que sirva predicciones con validación estricta, re-entrene en background y alerte si hay deriva de datos.
* **Correspondencia con el PDF:**
  * Unidades 1, 2, 3 y 4: Pipelines Scikit-Learn empaquetados en Docker, API REST con FastAPI, colas asíncronas de re-entrenamiento con Celery y detección estadística de Data Drift con Evidently AI.
* **Requerimientos Funcionales y Técnicos:**
  1. **Modelo Predictivo:** Clasificador de riesgo de fuga de clientes (*Customer Churn*) o detección de fraude bancario.
  2. **API de Inferencia (FastAPI):**
     * Endpoint `/predict`: recibe datos en JSON validados con Pydantic, ejecuta inferencia en < 20 ms y almacena las entradas en una base de datos de auditoría.
     * Endpoint `/health`: chequeo de estado y versión actual del modelo cargado en memoria.
  3. **Servicio de Re-entrenamiento Asíncrono (Celery + Redis):**
     * Endpoint `/retrain`: desencadena una tarea en background que ingiere nuevos datos, entrena una nueva versión del modelo, compara métricas contra el modelo en producción y, si supera el umbral, actualiza el artefacto.
  4. **Monitoreo de Data Drift:**
     * Cronjob que analiza semanalmente los datos de entrada vs el conjunto de entrenamiento usando la librería `Evidently` o pruebas KS.
     * Generación automática de reportes HTML de deriva y envío de alertas (webhook / Slack) si el *drift score* supera el umbral crítico.
  5. **Contenedorización:** `docker-compose.yml` orquestando la API, el worker de Celery, Redis y PostgreSQL.
* **Stack Tecnológico:** Python 3.11, FastAPI, Pydantic, Scikit-learn, Celery, Redis, PostgreSQL, Evidently AI, Docker.
* **Estructura Sugerida:**
  ```text
  mlops-production-pipeline/
  ├── app/
  │   ├── api/routes.py           # Endpoints de predicción y reentrenamiento
  │   ├── core/config.py          # Configuraciones de entorno
  │   ├── ml/
  │   │   ├── pipeline.py         # Sklearn Pipeline serializado
  │   │   └── model_loader.py     # Carga segura del modelo
  │   ├── schemas/prediction.py   # Validación Pydantic
  │   └── workers/tasks.py        # Tareas asíncronas Celery
  ├── monitoring/
  │   └── drift_detector.py       # Pruebas KS y reportes Evidently
  ├── Dockerfile
  ├── docker-compose.yml
  └── README.md
  ```
* **Valor en Entrevistas Técnicas:** Es el proyecto más codiciado para roles de **Machine Learning Engineer (MLE)** y **MLOps Engineer**.

---

### Proyecto 2: Servidor de Inferencia Ultrarrápido con ONNX Runtime y Comparador de Formatos de Serialización
* **Problema a Resolver:** En entornos de tiempo real (vehículos autónomos, trading de alta frecuencia), la inferencia nativa de Python/Pickle tiene latencias altas y problemas de seguridad (ejecución remota de código en des-serialización).
* **Correspondencia con el PDF:**
  * Unidad 2 y 3: Formatos estandarizados de empaquetado (ONNX), inferencia de alto rendimiento y optimización de latencias.
* **Requerimientos Funcionales:**
  1. Entrenar un modelo de Deep Learning o Gradient Boosting (XGBoost/LightGBM).
  2. Convertir y optimizar el modelo al formato estandarizado **ONNX**.
  3. Desplegar un servicio de inferencia usando **ONNX Runtime** en C++ o Python y comparar métricas:
     * Latencia de inferencia por petición (Scikit-Learn nativo vs ONNX Runtime con aceleración multi-core).
     * Tamaño en disco del artefacto serializado.
     * Consumo pico de memoria RAM.
* **Stack Tecnológico:** Python, ONNX, ONNX Runtime, FastAPI.
