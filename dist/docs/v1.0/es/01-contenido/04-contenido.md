---
title: "Guía de Introducción a Estructuras de Datos en Pandas"
position: 4
date: 2025-11-11
---

Pandas es una biblioteca de Python poderosa para trabajar con datos tabulares, como hojas de cálculo o bases de datos. Esta guía te introduce a las dos estructuras principales de Pandas: **Series** y **DataFrame**. Aprenderás cómo crearlas, manipularlas y usarlas para analizar datos de forma sencilla.

## Requisitos previos
- Tener instalado Python (versión 3.7 o superior).
- Instalar Pandas: `pip install pandas`.
- Opcional: Instalar NumPy para operaciones numéricas avanzadas: `pip install numpy`.

Importa Pandas en tu script con:
```python
import pandas as pd
import numpy as np  # Opcional, para algunos ejemplos
```

---

## 1. Series: Una columna de datos
Una **Series** es como una lista o arreglo unidimensional, pero con un índice que etiqueta cada elemento. Piensa en ella como una columna de una hoja de cálculo.

### Crear una Series
Puedes crear una Series a partir de una lista, un diccionario o un arreglo de NumPy.

#### Ejemplo 1: Series desde una lista
```python
# Crear una Series con una lista
datos = [10, 20, 30, 40]
serie = pd.Series(datos)
print(serie)
```
**Salida:**
```bash
0    10
1    20
2    30
3    40
dtype: int64
```
- Los números a la izquierda (0, 1, 2, 3) son el **índice** automático.
- `dtype: int64` indica el tipo de datos (enteros de 64 bits).

#### Ejemplo 2: Series con índice personalizado
```python
# Crear una Series con índices personalizados
serie = pd.Series([10, 20, 30, 40], index=['a', 'b', 'c', 'd'])
print(serie)
```
**Salida:**
```bash
a    10
b    20
c    30
d    40
dtype: int64
```

#### Ejemplo 3: Series desde un diccionario
```python
# Crear una Series desde un diccionario
datos_dict = {'manzana': 5, 'banana': 8, 'naranja': 3}
serie = pd.Series(datos_dict)
print(serie)
```
**Salida:**
```bash
manzana    5
banana     8
naranja    3
dtype: int64
```

### Operaciones básicas con Series
- **Acceder a un elemento**: Usa el índice como si fuera una clave de diccionario.
```python
print(serie['banana'])  # Salida: 8
```
- **Modificar un valor**:
```python
serie['manzana'] = 10
print(serie)
```
**Salida:**
```bash
manzana    10
banana      8
naranja     3
dtype: int64
```
- **Operaciones matemáticas**: Puedes sumar, restar, multiplicar, etc., elemento por elemento.
```python
print(serie * 2)
```
**Salida:**
```bash
manzana    20
banana     16
naranja     6
dtype: int64
```

### Nota
Si hay valores faltantes (`NaN`), Pandas los maneja automáticamente. Usa `pd.isna()` para detectar valores nulos.

---

## 2. DataFrame: Una tabla de datos
Un **DataFrame** es como una hoja de cálculo: tiene filas, columnas e índices. Cada columna es una Series.

### Crear un DataFrame
Puedes crearlo desde un diccionario, una lista de listas, un arreglo de NumPy o incluso un archivo (como CSV).

#### Ejemplo 1: DataFrame desde un diccionario
```python
# Crear un DataFrame desde un diccionario
datos = {
    'nombre': ['Ana', 'Bob', 'Clara'],
    'edad': [25, 30, 22],
    'ciudad': ['Madrid', 'Lima', 'Bogotá']
}
df = pd.DataFrame(datos)
print(df)
```
**Salida:**
```bash
   nombre  edad   ciudad
0    Ana    25  Madrid
1    Bob    30    Lima
2  Clara    22  Bogotá
```

#### Ejemplo 2: DataFrame con índice personalizado
```python
df = pd.DataFrame(datos, index=['a', 'b', 'c'])
print(df)
```
**Salida:**
```bash
   nombre  edad   ciudad
a    Ana    25  Madrid
b    Bob    30    Lima
c  Clara    22  Bogotá
```

