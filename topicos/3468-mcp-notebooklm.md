# MCP NotebookLM

> Tópico 3468 · 16 mensagens úteis de 36 totais

---

**INEMA** · 2026-03-01

https://youtu.be/yueY-kS1YtA

---

**INEMA** · 2026-03-01

**1️⃣ O modelo passa a enxergar o NotebookLM como ferramenta

**Pode chamar funções como

list_notebooks
query_notebook
create_notebook
add_source

---

**INEMA** · 2026-03-01

https://github.com/PleasePrompto/notebooklm-skill

---

**INEMA** · 2026-03-01

**Alternative: Claude Code Skill**
**Prefer Claude Code Skills over MCP?** This server is now also available as a native Claude Code Skill with a simpler setup:

[**NotebookLM Claude Code Skill**](https://github.com/PleasePrompto/notebooklm-skill) - Clone to `~/.claude/skills` and start using immediately

**Key differences:**

**MCP Server** (this repo): Persistent sessions, works with Claude Code, Codex, Cursor, and other MCP clients
**Claude Code Skill**: Simpler setup, Python-based, stateless queries, works only with local Claude Code
Both use the same browser automation technology and provide zero-hallucination answers from your NotebookLM notebooks.

---

**INEMA** · 2026-03-01

Se você está perguntando **quais comandos foram usados para configurar o MCP do NotebookLM**, são basicamente estes:

---

## 🔹 1️⃣ No Claude (CLI)

Adicionar o servidor MCP do NotebookLM:

```claude mcp add notebooklm npx notebooklm-mcp@latest```

Depois, dentro do Claude:

```Log me in to NotebookLM```

(Abre o navegador para autenticar na sua conta Google.)

---

## 🔹 2️⃣ No Codex (CLI)

Adicionar o servidor MCP:

```codex mcp add notebooklm -- npx -y notebooklm-mcp@latest```

Depois:

```Log me in to NotebookLM```

Para verificar servidores ativos:

```/mcp```

---

## 🔹 3️⃣ No Anti-Gravity

Não é via terminal direto.
Você adiciona no `mcp_config.json`:

```{
  "mcpServers": {
    "notebooklm": {
      "command": "npx",
      "args": ["-y", "notebooklm-mcp@latest"]
    }
  }
}```

Depois, no chat do agente:

```Log me in to NotebookLM```

---

## 🔹 Comandos que o MCP expõe (internamente)

Depois de conectado, o modelo pode chamar funções como:

* `list_notebooks`
* `query_notebook`
* `create_notebook`
* `add_sources`

Esses não são digitados manualmente — o modelo chama automaticamente.

---

**INEMA** · 2026-03-01

https://docs.cloud.google.com/mcp

---

**INEMA** · 2026-02-28

A forma mais “direta” é: **você roda o servidor MCP do NotebookLM (via `npx`) e cadastra esse servidor no cliente (AntiGravity / Claude / Codex)**. Aqui vai o passo a passo para cada um:

---

## 1) AntiGravity (IDE)

1. **Abra o painel de MCP no AntiGravity**: no painel do agente (lado direito) clique em **“…” → MCP Servers**. 
2. Clique em **Manage MCP Servers** e depois em **Edit configuration / View raw config** para abrir o arquivo `mcp_config.json`. 
3. Dentro de `mcp_config.json`, adicione um servidor assim (exemplo mínimo):

```{
  "mcpServers": {
    "notebooklm": {
      "command": "npx",
      "args": ["-y", "notebooklm-mcp@latest"]
    }
  }
}```

(O AntiGravity usa exatamente esse formato `mcpServers` com `command` e `args`.) 
4) Salve e volte para o chat do agente: você deve ver o servidor disponível. (O guia indica que o painel de conectores lista as tools depois de conectado.) 
5) **Faça o login 1x**: no chat, peça **“Log me in to NotebookLM”** — abre uma janela do Chrome para autenticar. 

---

## 2) Claude (Claude Code / CLI) — o mais simples

1. No terminal, rode:

```claude mcp add notebooklm npx notebooklm-mcp@latest```


2) No Claude, execute o login 1x dizendo: **“Log me in to NotebookLM”** (abre Chrome). 
3) Para conferir se está conectado no app, o suporte do Claude diz que dá pra checar pelo **“+” → Connectors** (mostra os MCPs e ferramentas).

