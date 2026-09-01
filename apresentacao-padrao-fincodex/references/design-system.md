# Design System

Referência de design para apresentações HTML interativas.
Define princípios estéticos, tipografia, layout e regras de componentes.
As cores concretas (CSS variables) estão nos arquivos de tema em `themes/`.

---

## 1. Intenção de Design

Toda apresentação deve transmitir: tecnologia, precisão, modernidade, premium, alto contraste, intenção visual.

Evite: aparência genérica de "gradiente azul de IA", visuais planos de SaaS, tipografia padrão de navegador, contraste fraco, slides lotados, muitas cores de destaque ao mesmo tempo.

---

## 2. DNA Visual

### Palavras-chave estéticas
- Sala de controle escura
- Dashboard premium
- Educação futurista
- Revelação de produto high-end

### Princípios
- Fundos escuros em primeiro lugar (temas claros são exceção)
- Destaques brilhantes em palavras-chave, bordas, contadores e detalhes de UI
- Títulos fortes e marcantes
- Mono apenas para contadores, labels, tags e metadados
- Layouts espaçosos com vazio intencional
- Cards devem parecer luminosos e premium, não planos

---

## 3. Equilíbrio de Cores

Distribuição recomendada:
- 70% fundos e superfícies
- 20% texto e linhas neutras
- 10% cor de destaque

Nunca use mais de 2 cores de destaque como dominantes no mesmo slide.

---

## 4. Fundos

Fundos nunca devem ser cor pura sólida.
Use superfícies em camadas com brilho radial sutil.

Tratamento preferido: gradiente radial discreto com 2 pontos de luz (accent e secondary) sobre gradiente linear base.

Opcional: textura de grade discreta, ruído muito sutil, brilho atrás de elementos hero.

Não faça: ilustrações carregadas como fundo, gradientes fortes que reduzem legibilidade, glassmorphism em excesso.

---

## 5. Tipografia

### Regras gerais
- Títulos: fortes, levemente condensados, alto peso
- Corpo: altamente legível, peso regular
- Mono: reservado para números de slide, tags, labels, métricas, detalhes de UI

### Escala tipográfica recomendada (via clamp)
- Display: 56px → 96px
- H1: 40px → 72px
- H2: 28px → 48px
- H3: 22px → 32px
- Body large: 18px → 24px
- Body: 18px fixo
- Small: 14px
- Mono: 13px

### Fontes a evitar
- Inter, Roboto, Arial, Times — são genéricas demais para este contexto

### Combinações recomendadas
As fontes concretas estão definidas em cada tema (`themes/`). O design system apenas define que são necessárias: uma fonte display (títulos), uma fonte body (texto), e uma fonte mono (labels/code).

---

## 6. Layout

### Padding de slide
- Desktop: 56px vertical, 64px horizontal
- Tablet: 44px vertical, 36px horizontal
- Mobile: 28px vertical, 20px horizontal

### Largura máxima de conteúdo
- 1280px centralizado

### Alinhamento
- Prefira texto alinhado à esquerda
- Centralize apenas: slides de título, citação e encerramento
- Mantenha ritmo vertical forte
- Cada slide deve ter um ponto focal dominante

### Densidade
Um slide deve parecer editorial, não lotado.
Se o conteúdo parecer apertado, divida em dois slides.

---

## 7. Estilo de Componentes

### Cards
- Fundo com gradiente sutil (white 4% → 2%)
- Borda com baixa opacidade (white 8%)
- Border-radius generoso (20–24px)
- Sombra suave
- Card destacado: borda com cor de accent + glow sutil

### Badges / Pills
- Totalmente arredondados (999px)
- Fonte mono
- Compactos
- Borda sutil
- Destaque apenas quando fizer sentido

### Linhas / Divisores
- Finos (1px)
- Baixa opacidade (white 10%)
- Usados para organizar, nunca dominar

### Botões / CTA
- Primário: fundo preenchido com accent, texto escuro
- Secundário: outline com glow sutil
- Grandes o suficiente para leitura à distância

---

## 8. Tratamento de Títulos

Títulos devem frequentemente incluir ênfase em 1–3 palavras.

Estilos de ênfase permitidos:
- Cor de destaque (accent)
- Sublinhado com glow sutil
- Palavra-chave em caixa destacada
- Composição em linhas separadas

Não faça: texto arco-íris, palavras demais enfatizadas, efeitos decorativos excessivos.

---

## 9. Dados e Estatísticas

Para slides com números:
- Número muito grande (tamanho display)
- Label curto (mono, uppercase)
- Frase de apoio opcional
- Micro label acima ou abaixo

Limites: 2 a 4 métricas por slide. Se precisar de mais, divida.

---

## 10. Diagramas

Diagramas devem parecer arquitetura de produto, não gráficos de sala de aula.

Use: blocos arredondados, linhas conectoras com accent em baixa opacidade, superfícies em camadas, labels contidos, tags mono para termos técnicos.

Evite: setas emaranhadas, cores demais, aparência de fluxograma genérico.

---

## 11. Movimento e Animação

A animação deve parecer refinada e calma.

Use: fade-up, leve scale-in, revelação escalonada, transições suaves.

Evite: bounce, spin, parallax exagerado, transições chamativas.

Timing: 0.5s a 0.8s, ease-out, escalonamento de 80ms a 140ms entre elementos.

---

## 12. Border Radius

Escala de arredondamento:
- Pequenos elementos de UI: 12px
- Cards: 20–24px
- Molduras grandes: 24–28px
- Pills/tags: 999px

Mantenha consistência — não misture valores demais.

---

## 13. Sombras e Glow

- Sombras: suaves, escuras, difusas — para separar camadas
- Glow: sutil, nunca dominante — para enfatizar importância

Bons usos de glow: palavra-chave hero, card ativo, CTA, métrica destacada, nó selecionado.

---

## 14. Heurística Rápida

Antes de finalizar um slide, verifique:
- Parece premium?
- Existe um ponto focal claro?
- A cor de destaque está sendo usada com intenção?
- A tipografia está forte o suficiente?
- Evita estética genérica?
- Caberia em um lançamento de produto high-end?

Se qualquer resposta for "não", simplifique e reestilize.