### Operaciones básicas con DataFrames
- **Ver una columna** (es una Series):
```python
print(df['nombre'])
```
**Salida:**
```bash
a      Ana
b      Bob
c    Clara
Name: nombre, dtype: object
```
- **Acceder a una fila** usando el índice:
```python
print(df.loc['a'])
```
**Salida:**
```bash
nombre       Ana
edad          25
ciudad    Madrid
Name: a, dtype: object
```
- **Filtrar filas** según una condición:
```python
print(df[df['edad'] > 23])
```
**Salida:**
```bash
   nombre  edad   ciudad
a    Ana    25  Madrid
b    Bob    30    Lima
```
- **Agregar una columna**:
```python
df['pais'] = ['España', 'Perú', 'Colombia']
print(df)
```
**Salida:**
```bash
   nombre  edad   ciudad      pais
a    Ana    25  Madrid   España
b    Bob    30    Lima      Perú
c  Clara    22  Bogotá  Colombia
```

### Manejo de datos faltantes
Si hay valores faltantes, Pandas usa `NaN`. Puedes manejarlos con métodos como:
- `df.fillna(0)`: Rellena valores faltantes con 0.
- `df.dropna()`: Elimina filas con valores faltantes.

#### Ejemplo: DataFrame con datos faltantes
```python
datos = {
    'nombre': ['Ana', 'Bob', 'Clara'],
    'edad': [25, None, 22]
}
df = pd.DataFrame(datos)
print(df)
```
**Salida:**
```bash
   nombre  edad
0    Ana  25.0
1    Bob   NaN
2  Clara  22.0
```
Rellenar valores faltantes:
```python
df['edad'] = df['edad'].fillna(0)
print(df)
```
**Salida:**
```bash
   nombre  edad
0    Ana  25.0
1    Bob   0.0
2  Clara  22.0
```

---

## 3. Trabajar con Series y DataFrames
Algunas operaciones comunes que puedes realizar:

### Selección de datos
- **Por columna**: `df['columna']`.
- **Por filas y columnas** (usando `loc` o `iloc`):
  - `loc`: Selecciona por etiquetas de índice.
  - `iloc`: Selecciona por posición numérica.
```python
print(df.loc[0, 'nombre'])  # Salida: Ana
print(df.iloc[0, 0])        # Salida: Ana
```

### Ordenar datos
- Ordenar por una columna:
```python
print(df.sort_values('edad'))
```
**Salida:**
```bash
   nombre  edad
1    Bob   0.0
2  Clara  22.0
0    Ana  25.0
```

### Estadísticas básicas
- Obtener estadísticas de columnas numéricas:
```python
print(df['edad'].describe())
```
**Salida:**
```bash
count     3.0
mean     15.7
std      13.3
min       0.0
25%      11.0
50%      22.0
75%      23.5
max      25.0
Name: edad, dtype: float64
```

---

## 4. Leer y guardar datos
Pandas facilita leer y escribir datos en formatos como CSV, Excel, JSON, etc.

### Leer un archivo CSV
```python
# Leer un archivo CSV (asegúrate de que el archivo exista)
df = pd.read_csv('datos.csv')
print(df)
```

### Guardar un DataFrame como CSV
```python
df.to_csv('nuevo_archivo.csv', index=False)
```

---

## 5. Consejos prácticos
- **Explora tus datos**: Usa `df.head()` para ver las primeras filas o `df.info()` para un resumen de las columnas y tipos de datos.
- **Evita bucles**: Pandas está optimizado para operaciones vectorizadas. En lugar de recorrer filas, usa métodos como `apply` o filtros.
- **Documentación oficial**: Si necesitas más detalles, consulta https://pandas.pydata.org/docs/.

---

## Ejemplo completo
Aquí tienes un script que combina varias ideas:
```python
import pandas as pd

# Crear un DataFrame
datos = {
    'producto': ['Laptop', 'Teléfono', 'Tablet'],
    'precio': [1200, 800, 300],
    'stock': [10, 15, 5]
}
df = pd.DataFrame(datos)

# Agregar una columna con descuento
df['precio_descuento'] = df['precio'] * 0.9

# Filtrar productos con stock mayor a 5
print("Productos con stock > 5:")
print(df[df['stock'] > 5])

# Guardar como CSV
df.to_csv('inventario.csv', index=False)
```
**Salida:**
```bash
Productos con stock > 5:
   producto  precio  stock  precio_descuento
0   Laptop   1200     10           1080.0
1  Teléfono   800     15            720.0
```

---

## Referencia oficial
Consulta la documentación oficial de Pandas para más detalles:
[https://pandas.pydata.org/docs/user_guide/dsintro.html](https://pandas.pydata.org/docs/user_guide/dsintro.html)


