---
title: "Proyecto Integrador: Ciencia de Datos"
position: 1
date: 2025-11-04
---

### 1) Crear Fork del Repositorio
Solo el líder del grupo debe crear el repositorio para la actividad.  

```bash
https://github.com/jfinfosena/proyecto_integrador_ciencia_datos.git
```

Pulsa el botón **Fork** (esquina superior derecha) desde la cuenta del líder.

### 2) El líder clona su fork en su equipo:

```bash
git clone https://github.com/LIDER-DEL-GRUPO/proyecto_integrador_ciencia_datos.git
cd proyecto_integrador_ciencia_datos
```

### 3) El líder agrega a los integrantes como colaboradores en su fork (Settings → Collaborators) o comparte el enlace del fork para que ellos lo clonen directamente:

```bash
git clone https://github.com/LIDER-DEL-GRUPO/proyecto_integrador_ciencia_datos.git
```

### 3) Flujo de trabajo recomendado:
- Rama `main` protegida (sin commits directos).
- Cada integrante crea ramas por funcionalidad: `feature/<nombre>` (ej. `feature/descripcion-datos`).

### 4) Registro del grupo: info.json
Antes de iniciar la preparación, diligencia el archivo `info.json` en la raíz del repositorio del líder con la siguiente estructura:

```json
{
  "nombres": "",
  "apellidos": "",
  "grupo": "datos-#"
}
```

Indicaciones:
- `nombres` y `apellidos`: del líder del grupo.
- `grupo`: reemplaza `#` por el número asignado (ej. `datos-3`).
- Este archivo sirve para identificar el grupo durante la evaluación.
- Inclúyelo en el primer commit del fork y actualízalo si cambia el liderazgo.

