# Build Anything with Claude Code

> Tópico 305 · 13 mensagens úteis de 30 totais

---

**INEMA** · 2025-08-23

https://www.youtube.com/watch?v=hq8J-nj_Sr0

---

**INEMA** · 2025-08-23

## Melhores Mensagens 

### 1. Sobre os 4 Pilares (mentalidade certa)

* “Esses quatro pilares são a diferença entre alguém que falha e produz lixo com Claude Code e alguém que constrói 5x, 10x, 20x mais rápido.”
* “Se você não tem clareza no que quer construir, o Claude não vai adivinhar por você.”

### 2. Sobre Contexto e Preparação

* “O mais importante que você pode ter é um arquivo principal em markdown que centralize o projeto. É a memória do time e do agente.”
* “Não comece já escrevendo código. Planeje primeiro — o tempo gasto no início acelera tudo depois.”
* “Escreva no cloud.md o que nunca deve ser feito, como ‘nunca rodar npm run build’. Isso evita erros caros.”

### 3. Sobre Prompt Engineering

* “Termine seus prompts com ‘think hard, answer in short’. Isso muda o nível de raciocínio do agente.”
* “Quanto mais específico o seu comando, mais próximo de um engenheiro sênior será a resposta.”
* “Use hooks para não repetir prompts. Dois segundos economizados aqui, vinte segundos ali, em meses viram horas de vantagem.”

### 4. Sobre Debug e Aprendizado

* “O segredo não é resolver tudo de uma vez, mas isolar o problema passo a passo como um sênior faria.”
* “Não peça para consertar tudo. Peça para adicionar logs nos pontos críticos e ver o que quebra.”
* “Se você não entender a lógica do bug, você nunca vai avançar — AI não substitui lógica.”

### 5. Sobre Pesquisa e Atualização

* “Claude tem corte de conhecimento. Sempre use web search para confirmar bibliotecas e SDKs recentes.”
* “Nunca confie só na resposta do modelo. Documente a correção e grave no projeto para não errar de novo.”

### 6. Sobre Mentalidade de Dev 10x

* “O verdadeiro segredo não é só o setup do Claude, é você melhorar junto dele. A cada bug, você aprende.”
* “AI vai tornar pessoas inteligentes ainda mais inteligentes, e pessoas preguiçosas ainda mais burras.”
* “Não terceirize seu pensamento para a IA. Você é o dono do produto, não o Claude.”
* “O que te torna 10x dev é compor: sua skill + o setup + clareza + prompts certos. Isso se acumula todo dia.”

### 7. Sobre Trabalho em Equipe / Produtividade

* “Quando alguém do time encontra um prompt poderoso, transforma em hook e compartilha. É assim que pequenos times vencem grandes empresas.”
* “Um time AI-first pode competir de igual pra igual com qualquer gigante, porque trabalha mais rápido e aprende em conjunto.”

---

Resumindo: as **melhores mensagens** giram em torno de três eixos —

1. **Clareza e documentação como base**
2. **Prompts inteligentes e hooks como vantagem prática**
3. **Mentalidade de aprendizado e disciplina como diferencial humano**

---

**INEMA** · 2025-08-23

**todos os prompts exatos** (ou estruturas de prompt) que o David citou ou demonstrou durante o vídeo. Aqui está a lista organizada por contexto/pilar:

---

## Prompts de Setup e Definição de Projeto

1. **“read project description”**
   – Usado em plan mode para o Claude ler o arquivo markdown do projeto.

2. **“help me think through what the ideal tech stack should be”**
   – Feito logo após criar o `project_description.md`.

3. **“looks good. Document this tech stack decision in the core MD file”**
   – Prompt para registrar decisões no markdown.

---

## Prompts de Planejamento (Plan Mode / Opus)

4. **“Help me design the ideal codebase structure for this project. Again, it should be a quick and dirty prototype, aka a simple MVP. Take a deep breath and make sure to ultra think about this like a world-class engineer would.”**

5. **“looks good, however make it even simpler”**
   – Refinando a estrutura proposta.

