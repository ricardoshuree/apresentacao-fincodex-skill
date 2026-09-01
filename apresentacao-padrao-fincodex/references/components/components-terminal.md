# Componentes — Terminal & Code

Terminal prompt, stream de logs, diff view, bloco de código e REPL.
Use quando o conteúdo envolve código, CLI, configuração ou output de sistema.

---

## Terminal Base

Container com barra de título (3 dots) e corpo de texto mono.

```html
<div class="terminal">
  <div class="terminal-bar">
    <span class="terminal-dot" style="background:#FF5F57;"></span>
    <span class="terminal-dot" style="background:#FEBC2E;"></span>
    <span class="terminal-dot" style="background:#28C840;"></span>
    <span style="font-size:11px;color:#8B949E;margin-left:8px;">~/project</span>
  </div>
  <div class="terminal-body">
    <!-- conteúdo -->
  </div>
</div>
```

---

## Prompt (Comandos CLI)

```html
<div class="terminal-body">
  <div><span class="terminal-prompt">❯ </span><span class="terminal-cmd">agent plan</span> <span class="terminal-string">--from "deploy pipeline"</span></div>
  <div><span class="terminal-prompt">❯ </span><span class="terminal-cmd">agent run</span> <span class="terminal-string">--env "prod"</span><span class="terminal-cursor"></span></div>
</div>
```

**Classes de syntax:**
- `.terminal-prompt` → verde (símbolo do prompt)
- `.terminal-cmd` → branco (comando)
- `.terminal-string` → azul claro (strings/argumentos)
- `.terminal-cursor` → bloco piscante (animação blink)

---

## Stream (Logs em Tempo Real)

```html
<div class="terminal-body">
  <div><span class="terminal-comment">14:02:11</span> <span class="terminal-keyword">info</span> load session devo/le4</div>
  <div><span class="terminal-comment">14:02:13</span> <span class="terminal-func">ok</span> plan drafted — 6 steps</div>
  <div><span class="terminal-comment">14:02:14</span> <span class="terminal-output">warn</span> lint: 2 unused imports</div>
  <div><span class="terminal-comment">14:02:16</span> <span class="terminal-func">ok</span> fixed — autoformatting</div>
</div>
```

**Classes de syntax:**
- `.terminal-comment` → cinza (timestamps)
- `.terminal-keyword` → vermelho (info, error)
- `.terminal-func` → roxo (ok, success)
- `.terminal-output` → cinza claro (output geral)

**Combina bem com:** Badge `.badge-live` no header do card.

---

## Diff View

```html
<div class="terminal-body">
  <div><span class="diff-info">@@ -14,6 +14,7 @@</span></div>
  <div>  function App() {</div>
  <span class="diff-del">-  const title = 'Hello'</span>
  <span class="diff-add">+  const title = 'Ship in minutes'</span>
  <span class="diff-add">+  const cta = 'Try the agent'</span>
  <div>    return &lt;h1&gt;{title}&lt;/h1&gt;</div>
</div>
```

**Classes:**
- `.diff-add` → fundo verde sutil, texto verde
- `.diff-del` → fundo vermelho sutil, texto vermelho
- `.diff-info` → azul (info de posição)

---

## Code Block (Syntax Highlighting)

```html
<div class="terminal-body">
  <div><span class="terminal-comment">// plan from intent</span></div>
  <div><span class="terminal-keyword">export async function</span> <span class="terminal-func">plan</span>(intent: <span class="terminal-number">string</span>) {</div>
  <div>  <span class="terminal-keyword">const</span> steps = <span class="terminal-keyword">await</span> agent.<span class="terminal-func">plan</span>(intent)</div>
  <div>  <span class="terminal-keyword">return</span> steps.<span class="terminal-func">filter</span>(s => s.safe)</div>
  <div>}</div>
</div>
```

**Classes adicionais:**
- `.terminal-number` → azul (tipos, números)
- `.terminal-func` → roxo (nomes de funções)

---

## REPL (Chat Agent)

```html
<div class="terminal-body">
  <div><span class="terminal-keyword">you&gt;</span> wire the contact form</div>
  <div><span class="terminal-func">agent&gt;</span> <span class="terminal-output">reading routes, picking endpoint</span></div>
  <div><span class="terminal-func">agent&gt;</span> <span class="terminal-output">writing handler</span><span class="terminal-cursor"></span></div>
</div>
```

---

## Run com Progress

Terminal com checklist de etapas e barra de progresso.

```html
<div class="terminal-body">
  <div><span class="terminal-prompt">&gt; </span>agent run ship</div>
  <div>  <span class="terminal-func">✓</span> read repo</div>
  <div>  <span class="terminal-func">✓</span> plan 6 steps</div>
  <div>  <span class="terminal-output">⟳ running tests</span></div>
  <div style="margin-top:6px;">
    <div style="height:3px;background:var(--brand-surface-2);border-radius:2px;">
      <div style="height:100%;width:65%;background:var(--brand-error);border-radius:2px;"></div>
    </div>
  </div>
</div>
```

---

## CSS Necessário

O CSS para todos os componentes de terminal está definido no `assets/template.html`.
Cores de syntax usam variáveis do tema quando possível, mas mantêm fallbacks hardcoded para o fundo escuro do terminal (#0D1117) que funciona em qualquer tema.
