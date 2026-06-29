# Clinical VarOps

## Operacionalización de variables

Clinical VarOps es una herramienta diseñada para apoyar la operacionalización de variables durante el diseño de una investigación.

Toda investigación científica parte de un **problema científico**, que puede formularse mediante preguntas de investigación o hipótesis, a partir de las cuales se derivan los objetivos del estudio. Sin embargo, para que dichos objetivos puedan analizarse empíricamente, sus componentes conceptuales deben traducirse en variables observables y medibles.

Este proceso se denomina **operacionalización de variables**.

Operacionalizar una variable consiste en definir con precisión qué característica será estudiada y cómo será registrada dentro de la investigación. De este modo, la operacionalización constituye el puente entre el diseño metodológico y el análisis de datos.

Clinical VarOps forma parte de un ecosistema de aplicaciones de apoyo a la investigación cuantitativa y cualitativa. Dentro de este ecosistema, cumple una función central: estructurar las variables del estudio para que otras herramientas puedan reutilizar esta información en procesos posteriores de validación, limpieza y análisis de datos.

## Estructura de una variable en Clinical VarOps

Cada variable registrada en el software queda definida mediante cuatro elementos fundamentales:

| Campo                | Descripción                    |
| -------------------- | ------------------------------ |
| **Variable**         | Nombre de la variable          |
| **Tipo**             | Clasificación estadística      |
| **Escala / Valores** | Categorías o rango de medición |
| **Descripción**      | Definición operacional         |

Esta estructura corresponde directamente con la tabla de operacionalización que el sistema genera automáticamente y que puede copiarse directamente en una tesis, protocolo o proyecto de investigación. Además, el fichero estructurado que produce la aplicación puede ser utilizado posteriormente por otras herramientas del ecosistema.

## Clasificación de variables

Clinical VarOps implementa la clasificación clásica de variables de la bioestadística, agrupándolas en **cualitativas** y **cuantitativas**.

| Clasificación     | Subtipo                            | Características                                                           | Manejo en Clinical VarOps                 |
| ----------------- | ---------------------------------- | ------------------------------------------------------------------------- | ----------------------------------------- |
| **Cualitativas**  | **Nominales**                      | No existen diferencias de magnitud o intensidad entre sus categorías      | Permite definir categorías sin orden      |
|                   | **Ordinales o cuasicuantitativas** | Sus categorías poseen un orden lógico                                     | Conserva explícitamente el orden definido |
| **Cuantitativas** | **Discretas o discontinuas**       | Toman valores enteros, sin valores intermedios entre enteros consecutivos | Admite valores numéricos discretos        |
|                   | **Continuas**                      | Entre dos valores existen infinitos valores intermedios                   | Admite mediciones continuas               |

La correcta clasificación de una variable determina su estructura dentro del software y condiciona cómo podrá ser procesada posteriormente.

## Funcionamiento general

El flujo de trabajo en Clinical VarOps consta de tres pasos esenciales:

### 1. Crear la variable

Se introducen:

* nombre
* tipo
* descripción

### 2. Configurar su estructura

Según el tipo seleccionado, el software habilita diferentes controles:

* **Variables nominales u ordinales:** agregar, editar o eliminar categorías
* **Variables cuantitativas discretas:** registrar valores enteros
* **Variables cuantitativas continuas:** definir escalas de medición continuas

### 3. Generar la tabla de operacionalización

El sistema produce automáticamente la tabla final, lista para su documentación y reutilización.

Clinical VarOps transforma así la operacionalización en una estructura formal, consistente y reutilizable, reduciendo ambigüedades en la definición de variables y fortaleciendo la calidad metodológica de la investigación.