6. **“Keep it simple”** (via hook `-d`).

---

## Prompts de Documentação / Context Engineering

7. **“Above are the official Anthropic docs. Are we following these docs properly or are we using the Vercel AI SDK?”**

8. **“Your task is to deeply investigate our code, figure out whether we are following the docs properly. Answer in short – dash u”**
   – Verificação crítica com ultra think.

9. **“Wrap the tech stack inside XML tags”**
   – Usado para estruturar contexto no arquivo markdown.

---

## Prompts de Debug / Erros

10. **“Do not do anything else. Just fix this.”**
    – Para corrigir settings.json.

11. **“Explain this error”** (ou “explain what is going on”) → atalho com `-e`.

12. **“Take a deep breath and investigate why we are not making the API chat request. What is the next small step we should take to get closer to solving this?”**

13. **“Add three or four concise debug log statements with colorful emojis at the start”**

14. **“When I send a prompt, the AI does not respond. Investigate why this is happening and suggest debug points.”**

15. **“Investigate why the text isn’t being displayed in the message bubbles properly and think hard about how a senior developer would fix it. The fewer lines of code the better.”**

---

## Prompts de Pesquisa e Validação

16. **“Be detailed and thorough, tell me everything I need to know about getting AI chat completions with the Anthropic API.”**

17. **“Give me the latest documentation for \[package/library] and how to integrate into a full-stack AI web app in JS/TS.”**

18. **“Are we following the official documentation or not? Are there any serious issues or is it basically correct? We should not overthink this.”**

19. **“What is the official API name of Claude for set in the Anthropic API when using it via Vercel AI SDK?”**

20. **“Tell me everything I need to know about V5 of the Vercel AI SDK. List the main differences.”**

---

## Prompts de Organização / Workflow

21. **“Create a new ****/docs**** folder and start by creating one file named ****vercel-sdk.md****. Put important documentation here.”**

22. **“Create a new ****cloud.md**** file in the root folder.”**
    – System prompt global.

23. **“Never ever run npm run build unless the user asks you.”**
    – Instrução fixa no `cloud.md`.

24. **“Your task is to help me connect our project locally to a new GitHub repo. Tell me step by step how to do this.”**

25. **“Create a new sub-agent specialized in web research that always checks 10+ sources.”**

---

## Prompts Filosóficos / Estratégicos

26. **“What is part of the scope? What is a V1 feature? What is a V2 feature?”**
    – Usado como reflexão dentro de deep research.

27. **“Essential CRM features — give me a detailed spec.”**

---

Ou seja, ele não só mostrou prompts exatos, mas também padrões recorrentes: **“Think hard”, “Ultra think”, “Answer in short”, “Take a deep breath”, “Do not do anything else”**.

---

---

**INEMA** · 2025-08-23

## Hacks de Setup e Configuração

* **`claude update`** → rodar toda manhã no terminal para garantir a última versão.
* **`command + escape`** → abrir Claude Code instantâneo.
* **`shift + tab`** → alternar rapidamente entre modos (default, auto accept, plan).
* **`****/model****`** → define modelo automático: Opus no plan mode, Sonnet no auto accept.
* **`****/status**** line`** → personalizar status (modelo usado, branch, tempo, gastos).
* Criar **`cloud.md`** no root → funciona como system prompt global do projeto.
* Criar **nested ****cloud.md** em pastas específicas (ex.: API, components) para controlar comportamento por contexto.

---

## Hacks de Hooks (atalhos personalizados)

* **`-d`** → adiciona “think hard, answer short, keep it simple”.
* **`-u`** → ultra think, máximo de raciocínio.
* **`-e`** → explicar traços de erro (error traces).
* **`----` + `-e`** → explicar logs complexos de erro.
* **Prompt “Never run npm run build unless I say so”** no `cloud.md` → evita bugs sérios.

---

## Hacks de Contexto e Prompting

