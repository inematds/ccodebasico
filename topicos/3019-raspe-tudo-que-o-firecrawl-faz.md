# Raspe tudo Que o Firecrawl Faz

> Tópico 3019 · 10 mensagens úteis de 24 totais

---

**INEMA** · 2026-02-13

No final, o objetivo de tudo isso é **transformar qualquer site da internet** 

# 🎯 Objetivo Técnico

Converter sites em:

* 📄 Texto limpo (Markdown)
* 📊 Dados estruturados (CSV / JSON)
* 🗺 Estrutura completa do site (Map)
* 🖼 Screenshots
* 🎨 Informações de branding
* 🧠 Conteúdo pronto para alimentar LLMs

Ou seja: transformar páginas desorganizadas da web em **dados organizados e prontos para uso inteligente**.

---

# 🧠 Objetivo Estratégico

Substituir isso:

> Configurar APIs manualmente
> Criar automações complexas
> Lidar com múltiplos endpoints
> Construir scrapers do zero

Por isso:

> Linguagem natural
> Claude decide as ferramentas
> Fluxo agentivo
> Execução automática

---

# 💼 Objetivo Prático (Aplicações Reais)

Você pode usar isso para:

* Criar bancos de dados a partir de sites
* Gerar datasets para treinar modelos
* Monitorar concorrentes
* Extrair produtos para e-commerce
* Coletar leads
* Analisar branding
* Construir RAG (Retrieval-Augmented Generation)
* Criar ferramentas SaaS baseadas em dados públicos

---

# 🚀 Objetivo Maior

Transformar a web inteira em:

> 🔹 Fonte estruturada de dados
> 🔹 Base para automação inteligente
> 🔹 Infraestrutura para negócios com IA

Em vez de ver sites como páginas estáticas, você passa a ver como:

> APIs prontas esperando para serem usadas.

---

# 🧩 Resumo Final

O objetivo não é só fazer scraping.

O objetivo é:

> Criar um sistema onde você pede o resultado em linguagem natural
> E a IA descobre como chegar lá sozinha.

Isso é o verdadeiro ganho.

QUALIFICAR NICHO

---

**INEMA** · 2026-02-13

Aqui estão os **principais hacks estratégicos** usados (e implícitos) no processo para extrair o máximo do Claude Code + Firecrawl:

---

# 🔥 1️⃣ Não diga qual ferramenta usar

**Hack:** nunca diga “use scrape” ou “use map”.

Só diga o resultado final desejado.

Exemplo bom:

```I want all job listings from this website as structured data in CSV format.```

Deixe o Claude decidir:

* Scrape → Map → Crawl → Extract
  Isso ativa o fluxo agentivo.

---

# 🔥 2️⃣ Use Plan Mode para tarefas grandes

Para sites com paginação ou muitas URLs:

```Create a plan before executing.```

Isso faz o Claude:

* Entender a estrutura
* Perguntar o que extrair
* Definir estratégia antes de gastar créditos

---

# 🔥 3️⃣ Limite o volume primeiro

Antes de extrair 1.700 itens, diga:

```Start with 50 results as a test.```

Hack de economia:

* Testa estrutura
* Evita gastar créditos desnecessários
* Ajusta campos antes de escalar

---

# 🔥 4️⃣ Sempre peça saída estruturada explícita

Em vez de:

```Get all jobs.```

Use:

```Return the results as structured data in CSV format with these fields:
title, company, location, salary, description, apply_url.```

Isso força Extract corretamente.

---

# 🔥 5️⃣ Use Map antes de Crawl (em sites grandes)

Se for site com múltiplas páginas:

```First map the website structure.
Then extract the data from all relevant pages.```

Hack: evita perder páginas paginadas.

---

# 🔥 6️⃣ Quando extract falhar

Se vier vazio, diga:

```The extract returned empty results. 
Try a more robust crawling strategy and then extract again.```

