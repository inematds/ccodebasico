# Comando Basicos

> Tópico 1051 · 41 mensagens úteis de 78 totais

---

**INEMA** · 2026-04-25

/model opusplan

---

**INEMA** · 2026-04-18

https://github.com/Luispitik/cognito

---

**INEMA** · 2026-04-07

usar os comandos acima ao usar o claude code

---

**INEMA** · 2026-04-07

export ANTHROPIC_BASE_URL=http://localhost:11434
export ANTHROPIC_AUTH_TOKEN=ollama
export ANTHROPIC_MODEL=qwen3.5
claude

---

**INEMA** · 2026-04-07

Claude Code 99% Free
https://t.me/c/3012468959/4594

---

**INEMA** · 2026-04-05

Claude Code - Permissões
https://t.me/c/3012468959/4678

---

**INEMA** · 2026-04-03

@"claude-code-guide (agent)" qual diferenca entre agentes e subagentes 

use o  @claude-code-guide

---

**INEMA** · 2026-04-03

**/insights** gera um relatório dos últimos 30 dias de uso, em forma de página HTML, mostrando pontos fortes, gargalos, padrões de trabalho e oportunidades de melhoria. Esse relatório analisa sessões, tipos de tarefa, ferramentas mais usadas, linguagens, erros recorrentes e recursos que valeria testar. Também sugere ações práticas, como hooks, regras e automações adaptadas ao jeito da pessoa usar o Claude Code.

---

**INEMA** · 2026-04-03

O /powerup funciona como um guia rápido de aprendizado, ensinando os fundamentos mais importantes, como conversar com a base de código, usar modos diferentes, automatizar fluxos e entender skills e agentes. A ideia é levar a pessoa de iniciante até um nível bem sólido de uso.

---

**Jefferson** · 2026-04-01

/status

---

**INEMA** · 2026-03-31

permite rodar no claude mais de 1 llms

---

**INEMA** · 2026-03-31

https://github.com/musistudio/claude-code-router

---

**INEMA** · 2026-03-31

https://github.com/anthropics/claude-plugins-official

---

**INEMA** · 2026-03-23

Recursos novos ou recentemente fortalecidos no Claude Code:

* **subagentes mais poderosos**, com mais controle e uso mais amplo
* **memória persistente para subagentes**
* **hooks por subagente**, em vez de regras globais para todos
* **auto memory**, para o Claude acumular aprendizados entre sessões
* **/btw**, para conversas paralelas rápidas sem poluir o contexto principal
* **/loop**, para repetir prompts periodicamente
* **/voice**, para usar voz nativamente
* **ajuste de nível de effort**, controlando quanto raciocínio/tokens o modelo usa
* **scheduled tasks e cron jobs**, para automações e tarefas recorrentes

Então, além de **1M de contexto**, **agent teams**, **git worktrees**, **/simplify**, **/batch** e **remote control**, ele também falou desses recursos mais “menores”, mas bem úteis no dia a dia.

---

**INEMA** · 2026-03-21

1. **`**[**/by**](tg://bot_command?command=by)**-the-way`**
2. **`**[**/fork**](tg://bot_command?command=fork)**`**
3. **`context fork` em arquivos `skill.md`**

---

**INEMA** · 2026-03-19

Dispacht - Novo Recuros do Cowork
https://t.me/c/3012468959/3996

---

**INEMA** · 2026-03-11

💎Claude Hack:
Use /btw para fazer uma pergunta rápida sem interromper o trabalho que Claude está fazendo.

---

**INEMA** · 2026-03-07

/loop - Novo Comando do CC2
https://t.me/c/3012468959/3614

---

**INEMA** · 2026-02-28

WAT Framework
https://t.me/c/3012468959/3442

---

**INEMA** · 2026-02-21

⎿  Tip: Working with HTML/CSS? Add the frontend-design plugin:
     /plugin marketplace add anthropics/claude-code                                                                                                                                
     /plugin install frontend-design@claude-code-plugins

---

**Carlos** · 2026-02-16