* **`****/clear****`** → reseta histórico (quando muda de assunto/projeto).
* **`****/compact****`** → resume histórico mantendo contexto relevante (evita context rot).
* **Autocompact automático** → Claude Code faz quando atinge limite de tokens.
* **Tagging de arquivos** (ex.: `read project_description.md`) → IA sempre entende o escopo.
* **XML tags** para tech stack, features, docs → melhora interpretação da IA.
* **Documentar versões** (ex.: V4 vs V5 SDK) no `project_description.md` → evita repetir erros.

---

## Hacks de Depuração

* **Debug logs com emojis** → facilita encontrar pontos críticos no console.
* **Usar `console.log` estratégicos** em 3–4 pontos chave → isola bugs sem tentar corrigir de uma vez.
* **Playwright MCP** → IA interage sozinha com o front-end (testa botões, inputs, UI).
* **Usar múltiplos Claude Codes em paralelo** → um debugando front-end, outro arrumando UI, outro pesquisando docs.
* **Trocar de modelo (Gemini, GPT, Claude)** em bugs difíceis → “nova perspectiva” resolve mais rápido.
* **Sempre testar com `****/compact****` antes de abrir nova instância** (se ainda for mesmo tema).
* **Usar `npm list`** + perplexity para verificar versões corretas de pacotes.

---

## Hacks de Produtividade

* **Transformar prompts repetidos em hooks ou comandos** (economia de tempo que acumula).
* **Criar comandos customizados** (ex.: `/file review`, `/create PR`, `/push to GitHub`).
* **Sub-agents especializados** (ex.: Web Research Validator) → delegar pesquisas sem poluir agente principal.
* **Usar Perplexity integrado** para sempre ter documentação mais recente (resolver problema do knowledge cutoff).
* **Anotar tudo em markdown** (`docs/`) → cada pesquisa relevante vira arquivo taggeável.
* **Diferenciar features de V1 e V2** → evita over-engineering em MVP.
* **Pergunta-chave**: “Are there any serious issues or is it basically correct?” → filtra problemas reais dos triviais.

---

Resumindo: os hacks são uma mistura de **atalhos técnicos (hooks, comandos, compact)** + **gestão de contexto (arquivos markdown, XML tags)** + **estratégia de desenvolvimento (debug passo a passo, documentar tudo, não vibe coding)**.

---

---

**INEMA** · 2025-08-23

**todos os prompts citados no vídeo** e em qual **pilar** eles se encaixam, porque no conteúdo o David vai jogando vários comandos e atalhos práticos.

---

## Pilar 1 – Setup (hooks, comandos, sub-agents)

**Prompts e comandos usados:**

* `claude update` → atualizar para a última versão.
* `command + escape` → abrir Claude Code rápido.
* `/model opus plan mode` → usar Opus só no modo de planejamento.
* `/status line` → mostrar modelo, branch, gasto, etc.
* Hooks criados:

  * `-d` → “think hard, answer short, keep it simple”
  * `-u` → “ultra think, use máximo de raciocínio”
  * `-e` → “explain error traces”
* `close others` → fechar sessões antigas.
* Criar **cloud.md** → arquivo central de sistema (regras do projeto).

---

## Pilar 2 – Clareza da Ideia

**Prompts usados:**

* “read project\_description.md” → sempre referenciar o arquivo central.
* “Document this tech stack decision in core.md”
* “Help me design the ideal codebase structure. Quick MVP, ultra think, worldclass engineer.”
* “Looks good, make it even simpler -d”
* “Take a deep breath and ultra think like a worldclass engineer would.”
* “Are there any serious issues? Think hard, answer short.”

---

## Pilar 3 – Skill (desenvolvimento técnico)

**Prompts usados:**

* “Fix this settings.json error. Do not do anything else.”
* “Investigate the codebase and think step by step like a senior developer.”
* “Run npm list (safe) and explain what this means.”
* “Add 3 debug log statements with emojis to see exactly where it breaks.”
* “What is the next step to test this app? Simple and safe.”
* “Revert the changes after npm run build.”
* “Step by step, do not over-engineer.”

---

## Pilar 4 – Prompting e Context Engineering

**Prompts usados:**

