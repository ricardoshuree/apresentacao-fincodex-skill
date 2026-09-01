# Componentes — Foundation

Cards, stat cards, badges, progress bars, donut rings.
Estes são os blocos fundamentais usados na maioria dos slides.

---

## Stat Card

Exibe uma métrica com valor grande, label mono e indicador de variação.

```html
<div class="stat-card">
  <div class="flex-between">
    <div class="stat-value">1,284 <span class="stat-unit">tasks/wk</span></div>
    <span class="badge badge-success">+48%</span>
  </div>
  <div class="stat-label">Throughput semanal</div>
</div>
```

**Props configuráveis:**
- `stat-value`: número grande (fonte headline, peso 800)
- `stat-unit`: unidade em tamanho menor
- `stat-label`: descrição em fonte secundária
- Badge de variação: `.badge-success` (positivo), `.badge-error` (negativo)

---

## Cover Stats (Stat Row)

Linha de 2–3 métricas no rodapé de um slide Cover.

```html
<div class="cover-stats">
  <div class="cover-stat">
    <div class="cover-stat-val" data-count="42">0</div>
    <div class="cover-stat-label">Hipóteses identificadas</div>
  </div>
  <div class="cover-stat">
    <div class="cover-stat-val">R$ 3.2M</div>
    <div class="cover-stat-label">Saving estimado</div>
  </div>
</div>
```

**Animação:** `data-count="N"` ativa contador animado no JS do motor.

---

## Comp Card (Card de Componente)

Card interativo com header (número + label), área visual, título e descrição.
Clique destaca o card (`.highlighted`) e pode exibir detail panel.

```html
<div class="comp-card" onclick="highlightCard(this)">
  <div class="comp-card-header">
    <div><span class="comp-card-num">01</span> <span class="comp-card-label">LABEL</span></div>
    <span class="badge badge-primary">Tag</span>
  </div>
  <div class="comp-card-visual">
    <!-- SVG, chart, ou componente visual -->
  </div>
  <div class="comp-card-title">Título do card</div>
  <div class="comp-card-desc">Descrição curta do que este card representa.</div>
</div>
```

**Variações:**
- `.highlighted`: borda accent + glow (estado ativo)
- Grid: `.comp-grid-3` (3 colunas), `.comp-grid-2` (2 colunas)

---

## Detail Panel

Painel que aparece abaixo de uma grid de cards ao clicar em um card.

```html
<div class="detail-panel" id="detail-panel">
  <strong>Título do detalhe</strong>
  <p>Informação contextual expandida sobre o card selecionado.</p>
</div>
```

**Comportamento:** Inicia com `display:none`. Recebe `.visible` via JS ao clicar no card.

---

## Badge

Indicador compacto de status ou categoria.

```html
<span class="badge badge-primary">Primary</span>
<span class="badge badge-success">Success</span>
<span class="badge badge-error">Error</span>
<span class="badge badge-secondary">Info</span>
<span class="badge badge-live">Live</span>
```

**Badge LIVE:** Tem animação de pulse e dot verde antes do texto.

---

## Progress Bar (Multi)

Múltiplas barras de progresso com labels e percentuais.

```html
<div style="display:flex;flex-direction:column;gap:12px;">
  <div>
    <div class="flex-between" style="margin-bottom:4px;">
      <span style="font-size:12px;">Compute</span>
      <span style="font-size:12px;color:var(--brand-primary);">78%</span>
    </div>
    <div style="height:6px;background:var(--brand-surface-2);border-radius:3px;">
      <div style="height:100%;width:78%;background:var(--brand-primary);border-radius:3px;transition:width 1s;"></div>
    </div>
  </div>
  <!-- mais barras -->
</div>
```

**Cores semânticas:** Use `--brand-primary` (normal), `--brand-success` (bom), `--brand-error` (crítico).

---

## Donut Ring

Anel circular com percentual e label central.

```html
<svg viewBox="0 0 120 120" width="120" height="120">
  <!-- Trilha de fundo -->
  <circle cx="60" cy="60" r="48" fill="none" stroke="var(--brand-surface-2)" stroke-width="10"/>
  <!-- Progresso -->
  <circle cx="60" cy="60" r="48" fill="none" stroke="var(--brand-primary)" stroke-width="10"
    stroke-dasharray="247" stroke-dashoffset="44" class="progress-ring-circle"/>
  <!-- Texto central -->
  <text x="60" y="55" text-anchor="middle" fill="var(--brand-primary)"
    font-size="24" font-weight="800" font-family="var(--font-headline)">82%</text>
  <text x="60" y="72" text-anchor="middle" fill="var(--text-muted)"
    font-size="10" font-family="var(--font-mono)">AUTO</text>
</svg>
```

**Cálculo do stroke-dashoffset:** `circumference × (1 - percentage)` onde `circumference = 2 × π × r ≈ 301` para r=48.
- 82% → offset = 301 × 0.18 ≈ 54
- 50% → offset = 301 × 0.50 ≈ 150

---

## Eyebrow

Label de seção com dot e texto mono.

```html
<div class="eyebrow">LABEL DA SEÇÃO</div>
```

**Estilo:** Dot 6px + font mono 11px + letter-spacing 2px + uppercase + cor primary.