/init

---

**INEMA** · 2026-02-08

Basico de usar o Claude Code
https://t.me/c/3012468959/2934

---

**INEMA** · 2026-02-07

**claude --model "opus[1m]"**

---

**INEMA** · 2026-01-22

ap91 - Domine **95% do Claude Code 30min
****https://t.me/c/3012468959/2729**

---

**INEMA** · 2026-01-18

https://mcpmarket.com/tools/skills

---

**INEMA** · 2026-01-18

https://mcpmarket.com/server

---

**INEMA** · 2026-01-16

**1. Usando o comando ****/context**** (principal)**Digite no Cloud Code:
`
/contex
`
Você verá a lista de:

MCP servers
skills
plugins
**
🔹 Como interpretar**:
**Cinza (grayed out)** → ❌ **NÃO carregado** (dormente, lazy loading ativo)
**Branco / ativo** → ✅ **Carregado no contexto** (consumindo tokens)

Se a maioria dos MCP servers aparecer **acinzentada**, o lazy loading está funcionando.

---

**INEMA** · 2026-01-16

Se o lazy loading não ativar automaticamente:

Defina a variável **enable tool search = true** ao iniciar o Cloud Code para garantir o uso da versão atualizada.

---

**INEMA** · 2026-01-16

Crie QQ App com CCode N8N
https://t.me/c/3012468959/2477

---

**INEMA** · 2026-01-08

**Código Oculto Claude Comando Dourado que você talvez ainda não saiba (ainda)

AskUserQuestionTool
**
Alguém ficou impressionado quando mostrei esse truque que achei conhecimento comum
O Claude Code às vezes oferece opções de múltipla escolha quando seu prompt é vago → mas normalmente só no início de sessões novas
Quando você está no meio da conversa, ele para de reagir e simplesmente segue o que você der
Aqui está o truque: adicione "AskUserQuestionTool" a qualquer prompt e ele força Claude a gerar opções em vez de adivinhar
Esse é exatamente o comando que Claude Code usa internamente quando decide que precisa de esclarecimento
Testei com um pedido simples de piada
→ disse "me diga outro" com o comando
→ instantaneamente ganhou opções para piadas de programação, piadas de pai, frases curtas
Você pode ir mais fundo com opções aninhadas em cada etapa
Isso é perfeito se você for menos técnico e não souber quais caminhos são possíveis de escolher
Em vez de Claude adivinhar errado e você corrigir o curso
→ você recebe um menu de instruções antes de começar a se formar
Funciona no terminal ou em qualquer outro lugar onde você esteja rodando o Claude Code
Adicione isso ao seu arsenal quando quiser que Claude pense antes de agir

---

**INEMA** · 2026-01-06

UDPC - Prompt Avancado de Depuracao Claude
https://t.me/c/3012468959/2404

---

**Carlos** · 2025-12-28

# Resumo: CLAUDE_CODE_MAX_OUTPUT_TOKENS

## Windows vs Linux

**O limite depende apenas do modelo Claude usado.
**
Windows:
**```set CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000
```**
Linux:
**```export CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000
```
## Limites: 32000 vs 64000

O valor máximo permitido depende do** modelo Claude:**

| Modelo | Limite Máximo |
|--------|---------------|
| Claude Sonnet 4 | 64.000 tokens |
| Claude Opus | 32.000 tokens |
| Claude Haiku | 8.192 tokens |

## Temporário vs Permanente

### Temporário (perdido ao fechar terminal ou reiniciar)
**
Windows CMD:
**```set CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000
```**
Windows PowerShell:
**```$env:CLAUDE_CODE_MAX_OUTPUT_TOKENS = "64000"
```**
Linux:
**```export CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000
```
### Permanente (sobrevive a reinicializações)
**
Windows:
**```setx CLAUDE_CODE_MAX_OUTPUT_TOKENS "64000"
```*Requer abrir nova janela de terminal para ter efeito*
**
Linux:
**Adicionar no arquivo` ~/.bashrc `ou` ~/.zshrc:````export CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000
```
---

