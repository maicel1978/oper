# 🏗️ ESPECIFICACIÓN TÉCNICA: JSON Maestro (Clinical VarOps)
**Versión del Esquema:** 7.0
**Uso:** Fuente Única de Verdad (SSoT) para Limpieza de Datos y Generación de Formularios.

---

## 1. Propósito del Fichero
Este fichero (extensión `.clinical` o `.json`) es el cerebro de la investigación. Contiene no solo qué variables se miden, sino **las reglas de ingeniería** para validar y normalizar los datos recogidos en el campo.

## 2. Estructura Raíz
El JSON se divide en dos grandes bloques:

| Nodo | Tipo | Descripción |
| :--- | :--- | :--- |
| `project` | Object | Metadatos administrativos del protocolo (Título, Especialidad, Fecha). |
| `variables` | Array | Lista secuencial de todas las variables operacionalizadas. |

---

## 3. Esquema de Variables (La Sala de Máquinas)
Cada objeto dentro del array `variables` sigue este contrato estricto:

### A. Identificadores Base
- **`name`**: ID técnico único en formato `snake_case` (ej: `presion_arterial`). **IMPORTANTE:** Este nombre debe coincidir exactamente con el encabezado de columna en tu base de datos de Excel/CSV.
- **`type`**: String que define si la variable es Nominal (Dicotómica/Politómica), Ordinal o Cuantitativa (Discreta/Continua).
- **`description`**: Definición operacional textual para la memoria de la tesis.

### B. El Objeto `metadata` (Reglas de Ejecución)
Aquí es donde reside la inteligencia para las otras aplicaciones:

- **`question`**: El texto exacto de la pregunta. Úsalo para generar automáticamente el "Label" en formularios (KoboToolbox, Google Forms, RedCap).
- **`unit`**: Unidad de medida. Fundamental para que la app de limpieza sepa en qué escala están los números.
- **`range`**: Contiene `min` y `max`.
    - *Lógica de Limpieza:* Si un valor en la base de datos es `< min` o `> max`, la aplicación debe marcarlo como **Outlier/Error**.
- **`categories`**: Array de objetos para variables cualitativas.
    - `label`: El nombre oficial (ej: "Masculino").
    - `synonyms`: Lista de valores posibles que pueden venir "sucios" (ej: `["m", "1", "masc", "H"]`).
    - *Lógica de Limpieza:* Busca cualquier coincidencia en `synonyms` y cámbiala automáticamente por el `label`. Así normalizas la base de datos en milisegundos.

---

## 4. Guía de Implementación para Proyectos Futuros

### Para el Módulo de Limpieza (Python/Pandas o R):
```javascript
// Pseudocódigo de lógica
fichero_maestro.variables.forEach(variable => {
    let columna = base_datos[variable.name];
    
    if (variable.metadata.categories.length > 0) {
        // Ejecutar normalización por diccionario
        variable.metadata.categories.forEach(cat => {
            columna.replace(cat.synonyms, cat.label);
        });
    }
    
    if (variable.metadata.range.min) {
        // Detectar errores de rango
        columna.findErrors(val => val < variable.metadata.range.min || val > variable.metadata.range.max);
    }
});
```

### Para el Generador de Formularios:
- Itera el array `variables`.
- Si `type` es "Nominal", crea un componente de "Selección única" (Radio Button) usando `categories.label`.
- Si `type` es "Cuantitativa", crea un "Input Numérico" limitado por `range`.

---
**Nota final:** Este esquema garantiza que si el investigador cambia una regla en esta herramienta, todas las demás aplicaciones se actualicen automáticamente al importar el nuevo fichero.
