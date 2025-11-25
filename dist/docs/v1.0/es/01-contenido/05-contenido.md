---
title: "Guía Básica de Pandas para Python"
position: 5
date: 2025-11-11
---

Pandas es una biblioteca de Python poderosa y flexible para manipular y analizar datos. Esta guía cubre los conceptos fundamentales de Pandas, incluyendo estructuras de datos, operaciones básicas, y cómo trabajar con datos de manera eficiente. Está diseñada para ser clara, práctica y fácil de seguir, con ejemplos que puedes probar directamente en Python.

**Requisitos previos**: Asegúrate de tener Pandas instalado (`pip install pandas`) y, opcionalmente, NumPy (`pip install numpy`), ya que Pandas depende de él.

---

## 1. Introducción a las Estructuras de Datos de Pandas

Pandas se basa en dos estructuras principales para organizar datos: **Series** y **DataFrame**. Estas son las herramientas que usarás para almacenar, manipular y analizar datos.

### 1.1. Series: Una Columna de Datos
Una **Series** es como una lista o arreglo unidimensional, pero con un índice que etiqueta cada elemento. Puedes pensar en ella como una columna de una tabla.

- **Características**:
  - Almacena datos de cualquier tipo (números, cadenas, fechas, etc.).
  - Tiene un índice que puede ser numérico (0, 1, 2...) o personalizado (por ejemplo, nombres o fechas).
  - Es similar a un array de NumPy, pero con más funcionalidades.

**Ejemplo: Crear una Series**

```python
import pandas as pd

# Crear una Series con una lista
datos = pd.Series([10, 20, 30, 40], index=['a', 'b', 'c', 'd'])
print(datos)
```

**Salida**:
```bash
a    10
b    20
c    30
d    40
dtype: int64
```

- **Explicación**:
  - `index=['a', 'b', 'c', 'd']` asigna etiquetas personalizadas.
  - `dtype: int64` indica que los datos son enteros de 64 bits.

### 1.2. DataFrame: Una Tabla de Datos
Un **DataFrame** es una tabla bidimensional con filas y columnas, similar a una hoja de cálculo o una tabla de base de datos.

- **Características**:
  - Cada columna es una Series.
  - Tiene índices para filas y nombres para columnas.
  - Puede contener datos de diferentes tipos (números, cadenas, etc.).

**Ejemplo: Crear un DataFrame**

```python
import pandas as pd

# Crear un DataFrame desde un diccionario
datos = {
    'Nombre': ['Ana', 'Bob', 'Clara'],
    'Edad': [25, 30, 22],
    'Ciudad': ['Madrid', 'Lima', 'Bogotá']
}
df = pd.DataFrame(datos)
print(df)
```

**Salida**:
```bash
   Nombre  Edad  Ciudad
0    Ana    25  Madrid
1    Bob    30    Lima
2  Clara    22  Bogotá
```

- **Explicación**:
  - Las claves del diccionario (`Nombre`, `Edad`, `Ciudad`) se convierten en nombres de columnas.
  - El índice por defecto es numérico (0, 1, 2).

---

## 2. Inspeccionar y Explorar Datos

Una vez que tienes un DataFrame o una Series, querrás inspeccionar su contenido. Pandas ofrece métodos sencillos para obtener información sobre tus datos.

### 2.1. Métodos Básicos de Inspección
Aquí tienes las herramientas más comunes para explorar un DataFrame:

| Método | Descripción | Ejemplo |
|--------|-------------|---------|
| `df.head(n)` | Muestra las primeras `n` filas (por defecto, 5). | `df.head(2)` |
| `df.tail(n)` | Muestra las últimas `n` filas. | `df.tail(2)` |
| `df.info()` | Resumen de columnas, tipos de datos y valores no nulos. | `df.info()` |
| `df.shape` | Devuelve una tupla con (filas, columnas). | `df.shape` |
| `df.describe()` | Estadísticas básicas (media, mínimo, máximo, etc.) para columnas numéricas. | `df.describe()` |

**Ejemplo: Inspeccionar un DataFrame**

```python
# Continuando con el DataFrame anterior
print("Primeras 2 filas:")
print(df.head(2))

print("\nInformación del DataFrame:")
print(df.info())

print("\nDimensiones:")
print(df.shape)
```

**Salida**:
```bash
Primeras 2 filas:
  Nombre  Edad  Ciudad
0    Ana    25  Madrid
1    Bob    30    Lima

Información del DataFrame:
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 3 entries, 0 to 2
Data columns (total 3 columns):
 #   Column  Non-Null Count  Dtype 
---  ------  --------------  ----- 
 0   Nombre  3 non-null      object
 1   Edad    3 non-null      int64 
 2   Ciudad  3 non-null      object
dtypes: int64(1), object(2)
memory usage: 200.0+ bytes

Dimensiones:
(3, 3)
```

