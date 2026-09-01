# Slide Templates

Padrões HTML para cada tipo de slide.
Use como estruturas-base — adapte conteúdo e componentes, mas preserve a lógica estrutural e os limites.

---

## Regras Globais

- Todo slide cabe em `100vh` — se transbordar, divida
- Use o wrapper `<section class="slide" data-slide="N">`
- Use `.animate` e `.delay-N` para revelações escalonadas
- Contador no formato `NN / TOTAL` via `.slide-counter`
- Uma ideia clara por slide
- HTML semântico sempre que possível

---

## Estrutura Base

```html
<section class="slide" data-slide="0">
  <div class="slide-inner">
    <div class="slide-counter">01 / 10</div>
    <!-- conteúdo do slide -->
  </div>
</section>
```

---

## 1. Cover (Título)

**Quando usar:** Abertura, título da apresentação, início de seção.

**Limites:** Eyebrow ≤ 4 palavras · Título ≤ 10 palavras · Subtítulo ≤ 20 palavras · Badge opcional: 1

```html
<section class="slide" data-slide="0">
  <div class="slide-inner cover-layout">
    <div class="slide-counter">01 / 10</div>
    <div>
      <div class="eyebrow">LABEL DA SEÇÃO</div>
      <h1 class="slide-title animate delay-1">
        Título com <span class="gradient-text">destaque</span>
      </h1>
      <p class="slide-subtitle animate delay-2">Linha de apoio breve.</p>
    </div>
    <!-- Componentes opcionais: stat cards, badges -->
  </div>
</section>
```

---

## 2. Agenda (TOC)

**Quando usar:** Índice interativo com navegação direta para slides.

**Limites:** 5–10 itens · Título do item ≤ 4 palavras · Descrição ≤ 8 palavras

```html
<section class="slide" data-slide="1">
  <div class="slide-inner agenda-layout">
    <div class="slide-counter">02 / 10</div>
    <div>
      <div class="eyebrow">AGENDA</div>
      <h1 class="slide-title">O que vamos <span class="gradient-text">cobrir</span></h1>
    </div>
    <div class="agenda-list">
      <div class="agenda-item animate delay-1" onclick="goToSlide(2)">
        <span class="agenda-item-num">03</span>
        <div class="agenda-item-content">
          <div class="agenda-item-title">Título da Seção</div>
          <div class="agenda-item-desc">Descrição curta</div>
        </div>
        <span class="agenda-item-arrow">→</span>
      </div>
      <!-- mais itens -->
    </div>
  </div>
</section>
```

---

## 3. Statement (Citação / Declaração)

**Quando usar:** Afirmação forte, tese, takeaway memorável.

**Limites:** Declaração ≤ 20 palavras · Atribuição opcional ≤ 4 palavras

```html
<section class="slide" data-slide="N">
  <div class="slide-inner" style="justify-content:center;align-items:center;text-align:center;">
    <div class="slide-counter">NN / TOTAL</div>
    <blockquote class="slide-title animate delay-1" style="max-width:14ch;">
      O melhor workflow é aquele que <span class="gradient-text">funciona sozinho</span>.
    </blockquote>
    <div class="section-label animate delay-2">Princípio central</div>
  </div>
</section>
```

---

## 4. Cards Grid (Grade de Conteúdo)

**Quando usar:** Features, benefícios, múltiplos itens com descrições curtas.

**Limites:** 3–6 cards · Título do card ≤ 5 palavras · Descrição ≤ 14 palavras

```html
<section class="slide" data-slide="N">
  <div class="slide-inner">
    <div class="slide-counter">NN / TOTAL</div>
    <div class="eyebrow">LABEL</div>
    <h2 class="slide-title" style="font-size:36px;">Título da <span class="gradient-text">seção</span></h2>
    <div class="comp-grid comp-grid-3 mt-24">
      <div class="comp-card animate delay-1">
        <div class="comp-card-header">
          <div><span class="comp-card-num">01</span> <span class="comp-card-label">TAG</span></div>
        </div>
        <div class="comp-card-visual"><!-- componente visual --></div>
        <div class="comp-card-title">Título</div>
        <div class="comp-card-desc">Descrição curta do item.</div>
      </div>
      <!-- mais cards -->
    </div>
  </div>
</section>
```

---

## 5. Comparison (Duas Colunas)

**Quando usar:** Antes vs depois, antigo vs novo, prós vs contras.

**Limites:** 2 colunas · Título ≤ 4 palavras · ≤ 5 bullets · Bullet ≤ 8 palavras

```html
<section class="slide" data-slide="N">
  <div class="slide-inner">
    <div class="slide-counter">NN / TOTAL</div>
    <div class="eyebrow">LABEL</div>
    <h2 class="slide-title" style="font-size:36px;">Título</h2>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-top:24px;">
      <div class="comp-card" style="opacity:0.8;">
        <h3>Antes</h3>
        <ul style="list-style:none;padding:0;color:var(--text-secondary);">
          <li>Item comparativo</li>
        </ul>
      </div>
      <div class="comp-card highlighted">
        <h3>Depois</h3>
        <ul style="list-style:none;padding:0;color:var(--text-secondary);">
          <li>Item comparativo melhor</li>
        </ul>
      </div>
    </div>
  </div>
</section>
```

---

## 6. Diagram (Workflow)

**Quando usar:** Workflows, arquitetura, sistemas conectados.

**Limites:** ≤ 6 nós · Título do nó ≤ 4 palavras · Nota ≤ 10 palavras

Use componentes de `components-flow.md` (pipeline, hub-spoke, data flow).

---

## 7. Stats (Métricas / Resultados)

