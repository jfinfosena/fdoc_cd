---
title: "Actividad 3: Exposición Conjunto de Datos"
position: 3
date: 2025-11-04
---

```admonition
type: info
title: Objetivo
---
El grupo de trabajo presentará una exposición detallada sobre un conjunto de datos seleccionado para un proyecto de análisis de datos. La actividad busca justificar la elección del conjunto, explorar su contenido, proyectar resultados posibles y evaluar su utilidad para un proyecto de analítica de datos. Además, se propone reflexionar sobre la calidad de los datos, posibles visualizaciones, filtros dinámicos y su relevancia para la toma de decisiones.
```

### Estructura de la Exposición

**Duración estimada**: 20-30 minutos por grupo (15 minutos de presentación + 5-10 minutos de preguntas y retroalimentación).

**Pasos de la actividad**:


```steps
### Primer Paso
**Introducción y Justificación del Conjunto de Datos (5 minutos)**  
   - **Tarea**: Explicar por qué se seleccionó el conjunto de datos.  
     - ¿Qué problema o pregunta de negocio busca resolver?  
     - ¿Por qué este conjunto es relevante para el contexto del proyecto?  
     - ¿Qué características del conjunto (tamaño, variables, fuente) lo hacen adecuado?  
   - **Ejemplo**: Si el conjunto es sobre ventas de una tienda en línea, justificar cómo puede ayudar a optimizar estrategias de marketing o predecir tendencias de consumo.

### Segundo Paso
**Descripción Completa del Conjunto de Datos (5 minutos)**  
   - **Tarea**: Presentar toda la información relevante del conjunto de datos:  
     - **Fuente**: ¿De dónde proviene? (Kaggle, gobierno, API, etc.)  
     - **Tamaño**: Número de filas y columnas.  
     - **Variables**: Tipos de datos (numéricos, categóricos, fechas, etc.), descripción de cada columna y su significado.  
     - **Calidad**: ¿Existen datos faltantes, duplicados o inconsistencias? ¿Qué preprocesamiento se necesita?  
     - **Ejemplo**: Mostrar una tabla con las primeras filas del conjunto o un resumen estadístico (media, mediana, valores únicos, etc.).

### Tercer Paso
**Proyección de Resultados (5 minutos)**  
   - **Tarea**: Explicar qué se puede obtener del conjunto de datos:  
     - **Preguntas clave**: ¿Qué hipótesis o preguntas pueden responderse? (Ej. ¿Qué productos generan más ingresos? ¿Cómo varía el comportamiento del cliente por región?)  
     - **Análisis posibles**:  
       - Análisis descriptivo (resumen de tendencias).  
       - Análisis predictivo (modelos de machine learning para predecir ventas, churn, etc.).  
       - Análisis prescriptivo (recomendaciones basadas en los datos).  
     - **Limitaciones**: ¿Qué no se puede obtener con este conjunto? ¿Faltan variables clave?  
   - **Criterios de evaluación**:  
     - Viabilidad de las preguntas planteadas.  
     - Creatividad y relevancia de los análisis propuestos.

### Cuarto Paso
**Evaluación de Utilidad y Recomendaciones (3 minutos)**  
   - **Tarea**: Reflexionar sobre si el conjunto de datos es adecuado para un proyecto de analítica de datos:  
     - ¿Los datos son suficientes para tomar decisiones accionables?  
     - ¿Es necesario complementar con otros conjuntos de datos?  
     - ¿Se recomienda cambiar el conjunto? Si sí, ¿por qué y qué alternativas se sugieren?  
   - **Ejemplo**: Si el conjunto tiene datos de ventas pero no incluye información demográfica, podría limitar análisis de segmentación de clientes.  


### Quinto Paso
**Visualizaciones y Filtros Dinámicos Propuestos (2 minutos)**  
   - **Tarea**: Sugerir posibles visualizaciones y filtros dinámicos para explorar los datos:  
     - **Gráficos sugeridos** (según el tipo de datos):  
       - **Histogramas**: Para distribuciones de variables numéricas (ej. distribución de precios de productos).  
       - **Gráficos de barras**: Para comparar categorías (ej. ventas por región o categoría de producto).  
       - **Gráficos de líneas**: Para tendencias temporales (ej. ventas mensuales).  
       - **Gráficos de dispersión**: Para relaciones entre variables (ej. precio vs. cantidad vendida).  
       - **Mapas de calor**: Para correlaciones entre variables numéricas.  
       - **Gráficos de pastel o anillo**: Para mostrar proporciones (ej. porcentaje de ventas por canal).  
     - **Filtros dinámicos**:  
       - Filtros por fechas (ej. seleccionar un rango temporal).  
       - Filtros por categorías (ej. región, tipo de cliente, producto).  
       - Filtros por valores numéricos (ej. ventas mayores a X).  
     - **Ejemplo**: Si el conjunto tiene datos de ventas por región y fecha, proponer un dashboard con un gráfico de barras de ventas por región, filtrable por mes o año.  
```