### 2.2. Acceder a Columnas y Filas
- **Columnas**: Usa el nombre de la columna como clave o atributo.
  - `df['Nombre']` o `df.Nombre` devuelve la columna como una Series.
- **Filas**: Usa `.loc[]` (por índice) o `.iloc[]` (por posición numérica).
  - `df.loc[0]` devuelve la fila con índice 0.
  - `df.iloc[0]` devuelve la primera fila (posición 0).

**Ejemplo: Acceder a datos**

```python
# Acceder a una columna
print(df['Nombre'])

# Acceder a una fila
print(df.loc[1])

# Acceder a un valor específico
print(df.loc[1, 'Edad'])
```

**Salida**:
```bash
0      Ana
1      Bob
2    Clara
Name: Nombre, dtype: object

Nombre      Bob
Edad         30
Ciudad     Lima
Name: 1, dtype: object

30
```

---

## 3. Operaciones Básicas con Datos

Pandas permite realizar operaciones matemáticas, filtrar datos, y manejar valores faltantes de manera sencilla.

### 3.1. Operaciones Matemáticas
Puedes aplicar operaciones a Series o columnas numéricas de un DataFrame.

**Ejemplo: Operaciones con una columna**

```python
# Aumentar la edad en 5 años
df['Edad'] = df['Edad'] + 5
print(df)
```

**Salida**:
```bash
   Nombre  Edad  Ciudad
0    Ana    30  Madrid
1    Bob    35    Lima
2  Clara    27  Bogotá
```

### 3.2. Filtrar Datos
Usa condiciones lógicas para seleccionar filas que cumplan ciertos criterios.

**Ejemplo: Filtrar por edad**

```python
# Seleccionar personas mayores de 30 años
filtro = df['Edad'] > 30
print(df[filtro])
```

**Salida**:
```bash
  Nombre  Edad Ciudad
1    Bob    35   Lima
```

### 3.3. Manejo de Valores Faltantes
Los valores faltantes en Pandas se representan como `NaN` (Not a Number). Puedes detectarlos y manejarlos con métodos específicos.

| Método | Descripción |
|--------|-------------|
| `df.isna()` | Devuelve `True` para valores faltantes. |
| `df.dropna()` | Elimina filas con valores faltantes. |
| `df.fillna(valor)` | Rellena valores faltantes con un valor específico. |

**Ejemplo: Manejar valores faltantes**

```python
# Crear un DataFrame con valores faltantes
datos = {
    'Nombre': ['Ana', 'Bob', 'Clara'],
    'Edad': [25, None, 22],
    'Ciudad': ['Madrid', 'Lima', None]
}
df = pd.DataFrame(datos)

# Detectar valores faltantes
print(df.isna())

# Rellenar valores faltantes
df_rellenado = df.fillna({'Edad': 0, 'Ciudad': 'Desconocido'})
print(df_rellenado)
```

**Salida**:
```bash
   Nombre  Edad  Ciudad
0  False  False   False
1  False   True   False
2  False  False    True

   Nombre  Edad      Ciudad
0    Ana  25.0      Madrid
1    Bob   0.0        Lima
2  Clara  22.0  Desconocido
```

---

## 4. Trabajar con Datos Externos

Pandas puede leer y escribir datos desde/hacia varios formatos, como CSV, Excel, JSON, y bases de datos.

### 4.1. Leer un Archivo CSV
El método `pd.read_csv()` es muy común para cargar datos.

**Ejemplo: Leer un CSV**

```python
# Suponiendo que tienes un archivo 'datos.csv'
df = pd.read_csv('datos.csv')
print(df.head())
```

### 4.2. Guardar un DataFrame
Puedes guardar tu DataFrame en diferentes formatos.

**Ejemplo: Guardar como CSV**

```python
df.to_csv('nuevo_datos.csv', index=False)
```

- **Nota**: `index=False` evita guardar el índice como una columna.

---

## 5. Consejos Prácticos

- **Explora tus datos primero**: Usa `df.info()` y `df.head()` para entender la estructura de tus datos antes de manipularlos.
- **Guarda copias**: Antes de modificar un DataFrame, crea una copia con `df.copy()` para evitar cambios accidentales.
- **Usa índices significativos**: Si tus datos tienen una columna que puede servir como identificador (como un ID o una fecha), configúrala como índice con `df.set_index('columna')`.
- **Consulta la documentación**: La documentación oficial de Pandas (https://pandas.pydata.org/docs/) es una gran referencia para funciones avanzadas.

---