* “Think hard, answer short” → força respostas concisas.
* “Ultra think” (hook `-u`) → IA gasta mais esforço de raciocínio.
* “Dash d” (`-d`) → append automático: think hard + answer short + simple.
* “Explain this error” (`-e`) → prompt otimizado para logs.
* “Compact conversation but keep only UI changes” → resumo de contexto.
* “Above are the docs, are we following them properly?”
* “Are there any serious problems or is it basically correct? Think hard, answer short.”
* “Implement fix like a 10x engineer, fewer lines of code the better.”
* “Read V5.md and propose a minimal fix.”
* “Your task is to deeply investigate docs and check if we’re following properly.”
* “Create a new command /file review to check this path.”
* “Add essential CRM features into project\_description.md.”

---

Ou seja:

* **Pilar 1** = comandos de setup, atalhos e hooks.
* **Pilar 2** = prompts de clareza e documentação do projeto.
* **Pilar 3** = prompts para depuração e desenvolvimento técnico.
* **Pilar 4** = prompts de raciocínio profundo, compactação e contexto.

---

**INEMA** · 2025-08-23

## Pilar 4 – Prompting e Context Engineering

### 1. Ideia e Conceito

* **Prompting** é a arte de guiar a IA com instruções claras, detalhadas e bem estruturadas.
* **Context Engineering** é organizar os arquivos, descrições e instruções para que a IA tenha sempre o contexto correto.
* Juntos, eles definem se você terá um **código lixo cheio de erros** ou um **projeto funcional e otimizado**.
* Aqui, a regra é: **quanto melhor você alimenta a IA, melhor ela devolve.**

---

### 2. Passo a Passo de Prompting e Context Engineering

1. **Crie um arquivo central de contexto**

   * Exemplo: `project_description.md`
   * Ali você escreve a ideia do projeto, requisitos, features, stack escolhida.
   * Sempre que pedir algo à IA, **referencie esse arquivo**.

2. **Descreva o projeto como um engenheiro faria**

   * Use linguagem clara:

     * “O projeto é um CRM simples”
     * “Usar Next.js, Tailwind, SQLite”
     * “Precisa ter chat + gestão de contatos”

3. **Use modos diferentes conforme a fase**

   * **Plan Mode** → pensar antes de codar (melhor para arquitetura).
   * **Auto Accept Mode** → executar rápido sem confirmar cada passo.
   * **Default Mode** → intermediário, bom para ajustes.

4. **Estruture prompts em etapas**

   * Evite pedir tudo de uma vez.
   * Exemplo:

     * Passo 1: “Desenhe a estrutura de pastas”
     * Passo 2: “Implemente apenas a tela inicial”
     * Passo 3: “Conecte o banco de dados”

5. **Compacte e limpe o contexto**

   * Use `/compact` para resumir a conversa quando fica longa.
   * Use `/clear` para recomeçar quando mudar radicalmente de tópico.

6. **Documente cada decisão técnica**

   * Stack escolhida, versão de pacotes, soluções de bug → registre no `project_description.md`.
   * Assim a IA e você têm uma memória consistente.

---

### 3. Hacks de Prompting e Context Engineering

* **Finalize prompts com gatilhos de raciocínio**

  * Exemplo: “think hard, answer in short” → força respostas mais precisas.
  * “ultra think” → IA usa mais tempo e esforço para raciocinar.

* **Use Hooks personalizados**

  * Crie atalhos como `-d` = “think hard, answer short, keep it simple”.
  * Isso economiza dezenas de segundos em cada prompt.

* **Use XML tags para organizar info**

  * Exemplo no `project_description.md`:

    ```    <tech_stack>
      Next.js, Tailwind, SQLite, Anthropic API
    </tech_stack>
    <features>
      Chat, gestão de contatos, leads e tarefas
    </features>
    ```
  * Isso ajuda a IA a interpretar melhor.

* **Divida V1 e V2 do projeto**

  * Sempre pergunte: “Isso é essencial para o MVP (V1) ou pode ficar para a V2?”
  * Evita sobrecarga de features inúteis.