---

### Evaluación Final

**Criterios Generales**:  
- Claridad y estructura de la presentación.  
- Profundidad en la justificación y análisis del conjunto de datos.  
- Creatividad en las proyecciones, visualizaciones y filtros.  
- Capacidad para identificar limitaciones y proponer soluciones.  


## Ejemplo Completo de Actividad: Exposición de Ciencia de Datos

**Contexto**: Un grupo de trabajo ha seleccionado un conjunto de datos sobre **"Consumo Energético en Hogares"** (ej. un conjunto como el "Household Electric Power Consumption" de UCI Machine Learning Repository o datos abiertos de una compañía eléctrica). Este conjunto será usado para un proyecto de analítica de datos enfocado en optimizar el consumo energético, identificar patrones de uso y proponer estrategias de sostenibilidad.

**Objetivo de la Actividad**: El grupo justificará la elección del conjunto, describirá su contenido, proyectará posibles análisis, propondrá visualizaciones y filtros dinámicos, y evaluará si los datos son adecuados para un proyecto de analítica de datos o si deben cambiarse. La exposición debe convencer a un "stakeholder" (ej. una empresa de servicios públicos o un organismo de sostenibilidad) de la utilidad de los datos.

---

### Estructura de la Exposición

**Duración**: 25 minutos (15 minutos de exposición + 10 minutos de preguntas y retroalimentación).

#### 1. Justificación de la Selección del Conjunto de Datos (5 minutos)

**Por qué se eligió**:  
El conjunto de datos sobre consumo energético en hogares fue seleccionado porque:  
- **Relevancia**: La eficiencia energética es clave para reducir costos, mitigar el impacto ambiental y cumplir con regulaciones de sostenibilidad.  
- **Alcance**: Permite analizar patrones de consumo por hora, día o temporada, identificar hogares con alto consumo y proponer estrategias de optimización (ej. tarifas dinámicas).  
- **Disponibilidad**: Los datos provienen de una fuente confiable (ej. medidores inteligentes de una compañía eléctrica), con alta granularidad temporal.  

**Contexto del proyecto**:  
El objetivo es responder preguntas como:  
- ¿Cuándo ocurren los picos de consumo energético?  
- ¿Qué factores (ej. hora del día, clima) influyen en el consumo?  
- ¿Es posible predecir el consumo futuro para optimizar la red eléctrica?  

#### 2. Descripción Completa del Conjunto de Datos (5 minutos)

**Detalles del conjunto**:  
- **Fuente**: Datos de medidores inteligentes de una compañía eléctrica (ej. UCI Household Electric Power Consumption).  
- **Tamaño**: 2,000,000 filas, 9 columnas.  
- **Variables**:  
  - **Fecha y hora**: Timestamp de la medición (formato: AAAA-MM-DD HH:MM).  
  - **Consumo total**: Consumo eléctrico en kWh (numérico).  
  - **Voltaje**: En voltios (numérico).  
  - **Intensidad**: En amperios (numérico).  
  - **Consumo por submedidor**: Consumo en cocina, lavandería y climatización (numéricos, en kWh).  
  - **Tipo de hogar**: Categórico (apartamento, casa, etc.).  
  - **Ubicación**: Ciudad o código postal (categórico).  
  - **Temperatura exterior**: En °C (numérico, disponible para algunas ubicaciones).  
- **Calidad de los datos**:  
  - ~10% de datos faltantes en temperatura exterior debido a fallos en estaciones meteorológicas.  
  - Algunos valores anómalos en consumo (ej. picos irreales de 100 kWh en una hora).  
  - Formato de fechas consistente, pero algunas ubicaciones tienen menos registros.  

