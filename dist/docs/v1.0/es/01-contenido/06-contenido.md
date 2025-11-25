---
title: "Filtros, Condiciones y Limpieza de Datos con Pandas"
position: 6
date: 2025-11-25
---

## Objetivos de Aprendizaje

Al finalizar esta semana, el estudiante será capaz de:

- Aplicar filtros y condiciones para seleccionar datos específicos
- Implementar técnicas de limpieza de datos
- Preparar datasets para análisis posteriores
- Manejar valores faltantes y duplicados

## 1. Filtrado de Datos y Operadores Condicionales

### 1.1 Introducción a los Filtros en Pandas

El filtrado de datos es una de las operaciones más fundamentales en el análisis de datos. Pandas proporciona múltiples formas de filtrar DataFrames utilizando operadores condicionales, métodos especializados y expresiones lógicas.

```python
import pandas as pd
import numpy as np
from datetime import datetime, timedelta

# Crear un DataFrame más completo para ejemplos
data = {
    'nombre': ['Ana García', 'Carlos López', 'María Rodríguez', 'Juan Pérez', 'Sofía Martín', 
               'Pedro Sánchez', 'Laura González', 'Miguel Torres', 'Carmen Ruiz', 'David Moreno'],
    'edad': [25, 30, 22, 35, 28, 45, 33, 29, 41, 26],
    'salario': [50000, 75000, 45000, 80000, 60000, 95000, 70000, 55000, 85000, 48000],
    'departamento': ['IT', 'Ventas', 'IT', 'Marketing', 'Ventas', 'IT', 'RRHH', 'Marketing', 'RRHH', 'Ventas'],
    'fecha_ingreso': ['2020-01-15', '2019-03-20', '2021-06-10', '2018-11-05', '2020-09-12',
                      '2017-02-28', '2019-08-14', '2021-01-30', '2018-05-22', '2020-12-03'],
    'activo': [True, True, True, False, True, True, True, True, False, True],
    'horas_semanales': [40, 45, 38, 40, 42, 48, 40, 35, 40, 44]
}

df = pd.DataFrame(data)
df['fecha_ingreso'] = pd.to_datetime(df['fecha_ingreso'])

print("DataFrame completo:")
print(df)
print("\nInformación del DataFrame:")
print(df.info())
```

### 1.2 Operadores de Comparación

#### 1.2.1 Operadores Básicos de Comparación

```python
# Operador de igualdad (==)
print("=== OPERADOR DE IGUALDAD (==) ===")
empleados_it = df[df['departamento'] == 'IT']
print("Empleados del departamento IT:")
print(empleados_it[['nombre', 'departamento']])

# Operador de desigualdad (!=)
print("\n=== OPERADOR DE DESIGUALDAD (!=) ===")
no_it = df[df['departamento'] != 'IT']
print("Empleados que NO son del departamento IT:")
print(no_it[['nombre', 'departamento']])

# Operador mayor que (>)
print("\n=== OPERADOR MAYOR QUE (>) ===")
salario_alto = df[df['salario'] > 70000]
print("Empleados con salario mayor a 70,000:")
print(salario_alto[['nombre', 'salario']])

# Operador menor que (<)
print("\n=== OPERADOR MENOR QUE (<) ===")
empleados_jovenes = df[df['edad'] < 30]
print("Empleados menores de 30 años:")
print(empleados_jovenes[['nombre', 'edad']])

# Operador mayor o igual que (>=)
print("\n=== OPERADOR MAYOR O IGUAL QUE (>=) ===")
experiencia_media = df[df['edad'] >= 30]
print("Empleados de 30 años o más:")
print(experiencia_media[['nombre', 'edad']])

# Operador menor o igual que (<=)
print("\n=== OPERADOR MENOR O IGUAL QUE (<=) ===")
salario_medio = df[df['salario'] <= 60000]
print("Empleados con salario de 60,000 o menos:")
print(salario_medio[['nombre', 'salario']])
```

#### 1.2.2 Comparaciones con Fechas

