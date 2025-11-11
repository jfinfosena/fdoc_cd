---
title: "Actividad 5: Pandas básico (Series y DataFrames)"
position: 5
date: 2025-11-11
---

Esta actividad está alineada con [01-contenido/05-contenido.md](01-contenido/05-contenido.md) (Guía Básica de Pandas). Trabajarás con Series y DataFrames, inspección, acceso a datos, operaciones básicas, filtrado, manejo de valores faltantes y lectura/escritura de archivos.

## Dataset base para la actividad

Usa este DataFrame para resolver los ejercicios. Incluye tipos mixtos y valores faltantes para practicar inspección, selección, operaciones y limpieza.

```python
import pandas as pd

datos = {
    'Nombre':  ['Ana', 'Bob', 'Clara', 'Diego', 'Eva'],
    'Edad':    [25, 30, 22, None, 28],
    'Ciudad':  ['Madrid', 'Lima', 'Bogotá', 'Medellín', None],
    'Ingreso': [3000, 4500, 2800, 5000, None]
}

df = pd.DataFrame(datos)

# Guarda el dataset base para ejercicios de lectura/escritura
df.to_csv('actividad_semana5.csv', index=False)
df.head()
```

## Ejercicios por tema

1) Series — crear y operar
- Crea una Series desde una lista y otra desde un diccionario.
- Accede por índice/clave, modifica un valor y aplica una operación (p. ej., multiplicar por 2).

2) DataFrame — crear y explorar
- Crea un DataFrame pequeño desde un diccionario (puedes reutilizar `datos`).
- Asigna nombres de columnas y verifica el tipo de cada columna.

3) Inspeccionar y explorar
- Muestra las primeras y últimas filas con `head` y `tail`.
- Obtén `info`, `shape` y `describe`.

4) Acceder a columnas y filas
- Obtén la columna `Nombre` como Series.
- Obtén la fila con índice 1 usando `loc` y `iloc`.
- Accede al valor específico (fila 1, columna `Edad`).

5) Operaciones básicas
- Incrementa `Edad` en 5 años.
- Crea una columna `Ingreso_anual` multiplicando `Ingreso` por 12 (maneja nulos con 0).

6) Filtrar datos
- Filtra filas con `Edad > 30`.
- Filtra filas donde `Ciudad` es `'Madrid'` o `'Lima'`.

7) Manejo de valores faltantes
- Detecta nulos con `isna` y cuenta faltantes por columna.
- Rellena nulos: `Edad` con 0, `Ciudad` con `'Desconocido'`, `Ingreso` con la mediana.

8) Leer y guardar datos
- Lee el CSV creado (`actividad_semana5.csv`) y muestra las primeras filas.
- Guarda un CSV con columnas seleccionadas (`Nombre`, `Edad`, `Ciudad`).

9) Ejercicio integrado
- Incrementa `Edad` en 5, filtra personas con `Ingreso_anual > 36000`, ordena por `Ingreso_anual` descendente y guarda como `personas_filtradas.csv`.


## Entrega (por Fork en GitHub)

- Repo base: `https://github.com/jfinfosena/fdoc_cd_act5.git`.
- Realizar un Fork, clonar su fork y resolver los ejercicios.