## Observações Importantes

- A configuração permanente no Windows com` setx `só terá efeito em novas janelas de terminal abertas após o comando
- O limite máximo depende do modelo Claude configurado no Claude Code
- Se tentar usar um valor acima do limite do modelo, receberá um erro de validação
- Esta variável controla o limite de tokens de** saída **(resposta), não de entrada (prompt)

---

**INEMA** · 2025-12-28

Linux

export CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000
claude --dangerously-skip-permissions

---

**INEMA** · 2025-12-28

Windows (PS)

$env:CLAUDE_CODE_MAX_OUTPUT_TOKENS = "16000"

claude



Windows(cmd)

set CLAUDE_CODE_MAX_OUTPUT_TOKENS=16000

claude

---

**INEMA** · 2025-12-28

Linux

export CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000
claude

---

**INEMA** · 2025-09-16

Aqui está a lista dos arquivos , organizados por função:

### Arquivos de configuração

* **claw\.md** → arquivo principal de regras globais (system prompt do projeto).
* **settings.local.json** → define permissões, hooks e configurações locais dentro da pasta `.claw/`.

### Arquivos de comandos (slash commands)

* **primer.md** → instruções para preparar o contexto (ler código, claw\.md, readme).
* **fixGithubIssue.md** → fluxo para pegar issue no GitHub, corrigir e abrir PR.
* **prep-parallel.md** → prepara execução paralela criando branches/worktrees.
* **execute-parallel.md** → roda as instâncias paralelas seguindo um plano.
* **plan.md** → documento onde você descreve a feature que quer implementar.

### Arquivos do framework PRP

* **initial.md** → descrição inicial da feature ou agente a ser criado.
* **PRP.md** (gerado) → Product Requirement Prompt, com todo o contexto detalhado.
* **results.md** (gerado) → resumo dos resultados das execuções paralelas.

### Arquivos de agentes (sub-agents)

* **validation-gates.md** → sub-agente especializado em rodar testes e validar código.
* **outros agentes em `.claw/agents/`** → cada um em seu próprio `.md` com sistema e descrição.

### Arquivos de hooks

* **hooks.json** → define quais ganchos (ações automáticas) serão rodados em certos momentos.
* **log-tool-usage.sh** → script bash que registra logs cada vez que o Claude edita algo.

### Dev Containers

* **Dockerfile / devcontainer.json** (no template do Anthropic) → definem o container isolado para rodar Claude Code em YOLO mode.

### Arquivos comuns do repositório

* **README.md** → guia/documentação do projeto, usado como referência pelo Claude.

---

**INEMA** · 2025-09-16

Aqui está a explicação simples de cada comando :

### Comandos do Claude Code

* **claude** → abre uma sessão do Claude Code no terminal.
* **cloud** → comando principal (CLI) para rodar todas as funções do Claude Code.
* **/init** → cria e configura os arquivos básicos do projeto, incluindo o `claw.md`.
* **/clear** → limpa a conversa atual e inicia o contexto do zero.
* **/agents** → guia você para criar um sub-agente (um arquivo de agente).
* **dangerously skip permissions** → executa ações sem pedir permissão (só seguro em ambiente isolado).
* **permissions** → menu interno para configurar lista de comandos permitidos ou bloqueados.

### Slash commands (exemplos)

* **/primer** → “aquece” o contexto: faz Claude mapear e entender o código e arquivos antes de trabalhar.
* **/generate**** PRP** → gera o Product Requirement Prompt (documento longo com instruções detalhadas).
* **/execute**** PRP** → executa o PRP para gerar código ou implementar a feature.
* **/fixGithubIssue** → lê um número de issue no GitHub, corrige o problema, testa e abre um PR automaticamente.
* **/prep****-parallel** → prepara múltiplas instâncias/branches para rodar agentes em paralelo.
* **/execute****-parallel** → executa as várias instâncias do Claude Code em paralelo com base num plano.
* **/analyze**** performance \$arguments** → comando parametrizado que recebe argumentos para análise (ex.: nome de função).