```python
print("\n=== FILTROS CON FECHAS ===")

# Empleados que ingresaron después de 2020
fecha_corte = pd.to_datetime('2020-01-01')
ingresos_recientes = df[df['fecha_ingreso'] > fecha_corte]
print("Empleados que ingresaron después del 1 de enero de 2020:")
print(ingresos_recientes[['nombre', 'fecha_ingreso']])

# Empleados con más de 3 años en la empresa
fecha_limite = datetime.now() - timedelta(days=3*365)
veteranos = df[df['fecha_ingreso'] < fecha_limite]
print("\nEmpleados con más de 3 años en la empresa:")
print(veteranos[['nombre', 'fecha_ingreso']])
```

### 1.3 Operadores Lógicos

#### 1.3.1 Operador AND (&)

```python
print("\n=== OPERADOR AND (&) ===")

# Empleados jóvenes del departamento IT
jovenes_it = df[(df['edad'] < 30) & (df['departamento'] == 'IT')]
print("Empleados menores de 30 años Y del departamento IT:")
print(jovenes_it[['nombre', 'edad', 'departamento']])

# Empleados con salario alto y activos
salario_alto_activos = df[(df['salario'] > 70000) & (df['activo'] == True)]
print("\nEmpleados con salario > 70,000 Y que están activos:")
print(salario_alto_activos[['nombre', 'salario', 'activo']])

# Múltiples condiciones AND
condiciones_multiples = df[
    (df['edad'] >= 25) & 
    (df['edad'] <= 35) & 
    (df['salario'] > 50000) & 
    (df['activo'] == True)
]
print("\nEmpleados entre 25-35 años, salario > 50,000 y activos:")
print(condiciones_multiples[['nombre', 'edad', 'salario', 'activo']])
```

#### 1.3.2 Operador OR (|)

```python
print("\n=== OPERADOR OR (|) ===")

# Empleados muy jóvenes o muy experimentados
edades_extremas = df[(df['edad'] < 25) | (df['edad'] > 40)]
print("Empleados menores de 25 años O mayores de 40:")
print(edades_extremas[['nombre', 'edad']])

# Empleados de IT o Marketing
it_marketing = df[(df['departamento'] == 'IT') | (df['departamento'] == 'Marketing')]
print("\nEmpleados de IT O Marketing:")
print(it_marketing[['nombre', 'departamento']])

# Salarios muy altos o muy bajos
salarios_extremos = df[(df['salario'] < 50000) | (df['salario'] > 80000)]
print("\nEmpleados con salario < 50,000 O > 80,000:")
print(salarios_extremos[['nombre', 'salario']])
```

#### 1.3.3 Operador NOT (~)

```python
print("\n=== OPERADOR NOT (~) ===")

# Empleados que NO son del departamento IT
no_it = df[~(df['departamento'] == 'IT')]
print("Empleados que NO son del departamento IT:")
print(no_it[['nombre', 'departamento']])

# Empleados que NO están activos
inactivos = df[~df['activo']]
print("\nEmpleados que NO están activos:")
print(inactivos[['nombre', 'activo']])

# Negación de condiciones complejas
no_jovenes_it = df[~((df['edad'] < 30) & (df['departamento'] == 'IT'))]
print("\nEmpleados que NO son (jóvenes Y de IT):")
print(no_jovenes_it[['nombre', 'edad', 'departamento']])
```

### 1.4 Métodos de Filtrado Avanzados

#### 1.4.1 Método isin()

```python
print("\n=== MÉTODO isin() ===")

# Filtrar por múltiples departamentos
departamentos_tecnicos = ['IT', 'Marketing']
empleados_tecnicos = df[df['departamento'].isin(departamentos_tecnicos)]
print("Empleados de departamentos técnicos (IT, Marketing):")
print(empleados_tecnicos[['nombre', 'departamento']])

# Filtrar por múltiples edades específicas
edades_especificas = [25, 30, 35]
empleados_edades_esp = df[df['edad'].isin(edades_especificas)]
print("\nEmpleados con edades específicas (25, 30, 35):")
print(empleados_edades_esp[['nombre', 'edad']])

# Negación con isin()
no_tecnicos = df[~df['departamento'].isin(departamentos_tecnicos)]
print("\nEmpleados que NO son de departamentos técnicos:")
print(no_tecnicos[['nombre', 'departamento']])
```

