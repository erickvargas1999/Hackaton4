# HACKATÓN IV: TALEND, BIGQUERY & LOOKER STUDIO

![BigQuery](https://img.shields.io/badge/Google_BigQuery-4285F4?style=for-the-badge&logo=google-bigquery&logoColor=white)
![Talend](https://img.shields.io/badge/Talend-FF0000?style=for-the-badge&logo=talend&logoColor=white)

## 1. Descripción del Proyecto
Este repositorio contiene la solución de ingeniería de datos desarrollada para la **Hackatón IV**. El proyecto se enfoca en la consolidación y análisis de indicadores socioeconómicos globales del Banco Mundial y datos de comercio exterior. La arquitectura está diseñada para aprovechar la potencia de cómputo de **Google BigQuery**, optimizando la carga de datos mediante el procesamiento directo en el Data Warehouse.

## 2. Arquitectura de la Solución
El pipeline de datos sigue un flujo optimizado para la nube:
1. **Ingesta:** Carga de archivos maestros y transaccionales a la capa de `staging` en BigQuery.
2. **Procesamiento Push-down:** Delegación de la lógica de transformación a BigQuery mediante componentes `tBigQuerySQLRow`.
3. **Almacenamiento:** Modelo dimensional en estrella (Star Schema).
4. **Visualización:** Consumo de datos mediante Looker Studio.

## 3. Modelo Dimensional
El diseño del Data Warehouse (`dw_hackaton`) consta de:
- **Tablas de Hechos:** `fact_comercio`, `fact_indicadores`.
- **Dimensiones:** `dim_pais`, `dim_producto`, `dim_indicador`, `dim_tiempo`.

## 4. Lógica Incremental y Código
Para evitar la duplicidad de información y optimizar costos, se implementó una lógica de **Carga Incremental**. El sistema identifica periodos ya procesados y solo inserta registros nuevos.
