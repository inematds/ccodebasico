# CLAUDE CODE - CCR - FREE

> Tópico 3767 · 9 mensagens úteis de 26 totais

---

**INEMA** · 2026-03-12

https://github.com/musistudio/claude-code-router

---

**INEMA** · 2026-03-12

Se você quiser usar **API Key do Claude (Anthropic)** em vez de login OAuth, o **Claude Code não guarda a chave em arquivo próprio**.
Ele espera que a chave esteja em **variável de ambiente**.

Ou seja: **você coloca a chave no sistema**, não dentro do Claude Code.

---

# ✅ Forma correta (recomendado)

Definir a variável:

```export ANTHROPIC_API_KEY=sk-ant-xxxx```

Depois rodar:

```claude code```

O Claude Code automaticamente lê:

```ANTHROPIC_API_KEY```

---

# 📍 Onde colocar essa variável

## Mac / Linux (mais comum)

Editar o arquivo do shell:

```nano ~/.zshrc```

ou

```nano ~/.bashrc```

Adicionar:

```export ANTHROPIC_API_KEY=sk-ant-xxxx```

Depois recarregar:

```source ~/.zshrc```

---

# 📦 Alternativa: usar `.env`

Se estiver em um projeto:

Arquivo:

```.env```

Conteúdo:

```ANTHROPIC_API_KEY=sk-ant-xxxx```

Mas o Claude Code só verá isso se você carregar o `.env`.

---

# 📊 Como o Claude Code encontra a chave

Fluxo interno:

```Claude Code
     ↓
procura variável ANTHROPIC_API_KEY
     ↓
usa chave na API Anthropic
     ↓
Claude model```

---

# 🔐 Dica de segurança

Nunca coloque chave em:

* código
* GitHub
* README
* prints

Sempre usar:

```variável de ambiente```

---

# 🧠 Exemplo completo

```export ANTHROPIC_API_KEY=sk-ant-123456
export ANTHROPIC_BASE_URL=https://api.anthropic.com

claude code```

---

✅ **Resumo simples**

Se usar **API key do Claude**, coloque em:

```ANTHROPIC_API_KEY```

como **variável de ambiente do sistema**.

---

**INEMA** · 2026-03-12

Segurança das **API keys** é muito importante quando você usa ferramentas como **Claude Code**. Vou explicar de forma simples e prática. 🔐

---

# 🧠 Regra principal

**Nunca coloque API keys direto no código.**

Errado ❌

```api_key = "sk-123456789"```

Porque:

* pode ir para GitHub
* outras pessoas podem ver
* bots roubam chaves automaticamente

---

# ✅ Método 1 — Variáveis de ambiente (mais comum)

Você guarda a chave no sistema, não no código.

Exemplo:

```export ANTHROPIC_API_KEY=sk-xxxx```

ou

```export OPENROUTER_API_KEY=sk-xxxx```

Depois o programa lê automaticamente.

📍 Onde fica armazenado?

Depende do sistema:

* **Linux / Mac**

  * `.bashrc`
  * `.zshrc`
  * `.profile`

Exemplo:

```nano ~/.zshrc```

Adicionar:

```export OPENROUTER_API_KEY=sk-xxxx```

---

# 📦 Método 2 — arquivo `.env`

Muito usado em projetos.

Arquivo:

```.env```

Exemplo:

```ANTHROPIC_API_KEY=sk-xxxx
OPENROUTER_API_KEY=sk-xxxx```

E no código você carrega:

```from dotenv import load_dotenv```

⚠️ importante:

Sempre colocar no `.gitignore`

```.env```

---

# 🔐 Método 3 — Secret Manager (produção)

Usado em servidores e empresas.

Exemplos:

* AWS Secrets Manager
* Google Secret Manager
* Hashicorp Vault
* GitHub Secrets

Fluxo:

```app → secret manager → API key```

Vantagens:

* criptografia
* rotação de chave
* controle de acesso

---

# 🧩 Para Claude Code especificamente

O jeito mais simples é **variável de ambiente**.

Exemplo:

```export ANTHROPIC_API_KEY=xxxxx
export OPENROUTER_API_KEY=xxxxx```

Se usar **Claude Code Router**:

```~/.claude-code-router/config.json```

Mas esse arquivo deve ter **permissão privada**:

```chmod 600 ~/.claude-code-router/config.json```

---

# 📊 Comparação

| método            | segurança | uso         |
| ----------------- | --------- | ----------- |
| variável ambiente | ⭐⭐⭐       | CLI / local |
| .env              | ⭐⭐        | projetos    |
| secret manager    | ⭐⭐⭐⭐      | produção    |

---

# ⚠️ Erros comuns

Nunca faça:

* subir `.env` no GitHub
* colocar chave em código
* mandar chave em screenshot
* deixar chave em README

Bots escaneiam GitHub **em segundos**.

---

# 🎯 Regra simples

Use:

```local → variáveis ambiente
projeto → .env
produção → secret manager```

---

**INEMA** · 2026-03-12

USAR O CLAUDE CODE - BASICO


