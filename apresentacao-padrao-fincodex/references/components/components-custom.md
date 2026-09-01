# Componentes — Custom

Flow-break, gauge/needle, drift, fresh-start, air-gap, waveform.
Componentes personalizados para narrativas visuais específicas.

---

## Flow Break ("Reads fine. Writes fail.")

Pipeline onde o fluxo funciona até um ponto de quebra.
Nós verdes (working) → break point vermelho → nó vermelho (broken).

```html
<svg viewBox="0 0 260 60" width="260" height="60">
  <!-- Nó READ (success) -->
  <rect x="10" y="18" width="55" height="24" rx="4"
    fill="var(--brand-success-dim)" stroke="var(--brand-success)" stroke-width="1"/>
  <text x="37" y="34" text-anchor="middle" font-size="9"
    fill="var(--brand-success)" font-family="var(--font-mono)">READ</text>

  <!-- Nó PLAN (success) -->
  <rect x="95" y="18" width="55" height="24" rx="4"
    fill="var(--brand-success-dim)" stroke="var(--brand-success)" stroke-width="1"/>
  <text x="122" y="34" text-anchor="middle" font-size="9"
    fill="var(--brand-success)" font-family="var(--font-mono)">PLAN</text>

  <!-- Nó WRITE (error) -->
  <rect x="180" y="18" width="65" height="24" rx="4"
    fill="var(--brand-error-dim)" stroke="var(--brand-error)" stroke-width="1"/>
  <text x="212" y="34" text-anchor="middle" font-size="9"
    fill="var(--brand-error)" font-family="var(--font-mono)">WRITE</text>

  <!-- Conectores -->
  <line x1="65" y1="30" x2="95" y2="30" stroke="var(--brand-success)" stroke-width="1.5" stroke-dasharray="4"/>
  <line x1="150" y1="30" x2="180" y2="30" stroke="var(--brand-error)" stroke-width="1.5" stroke-dasharray="4"/>

  <!-- Break indicator -->
  <circle cx="165" cy="30" r="6" fill="var(--brand-error)" opacity="0.8"/>
  <text x="165" y="33" text-anchor="middle" font-size="8" fill="#fff" font-weight="700">✕</text>

  <!-- Dot animado no caminho verde -->
  <circle r="4" fill="var(--brand-success)">
    <animateMotion dur="2s" repeatCount="indefinite" path="M37,30 L122,30"/>
  </circle>

  <!-- Labels -->
  <text x="37" y="55" text-anchor="middle" font-size="7"
    fill="var(--text-muted)" font-family="var(--font-mono)">WORKING</text>
  <text x="212" y="55" text-anchor="middle" font-size="7"
    fill="var(--brand-error)" font-family="var(--font-mono)">BROKEN</text>
</svg>
```

**Customização:** Troque os labels dos nós e ajuste a posição do break point.
O dot animado via `<animateMotion>` percorre apenas o caminho "working".

---

## Gauge / Needle (Ceiling)

Medidor semicircular com agulha indicando nível.

```html
<svg viewBox="0 0 200 120" width="200" height="120">
  <!-- Arco de fundo -->
  <path d="M 30 100 A 70 70 0 0 1 170 100" fill="none"
    stroke="var(--brand-surface-2)" stroke-width="8" stroke-linecap="round"/>

  <!-- Segmentos de cor -->
  <path d="M 30 100 A 70 70 0 0 1 80 35" fill="none"
    stroke="var(--brand-success)" stroke-width="8" stroke-linecap="round"/>
  <path d="M 80 35 A 70 70 0 0 1 130 35" fill="none"
    stroke="var(--brand-warning)" stroke-width="8" stroke-linecap="round"/>
  <path d="M 130 35 A 70 70 0 0 1 155 55" fill="none"
    stroke="var(--brand-primary)" stroke-width="8" stroke-linecap="round"/>

  <!-- Agulha -->
  <line x1="100" y1="100" x2="145" y2="50" stroke="var(--brand-primary)"
    stroke-width="2" stroke-linecap="round"/>
  <circle cx="100" cy="100" r="5" fill="var(--brand-primary)"/>

  <!-- Label -->
  <text x="100" y="90" text-anchor="middle" font-size="10"
    fill="var(--text-muted)" font-family="var(--font-mono)">TOKENS · 7,248 / 10K</text>
</svg>
```

**Customização:** Ajuste o endpoint da agulha (`x2`, `y2`) para indicar diferentes valores.
- Verde (baixo): `x2="55" y2="55"`
- Amarelo (médio): `x2="100" y2="30"`
- Vermelho (alto): `x2="155" y2="55"`

---

## Drift (Deterministic vs Non-deterministic)

Contraste visual entre output previsível e output variável.

