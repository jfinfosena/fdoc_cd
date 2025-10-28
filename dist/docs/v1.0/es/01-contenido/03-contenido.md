---
title: "Tipos de variables en análisis de datos"
position: 3
date: 2025-10-28
---

## 1. ¿QUÉ ES UNA VARIABLE?

Una **variable** es como una **columna en una tabla de Excel**.  
Cada columna tiene un nombre y contiene datos de un tipo específico.

Ejemplo:  
| Nombre | Edad | Ciudad | Salario |
|--------|------|--------|---------|
| Ana    | 25   | Madrid | 30000   |
| Luis   | 30   | Barcelona | 45000 |

Aquí hay 4 variables: `Nombre`, `Edad`, `Ciudad`, `Salario`.

---

## 2. TIPOS DE VARIABLES EN ANÁLISIS DE DATOS

Hay **3 grandes grupos**:

| Tipo | Ejemplos | ¿Para qué se usa? |
|------|--------|------------------|
| **Numéricas** | Edad, Salario, Peso | Sumar, promediar, gráficos |
| **Categóricas** | Ciudad, Género, Color | Contar, agrupar, filtrar |
| **Otras** | Fechas, Texto largo, IDs | Ordenar, extraer partes, limpiar |

Vamos a ver cada una **con ejemplos reales en código**.

---

## PREPARACIÓN: Importar Pandas y crear datos

```python
import pandas as pd

# Creamos una tabla (DataFrame) de ejemplo
data = {
    'Nombre': ['Ana', 'Luis', 'María', 'Pedro'],
    'Edad': [25, 30, 22, 35],
    'Ciudad': ['Madrid', 'Barcelona', 'Madrid', 'Valencia'],
    'Salario': [30000, 45000, 28000, 52000],
    'Fecha_Nacimiento': ['1998-05-10', '1993-03-15', '2001-07-22', '1988-11-30'],
    'ID_Empleado': ['E001', 'E002', 'E003', 'E004'],
    'Género': ['F', 'M', 'F', 'M']
}

df = pd.DataFrame(data)
print(df)
```

**Salida:**
```bash
  Nombre  Edad     Ciudad  Salario Fecha_Nacimiento ID_Empleado Género
0    Ana    25     Madrid    30000       1998-05-10        E001      F
1   Luis    30  Barcelona    45000       1993-03-15        E002      M
2  María    22     Madrid    28000       2001-07-22        E003      F
3  Pedro    35   Valencia    52000       1988-11-30        E004      M
```

---

## 1. VARIABLES NUMÉRICAS

Son números con los que **puedes hacer cálculos**.

### Subtipos:
| Tipo | Ejemplo | Operaciones |
|------|--------|-----------|
| **Enteros (int)** | Edad: 25, 30 | Sumar, restar |
| **Decimales (float)** | Salario: 30000.5 | Promedios, gráficos |

### ¿Cómo saber si una columna es numérica?

```python
print(df.dtypes)
```

**Salida:**
```bash
Nombre              object
Edad                 int64
Ciudad              object
Salario              int64
Fecha_Nacimiento    object
ID_Empleado         object
Género              object
dtype: object
```

- `int64` → número entero  
- `float64` → número con decimales  
- `object` → texto o mixto

### Ejemplos de uso:

```python
# Promedio de edad
print("Edad promedio:", df['Edad'].mean())

# Salario más alto
print("Salario máximo:", df['Salario'].max())

# Suma total de salarios
print("Suma de salarios:", df['Salario'].sum())
```

**Salida:**
```bash
Edad promedio: 28.0
Salario máximo: 52000
Suma de salarios: 155000
```

---

## 2. VARIABLES CATEGÓRICAS

Son **etiquetas**, no números para calcular.  
Sirven para **clasificar** o **agrupar**.

### Subtipos:
| Tipo | Ejemplo | ¿Repetidas? |
|------|--------|-----------|
| **Nominales** | Ciudad, Género | No tienen orden |
| **Ordinales** | Nivel: Bajo, Medio, Alto | Tienen orden |

### En nuestro ejemplo:
- `Ciudad`: Madrid, Barcelona → **Nominal**
- `Género`: M, F → **Nominal**

### ¿Cómo convertir a categórica en Pandas?

```python
# Convertimos 'Ciudad' a tipo categórico
df['Ciudad'] = df['Ciudad'].astype('category')

# Convertimos 'Género' también
df['Género'] = df['Género'].astype('category')

print(df.dtypes)
```

**Salida:**
```bash
Nombre              object
Edad                 int64
Ciudad            category
Salario              int64
Fecha_Nacimiento    object
ID_Empleado         object
Género            category
dtype: object
```

> **Ventaja**: ocupa menos memoria y es más rápido para agrupar.

### Ejemplos de uso:

```python
# ¿Cuántas personas por ciudad?
print(df['Ciudad'].value_counts())
```

**Salida:**
```bash
Madrid       2
Barcelona    1
Valencia     1
Name: Ciudad, dtype: int64
```

```python
# ¿Cuántos hombres y mujeres?
print(df['Género'].value_counts())
```

