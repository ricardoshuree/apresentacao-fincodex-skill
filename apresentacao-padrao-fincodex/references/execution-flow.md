# Fluxo de Execução — FinCodex

Processo de construção de apresentações em 3 fases.
Este arquivo define a sequência completa — da entrada do usuário ao arquivo final.

---

## Fase 1 — Plano

### Entrada do usuário
O usuário pode fornecer:
- Outline em texto livre (tópicos, bullets, notas)
- Roteiro de vídeo ou palestra
- Brief de tema ("apresentação sobre diagnóstico FinOps")
- Lista de pontos a cobrir

### O que fazer

1. Leia `references/design-system.md` para entender a direção estética
2. Leia `references/slide-templates.md` para conhecer os tipos de slide disponíveis
3. Leia `references/themes/theme-fincodex.md` para carregar a paleta e regras de identidade
4. Analise o input e extraia:
   - Narrativa central (qual é a história?)
   - Seções principais e transições entre ideias
   - Elementos-chave (listas, comparações, citações, etapas, métricas, diagramas)
5. Mapeie cada seção para um tipo de slide
6. Sugira componentes interativos adequados ao conteúdo
7. Para cada slide, esboce o roteiro de apresentação

### Pergunta obrigatória antes de avançar

**Sempre pergunte o modo padrão antes de gerar:**

> "Qual o modo padrão da apresentação? **(ESCURO / CLARO)**"
> *(Padrão sugerido: ESCURO — modo principal da FinCodex)*

Aguarde a resposta antes de ir para a Fase 2.

### Heurísticas de mapeamento conteúdo → componente

| Conteúdo | Componente sugerido |
|---|---|
| Etapas de processo | Pipeline / Flow nodes |
| Métricas e KPIs | Stat cards com `data-count` |
| Comparação A vs B | Comparison (duas colunas) |
| Código ou configuração | Terminal / Code block |
| Hierarquia | Tree / Hub-spoke |
| Tendência temporal | Line chart / Timeline |
| Distribuição | Donut / Bar chart |
| Afirmação forte | Statement com gradiente |

### Output da Fase 1

Tabela de plano com colunas: Nº | Tipo de Slide | Título | Componentes | Roteiro (resumo 1 linha)

---

## Fase 2 — Design (Modo Craft)

Para cada slide, em sequência:

1. Leia os arquivos de componentes relevantes para aquele slide
2. Construa o HTML do slide com fidelidade ao design system
3. Mostre o preview visual inline antes de seguir
4. Aguarde aprovação ou ajuste
5. Avance para o próximo slide

### Regras de design por slide

- Fundo do slide: sempre `var(--brand-bg)` — nunca hardcoded
- Máximo 1 destaque de cor por slide (sempre `var(--brand-primary)` = gold `#C08830`)
- Logo `finCodex` no canto superior direito (escuro: cream `#EAE0CC`; claro: espresso `#1E0E05`)
- Section labels: JetBrains Mono, 11px, letter-spacing 2px, `var(--text-muted)`
- Princípio: **uma informação por slide**

---

## Fase 3 — Montagem

### Placeholders a preencher

| Placeholder | O que colocar |
|---|---|
| `{{PRESENTATION_TITLE}}` | Título da apresentação |
| `{{GOOGLE_FONTS_LINK}}` | Tags `<link>` do Google Fonts FinCodex (Space Grotesk + Inter + JetBrains Mono) |
| `{{THEME_CSS_VARIABLES}}` | Bloco `:root { ... }` do modo escolhido (ESCURO ou CLARO) |
| `{{IS_DARK_DEFAULT}}` | `true` se modo ESCURO (padrão), `false` se modo CLARO |
| `{{SLIDES_CONTENT}}` | HTML de todos os slides aprovados em sequência |
| `{{ROTEIRO_DATA}}` | Array JS com roteiro de cada slide (ver formato abaixo) |

### Google Fonts FinCodex

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
```

### Formato do ROTEIRO_DATA

```javascript
[
  { slide: 0, texto: "Texto completo do roteiro do slide 1..." },
  { slide: 1, texto: "Roteiro do slide 2..." }
]
```

### Como preencher {{THEME_CSS_VARIABLES}}

**Modo ESCURO** (IS_DARK_DEFAULT = true — padrão FinCodex):
```css
--brand-bg: #1E0E05; --brand-surface: #281408; --brand-surface-2: #32180A;
--brand-border: #3C1E0A; --brand-border-hi: #503018;
--brand-primary: #C08830; --brand-primary-dim: rgba(192,136,48,0.18); --brand-primary-glow: rgba(192,136,48,0.35);
--brand-secondary: #DCAA46; --brand-secondary-dim: rgba(220,170,70,0.15);
--brand-success: #4ADE80; --brand-success-dim: rgba(74,222,128,0.15);
--brand-error: #EF4444; --brand-error-dim: rgba(239,68,68,0.15);
--brand-warning: #FBBF24;
--text-primary: #EAE0CC; --text-secondary: #B4AA96; --text-muted: #665A46;
--font-headline: 'Space Grotesk', sans-serif; --font-body: 'Inter', sans-serif;
--font-mono: 'JetBrains Mono', monospace; --font-display: 'Space Grotesk', sans-serif;
--gt1: #C08830; --gt2: #DCAA46; --gt3: #E6B858;
```

**Modo CLARO** (IS_DARK_DEFAULT = false):
```css
--brand-bg: #EAE0CC; --brand-surface: #F5EDD8; --brand-surface-2: #E0D4BA;
--brand-border: #D2C8AA; --brand-border-hi: #BEB096;
--brand-primary: #C08830; --brand-primary-dim: rgba(192,136,48,0.12); --brand-primary-glow: rgba(192,136,48,0.25);
--brand-secondary: #8C6018; --brand-secondary-dim: rgba(140,96,24,0.12);
--brand-success: #276747; --brand-success-dim: rgba(39,103,71,0.12);
--brand-error: #C0392B; --brand-error-dim: rgba(192,57,43,0.12);
--brand-warning: #8C7800;
--text-primary: #1E0E05; --text-secondary: #503018; --text-muted: #8C826E;
--font-headline: 'Space Grotesk', sans-serif; --font-body: 'Inter', sans-serif;
--font-mono: 'JetBrains Mono', monospace; --font-display: 'Space Grotesk', sans-serif;
--gt1: #C08830; --gt2: #8C6018; --gt3: #B07020;
```

### Saída da Fase 3

Um único arquivo `.html` com tudo embutido (CSS + JS + conteúdo + fontes via CDN).
Nenhuma dependência externa além do Google Fonts.