# 🧠 Regra básica do Claude Code

Ele sempre usa **duas variáveis**:

```API KEY
API URL```

Ou seja:

```Claude Code → URL da API → modelo```

---

# 📦 Caso 1 — usar Claude (Anthropic)

Você configura:

```export ANTHROPIC_API_KEY=sua_chave
export ANTHROPIC_BASE_URL=https://api.anthropic.com```

Fluxo:

```Claude Code
     ↓
Anthropic API
     ↓
Claude model```

---

# 📦 Caso 2 — usar OpenRouter

Você muda **apenas a URL e a chave**.

```export ANTHROPIC_API_KEY=sua_chave_openrouter
export ANTHROPIC_BASE_URL=https://openrouter.ai/api```

Fluxo:

```Claude Code
     ↓
OpenRouter
     ↓
GPT / Gemini / DeepSeek```

---

# 📦 Caso 3 — usar Router (melhor)

Aqui o Claude Code fala com **um servidor local**.

```Claude Code
     ↓
localhost router
     ↓
Anthropic ou OpenRouter```

Configuração:

```export ANTHROPIC_BASE_URL=http://localhost:3456```

E o router decide qual API usar.

---

# 🔑 Em resumo

Claude Code só precisa saber:

```1️⃣ qual chave usar
2️⃣ qual URL da API usar```

Exemplo mental:

```Claude Code
   |
   | chave API
   |
   ↓
API endpoint
   ↓
modelo```

---

# ⚡ Regra universal

Qualquer serviço que seja **compatível com API da Anthropic** funciona.

Exemplos:

* OpenRouter
* LiteLLM
* Claude Code Router
* servidores proxy

---

✅ **Resumo em uma frase**

> Para qualquer API falar com Claude Code você só precisa definir **a chave da API e o endpoint da API**.

---

**INEMA** · 2026-03-12

Você pode **continuar usando sua assinatura do Claude normalmente** e também **usar modelos do OpenRouter**, trocando com o comando `/model`.

O jeito mais limpo de fazer isso é **usar o Claude Code Router (CCR)**, porque ele permite **alternar provedores**.

---

# 🧠 Como fica o funcionamento

Você terá **dois provedores**:

* **Anthropic** → usa sua assinatura Claude
* **OpenRouter** → usa créditos do OpenRouter

Fluxo:

```Claude Code
     ↓
Claude Code Router
     ↓
┌───────────────┬───────────────┐
│ Anthropic     │ OpenRouter    │
│ Claude models │ outros modelos│
└───────────────┴───────────────┘```

Assim você pode trocar o modelo **em tempo real**.

---

# ⚙️ Passo 1 — instalar Claude Code Router

```brew install claude-code-router```

ou

```npm install -g claude-code-router```

---

# ⚙️ Passo 2 — criar API key no OpenRouter