#### 1.4.2 Método between()

```python
print("\n=== MÉTODO between() ===")

# Empleados en rango de edad
edad_media = df[df['edad'].between(25, 35)]
print("Empleados entre 25 y 35 años (inclusive):")
print(edad_media[['nombre', 'edad']])

# Salarios en rango específico
salario_medio = df[df['salario'].between(50000, 75000)]
print("\nEmpleados con salario entre 50,000 y 75,000:")
print(salario_medio[['nombre', 'salario']])

# between() con fechas
fecha_inicio = pd.to_datetime('2019-01-01')
fecha_fin = pd.to_datetime('2020-12-31')
ingresos_periodo = df[df['fecha_ingreso'].between(fecha_inicio, fecha_fin)]
print("\nEmpleados que ingresaron entre 2019 y 2020:")
print(ingresos_periodo[['nombre', 'fecha_ingreso']])
```

#### 1.4.3 Filtros con Strings

```python
print("\n=== FILTROS CON STRINGS ===")

# Nombres que contienen una subcadena
nombres_con_a = df[df['nombre'].str.contains('a', case=False)]
print("Empleados cuyo nombre contiene 'a' (sin distinción de mayúsculas):")
print(nombres_con_a[['nombre']])

# Nombres que empiezan con una letra específica
nombres_m = df[df['nombre'].str.startswith('M')]
print("\nEmpleados cuyo nombre empieza con 'M':")
print(nombres_m[['nombre']])

# Nombres que terminan con una subcadena
nombres_ez = df[df['nombre'].str.endswith('ez')]
print("\nEmpleados cuyo apellido termina en 'ez':")
print(nombres_ez[['nombre']])

# Filtros con expresiones regulares
import re
nombres_patron = df[df['nombre'].str.contains(r'^[A-M]', regex=True)]
print("\nEmpleados cuyo nombre empieza con letras A-M:")
print(nombres_patron[['nombre']])
```

### 1.5 Método query()

#### 1.5.1 Sintaxis Básica de query()

```python
print("\n=== MÉTODO query() - SINTAXIS BÁSICA ===")

# Consulta simple
resultado1 = df.query('edad > 30')
print("Empleados mayores de 30 años (usando query):")
print(resultado1[['nombre', 'edad']])

# Múltiples condiciones con and
resultado2 = df.query('edad > 25 and salario > 60000')
print("\nEmpleados > 25 años y salario > 60,000:")
print(resultado2[['nombre', 'edad', 'salario']])

# Múltiples condiciones con or
resultado3 = df.query('departamento == "IT" or departamento == "Marketing"')
print("\nEmpleados de IT o Marketing:")
print(resultado3[['nombre', 'departamento']])
```

#### 1.5.2 query() Avanzado

```python
print("\n=== MÉTODO query() - AVANZADO ===")

# Usando variables externas
edad_minima = 30
salario_minimo = 70000
resultado4 = df.query('edad >= @edad_minima and salario >= @salario_minimo')
print(f"Empleados >= {edad_minima} años y salario >= {salario_minimo}:")
print(resultado4[['nombre', 'edad', 'salario']])

# Consultas con listas
departamentos = ['IT', 'RRHH']
resultado5 = df.query('departamento in @departamentos')
print(f"\nEmpleados en departamentos {departamentos}:")
print(resultado5[['nombre', 'departamento']])

# Consultas complejas
resultado6 = df.query('(edad < 30 and salario > 50000) or (edad > 40 and departamento == "IT")')
print("\nEmpleados jóvenes con buen salario O veteranos de IT:")
print(resultado6[['nombre', 'edad', 'salario', 'departamento']])
```

### 1.6 Filtros con Condiciones Múltiples y Complejas

#### 1.6.1 Combinando Múltiples Operadores