**Salida:**
```bash
F    2
M    2
Name: Género, dtype: int64
```

```python
# Filtrar solo personas de Madrid
madrid = df[df['Ciudad'] == 'Madrid']
print(madrid[['Nombre', 'Salario']])
```

**Salida:**
```bash
  Nombre  Salario
0    Ana    30000
2  María    28000
```

---

# 3. OTRAS VARIABLES IMPORTANTES

## A. Fechas (Datetime)

No son números ni categorías → son **fechas**.

```python
# Convertir 'Fecha_Nacimiento' a fecha
df['Fecha_Nacimiento'] = pd.to_datetime(df['Fecha_Nacimiento'])

print(df['Fecha_Nacimiento'])
```

**Salida:**
```bash
0   1998-05-10
1   1993-03-15
2   2001-07-22
3   1988-11-30
Name: Fecha_Nacimiento, dtype: datetime64[ns]
```

### Ejemplos útiles:

```python
# Edad actual (aproximada)
from datetime import datetime
hoy = datetime.now()
df['Edad_Calculada'] = (hoy - df['Fecha_Nacimiento']).dt.days // 365
print(df[['Nombre', 'Edad', 'Edad_Calculada']])
```

> Extrae el año, mes, día, etc.

```python
print(df['Fecha_Nacimiento'].dt.year)  # Solo el año
print(df['Fecha_Nacimiento'].dt.month) # Solo el mes
```

---

## B. Texto (Strings / object)

- `Nombre`, `ID_Empleado` → son texto

```python
# Poner nombres en mayúsculas
df['Nombre_Mayus'] = df['Nombre'].str.upper()
print(df[['Nombre', 'Nombre_Mayus']])
```

**Salida:**
```bash
  Nombre Nombre_Mayus
0    Ana          ANA
1   Luis         LUIS
2  María        MARÍA
3  Pedro        PEDRO
```

```python
# ¿El ID empieza con 'E0'?
df['Es_Empleado_Reciente'] = df['ID_Empleado'].str.startswith('E00')
print(df[['ID_Empleado', 'Es_Empleado_Reciente']])
```

---

## C. Variables Booleanas (True/False)

Muy útiles para filtros.

```python
# ¿Es mayor de 30 años?
df['Mayor_30'] = df['Edad'] > 30
print(df[['Nombre', 'Edad', 'Mayor_30']])
```

**Salida:**
```bash
  Nombre  Edad  Mayor_30
0    Ana    25     False
1   Luis    30     False
2  María    22     False
3  Pedro    35      True
```

---

# RESUMEN VISUAL: TIPOS DE VARIABLES

| Variable | Tipo en Pandas | Ejemplo | Operaciones comunes |
|--------|----------------|--------|---------------------|
| Edad | `int64` | 25 | `.mean()`, `.sum()` |
| Salario | `int64` | 30000 | `.max()`, gráficos |
| Ciudad | `category` | Madrid | `.value_counts()` |
| Género | `category` | F | Contar, agrupar |
| Fecha_Nacimiento | `datetime64` | 1998-05-10 | extraer año, calcular edad |
| Nombre | `object` | Ana | `.str.upper()` |
| ID_Empleado | `object` | E001 | `.str.contains()` |
| Mayor_30 | `bool` | True | Filtrar |

---

# TRUCO FINAL: ¿Cómo saber el tipo de cada columna automáticamente?

```python
print(df.info())
```

Te dice:
- Nombre de columna
- Tipo de dato
- Cuántos valores no nulos

---

# CONSEJOS CLAVE (LO PRINCIPAL)

| Consejo | Por qué |
|-------|--------|
| Usa `category` para variables con pocas opciones repetidas | Ahorra memoria y acelera |
| Usa `datetime` para fechas | Puedes calcular diferencias |
| Usa `.value_counts()` para categóricas | Ves rápido la distribución |
| Usa `.describe()` para numéricas | Te da resumen estadístico |

```python
print(df.describe())  # Solo numéricas
print(df['Ciudad'].describe())  # Para categóricas
```

---

# EJERCICIO RÁPIDO (para practicar)

```python
# 1. Crea una columna "Salario_Anual" = Salario * 12
# 2. Crea una columna "Es_Joven" = True si Edad < 25
# 3. ¿Cuántas personas son de Madrid y ganan más de 30000?

# Solución:
df['Salario_Anual'] = df['Salario'] * 12
df['Es_Joven'] = df['Edad'] < 25

filtro = (df['Ciudad'] == 'Madrid') & (df['Salario'] > 30000)
print(df[filtro]['Nombre'])
```

---

## Notas

| Tipo | Cómo identificarlo | Cómo usarlo |
|------|---------------------|------------|
| **Numérica** | `int` o `float` | Cálculos, gráficos |
| **Categórica** | Pocas opciones repetidas | `category`, `value_counts()` |
| **Fecha** | Fechas | `pd.to_datetime()` |
| **Texto** | Nombres, IDs | `.str` métodos |
| **Booleana** | True/False | Filtros |

---

