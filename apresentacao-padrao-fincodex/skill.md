---
name: apresentacao-padrao-fincodex
description: Gera apresentações HTML interativas com a identidade visual FinCodex. Produz decks com navegação, roteiro popup, modo escuro/claro, componentes interativos e tema FinCodex (gold #C08830, espresso #1E0E05) — tudo em um único arquivo HTML.
---

## O que esta skill faz

Transforma conteúdo bruto (outlines, roteiros, briefs) em apresentações HTML interativas
no padrão visual da **FinCodex** — plataforma de diagnóstico FinOps multi-cloud, com:

- Tema FinCodex nativo (gold `#C08830`, espresso `#1E0E05`, cream `#EAE0CC`, Space Grotesk + Inter)
- Motor de navegação (teclado, swipe, dots, progress bar)
- **Botão R** na nav: abre popup de roteiro com timer, countdown por slide e sincronização
- **Botão ESCURO/CLARO** na nav: toggle de modo em runtime (padrão: ESCURO)
- Componentes interativos (charts, pipelines, terminais, flow diagrams)
- Animações escalonadas e refinadas
- Princípio: **uma informação por slide**

## Arquivos de referência

| Arquivo | Quando ler | O que contém |
|---|---|---|
| `references/execution-flow.md` | **Sempre** — no início de qualquer tarefa | Fluxo de trabalho em 3 fases + todos os placeholders |
| `references/design-system.md` | Na Fase 1 e 2 | Princípios estéticos, tipografia, layout, regras visuais |
| `references/slide-templates.md` | Na Fase 1 (mapeamento) | 16+ tipos de slide com padrões HTML e limites de conteúdo |
| `references/components/*.md` | Na Fase 2 (design de cada slide) | Biblioteca de componentes — leia apenas as categorias relevantes |
| `references/themes/theme-fincodex.md` | **Sempre** — tema padrão | CSS variables, cores, fontes e elementos da marca FinCodex |
| `assets/template.html` | Na Fase 3 (montagem) | Motor base com paletas FinCodex embutidas no toggle JS |

### Placeholders do template

| Placeholder | Fase | O que colocar |
|---|---|---|
| `{{PRESENTATION_TITLE}}` | 3 | Título da apresentação |
| `{{GOOGLE_FONTS_LINK}}` | 3 | Space Grotesk + Inter + JetBrains Mono |
| `{{THEME_CSS_VARIABLES}}` | 3 | Bloco CSS do modo escolhido (ver execution-flow.md) |
| `{{IS_DARK_DEFAULT}}` | 3 | `true` (ESCURO — padrão) ou `false` (CLARO) |
| `{{SLIDES_CONTENT}}` | 3 | HTML dos slides aprovados em sequência |
| `{{ROTEIRO_DATA}}` | 3 | Array JS `[{slide: 0, texto: "..."}, ...]` |

### Componentes disponíveis por categoria

- `components-foundation.md` → Cards, stats, badges, progress bars, donut rings
- `components-terminal.md` → Terminal, code, diff, REPL
- `components-flow.md` → Pipelines, hub-spoke, data flow, attention, sessions
- `components-dataviz.md` → Line chart, bar chart, donut, scatter, heatmap
- `components-visual.md` → Isometric, blueprint, parchment, exploded view
- `components-custom.md` → Flow-break, gauge, drift, air-gap, waveform

## Regras fundamentais

1. Idioma padrão: **PT-BR** — até que o usuário peça outro
2. Modo padrão: **Craft** (slide a slide) — mude para one-shot apenas se o usuário pedir explicitamente
3. Tema padrão: **FinCodex** — use `references/themes/theme-fincodex.md` automaticamente
4. O output final é sempre um **único arquivo .html** — CSS e JS embutidos, sem dependências externas exceto Google Fonts
5. **Pergunte o modo (ESCURO/CLARO) na Fase 1**, antes de avançar — padrão sugerido: **ESCURO**
6. **Sugira componentes proativamente** — baseado no conteúdo, não espere o usuário pedir
7. Cada slide deve caber em **100vh** — se transbordar, divida
8. **Uma informação por slide** — regra core; nunca sobrecarregue
9. Na Fase 2, mostre cada slide como **preview visual inline** antes de gerar o arquivo
10. Nunca use mais de **uma cor de destaque por slide** (sempre o gold `#C08830`)
11. Logo `finCodex` sempre no canto superior direito (cream em escuro, espresso em claro)
12. **Gere o roteiro de cada slide** na Fase 1 e preencha `{{ROTEIRO_DATA}}` na Fase 3
13. O botão **R** na nav abre o popup de roteiro — sempre visível em todos os slides

## Popup de Roteiro (funcionalidade nativa)

O template já inclui o sistema de roteiro completo:
- **Timer progressivo** — liga/desliga, zera ao desligar
- **Checkbox de sincronização automática** — destaca o slide ativo via polling
- **Countdown decrescente** — estimativa de tempo por slide (palavras ÷ 130 wpm) em vermelho, pulso quando < 15s
- **Controles de navegação** por slide — setas ← → em cada item
- **Toggle ESCURO/CLARO** próprio do popup — independente da apresentação

## Início

Ao receber uma tarefa de apresentação, leia `references/execution-flow.md` e `references/themes/theme-fincodex.md` e siga o fluxo descrito.