```html
<div style="display:flex;gap:24px;align-items:center;">
  <!-- Deterministic -->
  <div style="text-align:center;">
    <svg viewBox="0 0 80 50" width="80" height="50">
      <line x1="10" y1="25" x2="70" y2="25" stroke="var(--brand-success)" stroke-width="2"/>
      <line x1="10" y1="30" x2="70" y2="30" stroke="var(--brand-success)" stroke-width="2" opacity="0.5"/>
      <line x1="10" y1="20" x2="70" y2="20" stroke="var(--brand-success)" stroke-width="2" opacity="0.5"/>
    </svg>
    <div style="font-family:var(--font-mono);font-size:9px;color:var(--brand-success);">DETERMINISTIC</div>
  </div>

  <!-- Drifts -->
  <div style="text-align:center;">
    <svg viewBox="0 0 80 50" width="80" height="50">
      <line x1="10" y1="25" x2="70" y2="15" stroke="var(--brand-error)" stroke-width="2"/>
      <line x1="10" y1="25" x2="70" y2="35" stroke="var(--brand-error)" stroke-width="2" opacity="0.5"/>
      <circle cx="55" cy="12" r="2" fill="var(--brand-error)" opacity="0.4"/>
      <circle cx="65" cy="38" r="2" fill="var(--brand-error)" opacity="0.4"/>
    </svg>
    <div style="font-family:var(--font-mono);font-size:9px;color:var(--brand-error);">DRIFTS</div>
  </div>
</div>
```

---

## Fresh Start (Empty State)

Contraste entre caixa preenchida e caixa vazia/ghost.

```html
<svg viewBox="0 0 200 80" width="200" height="80">
  <!-- Caixa preenchida -->
  <rect x="30" y="15" width="50" height="50" rx="6"
    fill="var(--brand-surface-2)" stroke="var(--brand-primary)" stroke-width="1.5"/>
  <rect x="40" y="25" width="30" height="4" rx="2" fill="var(--brand-primary)" opacity="0.5"/>
  <rect x="40" y="33" width="20" height="4" rx="2" fill="var(--brand-primary)" opacity="0.3"/>

  <!-- Caixa ghost -->
  <rect x="120" y="15" width="50" height="50" rx="6" fill="none"
    stroke="var(--brand-border)" stroke-width="1" stroke-dasharray="4"/>
  <text x="145" y="44" text-anchor="middle" font-size="9"
    fill="var(--text-muted)" font-family="var(--font-mono)">EMPTY</text>
</svg>
```

---

## Air-Gap

Dois elementos separados por uma conexão quebrada.

```html
<svg viewBox="0 0 200 80" width="200" height="80">
  <!-- Local -->
  <rect x="20" y="20" width="40" height="40" rx="6"
    fill="var(--brand-surface-2)" stroke="var(--brand-border)" stroke-width="1"/>
  <text x="40" y="75" text-anchor="middle" font-size="8"
    fill="var(--brand-primary)" font-family="var(--font-mono)">LOCAL</text>

  <!-- Conexão quebrada -->
  <line x1="70" y1="40" x2="120" y2="40" stroke="var(--brand-border)" stroke-width="1" stroke-dasharray="6"/>
  <circle cx="95" cy="40" r="8" fill="var(--brand-error-dim)" stroke="var(--brand-error)" stroke-width="1"/>
  <text x="95" y="43" text-anchor="middle" font-size="8" fill="var(--brand-error)">✕</text>

  <!-- Cloud -->
  <rect x="130" y="20" width="50" height="40" rx="12"
    fill="var(--brand-surface-2)" stroke="var(--brand-border)" stroke-width="1"/>
  <text x="155" y="75" text-anchor="middle" font-size="8"
    fill="var(--text-muted)" font-family="var(--font-mono)">CLOUD</text>
</svg>
```

---

## Waveform (Voice / Audio)

Barras verticais com alturas variáveis simulando forma de onda.

```html
<svg viewBox="0 0 260 50" width="260" height="50" id="waveform-ID"></svg>
```

**JS para gerar:**
```javascript
(function() {
  const svg = document.getElementById('waveform-ID');
  let html = '';
  for (let i = 0; i < 50; i++) {
    const h = 5 + Math.random() * 35;
    const y = 25 - h / 2;
    html += `<rect x="${i*5+5}" y="${y}" width="3" height="${h}" rx="1.5"
      fill="var(--brand-primary)" opacity="${0.4 + Math.random()*0.5}"/>`;
  }
  svg.innerHTML = html;
})();
```

**Complemento visual:**
```html
<div style="text-align:center;font-family:var(--font-mono);font-size:11px;color:var(--text-muted);">
  'book a flight to Tokyo'
</div>
```

**Combina com:** Indicador REC (dot vermelho + timestamp) no header do card.
