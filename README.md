# ⚖️ Clinical VarOps

Clinical VarOps es una aplicación web local para apoyar la **operacionalización de variables** durante el diseño de investigaciones clínicas, académicas o metodológicas.

Su objetivo es ayudar a transformar conceptos de investigación en variables observables, medibles, documentadas y reutilizables.

## Qué hace

- Permite crear variables de investigación.
- Clasifica variables según tipo estadístico.
- Define categorías para variables cualitativas.
- Define unidades y rangos para variables cuantitativas.
- Permite registrar preguntas, sinónimos y reglas básicas de limpieza.
- Genera una tabla de operacionalización copiable a Word.
- Exporta un archivo `.clinical` reutilizable.

## Producto principal: `.clinical`

El archivo `.clinical` es un JSON que representa el diccionario operacional del estudio.

La estructura actual se mantiene estable por compatibilidad con otras aplicaciones:

```json
{
  "project": {},
  "variables": []
}
```

> **Decisión crítica:** no se modifica la estructura actual del `.clinical` ni se añaden campos obligatorios nuevos en esta etapa.

Ver detalles en [`docs/FORMATO-CLINICAL.md`](docs/FORMATO-CLINICAL.md).

## Qué no hace

Clinical VarOps no:

- analiza datos;
- almacena observaciones individuales;
- sustituye la revisión metodológica del investigador;
- valida automáticamente la pertinencia clínica de una variable;
- cifra automáticamente los datos guardados en el navegador.

## Uso básico

1. Complete los datos generales del proyecto.
2. Añada una variable nueva o use el catálogo común.
3. Defina nombre, tipo y descripción operacional.
4. Configure categorías, rangos, unidades y pregunta.
5. Copie la tabla para Word o exporte el archivo `.clinical`.

## Manual de usuario

La aplicación incluye un manual visible desde la interfaz en `manual.html`.

También se conserva el documento original [`manual de usuario.md`](manual%20de%20usuario.md).

## Relación con APU

Clinical VarOps es una aplicación independiente. Puede vincularse conceptualmente con el ecosistema APU como herramienta transversal para generar diccionarios operacionales de variables, pero no forma parte del pipeline lineal APU-01 → APU-06.

Ver [`docs/INTEGRACION-APU.md`](docs/INTEGRACION-APU.md).

## Privacidad

La aplicación funciona en el navegador y usa LocalStorage para persistencia local. LocalStorage no equivale a cifrado.

No se recomienda introducir datos identificables de pacientes. Clinical VarOps está pensada para definir variables, no para almacenar datos clínicos individuales.

Ver [`docs/PRIVACIDAD-Y-LIMITES.md`](docs/PRIVACIDAD-Y-LIMITES.md).

## Estructura del proyecto

```txt
index.html                    Interfaz principal
app.js                        Lógica de la aplicación
manual.html                   Manual visible desde la app
manual de usuario.md          Manual original en Markdown
ESPECIFICACION_TECNICA.md     Especificación técnica previa
docs/FORMATO-CLINICAL.md      Documentación del .clinical
docs/INTEGRACION-APU.md       Relación conceptual con APU
docs/PRIVACIDAD-Y-LIMITES.md  Privacidad y límites
examples/ejemplo-basico.clinical  Ejemplo compatible
```

## Licencia

Pendiente de formalizar en archivo `LICENSE` si se desea distribución pública explícita.
