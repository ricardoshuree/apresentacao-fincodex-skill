# Tema — FinCodex

Tema oficial da **FinCodex** — plataforma de diagnóstico FinOps multi-cloud.
Extraído de `fincodex.com.br` via pixel sampling e `meta-theme-color`.

Estética: quente, profunda, espresso + ouro âmbar. Inspira confiança técnica sem frieza corporativa.
Modo padrão para apresentações: **ESCURO** (homepage é dark).

---

## Paleta FinCodex

| Token                 | Hex         | Uso                                     |
|-----------------------|-------------|-----------------------------------------|
| Espresso (BG dark)    | `#1E0E05`   | Fundo principal no modo escuro          |
| Surface dark          | `#281408`   | Cards, painéis em dark                  |
| Surface dark-2        | `#32180A`   | Segundo nível de superfície             |
| Border dark           | `#3C1E0A`   | Bordas sutis em dark                    |
| Border dark-hi        | `#503018`   | Bordas em hover / destaque              |
| **Gold (acento)**     | `#C08830`   | Accent principal, ícones, destaques     |
| Gold light            | `#DCAA46`   | Variações do acento, gradientes         |
| Gold dim              | `rgba(192,136,48,0.18)` | Superfícies com tint ouro   |
| Gold glow             | `rgba(192,136,48,0.35)` | Glow / box-shadow ouro      |
| Cream (BG light)      | `#EAE0CC`   | Fundo principal no modo claro           |
| Cream surface         | `#F5EDD8`   | Cards, painéis em light                 |
| Cream surface-2       | `#E0D4BA`   | Segundo nível de superfície light       |
| Cream border          | `#D2C8AA`   | Bordas em light                         |
| Text cream            | `#EAE0CC`   | Texto em fundos escuros                 |
| Text espresso         | `#1E0E05`   | Texto em fundos claros                  |
| Text muted dark       | `#665A46`   | Texto secundário em dark                |
| Text muted light      | `#8C826E`   | Texto secundário em light               |

---

## Google Fonts

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
```

---

## CSS Variables — Modo ESCURO (padrão)

```css
:root {
  --brand-bg:        #1E0E05;
  --brand-surface:   #281408;
  --brand-surface-2: #32180A;
  --brand-border:    #3C1E0A;
  --brand-border-hi: #503018;

  --brand-primary:      #C08830;
  --brand-primary-dim:  rgba(192,136,48,0.18);
  --brand-primary-glow: rgba(192,136,48,0.35);
  --brand-secondary:    #DCAA46;
  --brand-secondary-dim: rgba(220,170,70,0.15);

  --brand-success:     #4ADE80;
  --brand-success-dim: rgba(74,222,128,0.15);
  --brand-error:       #EF4444;
  --brand-error-dim:   rgba(239,68,68,0.15);
  --brand-warning:     #FBBF24;

  --text-primary:   #EAE0CC;
  --text-secondary: #B4AA96;
  --text-muted:     #665A46;

  --font-headline: 'Space Grotesk', sans-serif;
  --font-body:     'Inter', sans-serif;
  --font-mono:     'JetBrains Mono', monospace;
  --font-display:  'Space Grotesk', sans-serif;

  --gt1: #C08830;
  --gt2: #DCAA46;
  --gt3: #E6B858;
}
```

## Background — Escuro

```css
body { background: #1E0E05; }
```

---

## CSS Variables — Modo CLARO (alternativo)

```css
:root {
  --brand-bg:        #EAE0CC;
  --brand-surface:   #F5EDD8;
  --brand-surface-2: #E0D4BA;
  --brand-border:    #D2C8AA;
  --brand-border-hi: #BEB096;

  --brand-primary:      #C08830;
  --brand-primary-dim:  rgba(192,136,48,0.12);
  --brand-primary-glow: rgba(192,136,48,0.25);
  --brand-secondary:    #8C6018;
  --brand-secondary-dim: rgba(140,96,24,0.12);

  --brand-success:     #276747;
  --brand-success-dim: rgba(39,103,71,0.12);
  --brand-error:       #C0392B;
  --brand-error-dim:   rgba(192,57,43,0.12);
  --brand-warning:     #8C7800;

  --text-primary:   #1E0E05;
  --text-secondary: #503018;
  --text-muted:     #8C826E;

  --font-headline: 'Space Grotesk', sans-serif;
  --font-body:     'Inter', sans-serif;
  --font-mono:     'JetBrains Mono', monospace;
  --font-display:  'Space Grotesk', sans-serif;

  --gt1: #C08830;
  --gt2: #8C6018;
  --gt3: #B07020;
}
```

## Background — Claro

```css
body { background: #EAE0CC; }
```

---

## Regras de Identidade FinCodex

1. **Logo**: `finCodex` — camelCase, Space Grotesk weight 700, sempre no canto superior direito
2. **Cor do logo**: cream `#EAE0CC` em dark; espresso `#1E0E05` em light
3. **Section labels**: caps, JetBrains Mono, 11px, letter-spacing 2px, `var(--text-muted)`
4. **Acento único**: apenas `#C08830` gold — nunca mais de uma cor accent por slide
5. **Modo padrão**: ESCURO — perguntar antes de gerar
6. **Gradiente texto**: de `#C08830` a `#DCAA46` a `#E6B858` (ouro quente)
7. **"Uma informação por slide"** — regra core mantida da metodologia FinCodex/Falconi

## Nota sobre fundos mixed

A FinCodex usa os dois modos na mesma plataforma:
- Homepage (`fincodex.com.br`): dark espresso
- Guia FOCUS (`fincodex.com.br/focus.html`): light cream

Para apresentações, o presenter pode alternar em runtime com o botão ESCURO/CLARO na nav.
