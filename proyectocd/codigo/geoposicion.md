### En este apartado se muestra el código realizado en phyton para la geolocalización de las escuelas primarias.

```python
import pandas as pd
import folium
# Cargar el conjunto de datos
df = pd.read_csv('30cctvp.csv')

# Mostrar las primeras filas del conjunto de datos
#print("Primeras filas del conjunto de datos:")
#print(df.head())

#print("Descripción estadística de variables numéricas:")
#print(df.describe())

# Tipo de datos de cada variable
#print("\nTipo de datos de cada columna:")
#print(df.dtypes)

# Valores únicos en variables categóricas
#print("\nValores únicos por variable categórica:")
#for column in df.select_dtypes(include='object').columns:
#    print(f"{column}: {df[column].unique()}")

# Verificar que las columnas de latitud y longitud existen
if 'INMUEBLE_LATITUD' in df.columns and 'INMUEBLE_LONGITUD' in df.columns:
    # Crear el mapa centrado en las coordenadas promedio de los datos
    centro_latitud = df['INMUEBLE_LATITUD'].mean()
    centro_longitud = df['INMUEBLE_LONGITUD'].mean()
    mapa = folium.Map(location=[centro_latitud, centro_longitud], zoom_start=6)

    # Iterar sobre el DataFrame y agregar puntos al mapa
    for index, row in df.iterrows():
        latitud = row['INMUEBLE_LATITUD']
        longitud = row['INMUEBLE_LONGITUD']
        nombre = row['C_NOMBRE'] if 'C_NOMBRE' in row else "Ubicación sin nombre"

        # Agregar un marcador para cada ubicación
        folium.Marker(
            location=[latitud, longitud],
            popup=f"{nombre}",
            tooltip="Click para más información"
        ).add_to(mapa)

    # Guardar el mapa como un archivo HTML
    mapa.save('mapa_geoposicion.html')
    print("Mapa guardado como 'mapa_geoposicion.html'.")

else:
    print("No se encontraron las columnas de latitud y longitud en el archivo.")
```
