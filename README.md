# apresentacao-padrao-fincodex-skill

> Skill para Claude que gera apresentações HTML interativas com a identidade visual finCodex — espresso `#1E0E05`, ouro `#C08830` e cream `#EAE0CC` — em um único arquivo `.html` autocontido.

---

## O que é

Uma **skill para Claude Desktop** que transforma qualquer outline, roteiro ou brief em uma apresentação HTML interativa com a identidade visual da **finCodex** — plataforma de diagnóstico FinOps multi-cloud.

O output é sempre **um único arquivo `.html` autocontido** — sem dependências externas além do Google Fonts, pronto para apresentar no browser ou compartilhar por e-mail.

---

## Funcionalidades

### Motor de navegação
- Navegação por **teclado** (← →), **swipe touch** e **dots clicáveis**
- **Barra de progresso** gold na parte superior
- Contador de slides (ex: `07 / 18`) sempre visível

### Roteiro popup (botão R)
- Abre em **window separada**, resizable, posicionada à direita da tela
- **Timer progressivo** (HH:MM:SS) com pause/resume
- **Sincronização automática** com o slide ativo por polling
- **Estimativa de tempo** por slide (palavras ÷ 130 wpm)
- Navegação direta por slide dentro do popup

### Toggle Claro / Escuro
- **Modo padrão: CLARO** — cream `#EAE0CC` com textos espresso
- **Modo escuro** — espresso `#1E0E05` com textos cream e accent ouro
- Alternância em runtime sem recarregar a página

### Componentes interativos
- **Line Chart com crosshair** — valor dinâmico atualizado via `mousemove`
- **Gauge Canvas 2D** — ponteiro animado com 4 variantes
- **Multi-state Detail Panel** — 5 cards clicáveis com painel de detalhe
- **Charts Tab Switcher** — Bar / Linha / Donut com animação
- **Isometric Conveyor** — esteira animada para pipelines de dados
- **Terminal & Code** — diff colorido, cursor blink, REPL
- **Pipeline com estados** — nós com animação de fluxo
- **Donut rings, progress bars, stat cards** com animação de contagem

### Temas disponíveis
| Tema | Fundo padrão | Accent |
|---|---|---|
| **finCodex** (padrão) | Cream `#EAE0CC` / Espresso `#1E0E05` | Gold `#C08830` |
| Midnight Executive | `#0A0A0A` | Âmbar `#D4A017` |
| Warm Terracotta | `#F5EFE6` | Terracota `#C4622D` |

---

## Estrutura do repositório

```
apresentacao-fincodex-skill/
├── apresentacao-padrao-fincodex-skill/   ← pasta do skill (instalar no Claude)
│   ├── skill.md                          ← instruções principais do skill
│   ├── assets/
│   │   └── template.html                 ← motor base de navegação e roteiro
│   └── references/
│       ├── design-system.md              ← princípios visuais e tipografia
│       ├── execution-flow.md             ← fluxo de 3 fases + placeholders
│       ├── slide-templates.md            ← 16+ tipos de slide documentados
│       ├── components/
│       │   ├── components-foundation.md
│       │   ├── components-dataviz.md
│       │   ├── components-flow.md
│       │   ├── components-terminal.md
│       │   ├── components-visual.md
│       │   └── components-custom.md
│       └── themes/
│           ├── theme-fincodex.md
│           ├── theme-midnight.md
│           └── theme-terracotta.md
├── guia-bolso-fincodex-skill.html        ← referência visual completa (19 slides)
├── apresentacao-padrao-fincodex-skill.zip
└── README.md
```

---

## Como instalar no Claude Desktop

### Pré-requisitos
- [Claude Desktop](https://claude.ai/download) instalado (macOS ou Windows)
- Conta Claude **Pro** ou **Team**

### Passo a passo

**1. Baixar o skill**

Faça o download do arquivo `apresentacao-padrao-fincodex-skill.zip` e descompacte em uma pasta de sua preferência.

**2. Abrir as configurações do Claude Desktop**

```
macOS:  Claude → Settings → Skills
Windows: Menu → Settings → Skills
```

**3. Adicionar o skill**

Clique em **"Add Skill"**, navegue até a pasta `apresentacao-padrao-fincodex-skill` descompactada e selecione o arquivo `skill.md`.

**4. Confirmar a instalação**

O skill aparecerá na lista como `apresentacao-padrao-fincodex`. A partir deste momento, o Claude terá acesso a todos os componentes, temas e ao fluxo de geração.

---

## Como usar

Após instalar, inicie uma conversa no Claude Desktop com qualquer um destes inputs:

```
"Crie uma apresentação sobre os resultados do Q3 com foco em redução de custos"

"Transforme esse outline em uma apresentação finCodex no modo escuro"

"Gere um deck executivo sobre a estratégia de FinOps para 2025"
```

O Claude seguirá o fluxo de **3 fases**:

| Fase | O que acontece |
|---|---|
| **1 — Plano** | Mapeia o conteúdo em slides, sugere componentes, esboça roteiro. Pergunta o modo (CLARO/ESCURO) |
| **2 — Design (Craft)** | Constrói cada slide individualmente com preview visual. Aguarda aprovação antes de avançar |
| **3 — Montagem** | Gera o arquivo `.html` final com todos os slides aprovados, roteiro e motor de navegação |

---

## Guia de Bolso

O arquivo `guia-bolso-fincodex-skill.html` é uma **referência visual interativa** com 19 slides demonstrando ao vivo todos os componentes disponíveis no skill.

Abra diretamente no browser para explorar.

---

## Princípios de design finCodex

- **Uma informação por slide** — regra core
- **Gold `#C08830`** como única cor de destaque por slide
- **Space Grotesk** para headlines, **Inter** para corpo, **JetBrains Mono** para labels
- Slides com scroll invisível quando o conteúdo ultrapassa a altura — sem divisão forçada
- Logo `finCodex` sempre no canto superior direito
- Modo padrão: **CLARO** — cream sobre espresso

---

## Prompt de teste

Copie e cole no Claude Desktop após instalar o skill para validar os componentes:

```
/apresentacao-padrao-fincodex-skill  Crie uma apresentação de teste para validar os componentes da skill.
Tema: FinOps na prática — primeiros 90 dias
Slides (5):

1. Cover — "FinOps na Prática" / subtítulo: "Os primeiros 90 dias que mudam o jogo"
2. Diagnóstico — 3 stats animados: R$ 2.8M gasto cloud / 34% sem tag / 12 serviços ociosos
3. Pipeline — 4 etapas: Mapeamento → Diagnóstico → Hipóteses → Captura
4. Statement — frase de impacto: "Visibilidade sem ação é só um relatório bonito."
5. CTA — próximos passos: workshop de priorização, validação técnica, kickoff Q3

Roteiro: gere um roteiro real para cada slide — como se eu fosse apresentar para um C-level em 10 minutos.
Tema finCodex obrigatório. Me pergunte o modo antes de gerar.
Mostre cada slide como preview inline para aprovação antes de montar o HTML final.
```

---

## Licença

Uso interno — finCodex.
