# Componentes — Flow & Pipelines

Pipelines animados, hub-and-spoke, data flow, attention queue, sessions, tabs.
Use quando o conteúdo descreve processos, conexões ou fluxos de dados.

---

## Pipeline Linear

Nós conectados por arestas com dot animado percorrendo o caminho.

```html
<div class="flow-nodes">
  <div class="flow-node success">Edit</div>
  <div class="flow-edge"><div class="flow-edge-dot"></div></div>
  <div class="flow-node success">Format</div>
  <div class="flow-edge"><div class="flow-edge-dot"></div></div>
  <div class="flow-node active">Lint</div>
  <div class="flow-edge"><div class="flow-edge-dot"></div></div>
  <div class="flow-node">Commit</div>
</div>
```

**Estados dos nós:**
- Sem classe: pendente (borda neutra)
- `.active`: em execução (borda primary + glow)
- `.success`: concluído (borda success)
- `.error`: falhou (borda error)

**Animação:** `.flow-edge-dot` percorre a aresta com `animation: flowDot 2s linear infinite`.

---

## Hub-and-Spoke

Nó central conectado a nós periféricos com linhas animadas (glow).

```html
<svg viewBox="0 0 200 140" width="200" height="140">
  <!-- Linhas base (traço cinza) -->
  <line x1="100" y1="70" x2="30" y2="25" stroke="var(--brand-border-hi)" stroke-width="1" stroke-dasharray="4"/>
  <line x1="100" y1="70" x2="170" y2="25" stroke="var(--brand-border-hi)" stroke-width="1" stroke-dasharray="4"/>
  <line x1="100" y1="70" x2="30" y2="115" stroke="var(--brand-border-hi)" stroke-width="1" stroke-dasharray="4"/>
  <line x1="100" y1="70" x2="170" y2="115" stroke="var(--brand-border-hi)" stroke-width="1" stroke-dasharray="4"/>

  <!-- Linhas glow (animadas) -->
  <line x1="100" y1="70" x2="30" y2="25" stroke="var(--brand-primary)" stroke-width="2" class="glow-line"/>
  <line x1="100" y1="70" x2="170" y2="25" stroke="var(--brand-primary)" stroke-width="2" class="glow-line" style="animation-delay:-0.5s"/>
  <line x1="100" y1="70" x2="30" y2="115" stroke="var(--brand-primary)" stroke-width="2" class="glow-line" style="animation-delay:-1s"/>
  <line x1="100" y1="70" x2="170" y2="115" stroke="var(--brand-primary)" stroke-width="2" class="glow-line" style="animation-delay:-1.5s"/>

  <!-- Hub central -->
  <circle cx="100" cy="70" r="16" fill="var(--brand-primary)" opacity="0.2"/>
  <circle cx="100" cy="70" r="8" fill="var(--brand-primary)"/>

  <!-- Nós periféricos -->
  <rect x="18" y="13" width="24" height="24" rx="4" fill="var(--brand-surface-2)" stroke="var(--brand-border)" stroke-width="1"/>
  <rect x="158" y="13" width="24" height="24" rx="4" fill="var(--brand-surface-2)" stroke="var(--brand-border)" stroke-width="1"/>
  <rect x="18" y="103" width="24" height="24" rx="4" fill="var(--brand-surface-2)" stroke="var(--brand-border)" stroke-width="1"/>
  <rect x="158" y="103" width="24" height="24" rx="4" fill="var(--brand-surface-2)" stroke="var(--brand-border)" stroke-width="1"/>
</svg>
```

**Animação glow-line:** `stroke-dasharray: 40 160; animation: glowFlow 3s linear infinite`.
Use `animation-delay` negativo para escalonar as linhas.

**Customização:** Ajuste posições dos nós periféricos. Para 6 nós, distribua em hexágono.

---

## Data Flow (Linear com Labels)

Blocos conectados com labels nas arestas.

```html
<svg viewBox="0 0 240 100" width="240" height="100">
  <text x="12" y="55" font-size="10" fill="var(--text-muted)" font-family="var(--font-mono)">IN</text>

  <rect x="36" y="35" width="50" height="30" rx="4" fill="var(--brand-surface-2)" stroke="var(--brand-border)" stroke-width="1"/>
  <text x="61" y="54" text-anchor="middle" font-size="9" fill="var(--text-secondary)" font-family="var(--font-mono)">PROC</text>

  <line x1="86" y1="50" x2="130" y2="50" stroke="var(--brand-border-hi)" stroke-width="1"/>
  <line x1="86" y1="50" x2="130" y2="50" stroke="var(--brand-primary)" stroke-width="2" class="glow-line"/>
  <text x="108" y="44" text-anchor="middle" font-size="8" fill="var(--text-muted)" font-family="var(--font-mono)">T1</text>

  <rect x="130" y="35" width="50" height="30" rx="4" fill="var(--brand-surface-2)" stroke="var(--brand-border)" stroke-width="1"/>
  <text x="155" y="54" text-anchor="middle" font-size="9" fill="var(--text-secondary)" font-family="var(--font-mono)">XFORM</text>

  <text x="218" y="55" font-size="10" fill="var(--text-muted)" font-family="var(--font-mono)">OUT</text>
</svg>
```

---

## Attention Queue

Lista de itens com um destacado como "needs you".

```html
<div style="display:flex;flex-direction:column;gap:8px;width:100%;">
  <div style="display:flex;align-items:center;gap:8px;">
    <div style="width:20px;height:20px;border:1px solid var(--brand-border);border-radius:3px;"></div>
    <div style="flex:1;height:4px;background:var(--brand-surface-2);border-radius:2px;"></div>
  </div>
  <div style="display:flex;align-items:center;gap:8px;">
    <div style="width:20px;height:20px;border:2px solid var(--brand-primary);border-radius:3px;background:var(--brand-primary-dim);"></div>
    <div style="flex:1;height:4px;background:var(--brand-primary);border-radius:2px;"></div>
    <span class="badge badge-primary" style="font-size:9px;">Needs you</span>
  </div>
</div>
```

---

## Sessions (Lista de Sessões)

```html
<div style="display:flex;flex-direction:column;gap:6px;font-family:var(--font-mono);font-size:11px;">
  <div style="display:flex;align-items:center;gap:8px;color:var(--text-muted);">
    <div style="width:8px;height:8px;border-radius:2px;background:var(--text-muted);"></div>robo
  </div>
  <div style="display:flex;align-items:center;gap:8px;color:var(--brand-primary);">
    <div style="width:8px;height:8px;border-radius:2px;background:var(--brand-primary);"></div>devo
    <span class="badge badge-live" style="font-size:8px;margin-left:auto;">Live</span>
  </div>
</div>
```

---

## Tabs (Surface)

```html
<div style="display:flex;gap:0;font-family:var(--font-mono);font-size:11px;">
  <div style="padding:6px 16px;border:1px solid var(--brand-border);border-bottom:none;border-radius:6px 6px 0 0;color:var(--text-muted);">Chat</div>
  <div style="padding:6px 16px;border:1px solid var(--brand-primary);border-bottom:none;border-radius:6px 6px 0 0;color:var(--brand-primary);background:var(--brand-primary-dim);">Tasks</div>
  <div style="padding:6px 16px;border:1px solid var(--brand-border);border-bottom:none;border-radius:6px 6px 0 0;color:var(--text-muted);">Diff</div>
</div>
<div style="border:1px solid var(--brand-border);border-radius:0 0 6px 6px;padding:12px;min-height:40px;">
  <!-- conteúdo da tab ativa -->
</div>
```
