📡 Proyecto ConnectaTel — Análisis de Clientes y Segmentación

Objetivo del Proyecto

Este proyecto tiene como propósito evaluar el comportamiento de los clientes de ConnectaTel, una empresa de telecomunicaciones en Latinoamérica, a partir de datos registrados hasta el año 2024.

El análisis busca:


Construir un perfil estadístico de los usuarios.
Detectar comportamientos atípicos (outliers) en el consumo.
Crear segmentos de clientes por nivel de uso y rango de edad.
Identificar patrones de consumo que permitan diseñar estrategias de retención y mejorar los planes ofrecidos.



Datasets Utilizados

El análisis trabaja con tres archivos CSV ubicados en la carpeta /datasets/:

ArchivoDescripciónplans.csvInformación de los planes disponibles: precio, minutos incluidos, GB incluidos y costo por excedente.users_latam.csvDatos de los clientes: edad, ciudad, fecha de registro, plan contratado y estado de churn.usage.csvDetalle del uso real de servicios por usuario: llamadas (duración en minutos) y mensajes de texto.


Etapas del Análisis

El notebook está organizado en 8 pasos:

Paso 1 — Carga y exploración inicial
Importación de librerías (pandas, seaborn, matplotlib, numpy), carga de los tres datasets y revisión preliminar de estructura, tipos de datos y dimensiones.

Paso 2 — Identificación de problemas de calidad
Detección de valores nulos (por columna y en proporción), identificación de valores inválidos o sentinels (ej. edad -999, ciudades marcadas como "?"), y revisión de columnas de fecha para detectar años fuera de rango.

Paso 3 — Limpieza básica de datos
Corrección de sentinels: reemplazo de -999 en age por la mediana, sustitución de "?" en city por NaN, y marcado como nulas de fechas imposibles. Verificación de nulos estructurales (MAR) en duration y length.

Paso 4 — Estadísticas de uso por usuario
Construcción de una tabla agregada por user_id con el total de mensajes, llamadas y minutos de llamada. Fusión con el dataset de usuarios para obtener un perfil unificado (user_profile). Resumen estadístico de variables numéricas y distribución del tipo de plan.

Paso 5 — Visualización de distribuciones y outliers
Histogramas por tipo de plan para age, cant_mensajes, cant_llamadas y cant_minutos_llamada. Detección visual de outliers con boxplots y cálculo de límites mediante el método IQR para decidir si conservarlos o descartarlos.

Paso 6 — Segmentación de clientes
Creación de la columna grupo_uso (Bajo uso / Uso medio / Alto uso) según el volumen de llamadas y mensajes, y de grupo_edad (Joven / Adulto / Adulto Mayor) según la edad. Visualización de ambas segmentaciones con gráficos de conteo.

Paso 7 — Insight ejecutivo para stakeholders
Síntesis de hallazgos clave: diagnóstico de calidad de datos, perfil de cada segmento de cliente, identificación de los segmentos más valiosos, análisis de outliers de consumo y recomendaciones estratégicas (nuevo plan intermedio, paquetes anti-exceso, estrategia de retención anticipada).

Paso 8 — Publicación en GitHub
Instrucciones para subir el notebook y el README al repositorio, con opciones via interfaz web de GitHub y via Google Colab.


Cómo Ejecutar el Notebook

Opción A — Google Colab (recomendada)


Abre Google Colab.
Ve a File → Upload notebook y selecciona el archivo .ipynb.
Sube los datasets a la carpeta /datasets/ en el entorno de Colab, o monta Google Drive si los tienes almacenados ahí:


python   from google.colab import drive
   drive.mount('/content/drive')


Ajusta las rutas de carga si es necesario (por defecto apuntan a /datasets/).
Ejecuta todas las celdas en orden con Runtime → Run all.


Opción B — Entorno local (Jupyter)


Clona o descarga este repositorio.
Instala las dependencias necesarias:


bash   pip install pandas matplotlib seaborn numpy


Coloca los archivos CSV en una carpeta llamada datasets/ en el mismo directorio que el notebook.
Lanza Jupyter Notebook o JupyterLab:


bash   jupyter notebook


Abre el archivo .ipynb y ejecuta las celdas en orden.



Guía de Reproducción

Para garantizar que el análisis sea completamente reproducible, sigue estos pasos:


Clona el repositorio:


bash   git clone <URL_DEL_REPOSITORIO>
   cd <NOMBRE_DEL_REPOSITORIO>


Verifica que los datasets estén presentes en la carpeta /datasets/:

plans.csv
users_latam.csv
usage.csv



Instala las dependencias (si trabajas en local):


bash   pip install pandas matplotlib seaborn numpy


Ejecuta el notebook de principio a fin, en orden secuencial. Cada paso depende del anterior: la limpieza del Paso 3 es requisito para la agregación del Paso 4, y así sucesivamente.
No modifiques las celdas de limpieza (Paso 3) sin revisar el impacto aguas abajo. Los valores imputados y los filtros aplicados afectan directamente las estadísticas y los segmentos generados en pasos posteriores.
Versión de Python recomendada: 3.9 o superior.



Estructura del Repositorio

├── datasets/
│   ├── plans.csv
│   ├── users_latam.csv
│   └── usage.csv
├── S7_Version-Estudiante-Project-ConnectaTel.ipynb
└── README.md


Tecnologías Utilizadas


Python 3.9+
pandas
NumPy
Matplotlib
Seaborn



Enlace al Repositorio

LINK a tu repo aquí
