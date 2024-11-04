# Manual Básico para Análisis Descriptivo de Datos en Python

## Introducción
Este manual te ayudará a realizar un análisis descriptivo de datos utilizando **Python**. Python es un lenguaje de programación popular por su sencillez y versatilidad, ampliamente usado en ciencia de datos, análisis de datos, desarrollo web, automatización y mucho más. Es conocido por su sintaxis clara y una amplia comunidad de desarrolladores que contribuyen a la creación de librerías y herramientas. Aprenderás a cargar un conjunto de datos, calcular estadísticas descriptivas y crear visualizaciones básicas utilizando las bibliotecas **pandas**, **matplotlib** y **seaborn**.

## Requisitos Previos
- **Python**: Es un lenguaje de programación que necesitas tener instalado en tu computadora. Si aún no lo tienes, sigue las instrucciones de instalación a continuación.
- Instalación de las librerías necesarias: `pandas`, `matplotlib`, `seaborn`.

### Instalación de Python

#### Windows
1. Visita el [sitio web oficial de Python](https://www.python.org/downloads/) y descarga la versión más reciente para Windows.
2. Durante la instalación, asegúrate de seleccionar la opción **"Add Python to PATH"**.
3. Una vez instalado, abre la terminal (puedes buscar "cmd" en el menú de inicio) y verifica la instalación escribiendo:

```bash
python --version
```

#### macOS
1. macOS a menudo incluye una versión de Python instalada, pero se recomienda instalar la última versión.
2. Usa [Homebrew](https://brew.sh/) para instalar Python ejecutando el siguiente comando en la terminal:

```bash
brew install python
```

3. Verifica la instalación escribiendo:

```bash
python3 --version
```

#### Linux
1. La mayoría de las distribuciones de Linux ya incluyen Python, pero para instalar la última versión, abre la terminal y ejecuta:

```bash
sudo apt update
sudo apt install python3
```

2. Verifica la instalación con:

```bash
python3 --version
```

### Instalación de las Librerías
Ejecuta estos comandos en la terminal para instalar las bibliotecas:

```bash
pip install pandas matplotlib seaborn
```

## Paso 1: Importar las Librerías

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

## Paso 2: Cargar el Conjunto de Datos

En este tutorial, usaremos el conjunto de datos **Iris**, disponible a través de una URL.

```python
# Cargar los datos de Iris desde GitHub
url = "https://raw.githubusercontent.com/uiuc-cse/data-fa14/gh-pages/data/iris.csv"
df = pd.read_csv(url)

# Mostrar las primeras filas del dataset
print(df.head())
```

## Paso 3: Estadísticas Descriptivas Básicas

```python
# Resumen estadístico del conjunto de datos
print(df.describe())
```

## Paso 4: Visualización de Histogramas

```python
# Configuración de estilo de Seaborn
sns.set(style="whitegrid")

# Crear histogramas de cada característica
features = df.columns[:-1]  # Excluyendo la columna 'species'

plt.figure(figsize=(12, 8))
for i, feature in enumerate(features):
    plt.subplot(2, 2, i + 1)
    sns.histplot(df[feature], kde=True)
    plt.title(f"Distribución de {feature}")

plt.tight_layout()
plt.show()
```

## Paso 5: Gráficos de Dispersión

```python
# Gráfico de dispersión entre pares de variables
sns.pairplot(df, hue="species", markers=["o", "s", "D"])
plt.suptitle("Gráfico de Dispersión entre Características por Especie", y=1.02)
plt.show()
```

## Paso 6: Matriz de Correlación

```python
# Calcular y mostrar la matriz de correlación
correlation_matrix = df.corr()

plt.figure(figsize=(8, 6))
sns.heatmap(correlation_matrix, annot=True, cmap="coolwarm")
plt.title("Matriz de Correlación entre Características")
plt.show()
```

## Ejercicios Prácticos

1. **Histograma de otra característica**: Crea un histograma para `sepal_width` o `petal_length`.
2. **Gráfico de dispersión diferente**: Modifica el gráfico de dispersión para explorar `petal_length` vs `petal_width`.
3. **Boxplot por especie**:

```python
plt.figure(figsize=(8, 6))
sns.boxplot(x="species", y="sepal_length", data=df)
plt.title("Longitud del Sépalo por Especie")
plt.show()
```

## Conclusión
Este manual te ha guiado a través de los pasos básicos para realizar un análisis descriptivo en **Python** utilizando **pandas**, **matplotlib** y **seaborn**. Sigue practicando con otros conjuntos de datos para mejorar tus habilidades en análisis de datos.

## Recursos Adicionales
- [Documentación de Pandas](https://pandas.pydata.org/pandas-docs/stable/)

---
© 2024 Proyecto DS-JLSO. Todos los derechos reservados.