* **Sempre valide com documentação externa**

  * Combine Claude Code com **Perplexity** ou docs oficiais.
  * A IA pode estar desatualizada, então sempre cheque pacotes e SDKs.

* **Crie sub-agents**

  * Sub-agente para pesquisa, outro para testes, outro para refatoração.
  * Isso evita poluir o agente principal.

* **Reutilize prompts vencedores**

  * Toda vez que um prompt gera resultado excelente, salve em um `prompts.md`.
  * Crie uma “biblioteca de prompts” para acelerar próximos projetos.

---

**INEMA** · 2025-08-23

## Pilar 3 – Habilidade Técnica

### 1. Ideia e Conceito

* Claude Code **não substitui seu entendimento técnico**: ele acelera, mas não inventa fundamentos para você.
* Quanto mais você entende de **lógica, APIs, frameworks e boas práticas**, mais a IA consegue trabalhar como um “multiplicador” do seu conhecimento.
* É o que diferencia quem produz “slop” (código ruim) de quem constrói **projetos funcionais e escaláveis**.
* **A IA potencializa sua skill, não cria ela do zero.**

---

### 2. Passo a Passo para Desenvolver Habilidade Técnica

1. **Dominar o básico da lógica de programação**

   * Variáveis, loops, funções, condicionais.
   * Isso ajuda a entender o que a IA está gerando.

2. **Aprender um framework base**

   * Exemplo: Next.js para web, React Native para mobile, FastAPI ou Express para backend.
   * A IA pode guiar, mas você precisa saber “onde as peças se encaixam”.

3. **Entender bancos de dados**

   * Diferença entre SQL (SQLite, Postgres) e NoSQL (MongoDB).
   * Como criar tabelas simples e relacionamentos.

4. **Estudar APIs**

   * Como enviar e receber dados (REST, GraphQL).
   * Como usar chaves de autenticação (API keys).

5. **Aprender debugging básico**

   * Ler mensagens de erro no terminal e console.
   * Saber quando usar `console.log`, breakpoints e logs para entender o fluxo.

6. **Praticar microprojetos rápidos**

   * Criar uma calculadora, um CRUD simples, um to-do list.
   * Isso prepara você para usar Claude Code em projetos maiores.

7. **Complementar com IA**

   * Use a IA como tutor: “explique este erro passo a passo”.
   * Isso acelera o aprendizado técnico e fixa os conceitos.

---

### 3. Hacks para Acelerar sua Skill Técnica

* **Aprenda “enquanto constrói”**

  * Não espere dominar tudo antes de começar.
  * Use Claude Code para gerar e pergunte: “Explique o que você fez aqui em linguagem simples”.

* **Use sempre a técnica de debug em etapas**

  * Se der erro, nunca peça “corrija tudo”.
  * Pergunte: “O que está acontecendo nesta linha? Qual o próximo pequeno passo para corrigir?”.

* **Peça comparações de soluções**

  * Exemplo: “Qual a diferença entre usar SQLite e Postgres neste projeto?”.
  * Isso acelera sua visão crítica como dev.

* **Construa documentação pessoal**

  * Crie um arquivo `knowledge.md` no projeto.
  * Ali você registra aprendizados, trechos de código úteis, melhores práticas.
  * Esse arquivo também serve como contexto para Claude Code.

* **Use Vercel, Supabase e serviços gerenciados**

  * Eles eliminam parte da dificuldade inicial (deploy, DB, autenticação).
  * Assim você foca em aprender lógica e fluxo antes da infraestrutura pesada.

* **Pratique versionamento no GitHub desde cedo**

  * Mesmo sem experiência, suba seus projetos no GitHub.
  * Além de backup, força você a organizar melhor o código.

---

**INEMA** · 2025-08-23

## Pilar 2 – Clareza da Ideia

### 1. Ideia e Conceito

* O Claude Code só funciona bem se **você souber exatamente o que quer construir**.
* Quanto mais vago o objetivo, mais o resultado será “slop” (código bagunçado, incompleto).
* Clareza significa transformar sua visão em algo **documentado, objetivo e fácil de referenciar**.
* A regra é: **quanto mais claro no início, menos retrabalho no final**.

