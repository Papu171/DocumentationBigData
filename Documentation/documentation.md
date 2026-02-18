#  Data Engineering & Cloud Infrastructure Stack

Este repositorio contiene documentación y recursos sobre conceptos fundamentales de **Big Data**, servicios de **AWS** y herramientas de **orquestación y desarrollo**.

![Build Status](https://img.shields.io/badge/build-passing-brightgreen)
![AWS](https://img.shields.io/badge/Cloud-AWS-orange)
![Spark](https://img.shields.io/badge/Data-Spark-red)
![Docker](https://img.shields.io/badge/Container-Docker-blue)

---

##  Tabla de Contenidos
1. [Conceptos de Big Data](#-conceptos-de-big-data)
    - [Las 5 Vs](#las-5-vs-del-big-data)
    - [ETL vs ELT](#-etl-vs-elt)
2. [Ecosistema AWS](#-ecosistema-aws)
3. [Herramientas de Desarrollo y Procesamiento](#-herramientas-de-desarrollo-y-procesamiento)

---

##  Conceptos de Big Data

### Las 5 V's del Big Data
Definición de las características esenciales para manejar grandes volúmenes de datos:

| Concepto | Descripción |
| :--- | :--- |
| **Volumen** | La cantidad masiva de datos generados (TB, PB, ZB). |
| **Velocidad** | La rapidez con la que los datos se generan y procesan (Streaming vs Batch). |
| **Variedad** | Diferentes formatos de datos: Estructurados (SQL), Semiestructurados (JSON/XML) y No estructurados (Video/Audio). |
| **Veracidad** | La calidad y confiabilidad de los datos (limpieza de ruido y anomalías). |
| **Valor** | La capacidad de transformar los datos en información útil para el negocio. |

###  ETL vs ELT
Diferencias clave en las arquitecturas de integración de datos:

#### **ETL (Extract, Transform, Load)**
*Enfoque tradicional (Data Warehouses).*
1. **Extract:** Se extraen datos de la fuente.
2. **Transform:** Se procesan y limpian en un servidor intermedio.
3. **Load:** Se cargan en el destino final.
* **Uso ideal:** Cuando el almacenamiento es costoso o se requiere estricta limpieza previa.

#### **ELT (Extract, Load, Transform)**
*Enfoque moderno (Data Lakes / Cloud).*
1. **Extract:** Se extraen datos.
2. **Load:** Se cargan tal cual (raw) en el destino (ej. S3).
3. **Transform:** Las transformaciones se ejecutan dentro del destino (ej. usando Athena o Redshift).
* **Uso ideal:** Big Data en la nube, flexibilidad y velocidad de ingestión.

---

##  Ecosistema AWS

###  Seguridad y Gobierno
* **IAM (Identity and Access Management):**
  * Controla **quién** (autenticación) puede hacer **qué** (autorización) en AWS.
  * Maneja Usuarios, Roles, Grupos y Políticas (JSON).
* **KMS (Key Management Service):**
  * Servicio gestionado para crear y controlar las claves de cifrado.
  * Se usa para encriptar datos en reposo (S3, EBS) y en tránsito.

###  Procesamiento y Catálogo
* **AWS Glue:**
  * Servicio de integración de datos *serverless*.
  * **Crawler:** Escanea datos en S3 para inferir esquemas.
  * **Data Catalog:** Metastore compatible con Hive.
  * **Jobs:** Ejecuta scripts de Spark/Python para ETL.
* **Amazon Athena:**
  * Servicio de consultas interactivo *serverless*.
  * Permite analizar datos directamente en **Amazon S3** usando **SQL estándar**.
  * No requiere cargar datos en bases de datos (Schema-on-Read).

---

##  Herramientas de Desarrollo y Procesamiento

###  Apache Spark
Motor de análisis unificado para procesamiento de datos a gran escala.
* **Características:** Procesamiento en memoria (más rápido que MapReduce).
* **Componentes:** Spark SQL, Streaming, MLlib (Machine Learning).
* **Lenguajes:** Scala, Python (PySpark), Java, R.

### Docker
Plataforma para desarrollar, enviar y ejecutar aplicaciones en **contenedores**.
* **Aislamiento:** Empaqueta código y dependencias para que funcione igual en cualquier entorno.
* **Uso en Data:** Despliegue reproducible de modelos de ML o entornos de Spark.

```bash
# Ejemplo básico de Docker
docker run -p 8888:8888 jupyter/pyspark-notebook