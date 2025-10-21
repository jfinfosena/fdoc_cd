---
title: "Pandas - Manipulación de Datos en Python"
position: 2
date: 2025-10-20
---



[https://pandas.pydata.org/docs/index.html](https://pandas.pydata.org/docs/index.html) 

Pandas es una biblioteca de software libre para el análisis de datos y la manipulación de estructuras de datos en  Python. Es una herramienta muy popular entre científicos de datos, analistas de datos y otros profesionales que trabajan con datos.

### ¿Qué ofrece Pandas?

-   **Estructuras de datos potentes:** Pandas ofrece dos estructuras de datos principales: Series y DataFrames. Las Series son vectores unidimensionales, mientras que los DataFrames son matrices bidimensionales con etiquetas de fila y columna. Estas estructuras de datos permiten almacenar y manipular datos de forma eficiente.
-   **Amplia gama de funciones:** Pandas ofrece una amplia gama de funciones para la limpieza de datos, el análisis estadístico, la visualización de datos y mucho más. Estas funciones permiten realizar análisis de datos complejos de forma rápida y sencilla.
-   **Fácil de usar:** Pandas tiene una sintaxis intuitiva y fácil de aprender, lo que la convierte en una herramienta accesible para usuarios de todos los niveles.
### ¿Cómo instalar Pandas?

#### Usando pip

- Abra una terminal o símbolo del sistema.
- Ejecute el siguiente comando:

```bash
pip install pandas
```

### Series en Pandas

Una Series en Pandas es una estructura de datos unidimensional similar a un array de Python. Se caracteriza por:

-   **Almacenar datos:** Puede contener diferentes tipos de datos, como números, cadenas de texto, fechas y valores booleanos.
-   **Tener un índice:** Cada elemento de la serie tiene un índice único que lo identifica.
-   **Ser ordenable:** Se puede ordenar por el índice o por los valores que contiene.
-   **Permitir operaciones:** Se pueden realizar operaciones matemáticas y estadísticas con otras Series o con valores escalares.
### Ejemplo de Series:

```python  
import pandas as pd

temperaturas = pd.Series([20, 25, 30, 22, 28])

# Acceder al valor del índice 2
print(temperaturas[2])

# Calcular la media
print(temperaturas.mean())

# Ordenar por valores
print(temperaturas.sort_values())
```

### DataFrames en Pandas

![Dataframe.](https://pandas.pydata.org/docs/_images/01_table_dataframe.svg)


Un DataFrame en Pandas es una estructura de datos bidimensional similar a una hoja de cálculo. Se caracteriza por:

-   **Almacenar datos:** Puede contener diferentes tipos de datos en diferentes columnas.
-   **Tener un índice:** Cada fila del DataFrame tiene un índice único que la identifica.
-   **Tener nombres de columna:** Cada columna del DataFrame tiene un nombre que identifica el tipo de dato que contiene.
-   **Permitir operaciones:** Se pueden realizar operaciones matemáticas y estadísticas con otros DataFrames o con valores escalares.
**Ejemplo de DataFrame:**


```python  
import pandas as pd

datos = {
    "Nombre": ["Pedro", "María", "Juan"],
    "Edad": [20, 25, 30],
    "Ciudad": ["Medellín", "Bogotá", "Cali"]
}

df = pd.DataFrame(datos)

# Ordenar por la columna "Nombre"
print(df)
```

### Relación entre Series y DataFrames:

-   Una Series puede ser vista como un DataFrame con una sola columna.
-   Un DataFrame puede ser creado a partir de una o más Series.
### Ventajas de usar DataFrames y Series:

-   Permiten almacenar y organizar datos de forma eficiente.
-   Facilitan la limpieza y el análisis de datos.
-   Ofrecen una amplia gama de funciones para la manipulación de datos.
-   Permiten crear visualizaciones de datos atractivas e informativas.


### Diferencias clave entre Series y DataFrames en Pandas:

| Característica | Series                                        | DataFrame                               |
|--------------|---------------------------------------------|--------------------------------------------|
| Dimensión     | Una dimensión (como una columna)                | Dos dimensiones (como una hoja de cálculo)       |
| Índice        | Un solo índice (etiqueta cada elemento)           | Índices de filas y columnas                     |
| Tipos de datos   | Un solo tipo de dato por Serie                  | Diferentes tipos de datos por columna          |
| Estructura    | Como una columna                               | Como una tabla o hoja de cálculo              |
| Analogía      | Columna de una hoja de cálculo                 | Hoja de cálculo completa                    |
| Uso común     | Datos de series de tiempo, datos con un solo atributo | Datos tabulares, conjuntos de datos con múltiples atributos |
| Ejemplo       | `pd.Series([10, 20, 30])`                      | `pd.DataFrame({'Nombre': ['Alicia', 'Bob'], 'Edad': [25, 30]})` | 


## Creando DataFrame

### Crear un DataFrame a partir de Series en Pandas:

**Ejemplo:**

```python
import pandas as pd

# Crear las Series
nombres = pd.Series(['Alicia', 'Bob', 'Carlos'])
edades = pd.Series([25, 30, 28])
ciudades = pd.Series(['Nueva York', 'Londres', 'París'])

# Crear el DataFrame a partir de las Series
mi_dataframe = pd.DataFrame({'Nombre': nombres, 'Edad': edades, 'Ciudad': ciudades})

# Imprimir el DataFrame
print(mi_dataframe)
```

**Salida:**

```bash
      Nombre   Edad      Ciudad
0      Alicia   25        Nueva York
1      Bob      30        Londres
2      Carlos   28        París
```

**Explicación:**

- **Crear las Series:** Se crean tres Series, una para cada columna del DataFrame: `nombres`, `edades` y `ciudades`.
- **Crear el DataFrame:** Se crea el DataFrame `mi_dataframe` usando un diccionario. Las claves del diccionario son los nombres de las columnas, y los valores son las Series que contienen los datos para cada columna.
- **Imprimir el DataFrame:** Se imprime el DataFrame para ver el resultado.

**Puntos Clave:**

* Cada Serie representa una columna del DataFrame.
* El diccionario que se usa para crear el DataFrame asocia los nombres de las columnas con las Series correspondientes.

### DataFrame desde un diccionario:
 
```python
import pandas as pd

# Crear un diccionario
datos = {"Nombre": ["Ana", "Juan", "Pedro"],
         "Edad": [25, 30, 35],
         "Ciudad": ["Madrid", "Barcelona", "Sevilla"]}

# Convertir el diccionario a un DataFrame
df = pd.DataFrame(datos)

print(df)

# Salida:
#   Nombre  Edad   Ciudad
# 0    Ana     25  Madrid
# 1    Juan     30  Barcelona
# 2   Pedro     35  Sevilla
```

#### **Explicación:**

-   Se crea un diccionario con las claves como nombres de las columnas y los valores como listas que representan las filas.
-   La función `pd.DataFrame` convierte el diccionario en un DataFrame.

### DataFrame desde una lista de diccionarios:

  

```python
import pandas as pd

datos = [{"Nombre": "Ana", "Edad": 25, "Ciudad": "Madrid"},
         {"Nombre": "Juan", "Edad": 30, "Ciudad": "Barcelona"},
         {"Nombre": "Pedro", "Edad": 35, "Ciudad": "Sevilla"}]

df = pd.DataFrame(datos)

print(df)

# Salida:
#   Nombre  Edad   Ciudad
# 0    Ana     25  Madrid
# 1    Juan     30  Barcelona
# 2   Pedro     35  Sevilla
```

#### **Explicación:**

-   Se crea una lista de diccionarios, donde cada diccionario representa una fila del DataFrame.
-   La función `pd.DataFrame` convierte la lista de diccionarios en un DataFrame.

### DataFrame desde una lista de listas:

  

```python
import pandas as pd

datos = [["Ana", 25, "Madrid"],
         ["Juan", 30, "Barcelona"],
         ["Pedro", 35, "Sevilla"]]

df = pd.DataFrame(datos, columns=["Nombre", "Edad", "Ciudad"])

print(df)

# Salida:
#   Nombre  Edad   Ciudad
# 0    Ana     25  Madrid
# 1    Juan     30  Barcelona
# 2   Pedro     35  Sevilla
```

#### **Explicación:**

-   Se crea una lista de listas, donde cada lista representa una fila del DataFrame.
-   La función `pd.DataFrame` convierte la lista de listas en un DataFrame, y se especifican los nombres de las columnas.

### DataFrame desde un archivo CSV:

```python
import pandas as pd

df = pd.read_csv("data.csv")

print(df)

# Salida:
#   Nombre  Edad   Ciudad
# 0    Ana     25  Madrid
# 1    Juan     30  Barcelona
# 2   Pedro     35  Sevilla
```

#### **Explicación:**

-   Se usa la función `pd.read_csv` para leer un archivo CSV y convertirlo en un DataFrame.


#### Cómo crear archivos CSV con encabezados desde Python, utilizando la biblioteca `csv`:

```python
import csv

# Define los nombres de las columnas
column_names = ["Nombre", "Edad", "Ciudad"]

# Crea una lista de datos para cada fila
data = [
    ["Ana", 25, "Madrid"],
    ["Juan", 30, "Barcelona"],
    ["Pedro", 35, "Sevilla"]
]

# Abre el archivo CSV en modo escritura
with open("data.csv", "w", newline="") as file:
    writer = csv.writer(file)

    # Escribe la fila de encabezados
    writer.writerow(column_names)

    # Escribe cada fila de datos
    for row in data:
        writer.writerow(row)

print("Archivo CSV creado correctamente.")
```
  


### DataFrame desde una URL:

```python
import pandas as pd

df = pd.read_csv("https://raw.githubusercontent.com/datasets/data/master/people.csv")

print(df)

# Salida:
#   Name  Age  City
# 0    Ana     25  Madrid
# 1    Juan     30  Barcelona
# 2   Pedro     35  Sevilla
```

#### **Explicación:**

-   Se usa la función `pd.read_csv` para leer un archivo CSV desde una URL y convertirlo en un DataFrame.

### DataFrame desde una consulta SQL:

```python
import pandas as pd

from sqlalchemy import create_engine

# Crear un motor de base de datos
engine = create_engine("sqlite:///database.sqlite")

# Leer la tabla "personas" en un DataFrame
df = pd.read_sql_table("personas", engine)

print(df)

# Salida:
#   Nombre  Edad   Ciudad
# 0    Ana     25  Madrid
# 1    Juan     30  Barcelona
# 2   Pedro     35  Sevilla
```

#### **Explicación:**

-   Se crea un motor de base de datos usando `sqlalchemy`.
-   La función `pd.read_sql_table` se usa para leer una tabla de la base de datos y convertirla en un DataFrame.

### DataFrame desde una hoja de cálculo de Excel:


```python
import pandas as pd

df = pd.read_excel("data.xlsx")

print(df)

# Salida:
#   Nombre  Edad   Ciudad
# 0    Ana     25  Madrid
# 1    Juan     30  Barcelona
# 2   Pedro     35  Sevilla
```


#### Explicación:

-   Se usa la función `pd.read_excel` para leer una hoja de cálculo de Excel y convertirla en un DataFrame.

### DataFrame desde un archivo JSON:


```json
[
  {
    "Nombre": "Ana",
    "Edad": 25,
    "Ciudad": "Madrid"
  },
  {
    "Nombre": "Juan",
    "Edad": 30,
    "Ciudad": "Barcelona"
  },
  {
    "Nombre": "Pedro",
    "Edad": 35,
    "Ciudad": "Sevilla"
  }
]
```


```python
import pandas as pd

df = pd.read_json("data.json")

print(df)

# Salida:
#   Nombre  Edad   Ciudad
# 0    Ana     25  Madrid
# 1    Juan     30  Barcelona
# 2   Pedro     35  Sevilla
```

#### Explicación:

-   Se usa la función `pd.read_json` para leer un archivo JSON y convertirlo en un DataFrame.

### DataFrame desde un objeto NumPy:

```python
import pandas as pd

import numpy as np

datos = np.array([["Ana", 25, "Madrid"],
                   ["Juan", 30, "Barcelona"],
                   ["Pedro", 35, "Sevilla"]])

df = pd.DataFrame(datos, columns=["Nombre", "Edad", "Ciudad"])

print(df)

# Salida:
#   Nombre  Edad   Ciudad
# 0    Ana     25  Madrid
# 1    Juan     30  Barcelona
# 2   Pedro     35  Sevilla
```

#### **Explicación:**

-   Se crea un array de NumPy con las filas y columnas del DataFrame.
-   La función `pd.DataFrame` convierte el array de NumPy en un DataFrame, y se especifican los nombres de las columnas.


### DataFrame desde Firebase:

```bash
pip install --upgrade firebase-admin
```

```python
import pandas as pd

import firebase_admin
from firebase_admin import credentials
from firebase_admin import firestore

# Use a service account.
cred = credentials.Certificate('key.json')
app = firebase_admin.initialize_app(cred)
db = firestore.client()

# Get data from a Firestore collection
users = db.collection('user').stream()
# Convert data to a list of dictionaries
users_data = [doc.to_dict() for doc in users]
# Create DataFrame
df = pd.DataFrame(users_data)

print(df)
```

#### **Explicación:**

**1\. Importaciones:**

-   **`pandas as pd`**: Importa la biblioteca Pandas para manipulación de datos y creación de DataFrames.
-   **Bibliotecas de Firebase Admin**:
    -   **`firebase_admin`**: Biblioteca base para interactuar con los servicios de Firebase Admin.
    -   **`credentials`**: Proporciona funciones para la autenticación con Firebase.
    -   **`firestore`**: Proporciona acceso a la base de datos Firestore.
**2\. Autenticación:**

-   **`cred = credentials.Certificate('key.json')`**: Carga las credenciales del proyecto Firebase desde un archivo llamado "key.json". Este archivo contiene información privada y es esencial para un acceso seguro a su proyecto.
-   **`app = firebase_admin.initialize_app(cred)`**: Inicializa la aplicación Firebase Admin utilizando las credenciales cargadas.

**3\. Acceso a Firestore:**

-   **`db = firestore.client()`**: Crea un objeto cliente para interactuar con la base de datos Firestore.

**4\. Recuperación de datos:**

-   **`users = db.collection('user').stream()`**: Recupera datos de la colección Firestore llamada "user". El método `stream()` recupera datos en tiempo real, lo que significa que puede capturar cualquier cambio que ocurra en la colección.

**5\. Conversión de datos:**

-   **`users_data = [doc.to_dict() para doc en users]`**: Esta línea itera a través de los datos recuperados (representados por objetos `doc`) y convierte cada documento en un diccionario utilizando el método `to_dict()`. Esto crea una lista de diccionarios, donde cada diccionario representa un solo documento en la colección.

**6\. Creación de DataFrame:**

-   **`df = pd.DataFrame(users_data)`**: Crea un DataFrame de Pandas a partir de la lista de diccionarios (`users_data`). El DataFrame tendrá columnas que corresponden a las claves de los diccionarios y filas que representan cada documento.

**7\. Impresión del DataFrame:**

-   **`print(df)`**: Imprime el DataFrame recién creado en la consola. Esto mostrará los datos recuperados de la colección Firestore en un formato tabular.

### DataFrame desde MongoDB:

```bash
python3 -m pip install pymongo
```

```python
import pymongo
import pandas as pd
from pymongo import MongoClient

client = MongoClient()

client = MongoClient('mongodb+srv://') #conexión mongodb
db = client["dbTest"]
collection = db["user"]

cursor = collection.find()
for document in cursor:
    print(document)

df = pd.DataFrame(list(collection.find()))
print(df)
```

#### **Explicación:**

**Importaciones:**

-   **`import pymongo`**: Importa la biblioteca `pymongo` para interactuar con la base de datos MongoDB.
-   **`import pandas as pd`**: Importa la biblioteca `pandas` para crear y manipular DataFrames.
-   **`from pymongo import MongoClient`**: Importa la clase `MongoClient` de la biblioteca `pymongo` para establecer la conexión con el servidor MongoDB.

**Conexión a MongoDB:**

-   **`client = MongoClient()`**: Crea una instancia del cliente `MongoClient` para conectarse al servidor MongoDB. La versión original dejaba la conexión incompleta, so here we establish a connection to a MongoDB server using the `MongoClient` constructor. You'll need to replace `'mongodb+srv://'` with the actual connection string for your MongoDB database, including authentication details if required.

**Acceso a la base de datos y colección:**

-   **`db = client["dbTest"]`**: Obtiene una referencia a la base de datos denominada "dbTest". Reemplace "dbTest" con el nombre real de su base de datos.
-   **`collection = db["user"]`**: Obtiene una referencia a la colección llamada "user" dentro de la base de datos "dbTest". Reemplace "user" con el nombre de su colección si es diferente.

**Lectura de datos:**

-   **`cursor = collection.find()`**: Realiza una consulta para recuperar todos los documentos de la colección "user". La variable `cursor` almacena un iterador que apunta a cada documento encontrado.

**Recorrido de documentos:**

-   **`for document in cursor:`**: Inicia un bucle `for` que itera a través de cada documento en el cursor.
-   **`print(document)`**: Dentro del bucle, imprime el contenido de cada documento completo en la consola. Esto puede ser útil para inspeccionar los datos individualmente.

**Creación de DataFrame:**

-   **`df = pd.DataFrame(list(collection.find()))`**: Convierte los documentos de la colección "user" en un DataFrame de Pandas.
    -   `collection.find()`: Ejecuta la consulta nuevamente para recuperar todos los documentos.
    -   `list()`: Convierte el resultado de la consulta en una lista de diccionarios, donde cada diccionario representa un documento.
    -   `pd.DataFrame()`: Crea un DataFrame de Pandas a partir de la lista de diccionarios.

**Impresión del DataFrame:**

-   **`print(df)`**: Imprime el DataFrame completo en la consola. Esto muestra los datos en una estructura tabular con columnas y filas, permitiendo una visualización más organizada.

### DataFrame desde una API REST:

```python
import pandas as pd
import requests

# Realizar petición GET a la API
response = requests.get('https://playground.mockoon.com/users')

# Verificar que la petición fue exitosa
if response.status_code == 200:
    # Convertir la respuesta JSON a DataFrame
    data = response.json()
    df = pd.DataFrame(data)
    
    print(df)
else:
    print(f"Error en la petición: {response.status_code}") 
```

#### **Explicación:**

**Importaciones:**

-   **`import pandas as pd`**: Importa la biblioteca Pandas para crear y manipular DataFrames.
-   **`import requests`**: Importa la biblioteca `requests` para realizar peticiones HTTP a APIs.

**Petición a la API:**

-   **`response = requests.get('https://playground.mockoon.com/users')`**: Realiza una petición GET a la API especificada. La variable `response` contiene la respuesta del servidor.

**Verificación de la respuesta:**

-   **`if response.status_code == 200:`**: Verifica que la petición fue exitosa (código de estado 200 significa "OK").

**Conversión a DataFrame:**

-   **`data = response.json()`**: Convierte la respuesta JSON de la API en un objeto Python (lista de diccionarios).
-   **`df = pd.DataFrame(data)`**: Crea un DataFrame de Pandas a partir de los datos JSON.

**Manejo de errores:**

-   **`else: print(f"Error en la petición: {response.status_code}")`**: Si la petición no fue exitosa, imprime el código de error.

**Ventajas de este método:**

-   Permite acceder a datos en tiempo real desde APIs públicas o privadas.
-   Facilita la integración de datos externos en análisis de datos.
-   Los datos se actualizan automáticamente cada vez que se ejecuta el código.

**Nota:** Es necesario instalar la biblioteca `requests` si no está disponible:

```bash
pip install requests
```

