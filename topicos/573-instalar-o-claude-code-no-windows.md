# Instalar o Claude Code no Windows

> Tópico 573 · 9 mensagens úteis de 22 totais

---

**INEMA** · 2025-08-30

Transforme ele em claude.md ou readme.md

---

**INEMA** · 2025-08-30

Modelos de Claude.md

---

### Modelo 1 – **claude.md**** mínimo funcional**

Esse serve para testar o fluxo. É só um texto simples e ele já cria a base do projeto.

```# Projeto Claude Code

Quero um projeto simples em Node.js + TypeScript que responda "Olá Mundo" no terminal.

Fluxo:
- Ao rodar `npm run dev`, deve imprimir "Olá Mundo do Claude Code".```

Com esse arquivo na pasta, ao rodar `npx create-claude@latest`, ele vai gerar a estrutura padrão (`package.json`, `tsconfig.json`, `claude.config.json`, `src/index.ts`) e já preencher o `index.ts` com esse comportamento.

---

### Modelo 2 – **claude.md**** detalhado (ONG de Pets)**

Esse já mostra agentes, fluxos e integrações.

```# Projeto Claude Code: ONG de Pets

Objetivo:
Criar um sistema para WhatsApp e Web que permita:
- Cadastro de pets perdidos e achados
- Controle de vacinação
- Doações via Pix
- Notificações internas por e-mail

Estrutura desejada:
- `src/agents/agenteCadastro.ts` → responsável por cadastrar pets
- `src/agents/agenteVacinacao.ts` → gerenciar calendário de vacinação
- `src/agents/agenteDoacao.ts` → lidar com pagamentos via Pix
- `src/tools/notificacaoEmail.ts` → envio de alertas internos

Fluxo inicial:
1. Usuário envia mensagem no WhatsApp via EvolutionAPI.
2. Sistema pergunta: "Deseja cadastrar pet, registrar vacinação ou doar?".
3. Dependendo da resposta, direcionar para o agente correto.

Configurações:
- Usar `.env` para chaves de API (WhatsApp EvolutionAPI, Pix, SMTP).
- O projeto deve rodar com `npm run dev`.```

Com esse `claude.md`, o Claude Code vai ler as instruções e já criar:

* `src/agents/agenteCadastro.ts`
* `src/agents/agenteVacinacao.ts`
* `src/agents/agenteDoacao.ts`
* `src/tools/notificacaoEmail.ts`
  e configurar os arquivos principais.

---

**INEMA** · 2025-08-30

Essa é uma dúvida essencial.

O **Claude Code não lê qualquer arquivo** – ele segue convenções específicas.

---

### Arquivo principal que ele lê

* O padrão é **`claude.md`**
* Esse é o **arquivo mestre** que o CLI reconhece e usa como blueprint do projeto.

---

### Outros formatos possíveis

1. **`claude.md`** → padrão principal, markdown com descrição em linguagem natural.
2. **`claude.config.json`** → arquivo de configuração formal (estrutural, com chaves/valores).

   * Esse é mais técnico, para ajustes finos (ex.: qual modelo usar, diretórios, etc.).
3. **`README.md`** → ele pode gerar/atualizar, mas não é interpretado como instrução, apenas documentação.

---

### E se for outro nome?

* Se você colocar, por exemplo, `meuprojeto.md` → **ele não lê automaticamente**.
* O CLI só olha para `claude.md` (ou `claude.config.json`) como **ponto de verdade**.

---

### Resumindo

* **Tem que ser `claude.md`** (ou `claude.config.json`).
* Qualquer outro nome/arquivo ele ignora.

---

**INEMA** · 2025-08-30

Isso é um ponto chave do Claude Code.

Sim — o **Claude Code consegue se basear em um arquivo `claude.md`** para gerar e organizar o projeto.
Esse arquivo funciona como um **guia em linguagem natural + instruções técnicas**, onde você descreve:

* o que o projeto deve fazer,
* quais agentes/funções precisa,
* fluxos de entrada/saída,
* restrições ou integrações.

---

### Como funciona na prática

1. Você cria um diretório vazio (ex: `meuprojeto/`).
2. Coloca dentro dele um **`claude.md`** com sua especificação (pode ser em texto corrido, estilo prompt).
3. Ao rodar:

```npx create-claude@latest```

o CLI vai **ler o `claude.md`**, interpretar e gerar automaticamente os arquivos obrigatórios (`package.json`, `tsconfig.json`, `claude.config.json`, `src/`, etc.) **baseados nas instruções do markdown**.

---

### Diferença entre usar `claude.md` ou não

* **Sem `claude.md`** → ele gera um boilerplate padrão (estrutura mínima, exemplo de agente, hello world).
* **Com `claude.md`** → ele personaliza o projeto conforme o que você descreveu no markdown.

---

### Exemplo de `claude.md` simples

```# Projeto Claude Code: Chatbot ONG Pets

Quero um chatbot para WhatsApp via Evolution API.
Funções principais:
- Cadastro de pets perdidos e achados
- Controle de vacinação
- Doações via Pix
- Notificações internas por e-mail

Fluxo inicial:
- Usuário envia mensagem → sistema pergunta se é cadastro de pet, vacinação ou doação.
- Cada fluxo deve ter um agente separado no diretório `src/agents/`.```

Se você deixar só isso no diretório e rodar `npx create-claude@latest`, ele monta a estrutura inicial já configurada para esse caso.

---

**INEMA** · 2025-08-30

**create-claude\****@latest** gera automaticamente no **Windows** (após rodar `npx create-claude@latest nome-do-projeto`).

---

### Estrutura inicial criada pelo Claude Code

Quando o comando roda, ele cria uma **pasta com o nome do projeto** (exemplo: `ccode1/`).
Dentro dela, os arquivos e diretórios obrigatórios são:

```ccode1/
│
├─ package.json        → metadados e dependências do projeto
├─ tsconfig.json       → configuração do TypeScript
├─ claude.config.json  → configuração do Claude Code
├─ .gitignore          → arquivos/pastas ignorados pelo Git
├─ README.md           → instruções básicas do projeto
│
├─ src/                → diretório do código-fonte
│   ├─ index.ts        → ponto de entrada (main)
│   ├─ agents/         → modelos/fluxos de agentes
│   ├─ tools/          → ferramentas customizadas
│   └─ routes/         → rotas (se usar API/servidor)
│
└─ node_modules/       → criado automaticamente pelo npm/yarn/pnpm```

---

### Observações importantes

* S**empre cria:** p`ackage.json,` t`sconfig.json,` c`laude.config.json,` .`gitignore,` R`EADME.md,` s`rc/.`
* n**ode\_modules **só aparece depois que você rodar n`pm install `(ou o gerenciador equivalente).
* Dentro de s`rc/ `o mínimo é um i`ndex.ts,` mas dependendo da flag/template escolhido no assistente, podem vir já subpastas como a`gents/ `e t`ools/.`
* Se você usar a opção de e**xemplo pronto,** ele adiciona exemplos em s`rc/agents/ `(como `helloAgent.ts`).

---

**INEMA** · 2025-08-30

Rode o claude no **PowerShell**.

---

**INEMA** · 2025-08-30

Para instalar e rodar o **Claude Code** no Windows, siga este passo a passo direto:

### Passo 1 – Instalar o Node.js

1. Acesse: [https://nodejs.org](https://nodejs.org/)
2. Baixe a versão **LTS** (recomendada).
3. Execute o instalador e vá clicando em **Next → Next → Finish**.

### Passo 2 – Abrir o Terminal

* Pressione **Win + R**, digite `cmd` e aperte **Enter** (Prompt de Comando).
* Ou abra o **PowerShell**.

### Passo 3 – Verificar se o Node.js foi instalado

Digite no terminal:

```node -v```

Se aparecer a versão (ex: `v20.x`), está ok.

### Passo 4 – Criar um novo projeto com Claude Code

No terminal, vá até a pasta onde quer criar o projeto (exemplo: Documentos) e rode:

```npx create-claude@latest```

### Passo 5 – Seguir as instruções do assistente

* Ele vai pedir o **nome do projeto**.
* Criar os arquivos básicos automaticamente.

---

**INEMA** · 2025-08-30

Instalar o Claude Code no Windows

---

**INEMA** · 2025-08-30

https://chatgpt.com/c/68b3754e-90f0-8326-be6b-0abb375fee5f
