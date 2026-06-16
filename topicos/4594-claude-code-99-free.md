# Claude Code 99% Free

> Tópico 4594 · 9 mensagens úteis de 25 totais

---

**INEMA** · 2026-04-07

export ANTHROPIC_BASE_URL=http://localhost:11434
export ANTHROPIC_AUTH_TOKEN=ollama
export ANTHROPIC_MODEL=qwen3.5
claude

---

**INEMA** · 2026-04-07

vc pode usar o ccr ou o litellm e ter um system prompt para isso

---

**King** · 2026-04-06

O PROPRIO CLAUDE CONSEGUE ESCOLHER A MELHOR OPÇAO PARA DETERMINADA AÇAO QUE IREI FAZER??

---

**INEMA** · 2026-04-05

https://youtu.be/MCdtVQknPO4

---

**INEMA** · 2026-04-05

Você configura em **2 lugares possíveis**:

---

# ✅ 1. Arquivo de configuração do Claude Code (RECOMENDADO)

Caminho:

```~/.claude/settings.json```

Ou dentro do projeto:

```.claude/settings.local.json```

Exemplo (OpenRouter):

```{
  "env": {
    "ANTHROPIC_BASE_URL": "https://openrouter.ai/api",
    "ANTHROPIC_AUTH_TOKEN": "sua-api-key",
    "ANTHROPIC_API_KEY": "",
    "ANTHROPIC_MODEL": "qwen/qwen3-coder:free",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "qwen/qwen3-coder:free",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "qwen/qwen3-coder:free",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "qwen/qwen3-coder:free",
    "ANTHROPIC_SMALL_FAST_MODEL": "qwen/qwen3-coder:free",
    "CLAUDE_CODE_SUBAGENT_MODEL": "qwen/qwen3-coder:free"
  }
}```

👉 Esse é o jeito mais seguro e permanente.

---

# ✅ 2. Variáveis de ambiente (terminal)

Você pode configurar direto no terminal:

### Linux / Mac

```export ANTHROPIC_BASE_URL="https://openrouter.ai/api"
export ANTHROPIC_AUTH_TOKEN="sua-api-key"
export ANTHROPIC_MODEL="qwen/qwen3-coder:free"```

### Windows (PowerShell)

```setx ANTHROPIC_BASE_URL "https://openrouter.ai/api"
setx ANTHROPIC_AUTH_TOKEN "sua-api-key"```

👉 Isso vale só para a sessão (ou até reiniciar, dependendo do método)

---

# 🔥 Para Ollama (local)

Você muda para:

```export ANTHROPIC_BASE_URL="http://localhost:11434"
export ANTHROPIC_AUTH_TOKEN="ollama"```

Ou simplesmente:

```ollama launch claude```

---

# ⚠️ ERRO MAIS COMUM

Se você **não configurar TODOS os modelos**, o Claude:
→ usa modelos pagos escondidos
→ e você pode ser cobrado sem perceber

---

# 🧠 Resumo simples

* Quer fixo → usa `settings.json`
* Quer testar rápido → usa terminal
* Local → aponta para `localhost`
* Nuvem → aponta para `openrouter`

---

**INEMA** · 2026-04-05

Como usar o **Claude Code de graça ou muito mais barato** trocando o modelo padrão por alternativas. A ideia central é que o Claude Code é só a interface (“carro”) e você pode trocar o modelo (“motor”).

Existem dois métodos principais:

**1. Modelo local (Ollama)**

* Você roda a IA no seu próprio computador
* Custo zero por uso (sem pagar por token)
* Total privacidade e uso offline
* Depende do seu hardware (pode ser lento ou limitado)
* Precisa baixar e configurar os modelos

**2. Modelos na nuvem (OpenRouter)**

* Usa modelos gratuitos via API
* Mais rápido e geralmente melhor que local
* Não precisa de hardware potente
* Tem limites de uso (requisições/dia)
* Precisa configurar variáveis corretamente para evitar cobranças

---

**Conceitos importantes:**

* Modelos **open source** são gratuitos e podem rodar localmente
* Modelos **fechados** (como Claude oficial) são mais poderosos, mas pagos
* A diferença entre eles está diminuindo

---

**Trade-offs principais:**

* Local → mais privado e barato, porém mais lento
* Nuvem → mais rápido e melhor, porém com limites
* Não existe “totalmente grátis” sem algum custo indireto (hardware ou limites)

---

**Quando usar modelos gratuitos:**

* Tarefas simples ou repetitivas
* Resumos, organização, buscas
* Código básico ou suporte leve
* Quando você atingiu limites do plano pago

---

**Cuidados:**

* Alguns modelos não funcionam perfeitamente com todas as ferramentas
* Podem ter menos contexto (memória)
* Configuração errada pode gerar cobrança sem perceber

---

**Resumo final:**
Você consegue usar Claude Code praticamente de graça trocando o modelo — com **Ollama (local)** ou **OpenRouter (nuvem)** — mas sempre equilibrando custo, desempenho e praticidade.

---

**INEMA** · 2026-04-05

**Como usar o código Claude com 99% de desconto (2 métodos)
**
Duas maneiras diferentes de executar o Claude Code totalmente de graça.

O primeiro método usa o Ollama para executar modelos de código aberto localmente em sua própria máquina, e o segundo usa o Open Router para acessar modelos gratuitos na nuvem.|

Abordo tudo, desde o download e a configuração de modelos até as vantagens e desvantagens entre o uso local e na nuvem, e quando é realmente preferível usar modelos de código aberto em vez de algo como o Opus.

"ANTHROPIC_BASE_URL": "https://openrouter.ai/api",
"ANTHROPIC_AUTH_TOKEN": "YOUR OPEN ROUTER API KEY",
"ANTHROPIC_API_KEY": "",
"ANTHROPIC_MODEL": "openrouter/free",
"ANTHROPIC_DEFAULT_SONNET_MODEL": "openrouter/free",
"ANTHROPIC_DEFAULT_OPUS_MODEL": "openrouter/free",
"ANTHROPIC_DEFAULT_HAIKU_MODEL": "openrouter/free",
"ANTHROPIC_SMALL_FAST_MODEL": "openrouter/free",
"CLAUDE_CODE_SUBAGENT_MODEL": "openrouter/free"

---

**INEMA** · 2026-04-05

Falam muito de usar o Claude Code Free, mas temos q pensar no Assunto, aqui um video do Nate, e eu reflito sobre o assunto

---

**INEMA** · 2026-04-05

Claude Code 99% Free
