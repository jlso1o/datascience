# Modelamiento de datos
## Selección de variables:
En este proyecto, las variables seleccionadas provienen de los Centros de Trabajo (CT) en el sistema educativo de Veracruz y están enfocadas en describir la estructura y distribución de las escuelas primarias. Entre las principales variables destacan: municipio, que permite identificar la ubicación geográfica de los CT; número total de docentes (DOC_TOT), que refleja los recursos humanos disponibles; y número total de alumnos (TOTAL_ALUMNOS), que representa la demanda educativa en cada escuela. Adicionalmente, se incluyen variables organizacionales, como el tipo de organización docente (TIPO_ORG_DOCENTE) y el número total de escuelas por municipio (NUMERO_ESCUELAS), para analizar patrones en la distribución de recursos y características escolares. Estas variables se eligieron por su capacidad de describir tanto la capacidad operativa de las escuelas como la equidad en la asignación de recursos entre municipios.

## Descripción del modelo:
El modelo utilizado en este proyecto tiene como objetivo identificar patrones en las características organizacionales de las escuelas primarias. Para este propósito, se aplicará un modelo descriptivo combinado con técnicas de agrupamiento geográfico, específicamente K-Means Clustering. Este enfoque permite agrupar municipios y escuelas con características similares, utilizando como variables clave la cantidad de docentes, alumnos, y el tipo de organización docente. Al mismo tiempo, se genera una tabla dinámica para comparar municipios y un análisis geográfico que visualiza la densidad de escuelas por región. Este modelo no solo permite identificar disparidades en la asignación de recursos, sino que también proporciona información útil para diseñar políticas públicas enfocadas en áreas prioritarias

## Proceso de Modelamiento:
El proceso de modelamiento comenzó con la limpieza y preparación de los datos, asegurando que las columnas seleccionadas estuvieran completas y consistentes. Posteriormente, se calcularon métricas básicas, como el número total de escuelas, docentes y alumnos por municipio. Estas métricas se utilizaron tanto para generar una tabla dinámica como para alimentar el modelo de agrupamiento. El algoritmo K-Means fue entrenado utilizando las coordenadas geográficas (latitud y longitud) y el número de alumnos y docentes, permitiendo identificar grupos de municipios y escuelas con características similares. Además, se generaron gráficos descriptivos, como la distribución de escuelas por municipio y la caracterización de los tipos de organización docente, para complementar el análisis. Finalmente, se evaluó la consistencia de los clusters mediante técnicas de validación cruzada y se ajustaron los parámetros para garantizar que los resultados fueran significativos e interpretables.

El código fuente para la obtención descriptiva lo puedes encontrar aquí: [haz click para ir](https://jlso1o.github.io/datascience/proyectocd/codigo/tabla1)

## Implementación del modelo:
La implementación del modelo se llevó a cabo mediante herramientas de análisis de datos como Python, utilizando bibliotecas como Pandas, Scikit-learn y Folium. La tabla dinámica y los gráficos descriptivos se integraron en este espacio de GitHub para facilitar su acceso y visualización por parte de los interesados. 
Los resultados del modelo de agrupamiento se utilizaron para generar un mapa interactivo que muestra los clusters de escuelas por municipio, resaltando patrones relevantes en la distribución de recursos educativos. Este mapa proporciona una herramienta visual para que las autoridades educativas y otros actores puedan identificar rápidamente las áreas con mayores necesidades o desigualdades. El modelo y su implementación están diseñados para ser reproducibles, permitiendo actualizaciones regulares conforme se disponga de nuevos datos o cambien las prioridades educativas.

El código para la geolocalización de las escuelas primarias, lo puedes consultar:
[haz click para ir](https://jlso1o.github.io/datascience/proyectocd/codigo/geoposicion)

El código para la geolocalización en la Densidad de las escuelas lo puedes consultar:
[haz click para ir](https://jlso1o.github.io/datascience/proyectocd/codigo/densidadescuelas)

El código para la geolocalización en la Densidad en la relación docentes/alumnos de las escuelas lo puedes consultar:
[haz click para ir](https://jlso1o.github.io/datascience/proyectocd/codigo/densidadaludoc)

[🏠 Menú](README.md)|[➡ Adelante](resultados.md)