```python
print("\n=== CONDICIONES MÚLTIPLES Y COMPLEJAS ===")

# Condición muy específica
condicion_compleja = df[
    ((df['edad'] >= 25) & (df['edad'] <= 35)) &  # Edad entre 25-35
    (df['salario'] > df['salario'].median()) &   # Salario sobre la mediana
    (df['activo'] == True) &                     # Empleado activo
    (df['horas_semanales'] >= 40)                # Tiempo completo
]
print("Empleados que cumplen condiciones complejas:")
print(condicion_compleja[['nombre', 'edad', 'salario', 'activo', 'horas_semanales']])

# Usando funciones lambda para condiciones personalizadas
def es_senior(row):
    return row['edad'] > 35 and row['salario'] > 75000

seniors = df[df.apply(es_senior, axis=1)]
print("\nEmpleados senior (>35 años y salario >75,000):")
print(seniors[['nombre', 'edad', 'salario']])
```

#### 1.6.2 Filtros Dinámicos

```python
print("\n=== FILTROS DINÁMICOS ===")

# Función para crear filtros dinámicos
def filtrar_empleados(df, edad_min=None, edad_max=None, salario_min=None, 
                     departamentos=None, solo_activos=False):
    """
    Función para filtrar empleados con múltiples criterios opcionales
    """
    resultado = df.copy()
    
    if edad_min is not None:
        resultado = resultado[resultado['edad'] >= edad_min]
    
    if edad_max is not None:
        resultado = resultado[resultado['edad'] <= edad_max]
    
    if salario_min is not None:
        resultado = resultado[resultado['salario'] >= salario_min]
    
    if departamentos is not None:
        resultado = resultado[resultado['departamento'].isin(departamentos)]
    
    if solo_activos:
        resultado = resultado[resultado['activo'] == True]
    
    return resultado

# Ejemplos de uso de filtros dinámicos
print("Filtro 1 - Solo empleados activos de IT con salario > 60,000:")
filtro1 = filtrar_empleados(df, salario_min=60000, departamentos=['IT'], solo_activos=True)
print(filtro1[['nombre', 'departamento', 'salario', 'activo']])

print("\nFiltro 2 - Empleados entre 25-40 años:")
filtro2 = filtrar_empleados(df, edad_min=25, edad_max=40)
print(filtro2[['nombre', 'edad']])
```

## 2. Manejo de Valores Faltantes

### 2.1 Identificación de Valores Nulos

```python
# Crear DataFrame con valores faltantes
data_con_nulos = {
    'A': [1, 2, np.nan, 4, 5],
    'B': [np.nan, 2, 3, 4, np.nan],
    'C': [1, 2, 3, 4, 5]
}
df_nulos = pd.DataFrame(data_con_nulos)

# Verificar valores nulos
print(df_nulos.isnull())
print(df_nulos.isnull().sum())
print(df_nulos.info())
```

### 2.2 Tratamiento de Valores Faltantes

```python
# Eliminar filas con valores nulos
df_sin_nulos = df_nulos.dropna()

# Eliminar columnas con valores nulos
df_sin_columnas_nulas = df_nulos.dropna(axis=1)

# Rellenar valores nulos
df_rellenado = df_nulos.fillna(0)  # Con cero
df_rellenado_media = df_nulos.fillna(df_nulos.mean())  # Con la media
df_rellenado_anterior = df_nulos.fillna(method='ffill')  # Valor anterior
```

## 3. Limpieza de Datos

### 3.1 Eliminación de Duplicados

```python
# Crear DataFrame con duplicados
data_duplicados = {
    'nombre': ['Ana', 'Carlos', 'Ana', 'María', 'Carlos'],
    'edad': [25, 30, 25, 22, 30]
}
df_dup = pd.DataFrame(data_duplicados)

# Identificar duplicados
print(df_dup.duplicated())

# Eliminar duplicados
df_sin_duplicados = df_dup.drop_duplicates()

# Eliminar duplicados basado en columnas específicas
df_sin_dup_nombre = df_dup.drop_duplicates(subset=['nombre'])
```

### 3.2 Transformación de Datos

