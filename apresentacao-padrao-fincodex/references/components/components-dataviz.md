# Componentes — Data Viz

Line chart, bar chart, donut multi-segmento, scatter/bubble, heatmap.
Todos implementados em SVG inline — sem dependências externas.

---

## Line Chart (Área)

Linha com preenchimento de área abaixo, ponto final destacado.

```html
<svg viewBox="0 0 260 100" width="260" height="100">
  <!-- Grid lines -->
  <line x1="30" y1="90" x2="250" y2="90" stroke="var(--brand-border)" stroke-width="0.5"/>
  <line x1="30" y1="60" x2="250" y2="60" stroke="var(--brand-border)" stroke-width="0.5"/>
  <line x1="30" y1="30" x2="250" y2="30" stroke="var(--brand-border)" stroke-width="0.5"/>

  <!-- Área de preenchimento -->
  <polyline points="30,80 70,72 110,55 150,60 190,35 230,20 230,90 30,90"
    fill="var(--brand-primary-dim)" stroke="none"/>

  <!-- Linha -->
  <polyline points="30,80 70,72 110,55 150,60 190,35 230,20"
    fill="none" stroke="var(--brand-primary)" stroke-width="2"
    stroke-linecap="round" stroke-linejoin="round"/>

  <!-- Ponto final -->
  <circle cx="230" cy="20" r="4" fill="var(--brand-primary)"/>

  <!-- Labels do eixo Y -->
  <text x="15" y="93" font-size="8" fill="var(--text-muted)" font-family="var(--font-mono)">0</text>
  <text x="10" y="33" font-size="8" fill="var(--text-muted)" font-family="var(--font-mono)">1K</text>
</svg>
```

**Customização:** Ajuste os pontos do polyline para seus dados. Y invertido (0 = topo).

---

## Bar Chart

Barras verticais com última barra em accent.

```html
<svg viewBox="0 0 260 100" width="260" height="100">
  <rect x="20" y="60" width="28" height="35" rx="3" fill="var(--brand-surface-2)"/>
  <text x="34" y="98" text-anchor="middle" font-size="7" fill="var(--text-muted)" font-family="var(--font-mono)">Q1</text>

  <rect x="58" y="45" width="28" height="50" rx="3" fill="var(--brand-surface-2)"/>
  <text x="72" y="98" text-anchor="middle" font-size="7" fill="var(--text-muted)" font-family="var(--font-mono)">Q2</text>

  <rect x="96" y="30" width="28" height="65" rx="3" fill="var(--brand-surface-2)"/>
  <text x="110" y="98" text-anchor="middle" font-size="7" fill="var(--text-muted)" font-family="var(--font-mono)">Q3</text>

  <!-- Barra destacada -->
  <rect x="134" y="20" width="28" height="75" rx="3" fill="var(--brand-primary)"/>
  <text x="148" y="98" text-anchor="middle" font-size="7" fill="var(--text-muted)" font-family="var(--font-mono)">Q4</text>

  <line x1="15" y1="95" x2="175" y2="95" stroke="var(--brand-border)" stroke-width="0.5"/>
</svg>
```

---

## Donut Multi-Segmento

Anel com múltiplos segmentos de cor e texto central.

```html
<svg viewBox="0 0 120 120" width="120" height="120">
  <!-- Trilha de fundo -->
  <circle cx="60" cy="60" r="44" fill="none" stroke="var(--brand-surface-2)" stroke-width="14"/>

  <!-- Segmento 1 (50%) -->
  <circle cx="60" cy="60" r="44" fill="none" stroke="var(--brand-primary)" stroke-width="14"
    stroke-dasharray="138 139" stroke-dashoffset="0" class="progress-ring-circle"/>

  <!-- Segmento 2 (25%) -->
  <circle cx="60" cy="60" r="44" fill="none" stroke="var(--brand-secondary)" stroke-width="14"
    stroke-dasharray="69 208" stroke-dashoffset="-138" class="progress-ring-circle"/>

  <!-- Segmento 3 (15%) -->
  <circle cx="60" cy="60" r="44" fill="none" stroke="var(--brand-success)" stroke-width="14"
    stroke-dasharray="40 237" stroke-dashoffset="-207" class="progress-ring-circle"/>

  <!-- Texto central -->
  <text x="60" y="58" text-anchor="middle" fill="var(--text-primary)"
    font-size="16" font-weight="700">R$ 3.2M</text>
  <text x="60" y="72" text-anchor="middle" fill="var(--text-muted)"
    font-size="8" font-family="var(--font-mono)">TOTAL</text>
</svg>
```

**Cálculo:** circumference = 2π × 44 ≈ 276.5.
- Segmento de X%: `stroke-dasharray="(276.5 × X/100) (276.5 - valor)"`
- `stroke-dashoffset` = negativo da soma dos segmentos anteriores

---

## Scatter / Bubble

Pontos com tamanho e cor variáveis.

```html
<svg viewBox="0 0 260 100" width="260" height="100">
  <!-- Eixos -->
  <line x1="30" y1="90" x2="250" y2="90" stroke="var(--brand-border)" stroke-width="0.5"/>
  <line x1="30" y1="0" x2="30" y2="90" stroke="var(--brand-border)" stroke-width="0.5"/>

  <!-- Pontos (cx, cy = posição; r = magnitude; fill = categoria) -->
  <circle cx="50" cy="75" r="5" fill="var(--brand-primary)" opacity="0.4"/>
  <circle cx="100" cy="55" r="8" fill="var(--brand-secondary)" opacity="0.5"/>
  <circle cx="160" cy="48" r="4" fill="var(--brand-success)" opacity="0.5"/>
  <circle cx="210" cy="20" r="12" fill="var(--brand-primary)" opacity="0.7"/>

  <!-- Linha de tendência (opcional) -->
  <line x1="40" y1="80" x2="240" y2="15" stroke="var(--brand-primary)" stroke-width="1" stroke-dasharray="4"/>
</svg>
```

---

## Heatmap (Activity Grid)

Grade 7×N (dias × semanas) gerada via JavaScript.

```html
<svg viewBox="0 0 520 90" width="100%" height="90" id="heatmap-ID"></svg>
```

**JS para gerar:**
```javascript
function generateHeatmap(svgId, cols) {
  const svg = document.getElementById(svgId);
  let html = '';
  const cellSize = 12, gap = 3;
  for (let col = 0; col < cols; col++) {
    for (let row = 0; row < 7; row++) {
      const val = Math.random();
      const opacity = val < 0.2 ? 0.05 : val < 0.4 ? 0.15 : val < 0.6 ? 0.3 : val < 0.8 ? 0.5 : 0.8;
      html += `<rect x="${col*(cellSize+gap)}" y="${row*(cellSize+gap)}" width="${cellSize}" height="${cellSize}" rx="2" fill="var(--brand-primary)" opacity="${opacity}"/>`;
    }
  }
  svg.innerHTML = html;
}
```

**Customização:** Para dados reais, substitua `Math.random()` por valores do dataset.
