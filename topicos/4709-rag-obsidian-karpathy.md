# RAG - Obsidian + Karpathy

> Tópico 4709 · 14 mensagens úteis de 33 totais

---

**INEMA** · 2026-04-06

**Extensão (Obsidian Web Clipper)** por um motivo bem prático:

### 👉 Principal função

Facilitar a **captura de conteúdo da internet direto pro seu “segundo cérebro”**.

---

### 🔹 Sem a extensão

Você teria que:

* copiar o texto manualmente
* colar no Obsidian
* organizar tudo na mão

👉 Mais lento e bagunçado.

---

### 🔹 Com a extensão

Você só:

1. Abre um artigo/site
2. Clica na extensão
3. Envia direto pra pasta `raw`

E pronto — o LLM faz o resto:

* lê o conteúdo
* organiza
* cria páginas
* conecta tudo automaticamente

---

### 🔹 Por que isso é importante?

Porque o sistema funciona assim:

> **raw (dados brutos) → LLM processa → wiki organizada**

A extensão garante que:

* o conteúdo entra **limpo e estruturado**
* você não perde tempo com formatação
* o fluxo fica automático

---

### 🔹 Resumindo

Usa a extensão para:

* economizar tempo
* evitar trabalho manual
* alimentar o sistema com dados de forma rápida

---

**INEMA** · 2026-04-06

[Texto colado #1 +62 linhas]

Agora você é meu agente de Wiki com LLM. Implemente exatamente este arquivo de ideia como meu segundo cérebro completo. Me guie passo a passo: crie o arquivo de esquema CLAUDE.md com todas as regras, configure index.md e log.md, defina convenções de pastas e me mostre o primeiro exemplo de ingestão. A partir de agora, toda interação segue esse esquema.

---

**INEMA** · 2026-04-06

[Pasted text #1 +62 lines]

You are now my LLM Wiki agent. Implement this exact idea file as my complete second brain. Guide me step-by-step: create the CLAUDE.md schema file with full rules, set up index.md and log.md, define folder conventions, and show me the first ingest example. From now on, every interaction follows the schema.

---

**INEMA** · 2026-04-06

### 🔗 Ferramentas

* **Obsidian (download):**
  [https://obsidian.md](https://obsidian.md/)

* **Obsidian Web Clipper (extensão Chrome):**
  [https://chromewebstore.google.com/detail/obsidian-web-clipper](https://chromewebstore.google.com/detail/obsidian-web-clipper)

---

### 🔗 Referência da ideia (Karpathy)

* Post/ideia sobre **LLM knowledge bases (wiki com LLM)**:
  [https://karpathy.ai/](https://karpathy.ai/) (site geral)
  👉 normalmente o conteúdo vem de posts no X (Twitter) — vale procurar:
  **“Andrej Karpathy LLM knowledge base wiki”**

---

### 🔗 Exemplo 

* Artigo usado como exemplo (**AI 2027**):
  [https://ai-2027.com](https://ai-2027.com/)

---

### 🔗 Ferramentas  (opcionais)

* **Visual Studio Code:**
  [https://code.visualstudio.com](https://code.visualstudio.com/)

---

**INEMA** · 2026-04-06

Aqui vai um resumo dos passos para montar esse “LLM wiki”/segundo cérebro: 

1. **Instale o Obsidian** e crie um **vault** novo.

2. **Abra a pasta do vault** no VS Code ou no ambiente onde você roda o Claude/Cloud Code.

3. **Cole o prompt/base do Andrej Karpathy** no Claude/Cloud Code e peça para ele implementar a estrutura do wiki no vault.

4. O agente vai criar a estrutura inicial, normalmente com:

   * pasta **raw** para arquivos brutos
   * pasta **wiki** para páginas organizadas
   * arquivos como **index**, **log** e **claude.md/claw.md** com regras do projeto. 

5. **Adicione fontes na pasta `raw`**, como artigos, PDFs, transcrições ou notas.

6. Para páginas da web, ele sugere usar o **Obsidian Web Clipper** e configurar o destino padrão para a pasta **raw**. 

7. Depois, peça ao Claude algo como: **“ingest this source”** para ele processar o material.

8. Durante a ingestão, dê **contexto sobre o objetivo do vault**:

   * pesquisa sobre IA
   * segundo cérebro pessoal
   * base de conhecimento do negócio
   * transcrições de YouTube etc. 

9. O agente então:

   * lê o material bruto
   * quebra em tópicos
   * cria várias páginas `.md`
   * conecta tudo com **links e backlinks**
   * atualiza **índice** e **log**. 

10. Use o **graph view** do Obsidian para visualizar os nós e relações.

11. Continue repetindo o processo: **jogue novos materiais em `raw` e mande ingerir**.

12. Opcionalmente, conecte esse wiki a outros agentes, como um **assistente executivo**, apontando esses agentes para a pasta **wiki**. 

**Ideia central:** em vez de usar uma stack complexa de RAG, você mantém uma base em **arquivos Markdown organizados**, que o LLM consegue atualizar, indexar e consultar com custo menor e boa navegabilidade em pequena e média escala.

---

**INEMA** · 2026-04-06

**Por que isso é importante?
**
* Eficiência de tokens + valor de longo prazo.
* Um usuário no X transformou:

  * 383 arquivos espalhados
  * * 130 transcrições de reuniões
* Em uma wiki compacta
* E reduziu o uso de tokens em ~95% ao consultar com Claude.
* Arquivos de ideia > código.
* O Karpathy enfatiza compartilhar “arquivos de ideia” (prompts/especificações) em vez de código.
* O trabalho do agente é implementar e customizar.
* Isso está crescendo porque se encaixa perfeitamente na era dos agentes.
* PRs (pull requests) viram “prompt requests”.

---

**INEMA** · 2026-04-06

**LLM Wiki File Tree → Estrutura de arquivos do LLM Wiki**

`my-wiki/
├── raw/        → você coloca conteúdo aqui (somente leitura)
├── wiki/       → o LLM escreve tudo aqui
│   ├── index.md → índice / sumário
│   ├── log.md   → histórico de operações
│   ├── *.md     → todas as páginas da wiki
└── CLAUDE.md   → regras / esquema do sistema`

---

**INEMA** · 2026-04-06

* Extremamente simples em escala pessoal.
* Não precisa de banco vetorial, embeddings ou infraestrutura RAG complexa.
* Apenas pastas + Markdown + Obsidian.
* O LLM faz indexação e síntese usando o `index.md`.

---

**INEMA** · 2026-04-06

**Por que isso é importante?
**
* Chats normais de IA (ou ferramentas como NotebookLM ou RAG básico) são efêmeros — o conhecimento desaparece após a conversa.
* O método do Karpathy faz o conhecimento **acumular como juros no banco**.
* Pessoas no X estão chamando isso de “revolucionário”, porque faz a IA parecer um colega incansável que lembra de tudo e se mantém organizado.

---

**INEMA** · 2026-04-06

https://obsidian.md/download

---

**INEMA** · 2026-04-06

https://ai-2027.com/

---

**INEMA** · 2026-04-06

https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

---

**INEMA** · 2026-04-06

**Obsidian + Karpathy = 95% mais barato "RAG" no código Claude**

---

**INEMA** · 2026-04-06

https://chatgpt.com/c/69d34041-e9c8-8333-8db9-bf68bfcfffc0