---

### 2. Passo a Passo para Clareza da Ideia

1. **Definir o objetivo do projeto**

   * Pergunte-se: o que estou construindo? (ex.: CRM simples, app de agendamento, dashboard).

2. **Registrar no arquivo `project_description.md`**

   * Escreva uma descrição curta e direta.
   * Adicione objetivos principais e “por que” o projeto existe.

3. **Listar funcionalidades essenciais**

   * Exemplo de CRM:

     * Criar e gerenciar contatos.
     * Gerenciar tarefas/leads.
     * Ter integração com um chatbot.

4. **Separar MVP de V2**

   * MVP (mínimo produto viável): só o essencial para rodar.
   * V2: recursos extras que podem esperar.
   * Isso evita escopo infinito.

5. **Definir stack inicial**

   * Linguagem, framework, banco de dados, IA usada.
   * Exemplo: Next.js + Tailwind + SQLite + Anthropic API.

6. **Adicionar ao arquivo central (****cloud.md**** ou project\_description.md)**

   * Colocar o escopo, features do MVP, stack e prazos.
   * Isso serve como **guia para a IA e para você mesmo**.

---

### 3. Hacks de Clareza da Ideia

* **Usar prompts curtos e objetivos no início**

  * Exemplo: “Build a quick MVP. Think hard, answer in short.”
  * Evita que a IA se perca em detalhes irrelevantes.

* **Documentar tudo em Markdown**

  * Use tags XML ou headers claros (`<stack>...</stack>`, `## MVP Features`).
  * Assim o Claude ou outro LLM “entende” melhor o contexto quando você referencia.

* **Perguntar sempre: V1 ou V2?**

  * Cada vez que pensar em adicionar algo, classifique: é essencial para V1? Se não, vira backlog.

* **Contexto rápido com Cursor/Claude Code**

  * Sempre inicie com: “Read project\_description.md and tell me if we’re aligned.”
  * Isso força a IA a respeitar seu documento central.

* **Deep research para validar ideia**

  * Use Perplexity ou web search antes de começar.
  * Pesquise: “Essential features of \[tipo do app]” e adicione no arquivo.
  * Assim você evita esquecer algo básico do setor.

---

**INEMA** · 2025-08-23

## Pilar 1 – Setup do Claude Code

### 1. Ideia e Conceito

O setup é o **alicerce**.
É o que separa quem usa Claude Code de forma casual de quem consegue produzir em nível 10x.
Ele consiste em **estruturar o ambiente** para:

* Ganhar velocidade.
* Evitar erros repetitivos.
* Garantir consistência nos projetos.
* Transformar prompts em **ferramentas reutilizáveis**.

Em resumo: **quanto mais otimizado seu setup, mais produtivo e confiável será seu fluxo**.

---

### 2. Passo a Passo do Setup

1. **Instalar Claude Code** no terminal.

   * Comando inicial para instalar globalmente.
   * Verificar atualização com `claude update` diariamente.

2. **Criar o Claude Folder** no root do projeto.

   * Estrutura com:

     * `hooks/` → atalhos de prompts frequentes.
     * `commands/` → fluxos repetitivos (ex.: /push GitHub, /create PR).
     * `sub-agents/` → agentes especializados (ex.: pesquisador web, revisor de código).

3. **Configurar o arquivo ****cloud.md**.

   * Arquivo central com instruções que orientam o Claude Code sempre que abrir o projeto.
   * Inclui regras como: “Nunca rode npm run build sem permissão do usuário”.

4. **Criar o arquivo project\_description.md**.

   * Descreve a ideia do projeto.
   * Inclui stack escolhida, funcionalidades principais, prazos e recursos.
   * Serve como “ponto de verdade” para humanos e IA.

5. **Personalizar ambiente**.

   * Configurar status line (modelo ativo, branch git, tempo, etc.).
   * Definir permissões no `settings.json` (o que pode rodar sem perguntar).
   * Organizar /docs para armazenar documentos, versões de pacotes e notas técnicas.

