# CLAUDE.md — Investigador

## Repository Overview

Agente de investigación y análisis construido sobre Claude Code.
Automatiza investigaciones: analiza fuentes web, sintetiza información y produce reportes estructurados en Markdown.

No tiene backend ni frontend propio — es un agente Claude Code activado por el comando `/investigar`.

## Cómo usarlo

```bash
# Desde Claude Code (con este repo abierto)
/investigar "¿Qué frameworks de agentes IA existen en 2025?"
/investigar "Competidores de MercadoPago en Argentina"
/investigar "Mejores prácticas de multi-tenancy en SaaS"
```

## Pipeline del agente

```
Input del usuario
      │
  Planificador  ← descompone el tema en 3-5 subtemas
      │
  Buscador      ← WebSearch por cada subtema (paralelo)
      │
  Lector        ← WebFetch de las URLs más relevantes
      │
  Sintetizador  ← Claude analiza, une y detecta contradicciones
      │
  Formateador   ← produce reporte Markdown con secciones y fuentes
```

## Archivos del agente

| Archivo | Rol |
|---------|-----|
| `.claude/commands/investigar.md` | Slash command `/investigar` — interfaz de usuario |
| `.claude/agents/planificador.md` | Subagente: descompone el tema |
| `.claude/agents/sintetizador.md` | Subagente: sintetiza fuentes en reporte |
| `AGENTS.md` | Instrucciones globales del agente para Claude |

## Output esperado

Reporte Markdown con:
- Resumen ejecutivo (2-3 párrafos)
- Hallazgos por subtema con evidencia citada
- Tabla comparativa si aplica
- Contradicciones detectadas entre fuentes
- Conclusiones accionables
- Lista de fuentes con URLs

## Reglas

- Siempre citar fuentes con URL
- Si hay contradicciones entre fuentes, señalarlas explícitamente
- Profundidad media por defecto: 5-8 fuentes, 3-5 subtemas
- No inventar datos — si no se encontró info, decirlo
