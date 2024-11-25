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
