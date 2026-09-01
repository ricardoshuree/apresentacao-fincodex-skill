# Componentes — Visual Styles

Isométrico, blueprint/planta-baixa, pergaminho/caderno, exploded view, wireframe 3D.
Estilos visuais especiais que adicionam personalidade e contexto temático.

---

## Isometric (Stacked Tower)

Blocos isométricos empilhados com glow line vertical.

```html
<svg viewBox="0 0 200 160" width="200" height="160">
  <!-- Plataforma base -->
  <polygon points="100,130 170,95 100,60 30,95"
    fill="var(--brand-surface-2)" stroke="var(--brand-border)" stroke-width="1"/>

  <!-- Bloco 1 (inferior) -->
  <polygon points="60,95 100,75 100,55 60,75" fill="var(--brand-primary)" opacity="0.3"/>
  <polygon points="100,75 140,95 140,75 100,55" fill="var(--brand-primary)" opacity="0.2"/>
  <polygon points="60,75 100,55 140,75 100,95" fill="var(--brand-primary)" opacity="0.4"/>

  <!-- Bloco 2 (superior, flutuante) -->
  <polygon points="70,65 100,50 100,30 70,45" fill="var(--brand-secondary)" opacity="0.3"/>
  <polygon points="100,50 130,65 130,45 100,30" fill="var(--brand-secondary)" opacity="0.2"/>
  <polygon points="70,45 100,30 130,45 100,60" fill="var(--brand-secondary)" opacity="0.4"/>

  <!-- Glow line (fluxo vertical) -->
  <line x1="100" y1="130" x2="100" y2="30" stroke="var(--brand-primary)"
    stroke-width="1" class="glow-line" stroke-dasharray="20 80"/>
</svg>
```

**Uso:** Arquitetura em camadas, stacks de tecnologia, composição modular.

---

## Blueprint (Planta Baixa)

Fundo com grid + componente técnico com dimension leaders.

```html
<div class="blueprint-bg">
  <svg viewBox="0 0 220 100" width="100%" height="100">
    <!-- Dimension leader horizontal -->
    <line x1="20" y1="15" x2="200" y2="15" stroke="var(--brand-primary)" stroke-width="0.8"/>
    <line x1="20" y1="12" x2="20" y2="18" stroke="var(--brand-primary)" stroke-width="0.8"/>
    <line x1="200" y1="12" x2="200" y2="18" stroke="var(--brand-primary)" stroke-width="0.8"/>
    <text x="110" y="12" text-anchor="middle" font-size="9"
      fill="var(--brand-primary)" font-family="var(--font-mono)">180.0 mm</text>

    <!-- Componente (caixa tracejada com elementos internos) -->
    <rect x="40" y="30" width="140" height="50" rx="2" fill="none"
      stroke="var(--text-secondary)" stroke-width="1" stroke-dasharray="4"/>
    <circle cx="80" cy="55" r="6" fill="var(--text-muted)" opacity="0.3"
      stroke="var(--text-secondary)" stroke-width="0.5"/>
    <circle cx="140" cy="55" r="6" fill="var(--text-muted)" opacity="0.3"
      stroke="var(--text-secondary)" stroke-width="0.5"/>

    <!-- Labels -->
    <text x="40" y="92" font-size="8" fill="var(--text-muted)" font-family="var(--font-mono)">SECT. A-A</text>
    <text x="200" y="92" text-anchor="end" font-size="8" fill="var(--text-muted)" font-family="var(--font-mono)">FLOW →</text>
  </svg>
</div>
```

**CSS para o fundo grid:**
```css
.blueprint-bg {
  background: linear-gradient(rgba(20,40,80,0.3) 1px, transparent 1px),
              linear-gradient(90deg, rgba(20,40,80,0.3) 1px, transparent 1px);
  background-size: 20px 20px;
  border-radius: var(--radius-sm);
  padding: 24px;
}
```

---

## Parchment (Pergaminho / Caderno)

Fundo claro com textura de linhas e destaques em vermelho.