---

### 3. Hacks de Setup (truques que dão vantagem)

* **Atalhos de prompting com hooks**

  * `-d` → adiciona automaticamente: *think hard, answer in short, keep it simple*.
  * `-e` → explica erros e mostra plano de correção.
  * `-u` → ultra think (máximo esforço de raciocínio).

* **Compactar contexto sempre que mudar de foco**

  * `/compact` → resume conversa, mantém só o necessário.
  * Evita “context rot” (respostas confusas por excesso de histórico).

* **Automatizar setup entre projetos**

  * Manter um Claude Folder “principal” otimizado.
  * Copiar para cada novo projeto (ganho de consistência e velocidade).

* **Personalizar status line**

  * Mostrar modelo usado, branch git e gasto de créditos.
  * Dá clareza sobre o que está rodando a cada momento.

* **Integrar web search com Perplexity**

  * Quando faltar doc atualizada, combine Claude Code + Perplexity.
  * Cole os resultados no `/docs` e marque com XML tags para reuso.

---

**INEMA** · 2025-08-23

**passo a passo prático** que você pode seguir para aplicar o método  no seu uso do **Claude Code**.

---

## Passo a passo para construir qualquer coisa com Claude Code

### 1. Preparar o ambiente

1. Instale o Claude Code no terminal (`claude` ou comando de setup).
2. Configure seu **Claude folder** com:

   * Hooks (atalhos de prompts).
   * Comandos (tarefas repetitivas como /create PR, /push GitHub).
   * Sub-agentes (pesquisa web, revisão de código, debugging).
3. Crie um arquivo **cloud.md** no projeto (serve como “sistema base” com instruções e contexto).

---

### 2. Definir a ideia

1. Abra um **arquivo central Markdown** chamado `project_description.md`.
2. Escreva nele:

   * Objetivo do projeto (ex.: “CRM simples com IA integrada”).
   * Principais funcionalidades (V1: essenciais, V2: futuras).
   * Stack tecnológica escolhida.
   * Recursos disponíveis (tempo, equipe, APIs).

---

### 3. Escolher stack e arquitetura

1. Use o **plan mode** (`Shift + Tab`) para discutir com o Claude Code:

   * Qual stack usar.
   * Qual estrutura de pastas e módulos.
2. Documente as decisões no `project_description.md`.
3. Se necessário, pesquise em **Perplexity** e adicione os docs ao arquivo.

---

### 4. Configurar fluxo de prompts

1. Use **atalhos de prompting**:

   * `think hard answer in short` → raciocínio profundo e resposta curta.
   * `-d` → aplica prompt padrão de pensar + responder curto.
   * `-e` → explicar erros (debugging).
   * `-u` → ultra think (máximo esforço de raciocínio).
2. Crie hooks para evitar repetir comandos.

---

### 5. Desenvolvimento iterativo

1. Comece sempre pelo **planejamento** (plan mode).
2. Só depois mude para **execução rápida** (auto accept).
3. Teste partes pequenas, não peça código gigante de uma vez.
4. Sempre documente cada decisão em Markdown (stack, versão de pacotes, erros corrigidos).

---

### 6. Debugging eficiente

1. Adicione **logs estratégicos** em pontos críticos.
2. Use **Playwright MCP** para testes automáticos de frontend.
3. Se o Claude Code travar, use:

   * `/clear` → limpa contexto.
   * `/compact` → resume histórico.
4. Quando errar, faça debugging **passo a passo**, nunca peça solução única.

---

### 7. Documentação contínua

1. Crie pasta `/docs` no projeto.
2. Salve nela:

   * Docs de bibliotecas usadas (copiados do Perplexity).
   * Versões de pacotes instalados.
   * Diferenças entre versões (ex.: V4 → V5 SDK).
3. Atualize sempre que resolver erros ou migrar dependências.

---

### 8. Integração e versionamento

