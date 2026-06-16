# Ollama no Claude Code

> Tópico 4824 · 10 mensagens úteis de 18 totais

---

**INEMA** · 2026-04-07

gemma4:e2b   # leve (≈4GB RAM)
gemma4:e4b   # padrão (≈8GB RAM)
gemma4:26b   # intermediário (≈14GB RAM)
gemma4:31b   # topo (≈19GB RAM) ⭐ recomendado

---

**INEMA** · 2026-04-07

export ANTHROPIC_MODEL=gemma4:31b
ollama launch claude

---

**INEMA** · 2026-04-07

ollama pull gemma4:31b
ollama launch claude

---

**INEMA** · 2026-04-07

# 🧠 O que é `ollama serve`?

É o comando que **liga o “servidor local de IA” do Ollama**.

Quando você roda:

```ollama serve```

👉 Você está basicamente dizendo:

> “Fica rodando em segundo plano esperando requisições de IA aqui na minha máquina”

---

## 🔌 O que ele faz na prática

* Abre uma API em:

```http://localhost:11434```

* Permite que outros programas (tipo Claude Code) conversem com o modelo

* Mantém os modelos carregados na memória

---

## 💡 Analogia simples

* `ollama serve` = ligar o motor 🚗
* `ollama run gemma4` = dirigir
* `claude` = passageiro que usa o motor

---

# 🤔 E por que usar `ollama launch claude`?

Essa é a parte mais importante 👇

---

## ❌ Se você rodar só:

```claude```

👉 O Claude Code vai tentar:

* Conectar na API da Anthropic (internet)
* Usar modelos pagos (Sonnet / Opus)
* Cobrar uso 💸

---

## ✅ Já com:

```ollama launch claude```

👉 O Ollama faz automaticamente:

1. Redireciona o Claude Code pra sua máquina local
2. Faz o Claude achar que está falando com Anthropic
3. Usa o modelo local (ex: gemma4)
4. Zero custo 💰

---

## 🔧 O que esse comando faz por baixo dos panos

Equivale a isso:

```export ANTHROPIC_BASE_URL=http://localhost:11434
export ANTHROPIC_AUTH_TOKEN=ollama
export ANTHROPIC_MODEL=gemma4:31b
claude```

Ou seja:

👉 Ele **engana o Claude Code (no bom sentido 😄)** pra usar o Ollama

---

# 🧩 Quando usar cada um

| Comando                | Quando usar                            |
| ---------------------- | -------------------------------------- |
| `ollama serve`         | Quando quer rodar API manualmente      |
| `ollama run gemma4`    | Testar modelo direto                   |
| `claude`               | Usar Claude real (pago)                |
| `ollama launch claude` | Usar Claude Code com IA local (GRÁTIS) |

---

# ⚡ Resumo ultra simples

👉 `ollama serve`
= liga o servidor local de IA

👉 `claude`
= usa IA da internet (paga)

👉 `ollama launch claude`
= usa IA local (Gemma) dentro do Claude Code

---

# 🔥 Regra de ouro

Se você quer:

* 💸 não pagar → use `ollama launch claude`
* 🧠 melhor qualidade → use `claude` (oficial)
* ⚙️ controle manual → use `ollama serve`

---

**INEMA** · 2026-04-07

export ANTHROPIC_BASE_URL=http://localhost:11434
export ANTHROPIC_AUTH_TOKEN=ollama
export ANTHROPIC_MODEL=gemma4:31b 
claude

---

**INEMA** · 2026-04-07

export ANTHROPIC_BASE_URL=http://localhost:11434
export ANTHROPIC_AUTH_TOKEN=ollama
export ANTHROPIC_MODEL=qwen3.5
claude

---

**INEMA** · 2026-04-07

este é o comando para vc rodar cada vez q entrar no claude

---

**INEMA** · 2026-04-07

Você pode usar o Ollama com o Claude Code de duas formas: pela integração pronta do próprio Ollama, ou apontando manualmente o Claude Code para a API compatível com Anthropic do Ollama. A documentação oficial do Ollama hoje recomenda a integração `ollama launch claude`, que configura e inicia o Claude Code sem precisar editar arquivos de configuração nem definir variáveis manualmente. 

O caminho mais simples é este:

```# 1) instale o Ollama
# macOS: via app ou Homebrew
# Linux/Windows: baixe no site oficial

# 2) baixe um modelo
ollama pull qwen3.5

# 3) abra o Claude Code usando o Ollama
ollama launch claude```

O comando `ollama launch` existe justamente para “configurar e iniciar” integrações suportadas, e a página de integração do Claude Code confirma que ele funciona sobre a API Anthropic-compatible do Ollama. 

Se você quiser fazer manualmente, o Ollama expõe uma API compatível com Anthropic. Nesse caso, você inicia o servidor local do Ollama e depois aponta o Claude Code para `http://localhost:11434`. A documentação do Ollama confirma essa compatibilidade e cita explicitamente o Claude Code como um dos clientes suportados. 

Exemplo manual no macOS/Linux:

```ollama serve```

Em outro terminal:

```export ANTHROPIC_BASE_URL=http://localhost:11434
export ANTHROPIC_AUTH_TOKEN=ollama
export ANTHROPIC_MODEL=qwen3.5
claude```

Isso funciona porque o Ollama implementa a compatibilidade com a Messages API da Anthropic, permitindo que ferramentas como Claude Code conversem com modelos locais pelo endpoint do Ollama. ([Ollama][3])

Um detalhe importante: a própria documentação atual do Ollama, na integração com Claude Code, destaca exemplos com modelos como `qwen3.5`, `glm-5:cloud` e `kimi-k2.5:cloud`. Então, embora você possa testar outros modelos, a experiência tende a ser melhor com modelos de código ou modelos explicitamente recomendados pelo Ollama para esse fluxo. 

Se der erro, os problemas mais comuns são: Ollama não estar rodando, o modelo ainda não ter sido baixado, ou o Claude Code não estar instalado no sistema. O Ollama também oferece um menu interativo via `ollama` no terminal e mostra integrações suportadas em “More…”, além da referência de CLI para `ollama launch`. 

Se quiser, eu posso te passar agora um passo a passo exato para o seu sistema: macOS, Linux ou Windows.

[1]: https://docs.ollama.com/integrations/claude-code?utm_source=chatgpt.com "Claude Code - Ollama"
[2]: https://docs.ollama.com/api/anthropic-compatibility?utm_source=chatgpt.com "Anthropic compatibility - Ollama"
[3]: https://ollama.com/blog/claude?utm_source=chatgpt.com "Claude Code with Anthropic API compatibility · Ollama Blog"
[4]: https://docs.ollama.com/cli?utm_source=chatgpt.com "CLI Reference - Ollama"

---

**INEMA** · 2026-04-07

Ollama no Claude Code

---

**INEMA** · 2026-04-07

https://chatgpt.com/c/69d556b5-8f20-8328-85aa-e4bd2e44191b