> Se você estiver usando **Claude Desktop**, a instalação hoje é via **Settings → Extensions** (inclui instalar extensões customizadas `.mcpb`). 

---

## 3) Codex (OpenAI Codex CLI)

1. No terminal:

```codex mcp add notebooklm -- npx -y notebooklm-mcp@latest```


2) Alternativa oficial: você também pode gerenciar tudo via `codex mcp …` e/ou editar o `~/.codex/config.toml`. 
3) No Codex, autentique 1x: **“Log me in to NotebookLM”** (abre Chrome). 
4) No TUI do Codex, use **`****/mcp****`** para ver os MCP servers ativos.

---

**INEMA** · 2026-02-28

# 🧠 Conceito Central

O grande insight é:

> A diferença entre imaginar algo e construir algo está ficando cada vez menor.

Notebook LM = conhecimento estruturado
Gemini = raciocínio avançado
Anti-gravity = execução programável

Juntos, formam um sistema de:

* Pesquisa
* Estratégia
* Automação
* Construção de software
* Produção de conteúdo

---

# 🎯 Benefícios Prometidos

* Economizar tempo
* Criar ativos mais rápido
* Construir sistemas personalizados
* Automatizar aprendizado
* Criar apresentações profissionais
* Gerar software sem código

---

**INEMA** · 2026-02-28

## 🔥 Visão Geral

Como os novos recursos do **Notebook LM**, combinados com **Gemini** e a integração com **“anti-gravity”**, desbloqueiam capacidades extremamente avançadas para:

* Criar apresentações
* Gerar conhecimento estruturado
* Automatizar pesquisas
* Construir software
* Usar IA como memória persistente (RAG)
* Criar sistemas personalizados de negócio

---

# 🆕 Atualizações do Notebook LM

### 1️⃣ Exportação para PowerPoint editável

* Agora é possível baixar notebooks como **PowerPoint editável** (em alguns países).
* Caso não esteja disponível, pode-se usar anti-gravity para converter.

### 2️⃣ Edição de estilo dos slides

* Dá para:

  * Escolher estilo (curto, padrão ou longo)
  * Ajustar visual
  * Revisar e pedir alterações (cores, textos, layout)
* Pode-se usar Gemini para analisar um design (via imagem) e gerar um prompt de estilo personalizado.

---

# 🤖 Gemini – O Diferencial

### Principais vantagens:

* Pode conversar com **vários notebooks ao mesmo tempo**
* Raciocina melhor que Notebook LM
* Permite usar **Personal Intelligence**:

  * Gmail
  * Google Drive
  * Calendário
  * Histórico

### Diferença importante:

| Notebook LM                       | Gemini                             |
| --------------------------------- | ---------------------------------- |
| Só usa dados internos do notebook | Usa conhecimento global            |
| Funciona como banco RAG fechado   | Funciona como bibliotecário global |

---

# 🚀 O Papel do Anti-Gravity

Anti-gravity permite:

* Criar notebooks automaticamente
* Extrair dados programaticamente
* Gerar:

  * Áudio overview
  * Vídeo overview
  * Slides
  * Relatórios
  * PDFs
  * Mapas mentais
  * Flashcards
  * Quizzes
  * Tabelas
* Construir software baseado no conteúdo

Além disso:

* Conexão com Notebook LM é feita uma vez (autenticação automática).
* Permite URLs compartilháveis.
* Possui 29+ skills disponíveis.

---

# 💡 5 Casos de Uso “Insanos”

## 1️⃣ Biblioteca Inteligente (Alexandria 2.0)

Criar múltiplos notebooks por tema:

Exemplo:

* CRO (Conversão)
* Marketing
* Retenção
* Estratégia

E depois:

* Consultar esses notebooks automaticamente ao construir apps ou projetos.

Pode servir para:

* Base de conhecimento de empresa
* RH
* Inteligência competitiva
* Estratégia de mercado

---

## 2️⃣ Notebook como Memória Persistente (RAG gratuito)

Usar Notebook LM como:

* Base de memória para projetos
* Armazenamento de bugs, testes e melhorias
* Banco de conhecimento interno

Vantagem:

* Não consome tokens do modelo principal
* Funciona como RAG sem precisar de Pinecone

---

## 3️⃣ “Brain + Hands”

