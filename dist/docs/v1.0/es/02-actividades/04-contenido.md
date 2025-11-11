---
title: "Actividad 4: Manejo de Datos con Pandas"
position: 4
date: 2025-11-11
---


Esta actividad está alineada con el contenido "Guía de Introducción a Estructuras de Datos en Pandas" [01-contenido/04-contenido.md](01-contenido/04-contenido.md). El objetivo es practicar Series y DataFrames, manejo de faltantes, selección, ordenamiento, estadísticas, y lectura/escritura de archivos.

## Dataset base para la actividad

Usa este DataFrame para los ejercicios. Incluye columnas numéricas y categóricas, índices personalizados y valores faltantes para practicar los temas.

```python
import pandas as pd

datos = {
    'nombre':   ['Ana', 'Bob', 'Clara', 'Diego', 'Eva'],
    'edad':     [25, 30, 22, None, 28],
    'ciudad':   ['Madrid', 'Lima', 'Bogotá', 'Medellín', None],
    'producto': ['Laptop', 'Teléfono', 'Tablet', 'Laptop', 'Tablet'],
    'precio':   [1200, 800, 300, 1150, None],
    'stock':    [10, 15, 5, 8, 0]
}

df = pd.DataFrame(datos, index=['a', 'b', 'c', 'd', 'e'])

# Guarda el dataset para ejercicios de lectura/escritura
df.to_csv('actividad_semana4.csv', index=True)
df
```

## Ejercicios por tema

### 1) Series — crear y operar
- Crea una Series desde una lista y otra desde un diccionario.
- Accede a elementos por índice, modifica un valor y realiza una operación matemática (por ejemplo, multiplicar por 2).


### 2) DataFrame — crear y explorar
- Crea un DataFrame desde un diccionario y aplica un índice personalizado.
- Accede a una columna, usa `loc` para una fila por etiqueta y `iloc` por posición.

### 3) Operaciones básicas
- Agrega una columna derivada (por ejemplo, `precio_descuento = precio * 0.9`).
- Aplica una operación vectorizada sobre una columna numérica.

### 4) Manejo de datos faltantes
- Detecta nulos con `isna` y cuenta faltantes por columna.
- Completa faltantes en `edad` con 0 y en `ciudad` con `'Desconocido'`.

### 5) Selección y filtrado
- Filtra filas con `precio > 500`.
- Filtra productos iguales a `'Laptop'` y stock mayor que 5.

### 6) Ordenar datos
- Ordena por `edad` ascendente.
- Ordena por `precio` descendente ignorando nulos (llena temporalmente nulos con 0 para ordenamiento).

### 7) Estadísticas básicas
- Obtén `describe()` para columnas numéricas.
- Obtén `value_counts()` para la columna `producto`.

### 8) Leer y guardar datos
- Lee el CSV creado (`actividad_semana4.csv`) y muestra las primeras filas.
- Guarda un nuevo CSV con columnas seleccionadas.

### 9) Ejercicio integrado
- Aplica descuento del 10% a `precio`, filtra productos con `stock > 5`, ordena por `precio_descuento` y guarda como `inventario_procesado.csv`.

## Entrega (por Fork en GitHub)

- Repo base: `https://github.com/jfinfosena/fdoc_cd_act4.git`.
- Realizar un Fork, clonar su fork y resolver los ejercicios.

