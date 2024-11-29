```python
import pandas as pd

# Cargar el archivo combinado
df = pd.read_csv('/Users/salida23/Desktop/Datos/archivo_completo.csv', encoding='ISO-8859-1', low_memory=False)

# Eliminar filas con valores faltantes en columnas clave
df = df.dropna(subset=['INMUEBLE_C_NOM_MUN', 'DOC_TOT', 'ING_T'])

# Calcular las métricas por municipio
tabla_ordenada = df.groupby('INMUEBLE_C_NOM_MUN').agg(
    Numero_Escuelas=('CV_CCT', 'count'),
    Total_Docentes=('DOC_TOT', 'sum'),
    Total_Alumnos=('ING_T', 'sum')
).reset_index()

# Ordenar de menor a mayor por número de escuelas
tabla_ordenada = tabla_ordenada.sort_values(by='Numero_Escuelas', ascending=True)

# Mostrar la tabla en la terminal
print("Tabla de distribución de escuelas por municipio con métricas adicionales:")
print(tabla_ordenada)

# Guardar la tabla como archivo Markdown
tabla_ordenada.to_markdown('/Users/salida23/Desktop/Datos/tabla_escuelas_por_municipio.md', index=False, tablefmt='github')
print("Tabla guardada como 'tabla_escuelas_por_municipio.md'.")```