**Quando usar:** KPIs, métricas, prova numérica.

**Limites:** 1 métrica hero OU 2–4 métricas menores · Label ≤ 4 palavras

### Variante A: Hero Stat

```html
<section class="slide" data-slide="N">
  <div class="slide-inner" style="justify-content:center;">
    <div class="slide-counter">NN / TOTAL</div>
    <div class="section-label animate delay-1">LABEL</div>
    <div class="slide-title animate delay-2" style="font-size:clamp(72px,11vw,180px);">72%</div>
    <p class="slide-subtitle animate delay-3">Linha de apoio explicando a métrica.</p>
  </div>
</section>
```

### Variante B: Stat Grid

Use stat cards ou componentes de `components-dataviz.md` (donut, bar, line).

---

## 8. Steps (Etapas / Numerada)

**Quando usar:** Instruções, processo, ordem de implementação.

**Limites:** 3–5 etapas · Título ≤ 4 palavras · Corpo ≤ 10 palavras

```html
<section class="slide" data-slide="N">
  <div class="slide-inner">
    <div class="slide-counter">NN / TOTAL</div>
    <div class="eyebrow">PROCESSO</div>
    <h2 class="slide-title" style="font-size:36px;">Título</h2>
    <div style="display:flex;flex-direction:column;gap:16px;margin-top:24px;">
      <div style="display:grid;grid-template-columns:72px 1fr;gap:18px;padding:20px 0;border-bottom:1px solid var(--brand-border);" class="animate delay-1">
        <div class="comp-card-num" style="font-size:24px;">01</div>
        <div>
          <h3>Título da etapa</h3>
          <p style="color:var(--text-secondary);font-size:15px;">Descrição breve.</p>
        </div>
      </div>
      <!-- mais etapas -->
    </div>
  </div>
</section>
```

---

## 9. Screenshot / Showcase

**Quando usar:** Evidência de UI, screenshots de produto, proof.

**Limites:** 1 screenshot por slide · Título opcional ≤ 6 palavras · Legenda ≤ 12 palavras

```html
<section class="slide" data-slide="N">
  <div class="slide-inner">
    <div class="slide-counter">NN / TOTAL</div>
    <div class="eyebrow">SHOWCASE</div>
    <h2 class="slide-title" style="font-size:36px;">Título</h2>
    <figure style="border-radius:24px;overflow:hidden;border:1px solid var(--brand-border);box-shadow:0 20px 60px rgba(0,0,0,0.35);margin-top:24px;">
      <img src="screenshot.jpg" alt="Descrição" style="width:100%;height:auto;" />
    </figure>
  </div>
</section>
```

---

## 10. CTA / Encerramento

**Quando usar:** Pitch final, contato, próximos passos.

**Limites:** Mensagem ≤ 10 palavras · Apoio ≤ 16 palavras · 1 CTA primário · 1 link secundário

```html
<section class="slide" data-slide="N">
  <div class="slide-inner cta-layout">
    <div class="slide-counter">NN / TOTAL</div>
    <div>
      <div class="eyebrow">PRÓXIMO PASSO</div>
      <h1 class="slide-title">Pronto para <span class="gradient-text">começar</span>?</h1>
      <p class="slide-subtitle">Linha de apoio.</p>
      <div class="contact-list"><!-- contact cards --></div>
    </div>
    <div class="qr-box"><!-- QR code --></div>
  </div>
</section>
```

---

## 11. Divider (Separador de Seção)

**Quando usar:** Quebra de capítulo, transição.

**Limites:** Eyebrow ≤ 3 palavras · Título ≤ 6 palavras · Linha opcional ≤ 10 palavras

---

## 12. Problem / Solution

**Quando usar:** Enquadramento de dor, desafio e resposta.

Usa o mesmo padrão de Comparison, com coluna esquerda "muted" (problema) e direita "highlighted" (solução).

---

## 13. Timeline

**Quando usar:** Roadmap, cronologia, lançamento em fases.

**Limites:** 3–5 pontos · Título ≤ 4 palavras · Descrição ≤ 8 palavras

---

## 14. Tree / Structure

**Quando usar:** Hierarquias de arquivos, camadas de sistema.

**Limites:** ≤ 3 níveis · ≤ 10 nós · Labels ≤ 5 palavras

---

## 15. FAQ / Q&A

**Quando usar:** Objeções previstas, perguntas frequentes.

**Limites:** 3–4 blocos · Pergunta ≤ 8 palavras · Resposta ≤ 14 palavras

---

## 16. Hub / Network

**Quando usar:** Hub-and-spoke, integrações, ecossistema.

Use componentes de `components-flow.md` (hub-spoke com glow lines).

---

## Guia Rápido de Seleção

| Conteúdo | Tipo de Slide |
|---|---|
| Gancho / abertura | Cover |
| Índice interativo | Agenda |
| Grande afirmação | Statement |
| Múltiplos itens curtos | Cards Grid |
| Antigo vs novo | Comparison |
| Workflow / sistema | Diagram |
| Números / prova | Stats |
| Processo / instruções | Steps |
| Prova de UI | Screenshot |
| Ação final | CTA |
| Quebra de capítulo | Divider |
| Dor e solução | Problem/Solution |
| Roadmap | Timeline |
| Hierarquia | Tree |
| FAQ | FAQ |
| Ecossistema | Hub |

---

## Anti-Padrões

- Parágrafos longos em cards
- Screenshots ao lado de texto denso
- 8+ itens em uma grade
- Múltiplos pontos focais competindo
- Timeline para conceitos sem relação
- Conteúdo transbordando "porque quase cabe"
