# Claude Code Agent Teams +Nano Banana

> Tópico 3052 · 9 mensagens úteis de 20 totais

---

**INEMA** · 2026-02-15

Vou te dar **o passo a passo direto, prático** para:

1. ✅ Implantar o sistema
2. ✅ Usar o sistema

Vou assumir que você quer rodar do jeito original (Claude Code + Gemini 3 Pro).

---

# 🚀 PARTE 1 — IMPLANTAÇÃO (SETUP)

## 🔹 PASSO 1 — Criar pasta do projeto

```mkdir banana-squad
cd banana-squad```

---

## 🔹 PASSO 2 — Instalar dependências

```pip install google-genai Pillow python-dotenv```

---

## 🔹 PASSO 3 — Criar arquivo `.env`

Na raiz do projeto:

```GEMINI_API_KEY=sua_chave_aqui```

Pegue a chave em:
[https://ai.google.dev/](https://ai.google.dev/)

---

## 🔹 PASSO 4 — Criar estrutura de pastas

```mkdir reference-images
mkdir outputs
mkdir -p .claude/skills/banana-image-gen```

Estrutura final deve ficar assim:

```banana-squad/
│
├── .env
├── CLAUDE.md
├── paperbanana.md
├── gemini-3-image-api-guide.md
├── spawn-team-prompt.md
│
├── reference-images/
├── outputs/
│
└── .claude/
    └── skills/
        └── banana-image-gen/
            └── SKILL.md```

---

## 🔹 PASSO 5 — Colocar os arquivos

Copie para dentro do projeto:

* CLAUDE.md
* paperbanana.md
* gemini-3-image-api-guide.md
* spawn-team-prompt.md
* banana-squad.skill (renomeie para `SKILL.md` dentro da pasta skill)

---

## 🔹 PASSO 6 — Ativar Agent Teams no Claude Code

Mac/Linux:

```export CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1```

Ou no `settings.json`:

```{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}```

---

## 🔹 PASSO 7 — Abrir Claude Code dentro da pasta

```claude .```

Agora o sistema está implantado.

---

# 🧠 PARTE 2 — COMO USAR

Você tem duas opções:

---

# ✅ OPÇÃO A — Manual (spawn-team-prompt)

1. Abra `spawn-team-prompt.md`
2. Copie o conteúdo inteiro
3. Cole no Claude Code
4. Ele vai fazer as perguntas obrigatórias
5. Responda
6. Aguarde o pipeline rodar
7. Veja imagens na pasta `outputs/`

---

# ✅ OPÇÃO B — Usando o Skill (recomendado)

Dentro do Claude Code, digite:

```/banana-image-gen```

ou o nome definido no skill.

Ele irá:

1. Fazer perguntas
2. Criar agentes
3. Rodar pipeline
4. Gerar 5 versões
5. Avaliar
6. Mostrar ranking
7. Encerrar agentes automaticamente

---

# 🎯 Exemplo real de uso

Ele vai perguntar:

* O que deseja gerar?
* Qual estilo?
* Qual proporção?
* Resolução?
* Texto?
* Referência?
* Uso final?
* Cores?
* O que evitar?

Você responde algo como:

> Quero um infográfico estilo Visual Capitalist sobre investimento global em IA em 2026, 16:9, 2K, estilo editorial moderno.

Ele faz o resto.

---

# 📦 Resultado

Na pasta:

```outputs/```

Você terá:

```ai-investment-v1-faithful.png
ai-investment-v2-enhanced.png
ai-investment-v3-alt-composition.png
ai-investment-v4-style-variation.png
ai-investment-v5-bold.png```

E o Critic dirá qual é a melhor.

---

# 🔁 Para iterar

Você pode dizer:

> Iterar sobre a v4, melhorar legibilidade do texto.

Ele roda novamente só naquela direção.

---

# 💰 Custo estimado

Cada execução:

* 5 imagens 2K
* * iteração crítica

Pode consumir tokens + custo de imagem.

Sempre usar graceful shutdown para não deixar agentes rodando.

---

# 🧩 RESUMO ULTRA DIRETO

Implantar:

1. Criar pasta
2. Instalar dependências
3. Colocar API key
4. Organizar arquivos
5. Ativar agent teams

Usar:

1. Rodar skill
2. Responder perguntas
3. Aguardar
4. Ver outputs

---

**INEMA** · 2026-02-15

# 🎯 Na prática, o que esse projeto faz?

Ele cria um **sistema automático que gera imagens profissionais (infográficos, diagramas, thumbnails, gráficos) usando uma equipe de agentes que trabalham juntos**, em vez de um único prompt simples.

---

# 🧠 Em termos simples

Você diz:

> “Quero um infográfico nesse estilo sobre investimento em IA em 2026.”

E o sistema:

1. Faz perguntas para entender exatamente o que você quer
2. Analisa imagens de referência
3. Cria 5 versões diferentes
4. Avalia qual ficou melhor
5. Recomenda a melhor
6. Permite iterar automaticamente

Tudo isso sozinho.

---

# 🔄 O que acontece por trás

Em vez de fazer:

```"gere um infográfico sobre IA"```

Ele faz:

### 🧑‍💼 Lead

Organiza tudo e faz perguntas.

### 🔍 Research Agent

Analisa referências e extrai:

* Estilo
* Layout
* Cores
* Tipografia
* Estrutura visual

### ✍️ Prompt Architect

Escreve 5 prompts extremamente detalhados (não lista de palavras).

### 🎨 Generator

Chama a API do Gemini (Nano Banana) e gera 5 imagens.

### 🧠 Critic

Avalia as imagens em:

* Fidelidade
* Clareza
* Limpeza visual
* Estética

Depois ranqueia e escolhe a melhor.

---

# 📦 O que você ganha na prática

Ele serve para gerar automaticamente:

* 📊 Infográficos estilo Visual Capitalist
* 📈 Gráficos estatísticos
* 🧾 Diagramas metodológicos
* 🧠 Diagramas técnicos
* 📺 Thumbnails de YouTube
* 🖼️ Ilustrações profissionais
* 🏢 Material visual corporativo

---

# 🚀 Qual é a grande diferença?

Prompt comum = tentativa única
Esse sistema = processo estruturado com controle de qualidade

Ele transforma geração de imagem em:

> Uma mini agência de design automatizada

---

# 📈 Por que isso importa?

Porque:

* A maioria das IAs gera algo “ok”
* Esse sistema gera algo “publicável”

Ele melhora:

* Estrutura
* Clareza
* Estética
* Precisão

---

**INEMA** · 2026-02-15

Vou organizar do mais conceitual → mais técnico → mais operacional.

---

# 📘 1️⃣ `paperbanana.md`

📄 Fonte: 

## O que é?

É o **paper científico original do Google** que propõe o framework PaperBanana.

## Para que serve?

Ele fornece:

* A arquitetura de 5 agentes
* O conceito de crítica iterativa
* O método de avaliação (4 métricas)
* A lógica de retrieval + planning + styling + critic loop
* Evidências experimentais

## Em resumo:

É a **base teórica** de tudo.

Sem ele, a Banana Squad seria apenas um pipeline de geração comum.
Com ele, vira um sistema estruturado e validado academicamente.

---

# 📂 2️⃣ `CLAUDE (6).md`

📄 Fonte: 

## O que é?

É o **arquivo de contexto do projeto no Claude Code**.

Funciona como o “manual operacional” do sistema.

## O que ele define?

* Como o pipeline funciona
* Regras obrigatórias
* Estrutura de pastas
* Como salvar outputs
* Como usar a API
* Regras do Lead
* Regras de geração
* Como nomear arquivos
* Instalação de dependências
* Modelo padrão (gemini-3-pro-image-preview)

## Em resumo:

É o **manual prático que transforma a teoria do paper em sistema funcional.**

PaperBanana = teoria
CLAUDE.md = execução prática

---

# ⚙️ 3️⃣ `gemini-3-image-api-guide.md`

📄 Fonte: 

## O que é?

É o guia técnico completo da API do Gemini 3 Pro (Nano Banana).

## Ele contém:

* Como autenticar
* Como chamar a API (Python / JS / REST)
* Como gerar imagem
* Como editar imagem
* Multi-imagem
* Multi-turn chat
* Google Search grounding
* Resoluções (1K, 2K, 4K)
* Aspect ratios
* Thinking mode
* Prompting best practices
* Limitações

## Em resumo:

É o **manual técnico da engine de geração**.

Se CLAUDE.md diz “o que fazer”,
o API Guide diz “como fazer”.

---

# 🧠 4️⃣ `spawn-team-prompt.md`

📄 Fonte: 

## O que é?

É o **mega prompt que cria a Banana Squad dentro do Claude Code**.

## O que ele faz?

Quando você cola ele no Claude:

* Cria os agentes
* Define papéis
* Define regras
* Define como eles se comunicam
* Define como o Lead deve agir
* Define perguntas obrigatórias
* Define fluxo de execução

## Em resumo:

É o **arquivo que literalmente dá vida à equipe de agentes**.

Sem ele, não existe Banana Squad.

---

# 🍌 5️⃣ `banana-squad.skill`

(arquivo de skill do Claude Code)

## O que é?

É a versão automatizada do spawn-team.

Transforma o mega prompt em um **comando reutilizável**.

Exemplo:

```/banana-squad```

Em vez de colar o mega prompt toda vez.

## O que ele faz?

* Spawna a equipe automaticamente
* Executa o fluxo
* Garante shutdown correto
* Evita desperdício de tokens

## Em resumo:

É a **versão “produto” do sistema**.
Automatiza o processo.

---

# 🧩 Como todos os arquivos se conectam

```paperbanana.md
        ↓ (teoria)
CLAUDE.md
        ↓ (regras práticas)
gemini-3-image-api-guide.md
        ↓ (implementação técnica)
spawn-team-prompt.md
        ↓ (criação da equipe)
banana-squad.skill
        ↓ (automação final)```

---

# 🏗️ Se fosse comparar com uma empresa

| Arquivo                     | Equivalente                              |
| --------------------------- | ---------------------------------------- |
| paperbanana.md              | O artigo científico que explica o método |
| CLAUDE.md                   | O manual interno da empresa              |
| gemini-3-image-api-guide.md | O manual da máquina de produção          |
| spawn-team-prompt.md        | O contrato que define os funcionários    |
| banana-squad.skill          | O botão “Executar Sistema”               |

---

# 🎯 Em uma frase cada:

* **paperbanana.md** → A teoria científica.
* **CLAUDE.md** → As regras do projeto.
* **gemini-3-image-api-guide.md** → Como usar a API.
* **spawn-team-prompt.md** → Cria os agentes.
* **banana-squad.skill** → Automatiza tudo.

---

**INEMA** · 2026-02-15

Planejamento estruturado
* 🎨 Padronização estética
* 🖼️ Geração multimodal
* 🔁 Loop de crítica iterativa

Resultado:
→ Diagramas acadêmicos com qualidade próxima (e às vezes superior) à humana
→ Processo totalmente automatizável
→ Aplicável a qualquer domínio que exija padrões visuais rígidos

---

**INEMA** · 2026-02-15

# 🍌 1. PaperBanana (O Paper Científico)

📄 Fonte: 

## 🎯 Objetivo

Automatizar a geração de **diagramas metodológicos e gráficos estatísticos acadêmicos** com qualidade de publicação (ex: NeurIPS).

## 🧠 Problema

Modelos de IA conseguem:

* Escrever papers
* Rodar experimentos
* Gerar código

Mas **não conseguem gerar figuras acadêmicas com fidelidade e estética profissional consistente**.

---

## 🏗️ Arquitetura Agentic (5 Agentes)

1. **Retriever** – busca referências relevantes
2. **Planner** – transforma texto em descrição detalhada do diagrama
3. **Stylist** – aplica diretrizes estéticas acadêmicas
4. **Visualizer** – gera imagem (ou código para gráficos)
5. **Critic** – avalia e refina em loop iterativo (3 rodadas)

---

## 🔁 Loop de Refinamento

O Critic:

* Compara com o texto original
* Corrige erros factuais
* Ajusta estética e clareza
* Gera nova descrição

Itera **T = 3 vezes** até chegar ao resultado final.

---

## 📊 Métricas de Avaliação

Avaliado em 4 dimensões:

1. **Faithfulness** (fidelidade ao conteúdo)
2. **Conciseness** (sem poluição visual)
3. **Readability** (clareza estrutural)
4. **Aesthetics** (qualidade visual)

Resultado:
PaperBanana supera baselines em todas as métricas (+17% overall).

---

## 📈 Extensão para Gráficos Estatísticos

Para gráficos:

* Visualizer gera **código Python (Matplotlib)** ao invés de imagem direta
* Critic valida precisão numérica
* Melhor desempenho que geração direta por imagem

Insight importante:

* **Imagem = mais bonita**
* **Código = mais fiel numericamente**
* Melhor solução: híbrido

---

## ⚠️ Limitações

* Saída é raster (não vetorial)
* Pequenos erros de conectividade ainda acontecem
* Trade-off entre padronização estética e diversidade
* Avaliação automática ainda tem desafios

---

# 🧠 2. Banana Squad (Implementação Prática no Claude Code)

📄 Fonte: 

É a versão prática inspirada no PaperBanana.

## 🔄 Pipeline

```Usuário
↓
Perguntas obrigatórias
↓
Research Agent
↓
Prompt Architect
↓
Generator (Gemini 3 Pro)
↓
Critic
↓
5 variações finais```

---

## 📌 Regras Críticas

### 1️⃣ Sempre perguntar antes de gerar

* Tema
* Estilo
* Aspect ratio
* Resolução
* Texto na imagem
* Referência específica
* Cores
* Uso final

---

### 2️⃣ Sempre gerar 5 variações

1. Faithful
2. Enhanced
3. Alternative Composition
4. Style Variation
5. Bold/Creative

Nunca gerar apenas uma.

---

### 3️⃣ Prompts narrativos (não lista de palavras)

Ruim:

```cat, wizard hat, cute, soft light```

Bom:

```A photorealistic portrait of a fluffy ginger cat wearing...```

---

### 4️⃣ Modelo padrão

`gemini-3-pro-image-preview`

* Resolução padrão: `"2K"`
* Aspect ratio padrão: `"16:9"`

---

# 🎨 3. Gemini 3 Pro Image API (Nano Banana Pro)

📄 Fonte: 

## 🔥 Modelos

| Modelo                     | Uso                   |
| -------------------------- | --------------------- |
| gemini-2.5-flash-image     | Rápido                |
| gemini-3-pro-image-preview | Profissional (até 4K) |

---

## ⚙️ Recursos

* Até 14 imagens de referência
* Geração e edição
* Multi-turn chat
* Google Search grounding
* Resolução até 4K
* Aspect ratios variados

---

## 📐 Resoluções

| Tamanho | Pixels aproximados |
| ------- | ------------------ |
| 1K      | ~1024px            |
| 2K      | ~2048px            |
| 4K      | ~4096px            |

⚠️ Deve usar `"2K"` com K maiúsculo.

---

## 🧠 Melhor Prática de Prompt

* Ser específico
* Usar termos fotográficos
* Controlar iluminação
* Descrever textura
* Controlar ângulo de câmera
* Iterar conversacionalmente

---

# 🎨 4. Guia Estético NeurIPS 2025

O Paper extraiu padrões visuais dominantes:

### Diagramas

* Pastéis suaves
* Containers arredondados
* Layout modular
* Serif para variáveis matemáticas
* Sans-serif para labels
* Nada de estilo “PowerPoint default”

### Gráficos

* Fundo branco
* Linhas tracejadas leves
* Paletas Viridis/Magma (sem Rainbow/Jet)
* Marcadores geométricos em line charts
* Heatmaps com células quadradas
* Legendas internas

---

# 🏆 Conclusão Geral

O sistema combina:

* 🔍 Recuperação de referências
* 🧠

---

**INEMA** · 2026-02-15

estruturado de crítica

É possível criar **gráficos e imagens profissionais com um único prompt**, usando uma arquitetura inteligente de agentes.

---

**INEMA** · 2026-02-15

## 🎯 Ideia Principal

Combinar **Claude Code Agent Teams** com **Nano Banana (Gemini 3 Pro API)** usando o framework do paper **“Paper Banana”** para gerar **ilustrações e gráficos profissionais com um único prompt**, sem precisar de Photoshop ou habilidades de design.

A chave é usar um **time de agentes especializados** que trabalham juntos em um ciclo com **crítica e iteração**.

---

# 📘 O que é o “Paper Banana”?

É um paper do Google que propõe tratar geração de imagens como uma **agência de design com especialistas**, em vez de um único modelo tentando fazer tudo.

## 🔎 Problema identificado

Modelos de IA conseguiam:

* Escrever papers
* Rodar experimentos
* Revisar literatura

Mas **não conseguiam gerar diagramas científicos com precisão consistente**.

## 💡 Solução proposta

Criar um **framework agentic com papéis especializados**:

1. **Retriever (Pesquisador)**
   Busca imagens de referência.

2. **Planner (Planejador)**
   Converte conceitos em descrições visuais detalhadas.

3. **Stylist (Estilista)**
   Aplica diretrizes estéticas.

4. **Visualizer (Gerador)**
   Cria a imagem em múltiplas tentativas.

5. **Critic (Crítico)**
   Avalia e gera feedback iterativo.

---

## 🔁 O Segredo: Loop de Crítica

O grande insight do paper:

* Sem crítica → ~45% de precisão
* Com 1 a 3 rodadas de crítica → +10% de melhoria

A crítica melhora:

* Fidelidade
* Clareza
* Estética
* Polimento visual

👉 **Conclusão:** O agente crítico é a arma secreta.

---

# 🍌 Implementação: “Banana Squad”

O autor cria sua própria equipe de agentes dentro do Claude Code.

## 👑 1. Lead (Orquestrador)

* Não executa tarefas
* Faz perguntas de clarificação
* Direciona trabalho aos agentes
* Apresenta resultados ranqueados

---

## 🔬 2. Research Agent

Analisa imagens de referência e extrai:

* Estilo
* Cores
* Composição
* Layout
* Branding
* Estrutura visual

Também lê:

* Guia da API Gemini
* Documentação técnica

---

## 🏗 3. Prompt Architect

Cria **5 prompts narrativos detalhados** (não lista de palavras-chave).

Cada prompt inclui:

* Sujeito
* Ambiente
* Iluminação
* Ângulo de câmera
* Mood
* Texturas
* Cores
* Composição

Objetivo: manter estilo, variar narrativa.

---

## 🎨 4. Generator Agent

* Usa Gemini 3 Pro via Nano Banana API
* Gera 5 imagens
* Salva na pasta “outputs”

---

## 🧠 5. Critic Agent

Avalia em 4 KPIs:

1. **Faithfulness** → Fidelidade ao pedido
2. **Conciseness** → Sem poluição visual
3. **Readability** → Clareza e legibilidade
4. **Beauty** → Qualidade estética profissional

Depois:

* Rankeia de 1 a 5
* Decide se precisa iterar novamente

---

# 🔄 Fluxo de Trabalho

Lead
→ Researcher
→ Prompt Architect
→ Generator
↔ Critic (loop até satisfatório)

---

# 🌍 Exemplos Práticos

O sistema foi usado para:

* Recriar gráficos estilo Visual Capitalist
* Aplicar o mesmo design a novos temas
* Criar infográficos sobre:

  * Consumo global per capita
  * Investimento em IA até 2026
  * Estatísticas futuras (com pesquisa via web)

Tudo com mínima intervenção manual.

---

# 🧩 Estrutura do Projeto

Arquivos incluídos:

* Prompt para spawn da equipe
* Claude.md (contexto do projeto)
* Guia da API Gemini
* Pasta de imagens referência (organizadas por estilo, composição etc.)
* Pasta “outputs” com todas as variações geradas

---

# ⚙️ Automação com Skill / Slash Command

Se for repetir o processo:

* Criar comando tipo: `banana squad`
* Ele:

  * Pergunta requisitos
  * Cria time
  * Executa pipeline
  * Apresenta ranking
  * Faz shutdown automático

⚠️ Importante:
Encerrar agentes após uso para evitar gasto excessivo de tokens.

---

# 🔥 Principais Insights 

✔️ Geração de imagens melhora muito com arquitetura multiagente
✔️ Crítica iterativa é mais importante que fine-tuning
✔️ Mostrar bons exemplos é melhor que treinar do zero
✔️ Estrutura > Prompt isolado
✔️ Sistema pode ser aplicado a:

* Thumbnails
* Diagramas
* Infográficos
* Ilustrações técnicas
* Design automatizado

---

# 🚀 Conclusão

Combinando:

* Framework do Paper Banana
* Claude Code Agent Teams
* Nano Banana (Gemini 3 Pro API)
* Loop

---

**INEMA** · 2026-02-15

**Claude Code Agent Teams** +**Nano Banana**

---

**INEMA** · 2026-02-15

https://chatgpt.com/c/698e349c-19e0-832c-b895-e44deeae9f3f