### MCP (gerenciamento)

* **claude mcp list** → lista os MCP servers conectados (como Serena, Archon).
* **cloud mcp remove serena** → remove um MCP server (no caso, Serena).

### Comandos de terminal usados pelo Claude

* **tree** → mostra a estrutura de pastas e arquivos do projeto.
* **ls** → lista arquivos do diretório atual.
* **cd** → muda de pasta no terminal.
* **mkdir** → cria uma nova pasta.
* **grep** → procura por palavras/frases em arquivos.
* **python** → executa código Python.
* **rm** → apaga arquivos (recomendado sempre pedir confirmação manual).

### Git e Worktrees

* **git worktree add** → cria uma cópia isolada do repositório em outro diretório.
* **git worktree list** → mostra todas as cópias (worktrees) existentes.
* **git checkout main** → volta para a branch principal do Git.
* **git merge** → junta alterações de uma branch no código principal.

### GitHub CLI

* **gh auth login** → autentica no GitHub pelo terminal.
* **gh repo list** → lista seus repositórios do GitHub.
* **gh issue view** → mostra detalhes de uma issue do GitHub.

### Dev Containers / VS Code

* **Reopen in Container** → comando do VS Code para abrir o projeto em um Dev Container (ambiente isolado com Docker).

---

**INEMA** · 2025-09-16

● Para obter ajuda com o Claude Code, você pode usar os seguintes recursos:

  - /help: Comando para obter ajuda dentro do Claude Code
  - Reportar problemas: Se encontrar bugs ou tiver feedback, reporte em
  https://github.com/anthropics/claude-code/issues

  Se tiver dúvidas específicas sobre como usar alguma funcionalidade do Claude Code, posso ajudar consultando a
  documentação oficial.

> /help

 Claude Code v1.0.113

 Always review Claude's responses, especially when running code. Claude has read access to files in the current
 directory and can run commands and edit files with your permission.

 Usage Modes:
 • REPL: claude (interactive session)
 • Non-interactive: claude -p "question"

 Run claude -h for all command line options

 Common Tasks:
 • Ask questions about your codebase > How does foo.py work?
 • Edit files > Update bar.ts to...
 • Fix errors > cargo build
 • Run commands > /help
 • Run bash commands > !ls

 Interactive Mode Commands:
  /add-dir - Add a new working directory
  /agents - Manage agent configurations
  /bashes - List and manage background tasks
  /clear - Clear conversation history and free up context
  /compact - Clear conversation history but keep a summary in context. Optional: /compact [instructions for
  summarization]
  /config - Open config panel
  /context - Visualize current context usage as a colored grid
  /cost - Show the total cost and duration of the current session
  /doctor - Diagnose and verify your Claude Code installation and settings
  /exit - Exit the REPL
  /export - Export the current conversation to a file or clipboard
  /feedback - Submit feedback about Claude Code
  /help - Show help and available commands
  /hooks - Manage hook configurations for tool events
  /ide - Manage IDE integrations and show status
  /init - Initialize a new CLAUDE.md file with codebase documentation
  /install-github-app - Set up Claude GitHub Actions for a repository
  /login - Sign in with your Anthropic account
  /logout - Sign out from your Anthropic account
  /mcp - Manage MCP servers
  /memory - Edit Claude memory files
  /migrate-installer - Migrate from global npm installation to local installation
  /model - Set the AI model for Claude Code
  /output-style - Set the output style directly or from a selection menu
  /output-style:new - Create a custom output style
  /permissions - Manage allow & deny tool permission rules
  /pr-comments - Get comments from a GitHub pull request
  /privacy-settings - View and update your privacy settings
  /release-notes - View release notes
  /resume - Resume a conversation
  /review - Review a pull request
  /security-review - Complete a security review of the pending changes on the current branch
  /status - Show Claude Code status including version, model, account, API connectivity, and tool statuses
  /statusline - Set up Claude Code's status line UI
  /terminal-setup - Install Shift+Enter key binding for newlines
  /todos - List current todo items
  /upgrade - Upgrade to Max for higher rate limits and more Opus
  /vim - Toggle between Vim and Normal editing modes