**Ejemplo de tabla (primeras filas)**:  
| Fecha       | Consumo (kWh) | Voltaje | Intensidad | Cocina (kWh) | Lavandería (kWh) | Climatización (kWh) | Tipo de Hogar | Ubicación | Temperatura (°C) |  
|-------------|---------------|---------|------------|--------------|------------------|---------------------|---------------|-----------|------------------|  
| 2025-01-01 00:00 | 1.2           | 230     | 5.2        | 0.3          | 0.1              | 0.8                 | Casa          | Madrid    | 10               |  
| 2025-01-01 00:01 | 1.1           | 228     | 4.8        | 0.2          | 0.1              | 0.8                 | Apartamento   | Barcelona | -                |  

**Preprocesamiento necesario**:  
- Imputar datos faltantes en temperatura (ej. usando promedio diario).  
- Detectar y corregir valores atípicos en consumo (ej. usando umbrales basados en desviación estándar).  
- Agrupar datos por hora o día para reducir granularidad si es necesario.  

#### 3. Proyección de Resultados (5 minutos)

**Preguntas clave que pueden responderse**:  
- ¿En qué horas o días se producen los picos de consumo energético?  
- ¿Cómo varía el consumo según el tipo de hogar o ubicación?  
- ¿Es posible predecir el consumo futuro basado en patrones históricos y temperatura?  
- ¿Qué electrodomésticos (cocina, lavandería, climatización) contribuyen más al consumo?  

**Análisis posibles**:  
- **Descriptivo**: Promedio de consumo por hora, día o tipo de hogar.  
- **Predictivo**: Modelos de series temporales (ej. ARIMA, LSTM) para predecir consumo diario o semanal.  
- **Prescriptivo**: Recomendaciones para implementar tarifas dinámicas (ej. precios más altos en horas pico) o campañas de ahorro energético.  

**Limitaciones**:  
- Falta de datos demográficos (ej. número de ocupantes por hogar) limita el análisis de patrones de uso.  
- Datos de temperatura no disponibles para todas las ubicaciones, lo que afecta correlaciones climáticas.  
- No incluye información sobre fuentes renovables (ej. paneles solares), lo que limita análisis de sostenibilidad.  


#### 4. Evaluación de Utilidad y Recomendaciones (3 minutos)

**Utilidad para la toma de decisiones**:  
- **Fortalezas**:  
  - Alta granularidad temporal permite identificar patrones detallados (ej. picos de consumo a las 19:00).  
  - Datos de submedidores (cocina, lavandería) habilitan análisis específicos por tipo de uso.  
  - Útil para optimizar la red eléctrica y diseñar campañas de ahorro energético.  
- **Debilidades**:  
  - La falta de datos demográficos (ej. tamaño del hogar) limita la segmentación de usuarios.  
  - Datos faltantes en temperatura reducen la capacidad de correlacionar con factores climáticos.  
  - No hay información sobre tarifas eléctricas, lo que dificulta análisis económicos.  

**Recomendaciones**:  
- **Continuar con el conjunto**: Es adecuado para análisis de patrones de consumo y predicciones, pero requiere preprocesamiento para manejar datos faltantes.  
- **Complementar datos**: Integrar datos demográficos (ej. número de ocupantes) o información climática adicional (ej. APIs meteorológicas).  
- **Cambiar el conjunto**: Si el objetivo es analizar impacto económico, buscar un conjunto que incluya tarifas eléctricas o datos de facturación.  

#### 5. Visualizaciones y Filtros Dinámicos Propuestos (2 minutos)

**Gráficos sugeridos**:  
- **Gráfico de líneas**: Consumo energético promedio por hora del día.  
  
- **Gráfico de barras**: Consumo promedio por tipo de hogar y ciudad.  
  
- **Gráfico de pastel**: Proporción de consumo por submedidor (cocina, lavandería, climatización).  
 

**Filtros dinámicos**:  
- **Por fecha**: Seleccionar un rango de fechas (ej. verano 2025).  
- **Por tipo de hogar**: Filtrar por casas o apartamentos.  
- **Por ciudad**: Seleccionar una o varias ciudades.  
- **Por submedidor**: Mostrar solo consumo de cocina, lavandería o climatización.  
---
