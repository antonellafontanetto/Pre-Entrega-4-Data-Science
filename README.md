# 🛢️ Proyecto 4x4 YPF - Análisis de Vaca Muerta
# Pre-Entrega 4 - Data Science
# Grupo 3 - Fundación YPF / Programa Ingenias+

# Introducción

El proyecto 4x4 de YPF tiene como objetivo principal cuadruplicar la producción de la compañía en los próximos 4 años, enfocándose en la eficiencia operativa, la generación de valor y la concentración de esfuerzos en los activos más rentables a corto plazo, como Vaca Muerta, la principal cuenca petrolera del país.

Este trabajo busca analizar el crecimiento de la producción de petróleo y gas en la cuenca neuquina desde el año 2021 en adelante, considerando exclusivamente los datos correspondientes a YPF S.A.. El análisis se basa en indicadores clave como la producción no convencional, las principales 5 áreas de concesiones y el subtipo de recurso producido, ya sea shale o tight en los últimos años.

En el análisis, se busca aportar evidencia empírica sobre la evolución y proyección del potencial de expansión de YPF en Vaca Muerta, en línea con los objetivos planteados en su plan estratégico 4x4.

# Objetivo

El objetivo del proyecto es analizar y predecir el crecimiento de la producción de petróleo y gas por parte de YPF S.A. en la cuenca neuquina, evaluando el impacto de diferentes variables relacionadas con la actividad extractiva y operativa.

# Integrantes - Grupo 3

Este proyecto fue desarrollado por el Grupo 3 del curso de Data Science de Fundación YPF en el marco del programa Ingenias+, que busca incorporar más mujeres al mundo de la programación.

* Cyntia Nasabun – Diplomada en Análisis de Datos e IA, IFES, Neuquén. 

* Antonella Fontanetto – Licenciada en Economía, Universidad de Buenos Aires

# Datasets utilizados

Los datos provienen de fuentes públicas oficiales del Gobierno Nacional y de la Provincia del Neuquén:

* Producción de Pozos de Petróleo y Gas http://datos.energia.gob.ar/dataset/produccion-de-petroleo-y-gas-por-pozo

Mapas y documentos complementarios:

* Mapa Energía Río Negro https://mapa.rionegro.com.ar/energia

* Distribución de Fluidos – Energía Neuquén https://www.energianeuquen.gob.ar/distribucion-de-fluidos/

* Línea estratégica YPF 4x4 https://www.rystadenergy.com/news/vaca-muerta-smashes-crude-output-record-in-3q

* Presentación IR Day 2025 – YPF https://inversores.ypf.com/documents/presentaciones/YPF-IR-DAY-2025-presentation.pdf

* YPF – Mayo 2024 – IAméricas https://iamericas.org/2024/05/YPF_Horacio-Marin_Mesa-Redonda_Mayo-8-presentation.pdf

* Análisis potencial exportador de Vaca Muerta – La Nación  https://www.lanacion.com.ar/el-potencial-exportador-vaca-muerta-el-planparaalcanzarlos30milmillonesdedolares

# Estructura del repositorio

📁

├── data/           # Datasets procesados

├── notebooks/      # Notebooks (diferentes versiones estudiadas)

├── README.md       # Este archivo

# Metodología

La metodología implementada en el proyecto está relacionada con la búsqueda minuciosa de información relevante para el desarrollo del mismo, en función de las respuestas a nuestro modelo predictivo. Teniendo como eje principal la proyección de la producción de petróleo y gas en Vaca Muerta por parte de YPF S.A. para los próximos años.

En el análisis se implementaron varios modelos de aprendizaje no supervisado, es decir, modelos que aprenden de datos no etiquetados del pasado para luego hacer predicciones, de esta manera estos modelos nos permiten dar soporte a decisiones estratégicas para la compañía.

Los modelos utilizados fueron:

* KMeans: Algoritmo de clustering que agrupa los datos en k grupos, minimizando la distancia entre los puntos y el centroide del cluster. Requiere definir el número de clusters previamente.

* MeanShift: Algoritmo de clustering que no necesita definir k previamente. Agrupa puntos buscando áreas de mayor densidad, ajustando dinámicamente el número de clusters.

* TimeSeries KMeans: Versión de KMeans diseñada para datos temporales. Agrupa series de tiempo según su forma o patrón de comportamiento a lo largo del tiempo, usando métricas como DTW o Euclídea.

* DBSCAN: Algoritmo basado en densidad. Agrupa puntos cercanos y densamente conectados, y clasifica como ruido a los puntos que no pertenecen a ningún grupo. No requiere especificar el número de clusters.

* PCA (Análisis de Componentes Principales): Técnica de reducción de dimensionalidad. Transforma los datos originales en nuevas variables (componentes) que conservan la mayor parte de la varianza con menos dimensiones, útil para visualizar o preprocesar datos.

Además por cada modelo se implementó la utilización y cálculo de métricas para corroborar que tan bien el modelo podía predecir nuestro objetivo. Las métricas utilizadas fueron:

* Silhouette Score: Mide qué tan bien están definidos los clusters: combina la cohesión interna (qué tan cerca están los puntos de su propio grupo) y la separación externa (qué tan lejos están de otros clusters).
Rango: de -1 a 1 (valores cercanos a 1 son mejores).

* Davies-Bouldin Index: Evalúa la similitud entre clusters, comparando la distancia entre ellos y su dispersión interna.
Rango: positivo, y valores más bajos indican mejor separación entre clusters.

* Calinski-Harabasz Index (o Variance Ratio Criterion): Mide la proporción entre la dispersión entre clusters y dentro de los clusters. Valores más altos indican una mejor definición de los grupos.

* Inercia (Within-cluster sum of squares): Utilizada en KMeans, mide la suma de las distancias cuadradas entre los puntos y el centroide del cluster. A menor inercia, mejor ajuste (aunque puede sobreajustar si hay demasiados clusters).

# Breve análisis de cada versión estudiada

* Versión con outliers: se decidió aplicar los diferentes modelos anteriores para el dataframe completo con outliers (prod_encoded_df) y así analizar cuales fueron los resultados de las métricas. En este caso el coeficiente de determinación (R²) resultó ser de 60% lo que indica que debería reajustarse el modelo ya que no es un resultado óptimo para predecir la proyección futura de la producción de petróleo y gas.

* Versión con datos agrupados: para esta versión se trabajó con un un dataset con los datos agrupados por mes de la producción de petróleo y gas (prod_encoded_df(2)) y de esta manera se aplicaron todos los modelos de aprendizaje no supervisado. En este caso para el modelo KMeans 

# Herramientas utilizadas 

Lenguaje: Python 3.10+

Librerías:

Tercera entrega

* Análisis exploratorio de datos: Nunpy, Pandas

* Modelado: RandomForestRegressor,SVR, XGBRegressor,GridSearchCV, MultiOutputRegressor, Prophet, train_test_split, mean_absolute_error

* Visualización: matplotlib, seaborn, plotly, contextily, scipy

* Otros: jupyter, openpyxl, google colab, GitHub
