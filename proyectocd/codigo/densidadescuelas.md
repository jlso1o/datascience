### En este apartado se muestra el código realizado en phyton para la geolocalización de la densidad de las escuelas.

```python
import pandas as pd
import folium

# Cargar el archivo combinado
df = pd.read_csv('archivo_completo.csv', encoding='ISO-8859-1', low_memory=False)

# Eliminar filas con valores faltantes en municipio, latitud y longitud
df = df.dropna(subset=['INMUEBLE_C_NOM_MUN', 'INMUEBLE_LATITUD', 'INMUEBLE_LONGITUD'])

# Calcular el número de escuelas por municipio
escuelas_por_municipio = df.groupby('INMUEBLE_C_NOM_MUN').agg(
    Numero_Escuelas=('CV_CCT', 'count'),
    Latitud_Media=('INMUEBLE_LATITUD', 'mean'),
    Longitud_Media=('INMUEBLE_LONGITUD', 'mean')
).reset_index()

# Ordenar municipios por densidad de escuelas
top_municipios = escuelas_por_municipio.nlargest(10, 'Numero_Escuelas')
bottom_municipios = escuelas_por_municipio.nsmallest(10, 'Numero_Escuelas')

# Crear un mapa centrado en Veracruz
centro_latitud = df['INMUEBLE_LATITUD'].mean()
centro_longitud = df['INMUEBLE_LONGITUD'].mean()
mapa_municipios = folium.Map(location=[centro_latitud, centro_longitud], zoom_start=7)

# Agregar municipios con mayor densidad (color verde)
for _, row in top_municipios.iterrows():
    folium.Marker(
        location=[row['Latitud_Media'], row['Longitud_Media']],
        popup=(f"<b>Municipio:</b> {row['INMUEBLE_C_NOM_MUN']}<br>"
               f"<b>Número de Escuelas:</b> {row['Numero_Escuelas']}"),
        icon=folium.Icon(color='green', icon="info-sign")
    ).add_to(mapa_municipios)

# Agregar municipios con menor densidad (color rojo)
for _, row in bottom_municipios.iterrows():
    folium.Marker(
        location=[row['Latitud_Media'], row['Longitud_Media']],
        popup=(f"<b>Municipio:</b> {row['INMUEBLE_C_NOM_MUN']}<br>"
               f"<b>Número de Escuelas:</b> {row['Numero_Escuelas']}"),
        icon=folium.Icon(color='red', icon="info-sign")
    ).add_to(mapa_municipios)

# Guardar el mapa interactivo
mapa_municipios.save('mapa_densidad_escuelas.html')
print("Mapa guardado como 'mapa_densidad_escuelas.html'.") 
```
