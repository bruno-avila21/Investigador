# /investigar

Investiga un tema en profundidad usando búsqueda web y produce un reporte estructurado en Markdown.

## Uso

```
/investigar <tema>
/investigar <tema> --profundidad <baja|media|alta>
```

## Ejemplos

```
/investigar "¿Qué frameworks de agentes IA existen en 2025?"
/investigar "Competidores de MercadoPago en Argentina" --profundidad alta
/investigar "Mejores prácticas de multi-tenancy en SaaS" --profundidad baja
```

## Comportamiento

1. **Planificar**: descomponer el tema en 3-5 subtemas de investigación
2. **Buscar**: WebSearch para cada subtema con queries específicas
3. **Leer**: WebFetch de las URLs más relevantes (5-8 fuentes para profundidad media)
4. **Sintetizar**: analizar, detectar consensos y contradicciones
5. **Reportar**: producir reporte Markdown con resumen, hallazgos, tabla comparativa (si aplica), y fuentes citadas

## Output

Reporte Markdown guardado en `./output/YYYY-MM-DD-<tema-slug>.md` y mostrado en pantalla.

Incluye:
- Resumen ejecutivo
- Hallazgos por subtema con citas
- Contradicciones detectadas entre fuentes
- Conclusiones accionables
- Lista de fuentes con URLs

## Notas

- Profundidad por defecto: media
- Nunca inventar datos — si no hay fuentes, lo dice explícitamente
- Siempre citar URL de cada dato o cita