Isso ativa autocorreção.

---

# 🔥 7️⃣ Peça resumo em vez de descrição completa

Economiza tokens e créditos:

```Return summary instead of full descriptions.```

---

# 🔥 8️⃣ Combine tarefas em paralelo

Abra dois agentes:

* Um faz map
* Outro faz branding

Hack de produtividade.

---

# 🔥 9️⃣ Peça sempre os links de origem

Para rastreabilidade:

```Include the source URL for each item.```

---

# 🔥 🔟 Use o CLAUDE.md estrategicamente

Inclua regras como:

* Sempre preferir extract para dados estruturados
* Sempre mapear antes de crawl em sites grandes
* Sempre perguntar campos antes de executar

Isso transforma o projeto em sistema inteligente.

---

# 🚀 Hack avançado (nível profissional)

Em vez de pedir scraping direto, use:

```Analyze this website and propose the best extraction strategy before executing.```

Isso faz o Claude pensar antes de agir.

---

# 🎯 Hack mental mais importante

Não pense:

> “Qual endpoint usar?”

Pense:

> “Qual resultado eu quero?”

Deixe o MCP decidir o resto.

---

---

**INEMA** · 2026-02-13

**Principais prompts usados ao longo do processo**, organizados por etapa:

---

# 🔹 1️⃣ Conectar ao MCP do Firecrawl

```Hey Claude, I want to connect to Firecrawl's MCP server. 
You can do that using this command. 
But I’m not going to give you my API key here — I’ll put it in a .env file. 
So please create that file for me, then initialize and connect to Firecrawl’s MCP server.```

---

# 🔹 2️⃣ Testar se está funcionando

```Scrape this website and return the content in markdown.```

(Usado apenas para validar que o MCP está ativo.)

---

# 🔹 3️⃣ Criar Cheat Sheet do Firecrawl

```Create a Firecrawl cheat sheet as a markdown file in this project that you can reference. 
It should explain the different tools and when to use each one.```

---

# 🔹 4️⃣ Criar o CLAUDE.md (sistema do projeto)

```Help me set up a CLAUDE.md file for this project. 
This project is specifically for scraping data, extracting it, getting screenshots, 
crawling websites, and mapping sites. 

You have access to the Firecrawl MCP server and the firecrawl-cheatsheet.md 
which explains how the MCP server works and when to use each tool.```

---

# 🔹 5️⃣ Caso prático – Extrair 1.700 vagas

```I found this website and I have about 1,700 job opportunities I want to look at. 
I need help using the Firecrawl MCP server to get all of them listed out. 

I want these as structured data so I can put them into a Google Sheet.```

Depois ele responde perguntas como:

* How many listings?
* What data fields?
* Full descriptions or summaries?

---

# 🔹 6️⃣ Screenshot + Branding

```Please grab screenshots of this page and help me understand the branding.```

---

# 🔹 7️⃣ Mapear um site completo

```Go ahead and map out this site for me and show me what it looks like.```

---

# 🔹 8️⃣ Versão mais estratégica (quando usa Plan Mode)

```Create a plan to scrape, map, and extract structured data from this website 
using the Firecrawl MCP server.```

---

# 🎯 Estrutura padrão dos prompts usados

Eles seguem esse padrão:

1. 🔎 Contexto do que você quer
2. 📊 Resultado esperado (structured data, screenshot, map)
3. 🧠 Deixar Claude decidir quais ferramentas usar
4. 📁 Pedir saída em formato específico (CSV, markdown, JSON)

---

**INEMA** · 2026-02-13

https://www.firecrawl.dev/

---

**INEMA** · 2026-02-13

branding.”

Retorna:

* screenshot full page,
* logo, favicon/OG image,
* paleta de cores,
* tipografia,
* componentes/estilo.

### B) Mapear um site inteiro

Peça:

* “Mapeie o site completo e mostre as principais seções.”

Retorna:

* sitemap com páginas, categorias, coleções, produtos, guias etc.
  Depois disso, você pode:
* dar crawl em uma seção específica,
* extrair para banco,
* montar dataset.

---

## 13) Rodar duas tarefas em paralelo (quando fizer sentido)

Você pode abrir dois “agentes” no Claude Code:

* um fazendo **map**
* outro fazendo **branding/screenshot**
  ao mesmo tempo.

---

**INEMA** · 2026-02-13

Passo a Passo

## 1) Entenda o objetivo

Você quer transformar **qualquer site** em **dados prontos para LLM**, podendo gerar:

* conteúdo (texto + metadados),
* **estrutura do site (mapa de URLs)**,
* **dados estruturados** (tabela/CSV),
* **screenshots**,
* **branding** (logo, cores, tipografia).

---

## 2) Teste rápido no Playground do Firecrawl (opcional, mas recomendado)

1. Abra o **Playground** do Firecrawl.
2. Cole a URL do site.
3. Selecione o formato de saída (ex.: **Markdown**, **AI summary**, **Links**, **HTML**, **Screenshot**, **Branding**, **JSON**).
4. Rode o scrape e confira o retorno para entender o que a ferramenta entrega.

---

## 3) Crie um projeto no VS Code

1. Abra o **VS Code**.
2. Crie/abra uma pasta vazia (ex.: `scraper/`).
3. Deixe o projeto “limpo” (sem arquivos), para acompanhar tudo que será gerado.

---

## 4) Instale e conecte o Firecrawl via MCP no Claude Code

1. Vá na **documentação do Firecrawl** e encontre a seção **MCP Server**.
2. Copie o **comando de instalação para Claude Code** (uma linha).
3. No Claude Code, peça para ele:

   * executar esse comando,
   * **criar um arquivo `.env`**,
   * e usar o `.env` para ler sua API key (sem você colar a chave no chat).

> A ideia aqui é: **MCP instalado + chave no `.env` = Claude pode chamar as ferramentas do Firecrawl automaticamente.**

---

## 5) Coloque sua API Key no `.env`

1. Abra o arquivo `.env` criado.
2. Pegue sua **API key** no painel (dashboard) do Firecrawl.
3. Cole no `.env` e salve.
4. Feche o arquivo.

**Por que `.env`?**
Para manter a chave fora do histórico de conversa.

---

## 6) Recarregue o VS Code para “ativar” o MCP

1. Pressione `Ctrl + Shift + P`
2. Execute **Developer: Reload Window**

Isso garante que o Claude Code passe a enxergar o MCP já configurado.

---

## 7) Faça um teste simples (sanity check)

1. Peça para o Claude extrair uma página conhecida (algo direto, tipo “scrape essa URL e me devolva em markdown”).
2. Verifique se ele retorna o conteúdo e se realmente chamou a ferramenta correta (normalmente ele escolhe **Scrape** nesse teste).

---

## 8) Crie um “cheat sheet” de ferramentas (para o projeto ficar inteligente)

Peça ao Claude para criar um arquivo markdown tipo:

* `firecrawl-cheatsheet.md`

Esse arquivo deve conter:

* quais ferramentas existem (Scrape/Map/Crawl/Search/Extract),
* exemplos de uso,
* um guia rápido de decisão (“quando usar cada uma”).

---

## 9) Crie um `CLAUDE.md` (prompt de sistema do projeto)

Peça ao Claude para criar um arquivo `CLAUDE.md` dizendo que:

* o projeto é para **scraping e extração**,
* ele pode gerar **screenshots, mapear e rastrear sites**,
* ele tem acesso ao **MCP do Firecrawl**,
* e deve consultar o `firecrawl-cheatsheet.md` quando precisar.

A lógica:

* `CLAUDE.md` = objetivo e regras gerais (curto)
* `cheatsheet` = detalhes e referências (longo)

---