```python
# Convertir tipos de datos
df['edad'] = df['edad'].astype('int32')
df['salario'] = df['salario'].astype('float64')

# Limpiar texto
df['nombre'] = df['nombre'].str.strip()  # Eliminar espacios
df['nombre'] = df['nombre'].str.upper()  # Convertir a mayúsculas

# Reemplazar valores
df['departamento'] = df['departamento'].replace('IT', 'Tecnología')
```

## 4. Validación y Preparación de Datos

### 4.1 Validación de Rangos

```python
# Validar rangos de edad
edades_validas = df[(df['edad'] >= 18) & (df['edad'] <= 65)]

# Identificar outliers usando IQR
Q1 = df['salario'].quantile(0.25)
Q3 = df['salario'].quantile(0.75)
IQR = Q3 - Q1
limite_inferior = Q1 - 1.5 * IQR
limite_superior = Q3 + 1.5 * IQR

sin_outliers = df[(df['salario'] >= limite_inferior) & (df['salario'] <= limite_superior)]
```

### 4.2 Normalización y Estandarización

```python
from sklearn.preprocessing import StandardScaler, MinMaxScaler

# Normalización (0-1)
scaler_minmax = MinMaxScaler()
df['salario_normalizado'] = scaler_minmax.fit_transform(df[['salario']])

# Estandarización (media=0, std=1)
scaler_standard = StandardScaler()
df['salario_estandarizado'] = scaler_standard.fit_transform(df[['salario']])
```

## 5. Ejercicios Prácticos

### Ejercicio 1: Limpieza Completa

```python
# Dataset de ejemplo con problemas comunes
data_problematica = {
    'nombre': ['  Ana  ', 'CARLOS', 'maría', '  Juan', 'Sofía', 'Ana'],
    'edad': [25, 30, np.nan, 35, 28, 25],
    'email': ['ana@email.com', 'CARLOS@EMAIL.COM', 'maria@email', 'juan@email.com', None, 'ana@email.com'],
    'salario': [50000, 75000, 45000, 999999, 60000, 50000]  # 999999 es outlier
}

df_problematico = pd.DataFrame(data_problematica)

# Proceso de limpieza paso a paso
# 1. Limpiar nombres
df_limpio = df_problematico.copy()
df_limpio['nombre'] = df_limpio['nombre'].str.strip().str.title()

# 2. Manejar valores faltantes
df_limpio['edad'].fillna(df_limpio['edad'].median(), inplace=True)
df_limpio.dropna(subset=['email'], inplace=True)

# 3. Validar emails
df_limpio = df_limpio[df_limpio['email'].str.contains('@.*\.', regex=True)]

# 4. Eliminar duplicados
df_limpio.drop_duplicates(inplace=True)

# 5. Tratar outliers
Q1 = df_limpio['salario'].quantile(0.25)
Q3 = df_limpio['salario'].quantile(0.75)
IQR = Q3 - Q1
df_limpio = df_limpio[
    (df_limpio['salario'] >= Q1 - 1.5 * IQR) & 
    (df_limpio['salario'] <= Q3 + 1.5 * IQR)
]

print("Dataset original:")
print(df_problematico)
print("\nDataset limpio:")
print(df_limpio)
```

## 6. Mejores Prácticas

### 6.1 Pipeline de Limpieza

```python
def limpiar_dataset(df):
    """
    Pipeline de limpieza de datos
    """
    df_limpio = df.copy()
    
    # 1. Eliminar duplicados
    df_limpio.drop_duplicates(inplace=True)
    
    # 2. Manejar valores faltantes
    for columna in df_limpio.select_dtypes(include=[np.number]).columns:
        df_limpio[columna].fillna(df_limpio[columna].median(), inplace=True)
    
    for columna in df_limpio.select_dtypes(include=['object']).columns:
        df_limpio[columna].fillna('Desconocido', inplace=True)
    
    # 3. Limpiar texto
    for columna in df_limpio.select_dtypes(include=['object']).columns:
        df_limpio[columna] = df_limpio[columna].str.strip()
    
    return df_limpio

# Usar el pipeline
df_resultado = limpiar_dataset(df_problematico)
```



