# Formato `.clinical`

## Propósito

El archivo `.clinical` es el producto principal de Clinical VarOps. Representa el diccionario operacional de variables de un estudio.

Este archivo permite conservar y reutilizar la definición formal de las variables: nombre técnico, tipo estadístico, descripción operacional, pregunta, unidad, rango, categorías y sinónimos.

## Decisión crítica de compatibilidad

La estructura actual del archivo `.clinical` **no debe modificarse de forma incompatible**, porque otras aplicaciones pueden depender de ella.

La estructura raíz estable es:

```json
{
  "project": {},
  "variables": []
}
```

Cualquier mejora futura debe preservar estos dos nodos y su significado.

## Estructura general actual

```json
{
  "project": {
    "name": "Nombre del proyecto",
    "specialty": "Especialidad",
    "date": "2026-06-29"
  },
  "variables": [
    {
      "name": "edad",
      "type": "Cuantitativa Discreta",
      "description": "Edad cronológica en años cumplidos.",
      "metadata": {
        "question": "¿Qué edad tiene el paciente?",
        "unit": "años",
        "range": {
          "min": "0",
          "max": "115"
        },
        "categories": []
      }
    }
  ]
}
```

## Nodo `project`

Contiene metadatos generales del proyecto o protocolo.

| Campo | Tipo actual | Descripción |
|---|---|---|
| `name` | string | Nombre o título de la investigación. |
| `specialty` | string | Especialidad o área de conocimiento. |
| `date` | string | Fecha del proyecto. |

## Nodo `variables`

Contiene la lista ordenada de variables operacionalizadas.

| Campo | Tipo actual | Descripción |
|---|---|---|
| `name` | string | Nombre técnico de la variable. Debe ser compatible con columnas de bases de datos. |
| `type` | string | Tipo estadístico de la variable. |
| `description` | string | Definición operacional. |
| `metadata` | object | Reglas y metadatos asociados. |

## Nodo `metadata`

| Campo | Tipo actual | Descripción |
|---|---|---|
| `question` | string | Pregunta o etiqueta de recolección. |
| `unit` | string | Unidad de medida para variables cuantitativas. |
| `range.min` | string | Valor mínimo esperado. En la estructura actual se guarda como texto. |
| `range.max` | string | Valor máximo esperado. En la estructura actual se guarda como texto. |
| `categories` | array | Categorías para variables nominales u ordinales. |

## Categorías

Cada categoría tiene esta forma:

```json
{
  "label": "Masculino",
  "synonyms": ["m", "masc", "1"]
}
```

| Campo | Tipo actual | Descripción |
|---|---|---|
| `label` | string | Nombre oficial de la categoría. |
| `synonyms` | array | Valores alternativos que pueden aparecer en datos sucios. |

## Qué garantiza el `.clinical`

Un archivo `.clinical` describe variables. Puede utilizarse para:

- documentar la tabla de operacionalización;
- reutilizar definiciones en otras herramientas;
- preparar reglas de limpieza;
- mantener consistencia entre protocolo, recolección y análisis.

## Qué no garantiza

El archivo `.clinical` no garantiza por sí solo:

- que los datos hayan sido recogidos;
- que los valores observados sean correctos;
- que las reglas sean clínicamente adecuadas;
- que exista cifrado;
- que contenga datos individuales de pacientes.

## Relación con otras aplicaciones

Las aplicaciones que consuman `.clinical` deben asumir como contrato mínimo la existencia de:

```json
{
  "project": {},
  "variables": []
}
```

No deben depender de campos no documentados sin validarlos antes.