Notebook LM = cérebro (conhecimento estruturado)
Anti-gravity = mãos (execução e software)

Exemplo:

* Empresa e-commerce de $20k/mês
* Anti-gravity puxa dados relevantes
* Cria roadmap de 90 dias personalizado
* Considera:

  * Localização (Dubai)
  * Produto
  * Contexto pessoal
  * Pesquisa extra

---

## 4️⃣ Construção de Software Automática

Com um único prompt, foi criado:

* Página interativa
* Sliders
* Calculadora de receita
* Planejador de orçamento
* Rastreador de metas
* Checklist animado

Tudo baseado no roadmap gerado.

Ou seja:

> Ideia → Notebook → Sistema interativo pronto

---

## 5️⃣ Conversão Automática para Slides

Usando uma skill específica:

* Notebook → Google Slides
* Notebook → PowerPoint
* Notebook → PDF
* Notebook → Web slideshow

Mesmo que o recurso ainda não esteja liberado oficialmente na sua conta.

---

# 🎨 Hack de Design

Processo:

1. Screenshot de um site bonito.
2. Enviar imagem para Gemini.
3. Pedir análise de:

   * Filosofia de marca
   * Cores
   * Tipografia
   * Vibe
4. Usar isso como prompt no Notebook LM.
5. Gerar slides com aquele estilo.

Resultado: apresentações com identidade visual personalizada.

---

# 🔐 Integração com Google Drive

Agora é possível:

* Buscar arquivos no Drive
* Incorporar automaticamente em notebooks
* Usar documentos próprios como fonte

---

---

**INEMA** · 2026-02-28

## 🧠 **Resumo rápido**

| Ferramenta         | Função na integração                                                          |
| ------------------ | ----------------------------------------------------------------------------- |
| **Notebook LM**    | Biblioteca de conhecimento/contexto                                           |
| **Anti-Gravity**   | Execução/automação, construção de artefatos                                   |
| **Claude / Codex** | Agentes que usam o conhecimento de notebooks em respostas e geração de código |
| **MCP / Skills**   | Canal de comunicação que possibilita o acesso entre notebooks e agentes       |

---

**INEMA** · 2026-02-28

Como **integrar o Notebook LM com Anti-Gravity ou com outros modelos/agentes como Claude ou Codex**:

---

## 🧠 **1. O que é necessário para integrar**

A integração entre Notebook LM e outras ferramentas é feita usando um **protocolo de contexto/integração** (como MCP — *Model Context Protocol*), que permite que outros agentes conversem diretamente com os notebooks e extraiam respostas fundamentadas nas suas notas. 
---

## 🔗 **2. Integração com *Anti-Gravity***

### 🧱 Passos principais

1. **Tenha o Anti-Gravity instalado**

   * Crie um workspace/projeto dentro do Anti-Gravity. 

2. **Use MCP para conectar ao Notebook LM**

   * MCP é um protocolo que atua como “controle universal” para permitir que o Anti-Gravity acesse o conhecimento dos notebooks. 

3. **Instalação/configuração MCP**

   * Dentro do Anti-Gravity, cole o código/prompts do servidor MCP para ativar a conexão com o Notebook LM.
   * Ao executar a configuração, o navegador abre para autenticar uma vez com sua conta do Notebook LM.

4. **Resultados da integração**

   * Depois de conectado, o Anti-Gravity pode **consultar vários notebooks em uma mesma consulta**.
   * Você pode pedir a criação de novos notebooks programaticamente e automatizar conteúdos.
   * O Anti-Gravity pode **criar software, dashboards, apresentações e muito mais usando o conhecimento do Notebook LM**.

👉 Resumo: **Anti-Gravity usa Notebook LM como “biblioteca de contexto” e combina isso com seus recursos de execução/automação** — o Notebook LM fornece conhecimento e o Anti-Gravity usa esse conhecimento para gerar artefatos e sistemas. 

---

## 🤖 **3. Integração com Claude ou Codex**

### 📌 Usando servidores MCP ou *skills*

Existem projetos e ferramentas que permitem que Claude ou Codex acessem diretamente os notebooks:

#### ✔️ **MCP Server para Notebook LM**

* Instale um servidor MCP que permita que agentes como Claude, Cursor, Codex, etc., “perguntem” ao Notebook LM diretamente.
* Isso elimina a necessidade de copiar/colar conteúdo manualmente. 