1. Configure **.gitignore** para não subir chaves ou `.env`.
2. Suba o projeto no **GitHub** desde o início.
3. Use comandos rápidos (/push GitHub, /create PR) para manter controle de versão.

---

### 9. Evolução constante

1. Revise diariamente seu setup (`claude update`).
2. Sempre transforme tarefas repetitivas em **hooks, comandos ou sub-agentes**.
3. Compartilhe setup com sua equipe (cada um ganha produtividade).

---

**INEMA** · 2025-08-23

Aqui está o resumo estruturado  **Build Anything with Claude Code, Here’s How**:

---

## 1. Ideia central

O vídeo mostra como usar o **Claude Code (CL Code)** para construir praticamente qualquer coisa: aplicativos móveis, agentes de IA, sites ou até animações 3D. O criador, **David Andre**, compartilha sua experiência de mais de 300 horas de uso, destacando que o segredo está em quatro pilares.

---

## 2. Os quatro pilares do sucesso com Claude Code

1. **Setup personalizado**

   * Configuração de hooks, comandos, prompts, sub-agentes.
   * Torna o Claude Code mais rápido, confiável e eficiente.

2. **Clareza de ideia**

   * Definir claramente o que se deseja construir.
   * Exemplo: um CRM simples com IA integrada.

3. **Habilidade técnica**

   * Conhecimento em ciência da computação e boas práticas de desenvolvimento.
   * Não dá para pular o desenvolvimento de skill — isso compõe a velocidade e qualidade.

4. **Context engineering e prompting**

   * Saber guiar a IA com prompts claros, curtos e objetivos.
   * Usar truques como “think hard, answer in short” para melhorar raciocínio.

---

## 3. Fluxo de trabalho recomendado

* Criar um **arquivo central em Markdown** (project\_description.md) com descrição do projeto, stack e objetivos.
* Definir stack tecnológica adequada ao propósito (exemplo do vídeo: Next.js, Tailwind, SQLite, Anthropic API via Vercel SDK).
* Usar **plan mode** para estruturar decisões (arquitetura, organização de código) antes de começar a codar.
* Alternar entre **plan mode** (precisão e raciocínio profundo) e **auto accept mode** (execução rápida).

---

## 4. Ferramentas e técnicas mostradas

* **Hooks personalizados**: atalhos para prompts recorrentes (ex.: “-d” = pensar profundamente e responder curto).
* **Comandos**: automatizam ações repetitivas (/create PR, /file review, /push GitHub).
* **Sub-agentes**: delegam tarefas especializadas (ex.: pesquisa de documentação atualizada).
* **Compactação de contexto (****/compact****)**: resume conversas longas e evita “context rot”.
* **Integração com Perplexity**: essencial para buscar documentação atualizada (já que LLMs têm corte de conhecimento).
* **Playwright MCP**: usado para testes automatizados e debugging de frontend.

---

## 5. Principais aprendizados práticos

* **Não agir como “vibe coder”** (sair pedindo código direto). Primeiro planeje arquitetura, stack e features.
* **Documente tudo em Markdown**: decisões, versões de pacotes, estrutura do código. Isso cria memória útil para IA e humanos.
* **Comece simples (MVP)**: diferencie features de **V1 (essenciais)** e **V2 (avançadas)**.
* **Debug passo a passo**: em vez de pedir solução única, adicionar logs estratégicos e isolar problemas.
* **Evolução contínua**: setup de Claude Code, hooks e comandos deve ser melhorado semanalmente.

---

## 6. Conclusão do vídeo

Claude Code permite construir sistemas complexos rapidamente, mas o diferencial está no **setup bem feito + clareza do projeto + habilidades técnicas + prompting eficaz**.
Combinado a ferramentas externas como **Perplexity** e boas práticas de documentação, qualquer pessoa pode evoluir como desenvolvedor e até competir com times maiores.

---

**INEMA** · 2025-08-23

**Build Anything with Claude Code**

---

**INEMA** · 2025-08-23

https://chatgpt.com/c/68a935fd-56d8-8320-8ff1-e21b9103f0a8
