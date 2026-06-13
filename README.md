# 📡 Proyecto ConnectaTel — Análisis de Clientes y Segmentación

## Objetivo del Proyecto

Este proyecto tiene como propósito evaluar el **comportamiento de los clientes** de ConnectaTel, una empresa de telecomunicaciones en Latinoamérica, a partir de datos registrados hasta el año 2024.

El análisis busca:

- Construir un **perfil estadístico** de los usuarios.
- Detectar **comportamientos atípicos** (outliers) en el consumo.
- Crear **segmentos de clientes** por nivel de uso y rango de edad.
- Identificar **patrones de consumo** que permitan diseñar estrategias de retención y mejorar los planes ofrecidos.

---

## Datasets Utilizados

El análisis trabaja con tres archivos CSV:

| Archivo | Descripción |
|---|---|
| `plans.csv` | Información de los planes disponibles: precio, minutos incluidos, GB incluidos y costo por excedente. |
| `users_latam.csv` | Datos de los clientes: edad, ciudad, fecha de registro, plan contratado y estado de churn. |
| `usage.csv` | Detalle del uso real de servicios por usuario: llamadas (duración en minutos) y mensajes de texto. |

---

## Etapas del Análisis

**Paso 1 — Carga y exploración inicial**
Importación de librerías, carga de los tres datasets y revisión preliminar de estructura, tipos de datos y dimensiones.

**Paso 2 — Identificación de problemas de calidad**
Detección de valores nulos, identificación de valores inválidos o *sentinels* (ej. edad `-999`, ciudades `"?"`) y revisión de fechas fuera de rango.

**Paso 3 — Limpieza básica de datos**
Reemplazo de `-999` en `age` por la mediana, sustitución de `"?"` en `city` por `NaN`, marcado de fechas imposibles como nulas y verificación de nulos estructurales en `duration` y `length`.

**Paso 4 — Estadísticas de uso por usuario**
Tabla agregada por `user_id` con total de mensajes, llamadas y minutos. Fusión con el dataset de usuarios para obtener un perfil unificado (`user_profile`).

**Paso 5 — Visualización de distribuciones y outliers**
Histogramas por tipo de plan y boxplots para detectar outliers. Cálculo de límites con el método IQR para decidir si conservarlos.

**Paso 6 — Segmentación de clientes**
Columna `grupo_uso` (Bajo uso / Uso medio / Alto uso) y `grupo_edad` (Joven / Adulto / Adulto Mayor), con visualización de cada segmento.

**Paso 7 — Insight ejecutivo para stakeholders**
Síntesis de hallazgos: diagnóstico de calidad, perfil por segmento, outliers de consumo y recomendaciones estratégicas (plan intermedio, paquetes anti-exceso, retención anticipada).

---

## Cómo Ejecutar el Notebook

### Opción A — Google Colab (recomendada)

1. Abre [Google Colab](https://colab.research.google.com/).
2. Ve a **File → Upload notebook** y selecciona el archivo `.ipynb`.
3. Sube los datasets a la carpeta `/datasets/` o monta Google Drive:
```python
   from google.colab import drive
   drive.mount('/content/drive')
```
4. Ejecuta todas las celdas con **Runtime → Run all**.

### Opción B — Entorno local (Jupyter)

1. Instala las dependencias:
```bash
   pip install pandas matplotlib seaborn numpy
```
2. Coloca los CSV en una carpeta `datasets/` junto al notebook.
3. Lanza Jupyter y ejecuta las celdas en orden.

---

## Guía de Reproducción

1. Clona el repositorio:
```bash
   git clone <URL_DEL_REPOSITORIO>
```
2. Verifica que los tres datasets estén en `/datasets/`.
3. Ejecuta el notebook **en orden secuencial** — cada paso depende del anterior.
4. No modifiques las celdas de limpieza (Paso 3) sin revisar el impacto en los pasos siguientes.

---

## Tecnologías Utilizadas

- Python 3.9+
- pandas · NumPy · Matplotlib · Seaborn
