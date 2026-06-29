# Clinical VarOps e integración con el ecosistema APU

Clinical VarOps es una aplicación independiente. No forma parte del pipeline lineal APU-01 → APU-06, pero puede funcionar como herramienta transversal de diseño metodológico.

## Relación conceptual

El ecosistema APU trabaja con herramientas atómicas, local-first y conectadas por contratos de datos. Clinical VarOps encaja como generador de un diccionario operacional de variables, útil antes o durante el procesamiento de materiales de investigación.

## Qué produce

Clinical VarOps produce archivos `.clinical` con esta estructura raíz estable:

```json
{
  "project": {},
  "variables": []
}
```

## Usos posibles dentro de flujos APU

- Definir covariables del estudio.
- Documentar variables de participantes, sesiones o grupos.
- Preparar reglas de limpieza para datos estructurados.
- Generar tablas de operacionalización para informes o tesis.
- Servir como referencia metodológica para fases de análisis y exportación.

## Decisión de diseño

Clinical VarOps mantiene su independencia y su formato actual. La integración con APU debe ser documental y por compatibilidad de archivos, no mediante absorción de la aplicación ni ruptura del `.clinical` existente.

## Restricción crítica

No se debe cambiar de forma incompatible la estructura actual del `.clinical`, porque otras aplicaciones pueden depender de ella.

Cualquier aplicación que consuma `.clinical` debe validar defensivamente el archivo antes de usarlo.