[https://openrouter.ai/settings/keys](https://openrouter.ai/settings/keys)

Copie a key.

---

# ⚙️ Passo 3 — criar config

Arquivo:

```~/.claude-code-router/config.json```

Exemplo:

```{
  "providers": {
    "anthropic": {
      "api_key": "ANTHROPIC_API_KEY"
    },
    "openrouter": {
      "api_key": "OPENROUTER_API_KEY",
      "base_url": "https://openrouter.ai/api/v1"
    }
  }
}```

---

# ⚙️ Passo 4 — ativar router

```ccr start
eval "$(ccr activate)"```

---

# 🚀 Passo 5 — usar no Claude Code

Agora você pode alternar modelos.

### Claude (sua assinatura)

```/model claude-3-7-sonnet```

ou

```/model claude-3-opus```

---

### Modelos do OpenRouter

Exemplo:

```/model openrouter,deepseek/deepseek-reasoner```

ou

```/model openrouter,google/gemini-2.0-flash```

ou

```/model openrouter,meta-llama/llama-3.3-70b```

---

# 🔥 Exemplo de workflow real

Coding pesado:

```/model claude-3-7-sonnet```

Debug rápido:

```/model openrouter,deepseek-chat```

Explicação barata:

```/model openrouter,gpt-4o-mini```

---

# 💰 Vantagem enorme

Claude Code fica **muito mais barato**.

Exemplo típico:

| tarefa        | modelo        |
| ------------- | ------------- |
| arquitetura   | Claude Sonnet |
| coding grande | Claude        |
| refatoração   | DeepSeek      |
| explicação    | Gemini        |

Você economiza **70–90%**.

---

**INEMA** · 2026-03-12

---

# 🔎 Comparação dos 3 métodos


# 1️⃣ Método oficial (OpenRouter docs)

### Como funciona

Você **só muda o endpoint da API**.

```export ANTHROPIC_BASE_URL=https://openrouter.ai/api
export ANTHROPIC_API_KEY=OPENROUTER_KEY```

Claude Code continua achando que está falando com **Anthropic**, mas na verdade fala com **OpenRouter**.

### Fluxo

```Claude Code
     ↓
OpenRouter
     ↓
Modelo escolhido```

### Quando usar

✅ setup rápido
✅ uso pessoal
✅ testes simples

---

# 2️⃣ Método Hypereal (proxy)

### Como funciona

Um **proxy/roteador de API** intercepta as chamadas.

Fluxo:

```Claude Code
     ↓
Proxy
     ↓
OpenRouter
     ↓
Modelo```

### Vantagens

* mais controle
* pode mudar comportamento da API
* pode adicionar lógica

### Quando usar

✅ automações
✅ pipelines
✅ uso com agentes

---

# 3️⃣ Método CCR (Claude Code Router)

Esse é o **mais poderoso**.

Ele instala um **router local chamado CCR**.

Fluxo:

```Claude Code
     ↓
Claude Code Router (local)
     ↓
OpenRouter
     ↓
Modelo```

### O router permite

* trocar modelo no comando
* fallback automático
* roteamento inteligente
* múltiplos provedores

Exemplo:

```/model openrouter,deepseek/deepseek-reasoner```

### Quando usar

✅ dev avançado
✅ usar muitos modelos
✅ custo otimizado
✅ agentes de código

---

# ⚡ Diferença prática usando Claude Code

| Situação                | Melhor método      |
| ----------------------- | ------------------ |
| só quer usar OpenRouter | **método oficial** |
| quer flexibilidade      | **proxy**          |
| quer sistema completo   | **CCR router**     |

---

# 🧠 Resumo simples

**OpenRouter docs**
→ muda endpoint (mais simples)

**Hypereal**
→ usa proxy intermediário

**Bossolani**
→ usa router local completo

---

✅ **Conclusão:**
Todos fazem o Claude Code usar outros modelos, mas o **CCR (Bossolani)** é o que transforma o Claude Code em **uma plataforma multi-modelo completa**.

---

**INEMA** · 2026-03-12

# 🧠 Como o Claude Code funciona normalmente

O **Claude Code CLI** conversa com a **API da Anthropic** usando **uma chave API**.

Fluxo normal:

```Claude Code
     ↓
Anthropic API
     ↓
Claude model (Sonnet / Opus / etc)```

Ele usa geralmente duas variáveis de ambiente:

```ANTHROPIC_API_KEY
ANTHROPIC_BASE_URL```

Normalmente:

```ANTHROPIC_BASE_URL=https://api.anthropic.com```

---

# 🔑 Então o Claude Code sempre fala com uma chave?

Sim.

Ele sempre envia algo como:

```Authorization: Bearer SUA_API_KEY```

Para o endpoint da API.

---

# ⚙️ O que muda quando usamos OpenRouter

O OpenRouter cria **uma API compatível com Anthropic**.

Então você pode fazer o Claude Code pensar que ainda está falando com Anthropic.

Fluxo:

```Claude Code
     ↓
OpenRouter API
     ↓
modelo escolhido```

Configuração:

```ANTHROPIC_BASE_URL=https://openrouter.ai/api
ANTHROPIC_API_KEY=OPENROUTER_KEY```

Agora:

* Claude Code manda requisição
* OpenRouter recebe
* OpenRouter decide qual modelo usar

---

# 🔀 O problema disso

Se você fizer isso, o Claude Code **não usa mais sua conta Claude**.

Ele passa a usar **só o OpenRouter**.

Por isso precisamos de algo melhor.

---

# 🧩 Como funciona o Claude Code Router (CCR)

O CCR cria **um servidor local intermediário**.

Fluxo:

```Claude Code
     ↓
localhost (Claude Code Router)
     ↓
┌───────────────┬───────────────┐
│ Anthropic     │ OpenRouter    │
│ Claude models │ outros modelos│
└───────────────┴───────────────┘```

O Claude Code **acha que está falando com Anthropic**, mas na verdade fala com o router.

---

# 📡 O router decide para onde mandar

Quando você muda modelo:

```/model claude-3-7-sonnet```

Router envia para:

```Anthropic API```

Quando você faz:

```/model openrouter,deepseek/deepseek-reasoner```

Router envia para:

```OpenRouter API```

---

# 🔑 Então existem duas chaves

No router:

```ANTHROPIC_API_KEY
OPENROUTER_API_KEY```

E ele usa a certa dependendo do modelo.

---

# 📦 Exemplo real de requisição

Se você usar:

```/model claude-3-7-sonnet```

router faz:

```POST api.anthropic.com
Authorization: ANTHROPIC_API_KEY```

---

Se usar:

```/model openrouter,deepseek```

router faz:

```POST openrouter.ai/api
Authorization: OPENROUTER_API_KEY```

---

# 🎯 Resumo simples

Claude Code **sempre fala com uma API**.

| situação          | para quem fala                   |
| ----------------- | -------------------------------- |
| normal            | Anthropic                        |
| OpenRouter direto | OpenRouter                       |
| com router        | Router → Anthropic ou OpenRouter |

---

**INEMA** · 2026-03-12

CLAUDE CODE - CCR  - FREE

---

**INEMA** · 2026-03-12

https://chatgpt.com/c/69b25908-0dbc-832f-8dd2-aa5e067f02ac
