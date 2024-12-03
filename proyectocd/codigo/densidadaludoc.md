### En este apartado se muestra el código realizado en phyton para la geolocalización de la densidad en la relación docentes/alunos de las escuelas.

```python
import pandas as pd
import folium

# Cargar el archivo combinado
df = pd.read_csv('/Users/salida23/Desktop/Datos/archivo_completo.csv', encoding='ISO-8859-1', low_memory=False)

# Eliminar filas con valores faltantes en municipio, docentes, alumnos, latitud y longitud
df = df.dropna(subset=['INMUEBLE_C_NOM_MUN', 'DOC_TOT', 'ING_T', 'INMUEBLE_LATITUD', 'INMUEBLE_LONGITUD'])

# Calcular métricas por municipio
metricas_por_municipio = df.groupby('INMUEBLE_C_NOM_MUN').agg(
    Total_Docentes=('DOC_TOT', 'sum'),
    Total_Alumnos=('ING_T', 'sum'),
    Latitud_Media=('INMUEBLE_LATITUD', 'mean'),
    Longitud_Media=('INMUEBLE_LONGITUD', 'mean')
).reset_index()

# Seleccionar los 10 municipios con más y menos docentes y alumnos
top_municipios = metricas_por_municipio.nlargest(10, 'Total_Alumnos')
bottom_municipios = metricas_por_municipio.nsmallest(10, 'Total_Alumnos')

# Crear un mapa centrado en Veracruz
centro_latitud = df['INMUEBLE_LATITUD'].mean()
centro_longitud = df['INMUEBLE_LONGITUD'].mean()
mapa_municipios = folium.Map(location=[centro_latitud, centro_longitud], zoom_start=7)

# Agregar municipios con más alumnos y docentes (color verde)
for _, row in top_municipios.iterrows():
    folium.Marker(
        location=[row['Latitud_Media'], row['Longitud_Media']],
        popup=(f"<b>Municipio:</b> {row['INMUEBLE_C_NOM_MUN']}<br>"
               f"<b>Total Docentes:</b> {row['Total_Docentes']}<br>"
               f"<b>Total Alumnos:</b> {row['Total_Alumnos']}"),
        icon=folium.Icon(color='green', icon="info-sign")
    ).add_to(mapa_municipios)

# Agregar municipios con menos alumnos y docentes (color rojo)
for _, row in bottom_municipios.iterrows():
    folium.Marker(
        location=[row['Latitud_Media'], row['Longitud_Media']],
        popup=(f"<b>Municipio:</b> {row['INMUEBLE_C_NOM_MUN']}<br>"
               f"<b>Total Docentes:</b> {row['Total_Docentes']}<br>"
               f"<b>Total Alumnos:</b> {row['Total_Alumnos']}"),
        icon=folium.Icon(color='red', icon="info-sign")
    ).add_to(mapa_municipios)

# Guardar el mapa interactivo
mapa_municipios.save('/Users/salida23/Desktop/Datos/mapa_docentes_alumnos.html')
print("Mapa guardado como 'mapa_docentes_alumnos.html'.") 
```
