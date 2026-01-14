# 📂 AERO-RISK: Datos y Código de Análisis (Simulación)
[![DOI](https://zenodo.org/badge/1134353214.svg)](https://doi.org/10.5281/zenodo.18247133)

Este repositorio contiene el conjunto de datos, el código de generación y el pipeline de análisis estadístico para el proyecto **AERO-RISK**. El estudio investiga el impacto de la práctica previa en la toma de decisiones bajo riesgo (aversión a la incertidumbre vs. aversión al riesgo) utilizando una tarea de lanzamiento de aviones de papel.

> **Nota:** Los datos contenidos en este repositorio son **datos sintéticos (simulados)** generados computacionalmente para propósitos de demostración y reproducibilidad del flujo de trabajo científico.

## 🗂 Estructura del Repositorio

El flujo de trabajo se divide en tres componentes principales:

### 1. Generación de Datos (`01_data_generator.ipynb`)
Script en Python encargado de crear el conjunto de datos simulado.
* **Función:** Genera participantes virtuales (N=128) y asigna aleatoriamente condiciones (Control vs. Tratamiento).
* **Parámetros:** Simula una distribución normal basada en la hipótesis del estudio (Media Tratamiento > Media Control).
* **Reproducibilidad:** Utiliza una semilla fija (`np.random.seed(42)`) para garantizar que la simulación siempre produzca los mismos datos "aleatorios".

### 2. Datos Crudos (`aero_risk_128.csv`)
El conjunto de datos resultante en formato abierto (CSV). No ha sufrido manipulaciones manuales.
* **Total de registros:** 128 participantes.
* **Diccionario de Datos:**
    * `id_participante`: Identificador único y anónimo (ej. P001).
    * `grupo`: Variable independiente. Valores: "Control" (sin práctica) o "Tratamiento" (con práctica).
    * `distancia_apuesta_cm`: Variable dependiente. Distancia en centímetros que el participante apostó que alcanzaría.

### 3. Pipeline de Análisis (`02_analysis_pipeline.ipynb`)
Cuaderno de código que ingesta los datos crudos y ejecuta la inferencia estadística.
* **Carga:** Lee `aero_risk_128.csv` directamente desde este repositorio.
* **Estadística:** Verifica supuestos (Levene) y ejecuta una prueba T de Student para muestras independientes. Calcula el tamaño del efecto (d de Cohen).
* **Visualización:** Genera gráficos de caja (Boxplots) y enjambre (Swarmplots) para visualizar la distribución.

---

## 🚀 Instrucciones de Reproducción

Para replicar los resultados de este estudio caso práctico:

1.  **Opción A (Nube - Recomendado):** Abra el archivo `02_analysis_pipeline.ipynb` y haga clic en el botón "Open in Colab". El script descargará automáticamente los datos del repositorio y ejecutará el análisis.
2.  **Opción B (Local):**
    * Clone este repositorio.
    * Instale las dependencias: `pip install pandas numpy seaborn matplotlib scipy`
    * Ejecute primero el generador (opcional) o directamente el análisis.

## 🛠 Requisitos del Sistema
El código ha sido probado en **Python 3.8+** con las siguientes librerías:
* `pandas` (Manipulación de datos)
* `numpy` (Cálculo numérico)
* `scipy` (Pruebas estadísticas)
* `seaborn` & `matplotlib` (Visualización)

## 📄 Licencia y Citación
Este conjunto de datos y código se libera bajo la licencia **MIT**. Si utiliza este material, por favor cite:

> Alfonso, A. (2026). *AERO-RISK: Reproducible Workflow for Risk Taking Experiments*. GitHub Repository.
