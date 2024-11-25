# Conjunto de datos
El conjunto de datos utilizado en este proyecto contiene información detallada sobre las escuelas primarias del estado de Veracruz. Estos datos provienen de registros oficiales que incluyen características organizacionales, geográficas y de recursos de los Centros de Trabajo (CT). A continuación, se describe cada uno de los elementos clave del conjunto de datos:

## Columnas Principales
CCT (Clave del Centro de Trabajo): Identificador único para cada escuela primaria. Esta columna es esencial para vincular información entre diferentes bases de datos.
1. NOMBRE: Nombre oficial de la escuela primaria, según los registros educativos.
2. INMUEBLE_C_NOM_MUN: Nombre del municipio donde se encuentra ubicado el CT.
3. INMUEBLE_LATITUD: Coordenada geográfica (latitud) que indica la ubicación exacta de la escuela.
4. INMUEBLE_LONGITUD: Coordenada geográfica (longitud) que indica la ubicación exacta de la escuela.
5. TIPO_ORG_DOCENTE: Tipo de organización docente de la escuela. Puede ser:
6. MULTIGRADO: Un docente atiende múltiples grados simultáneamente.
7. COMPLETA: Cada grado cuenta con un docente asignado.
8. INCOMPLETA: No se atienden todos los grados en la escuela.
9. TIPO_ORG_ALUMNOS: Tipo de organización de los alumnos, indicando si la escuela es completa o incompleta en términos de grados atendidos.
10. DOC_TOT: Número total de docentes asignados a la escuela.

## Información Geográfica
Este conjunto de datos incluye coordenadas geográficas (latitud y longitud) que permiten georreferenciar cada escuela primaria. Esta información es fundamental para realizar análisis geográficos y visualizaciones, como mapas interactivos que muestran la distribución de los CT en el estado.

## Variables Contextuales
1. MUNICIPIO: Nombre del municipio al que pertenece cada CT.
2. ENTIDAD: Código de la entidad federativa (en este caso, Veracruz está representado con el código 30).
3. N_ENTIDAD: Nombre de la entidad federativa (Veracruz).

## Cantidad de Registros
El conjunto de datos incluye un total de:

1. Número total de CT: Representa el número de escuelas primarias registradas en el estado de Veracruz.
2. Número de municipios: Indica cuántos municipios están representados en el conjunto de datos.

# Propósitos del Conjunto de Datos
El conjunto de datos es utilizado para:

## Análisis descriptivo:
1. Distribución de escuelas por municipio.
2. Caracterización de tipos de organización docente.

## Análisis geográfico:
1. Visualización de la ubicación exacta de los CT.
2. Identificación de municipios con mayor o menor densidad de escuelas.

## Identificación de disparidades:
1. Comparación de recursos asignados entre escuelas completas, incompletas y multigrado.
2. Evaluación de necesidades en municipios rurales y marginados.

[🏠 Menú](README.md)