## 10) Use caso real: extrair muitas páginas (ex.: listagens)

Quando o site tem muitas páginas (paginação), o fluxo recomendado é:

1. **Scrape inicial**
   Para entender a estrutura e os elementos da página.

2. **Map**
   Para descobrir todas as URLs (especialmente páginas paginadas).

3. **Plano + perguntas**
   O assistente deve alinhar:

   * Quantos itens você quer (ex.: 200 vs tudo),
   * Quais campos extrair,
   * Se quer descrição completa ou resumo.

4. **Extract / Crawl**

   * Se precisar ir página a página, usa **Crawl**.
   * Se quer dados estruturados, usa **Extract**.

5. **Exportação**
   Gerar saída em **CSV** (ideal para Google Sheets) com colunas como:

   * título, empresa, tipo, local, salário, experiência, categoria, data, URL, descrição, tags.

---

## 11) Autocorreção (quando algo não funciona)

Se o **Extract** retornar vazio ou a página exigir mais “manejo”:

* o assistente troca a abordagem automaticamente (ex.: usar um modo/agente mais robusto do Firecrawl, ajustar estratégia, trocar ordem de ferramentas etc.)
* e tenta novamente até extrair.

---

## 12) Outros 2 fluxos prontos

### A) Screenshot + Branding

Peça:

* “Gere screenshots da página e extraia

---

**INEMA** · 2026-02-13

## 3️⃣ Instalar o MCP no Claude Code

* Criar novo projeto no VS Code
* Copiar comando MCP da documentação
* Pedir para Claude instalar e conectar

---

## 4️⃣ Configurar segurança da API

* Criar arquivo `.env`
* Inserir API key
* Recarregar o VS Code

---

## 5️⃣ Testar se está funcionando

* Fazer um scrape simples
* Confirmar que Claude chama automaticamente o endpoint correto

---

## 6️⃣ Organizar o projeto

Criar:

### 🔹 Cheat Sheet

Guia com:

* Quais ferramentas existem
* Quando usar cada uma

### 🔹 CLAUDE.md

Define:

* Objetivo do projeto
* Acesso ao MCP
* Referência ao cheat sheet

---

## 7️⃣ Caso prático 1 – Extração em escala

* Scrape inicial
* Mapear o site
* Criar plano
* Fazer perguntas de refinamento
* Executar extração
* Exportar CSV estruturado

🔎 Destaque: autocorreção quando algo falha.

---

## 8️⃣ Caso prático 2 – Screenshot + Branding

* Gerar screenshot full page
* Extrair logo, cores, tipografia

---

## 9️⃣ Caso prático 3 – Mapear site completo

* Gerar sitemap
* Listar categorias e páginas
* Preparar para crawl ou extração futura

---

## 🔟 Mostrar custo e escalabilidade

* Créditos usados
* Diferença entre planos
* Concorrência de requisições

---

# 🎯 Enfatizo

* Uso do **MCP Server**
* Linguagem natural ao invés de configurar APIs manualmente
* Workflow agentivo com autocorreção
* Rapidez comparado a automações tradicionais
* Baixo custo inicial

---

**INEMA** · 2026-02-13

https://www.youtube.com/watch?v=4efAzBiTeVo

---

**INEMA** · 2026-02-13

# 🎯 Tema Central

Como transformar **qualquer site em dados prontos para LLM (LLM-ready data)** em segundos usando **Claude Code + Firecrawl (MCP Server)**.

---

# 1️⃣ O Que o Firecrawl Faz

Firecrawl permite:

* **Scrape** → Extrair todo conteúdo de uma página
* **Map** → Mapear todas as URLs e arquitetura do site
* **Crawl** → Navegar e explorar múltiplas páginas
* **Search** → Buscar no Google antes de extrair
* **Extract** → Transformar conteúdo em dados estruturados

Formatos disponíveis:

