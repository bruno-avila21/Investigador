---
title: Investigador
description: Agente Claude Code para investigación profunda — WebSearch + síntesis en Markdown
---

# Investigador

Agente de investigación construido sobre Claude Code. Analiza fuentes web, sintetiza información y produce reportes estructurados en Markdown.

## Qué hace

- Descompone el tema en subtemas de investigación
- WebSearch por cada subtema con queries específicas
- WebFetch de las URLs más relevantes
- Sintetiza múltiples fuentes detectando consensos y contradicciones
- Produce reporte Markdown con resumen, hallazgos, tabla comparativa y fuentes citadas

## Cómo usarlo

```bash
# Desde Claude Code (con este repo abierto como working directory)
/investigar "¿Qué frameworks de agentes IA existen en 2025?"
/investigar "Competidores de MercadoPago en Argentina" --profundidad alta
```

## Pipeline

```
Input
  │
  ├─ Planificador  → descompone en 3-5 subtemas
  │
  ├─ Buscador      → WebSearch por subtema (paralelo)
  │
  ├─ Lector        → WebFetch de URLs relevantes
  │
  ├─ Sintetizador  → analiza, detecta consensos/contradicciones
  │
  └─ Formateador   → reporte Markdown con citas y fuentes
```

## Profundidades

| Nivel | Subtemas | Fuentes | Longitud |
|-------|----------|---------|----------|
| `baja` | 2-3 | 3-4 | ~400 palabras |
| `media` (default) | 3-5 | 5-8 | ~800 palabras |
| `alta` | 5-8 | 10-15 | ~1500 palabras |

## Estructura

```
.claude/
├── commands/
│   └── investigar.md    # slash command /investigar
└── agents/
    └── sintetizador.md  # subagente de síntesis
CLAUDE.md                # contexto para Claude Code
AGENTS.md                # instrucciones del pipeline completo
```
