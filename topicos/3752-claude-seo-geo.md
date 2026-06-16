# Claude - SEO - GEO

> Tópico 3752 · 5 mensagens úteis de 12 totais

---

**INEMA** · 2026-03-13

Dentro desse repositório **`inematds/claude-seo`**, a empresa que aparece relacionada a **dados reais / quase em tempo real** é:

### 🟢 DataForSEO

O projeto menciona uma **integração opcional com a API da DataForSEO** para obter dados externos mais atualizados.

#### O que a DataForSEO fornece

* Dados reais de **Google SERP**
* **Keywords e volume de busca**
* **Ranking de sites**
* **Dados por país e cidade**
* Resultados quase **em tempo real via API**

#### Para que o repo usa isso

Quando conectada, a API pode alimentar a skill com:

* pesquisa de **keywords atualizadas**
* **dados de ranking reais**
* análise competitiva
* métricas de SEO mais confiáveis

Sem essa API, a skill ainda funciona, mas usa **análise estrutural do site e heurísticas**, não dados externos.

### ⚙️ Resumindo

Dentro desse Git:

| Tipo                 | Fonte                    |
| -------------------- | ------------------------ |
| análise do site      | feita pela própria skill |
| dados externos reais | **DataForSEO API**       |
| realtime SEO data    | **DataForSEO**           |

---

**INEMA** · 2026-03-12

A **Claude SEO** é uma skill para **Claude Code** focada em fazer **auditorias completas de SEO**. Ela analisa SEO técnico, páginas individuais, qualidade de conteúdo com critérios **E-E-A-T**, dados estruturados, imagens, sitemap, hreflang e também otimização para **buscas por IA/GEO**, como Google AI Overviews, ChatGPT web search e Perplexity. 

Na prática, ela funciona por comandos como:
`/seo audit <url>`, `/seo page <url>`, `/seo schema <url>`, `/seo technical <url>`, `/seo content <url>` e `/seo geo <url>`. O comando mais forte é o **`****/seo**** audit`**, que faz uma auditoria completa do site com **subagentes paralelos**. 

Além da parte tradicional de SEO, a skill traz módulos mais avançados, como:

* **programmatic SEO** para planejar páginas em escala;
* **páginas comparativas de concorrência** (“X vs Y”);
* **auditoria hreflang/i18n** para sites multilíngues;
* geração e validação de **Schema.org**** markup**;
* geração de sitemap com templates por setor. 

Ela também incorpora referências atuais de SEO, como metas de **Core Web Vitals** (LCP, INP e CLS), atualização das diretrizes de qualidade **E-E-A-T** e suporte a tipos de schema para **vídeo e transmissões ao vivo**. 

Em estrutura, o projeto é modular: o README cita uma skill principal, várias sub-skills e subagentes, com requisitos de **Python 3.10+**, **Claude Code CLI** e Playwright opcional para screenshots. Há ainda integrações opcionais com MCPs e uma extensão para **DataForSEO** para puxar dados mais “ao vivo”, embora a própria skill funcione sem isso. 

**Resumo em 1 frase:**
é uma skill feita para transformar o Claude Code em uma ferramenta de **auditoria, planejamento e otimização de SEO**, incluindo SEO tradicional e SEO para mecanismos de busca com IA. 

Tem um detalhe curioso: embora o repositório seja `inematds/claude-seo`, o README exibido no GitHub .

---

**INEMA** · 2026-03-12

https://github.com/inematds/claude-seo

---

**INEMA** · 2026-03-12

Claude - SEO - GEO

---

**INEMA** · 2026-03-12

https://chatgpt.com/c/69b1792a-1588-832e-aa75-524ff81efce8