* Markdown
* HTML
* JSON
* Screenshot da página
* Branding (logo, cores, tipografia)
* Resumo gerado por IA

O diferencial: usar o **MCP Server**, permitindo que Claude escolha automaticamente qual ferramenta usar com base em linguagem natural.

---

# 2️⃣ Demonstração no Playground

No site firecrawl.dev:

1. Inserir URL
2. Escolher formato
3. Executar scrape

Resultado inclui:

* Conteúdo completo em markdown
* Resumo IA
* Screenshot
* Informações de branding
* JSON estruturado

---

# 3️⃣ Integração com Claude Code

## Passos principais:

1. Criar novo projeto no VS Code
2. Copiar comando MCP Server da documentação
3. Pedir para Claude conectar ao MCP
4. Criar arquivo `.env`
5. Inserir API Key
6. Reload do VS Code

Após isso, Claude consegue usar Firecrawl automaticamente.

---

# 4️⃣ Organização do Projeto

Criados dois arquivos importantes:

### 🔹 firecrawl-cheatsheet.md

Guia detalhado das ferramentas e quando usar cada uma.

### 🔹 CLAUDE.md

Prompt de sistema do projeto explicando:

* O objetivo (scraping)
* Acesso ao MCP
* Referência ao cheat sheet

Separação mantém o sistema limpo e organizado.

---

# 5️⃣ Caso de Uso 1 – 1.700 Vagas de Emprego

Problema:
Extrair 1.700 vagas distribuídas em 60+ páginas e transformar em planilha.

Fluxo do Claude:

1. Scrape inicial
2. Map do site
3. Criação de plano
4. Perguntas de refinamento
5. Execução
6. Autocorreção quando extract falhou

Resultado:
CSV com 200 vagas contendo:

* Título
* Empresa
* Tipo
* Local
* Salário
* Experiência
* Categoria
* Data
* URL
* Descrição
* Tags

🔥 Destaque: **Agentic Workflow**
Claude detecta erro, ajusta estratégia e continua sozinho.

---

# 6️⃣ Caso de Uso 2 – Branding & Screenshot

Prompt:
“Pegue screenshots e analise o branding.”

Resultado:

* Screenshot completa
* Paleta de cores
* Tipografia
* Espaçamento
* Componentes
* Logo

Aplicações:

* Análise competitiva
* Briefing de design
* Estudo de identidade visual

---

# 7️⃣ Caso de Uso 3 – Mapeamento de Site

Prompt:
“Mapeie esse site.”

Resultado:

* Páginas principais
* Categorias
* Coleções
* Produtos
* Guias
* Localizações

Depois é possível:

* Fazer crawl específico
* Extrair produtos
* Construir banco de dados

---

# 8️⃣ Execução Paralela

Dois agentes Claude rodando ao mesmo tempo:

* Um mapeando site
* Outro extraindo branding

Mostra capacidade de operações paralelas.

---

# 9️⃣ Custos

Uso total na demo:

* ~30 créditos
* De 500 gratuitos
* Apenas 6%

Diferenças de planos:

* Créditos
* Número de páginas
* Requisições simultâneas (2 no free, 5 no hobby, mais nos planos superiores)

---

# 🔟 Principais Insights

* Não é necessário configurar endpoints manualmente.
* Claude decide automaticamente quais ferramentas usar.
* Fluxo agentivo permite autocorreção.
* Extremamente rápido comparado a automações tradicionais.
* Baixo custo para uso inicial.

---

# 🚀 Conclusão

Firecrawl + Claude Code permitem:

✔ Transformar qualquer site em dados estruturados
✔ Extrair grandes volumes rapidamente
✔ Fazer análise visual e estrutural
✔ Automatizar scraping complexo via linguagem natural
✔ Construir workflows de automação muito mais rápidos

---

**INEMA** · 2026-02-13

https://chatgpt.com/c/698d518c-93fc-8325-93ad-d70568823f94