---

**INEMA** · 2025-09-16

**comandos exatos de instalação e configuração** são:

* Verificação do Node.js:

  ```  node -v
  npm -v
  ```

* Instalação global via npm:

   ``` npm install -g @anthropic-ai/claude-code
  
```
* Iniciar no diretório do projeto:

    ```cd nome-do-seu-projeto
  claude
  

```* Login manual dentro da sessão (se necessário):

    /`login
  

*` Verificação da instalação (comando de diagnóstico):

    cl`aude doctor
  

* `Atualização da instalação:

    cla`ude update`

---

**INEMA** · 2025-09-16

Aqui está a lista simples,  com cada comando seguido da explicação:

---

### Comandos Claude Code e do Terminal

`claude`
Inicia o Claude Code no terminal.

`cloud`
Executa o Cloud CLI, base para todos os subcomandos.

`cloud init`
Inicializa um novo projeto Claude Code, criando a estrutura de pastas e arquivos.

`cloud plan`
Entra em modo de planejamento, onde Claude pesquisa e organiza ideias antes de escrever código.

`cloud chat`
Abre um chat com o Claude diretamente no terminal.

`cloud login`
Faz login na conta Claude para autenticar o uso.

`cc`
Alias personalizado para rodar `cloud` em modo de permissão total.

`cloud run dangerously` ou `dangerously skip permissions`
Executa tudo sem pedir confirmação. É arriscado, recomendado apenas para quem sabe o que está fazendo.

`cloud --model opus`
Força o uso manual do modelo Opus em vez do padrão.

`@caminho-do-arquivo`
Inclui diretamente um arquivo no contexto do Claude usando o símbolo `@`.

---

### Slash Commands (comandos internos do Claude)

`/issues`
Cria issues a partir de uma ideia ou tarefa.

`/plan`
Inicia um plano de ação detalhado.

`/review`
Revisa código ou conteúdo (muito usado em pull requests).

`/research`
Pede pesquisa de melhores práticas antes de começar a programar.

`/proofread`
Analisa e corrige estilo de textos e cópias.

`/fix_critical`
Faz revisões em pontos críticos, com foco em segurança.

`/best_practices`
Confere se o código segue boas práticas do framework usado.

`/pr_comments`
Coleta e organiza comentários de um pull request para análise.

---

### Palavras-chave de gatilho em prompts

`think ultra hard`
Pede ao Claude um raciocínio mais profundo e detalhado.

`create to-dos`
Transforma uma solicitação em lista de tarefas.

`think deeply` ou `think hard`
Alternativas para pedir um raciocínio mais estruturado.

`yolo`
Ativa execução sem confirmações, equivalente ao modo perigoso.

---

### Comandos Git + Worktree

`git worktree add`
Cria uma nova pasta com outra branch paralela do projeto.

`wt`
Alias usado para simplificar a criação de worktree com o nome do recurso.

`get worktrees`
Lista todas as worktrees existentes.

`git checkout`
Troca para a branch desejada.

`git commit`
Confirma as alterações feitas nos arquivos.

`git push`
Envia as alterações confirmadas para o repositório remoto.

`create pull request`
Cria uma pull request, seja via Claude ou GitHub CLI.

---

### Outros comandos e práticas citadas

`slash command folder: cloud/commands`
Indica a pasta onde ficam os comandos `.md` personalizados.

`use starter projects`
Sugestão de usar projetos base prontos, como Jumpstart Pro, para começar mais rápido.

`reference blog posts`
Claude pode usar links de blogs ou artigos como referência de contexto.

`context7 (MCP)`
Fonte de contexto curado para pesquisas mais precisas dentro do Claude.

---

---

**INEMA** · 2025-09-16

https://chatgpt.com/c/68c9c2d6-8168-8333-be34-928eb22b07cd
