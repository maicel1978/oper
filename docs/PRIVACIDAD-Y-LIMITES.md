# Privacidad y límites

## Procesamiento local

Clinical VarOps funciona en el navegador. La información introducida se conserva localmente mediante LocalStorage y puede exportarse manualmente como archivo `.clinical`.

## Advertencia sobre LocalStorage

LocalStorage no equivale a cifrado. Una persona con acceso al navegador, al perfil del usuario o al equipo podría inspeccionar la información guardada.

## Datos sensibles

Se recomienda no introducir datos identificables de pacientes. Clinical VarOps está pensada para definir variables, no para almacenar observaciones individuales ni historias clínicas.

## Qué contiene un `.clinical`

Un archivo `.clinical` contiene definiciones de variables, no registros individuales.

Puede incluir:

- nombre de la variable;
- tipo estadístico;
- descripción operacional;
- pregunta;
- unidad;
- rango;
- categorías;
- sinónimos.

## Qué no hace la aplicación

Clinical VarOps no:

- analiza datos;
- valida la pertinencia clínica de una variable;
- sustituye la revisión metodológica;
- cifra automáticamente los archivos exportados;
- envía datos a un servidor propio.

## Recursos externos

La versión actual puede cargar recursos externos de presentación, como Tailwind vía CDN y fuentes web. Si se requiere una operación estrictamente offline/local-first, se recomienda empaquetar esos recursos localmente en una versión futura.