```html
<div class="parchment-card">
  <div style="font-family:var(--font-mono);font-size:10px;color:#8B7355;text-transform:uppercase;letter-spacing:1px;margin-bottom:12px;">
    Journal of Agentic Work · Vol. III
  </div>
  <p style="font-size:14px;line-height:1.7;position:relative;z-index:1;">
    Texto do conteúdo com <span class="parchment-highlight">destaque em vermelho</span> nas palavras-chave.
  </p>
  <div style="font-family:var(--font-mono);font-size:10px;color:#8B7355;margin-top:16px;">
    Autor · 2026 · pp. 12-47
  </div>
</div>
```

**CSS:**
```css
.parchment-card {
  background: #F5F0E8;
  border: 1px solid #D4C9B8;
  border-radius: var(--radius-sm);
  padding: 24px;
  color: #2C2418;
  font-family: var(--font-display);
}
.parchment-card::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0; bottom: 0;
  background: repeating-linear-gradient(transparent, transparent 27px, #E8DDD0 28px);
  pointer-events: none;
  opacity: 0.4;
}
.parchment-highlight {
  background: rgba(239,68,68,0.15);
  padding: 1px 4px;
  border-radius: 2px;
  color: #C0392B;
}
```

**Uso:** Citações acadêmicas, princípios, listas de regras, conteúdo reflexivo.

---

## Exploded View

Camadas separadas com dimension leaders laterais.

```html
<svg viewBox="0 0 200 140" width="200" height="140">
  <!-- Dimension line lateral -->
  <line x1="25" y1="20" x2="25" y2="120" stroke="var(--brand-border-hi)" stroke-width="0.5" stroke-dasharray="3"/>
  <text x="18" y="18" font-size="8" fill="var(--text-muted)" font-family="var(--font-mono)">ø 12</text>

  <!-- Camada 1 -->
  <rect x="50" y="15" width="100" height="25" rx="4"
    fill="var(--brand-surface-2)" stroke="var(--brand-border)" stroke-width="1"/>
  <text x="100" y="31" text-anchor="middle" font-size="9"
    fill="var(--text-secondary)" font-family="var(--font-mono)">A1 — INTAKE</text>

  <!-- Camada 2 -->
  <rect x="50" y="50" width="100" height="25" rx="4"
    fill="var(--brand-surface-2)" stroke="var(--brand-border)" stroke-width="1"/>
  <text x="100" y="66" text-anchor="middle" font-size="9"
    fill="var(--text-secondary)" font-family="var(--font-mono)">A2 — PLANNER</text>

  <!-- Camada 3 (destacada) -->
  <rect x="50" y="85" width="100" height="25" rx="4"
    fill="var(--brand-primary-dim)" stroke="var(--brand-primary)" stroke-width="1"/>
  <text x="100" y="101" text-anchor="middle" font-size="9"
    fill="var(--brand-primary)" font-family="var(--font-mono)">A3 — TOOLS</text>
</svg>
```

---

## Wireframe 3D (Axonometric)

Cubo wireframe com eixos rotulados.

```html
<svg viewBox="0 0 200 140" width="200" height="140">
  <!-- Faces do cubo -->
  <polygon points="100,20 160,50 100,80 40,50" fill="none" stroke="var(--text-secondary)" stroke-width="1"/>
  <line x1="100" y1="20" x2="100" y2="60" stroke="var(--text-secondary)" stroke-width="1"/>
  <line x1="160" y1="50" x2="160" y2="90" stroke="var(--text-secondary)" stroke-width="1"/>
  <line x1="100" y1="80" x2="100" y2="120" stroke="var(--text-secondary)" stroke-width="1"/>
  <line x1="40" y1="50" x2="40" y2="90" stroke="var(--text-secondary)" stroke-width="1" stroke-dasharray="4"/>
  <polygon points="100,60 160,90 100,120 40,90" fill="none" stroke="var(--text-secondary)" stroke-width="1"/>

  <!-- Eixos -->
  <text x="100" y="135" text-anchor="middle" font-size="8" fill="var(--text-muted)" font-family="var(--font-mono)">X 100</text>
  <text x="170" y="72" font-size="8" fill="var(--text-muted)" font-family="var(--font-mono)">Y 100</text>
  <text x="25" y="72" font-size="8" fill="var(--brand-primary)" font-family="var(--font-mono)">Z 60 ▲</text>
</svg>
```