Configuração típica:

```# Exemplo de comando para adicionar NotebookLM ao Claude/Codex via MCP
claude mcp add notebooklm npx notebooklm-mcp@latest
# ou para Codex:
codex mcp add notebooklm -- npx notebooklm-mcp@latest```

(O comando instala o MCP server e registra a integração no agente.) 

#### ✔️ **Claude Code Skill**

* Uma *skill* que permite que Claude Code interaja com o Notebook LM diretamente para respostas com citações.
* Isso é especialmente útil para trazer conhecimento de notebooks para **respostas de código e sínteses específicas**. 
---

## 🔄 **4. Como funciona a integração na prática**

### 📌 Fluxo típico

1. Você **cria e preenche um notebook no Notebook LM** com documentos, links, vídeos, PDFs etc.
2. Você **conecta o Notebook LM ao Anti-Gravity ou a um agente como Claude/Codex** via MCP ou Skill.
3. O agente pode **consultar o conhecimento do notebook e responder com contexto real**, produzir código, relatórios ou gerar artefatos. 

---

## 🧩 **5. Porque essa integração é útil**

✔️ **Contexto profundo e fundamentado**

* O Notebook LM já pré-processa documentos e gera respostas coerentes, o que melhora a qualidade do que o Anti-Gravity ou outros agentes usam. 

✔️ **Redução de custo/token**

* Em vez de carregar grandes arquivos internamente no agente, a integração permite que o Notebook LM sirva como um **repositório de conhecimento otimizado**. 

✔️ **Automação avançada**

* Isso permite que você crie **software, apresentações, conteúdo, tarefas automatizadas e dashboards** com base no conhecimento dos notebooks.
---

---

**INEMA** · 2026-02-28

O **MCP do NotebookLM** (Model Context Protocol) é basicamente um **servidor intermediário** que permite que outras IAs (como Claude, Codex ou ferramentas como Anti-Gravity) acessem seus notebooks de forma estruturada e automática.

### 🔎 O que ele é na prática

Ele funciona como uma **ponte** entre:

* 📚 NotebookLM (sua base de conhecimento)
* 🤖 Um agente externo (Claude, Codex, etc.)

Em vez de copiar e colar conteúdo, o agente faz chamadas ao servidor MCP, que:

1. Autentica na sua conta Google
2. Lista seus notebooks
3. Consulta conteúdos
4. Retorna respostas fundamentadas nos documentos

---

## 🧱 Como ele funciona tecnicamente

O MCP:

* Roda como um **servidor local (Node.js / npx)**
* Usa sua sessão Google para acessar o NotebookLM
* Expõe “ferramentas” como:

  * `list_notebooks`
  * `query_notebook`
  * `create_notebook`
  * `add_sources`
* O modelo (Claude, por exemplo) chama essas ferramentas automaticamente

Ou seja:

Modelo → chama ferramenta MCP → MCP consulta NotebookLM → devolve resposta → Modelo usa isso no raciocínio.

---

## ⚙️ Como instalar (exemplo com Claude)

Normalmente algo como:

```claude mcp add notebooklm npx notebooklm-mcp@latest```

Ou com Codex:

```codex mcp add notebooklm -- npx notebooklm-mcp@latest```

Depois:

* Abre navegador
* Você faz login no Google
* Autenticação fica salva
* Pronto para usar

---

## 🧠 O que isso permite

Com MCP ativo você pode dizer:

> “Consulte meu notebook sobre CRO e gere um plano técnico em código.”

E o Claude:

* Busca no NotebookLM
* Puxa os dados estruturados
* Usa isso para gerar resposta, estratégia ou código

---

## 📌 Conceito simplificado

NotebookLM = banco RAG
MCP = API informal que expõe esse banco
Claude/Codex = cérebro que usa o banco

---

**INEMA** · 2026-02-28

https://github.com/PleasePrompto/notebooklm-mcp

---

**INEMA** · 2026-02-28

https://github.com/khengyun/notebooklm-mcp/blob/main/docs/quick-setup-guide.md

---

**INEMA** · 2026-02-28

MCP NotebookLM

---

**INEMA** · 2026-02-28

https://chatgpt.com/c/69a3762c-7e10-8331-b6d6-56cc2b18d45f
