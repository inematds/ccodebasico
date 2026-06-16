# Criando Agentes com TRIGGER DEV

> Tópico 3224 · 3 mensagens úteis de 14 totais

---

**INEMA** · 2026-02-20

No vídeo **ele não mostra rodando `npx` ou `npm` manualmente**, mas sim — **por baixo dos panos isso existe**.

Deixa eu explicar melhor:

---

# 🧠 O que está acontecendo de verdade

Quando você usa **Cloud Code (Claude Code)**:

* Ele cria o projeto
* Ele gera os arquivos TypeScript
* Ele instala dependências automaticamente
* Ele roda o servidor local

Ou seja:

👉 **O Cloud Code executa os comandos npm/npx para você.**

Você não vê ele digitando:

```npm install
npx trigger dev```

Mas isso está acontecendo internamente.

---

# 🔹 Se você fosse fazer manualmente (sem Cloud Code)

Você precisaria algo como:

```npm init -y
npm install @trigger.dev/sdk
npx trigger dev```

E depois conectar ao projeto com o Project Ref.

---

# 🔹 Por que no vídeo não aparece?

Porque o foco é:

> “Você não precisa mais escrever código nem configurar tudo manualmente.”

O Cloud Code abstrai:

* Setup de projeto
* Instalação de dependências
* Estrutura de pastas
* Configuração inicial

---

# 🔥 Resumo direto

Ele não digita `npm` ou `npx` no vídeo
Mas sim — o projeto depende de Node.js e esses comandos estão rodando por trás.

---

**INEMA** · 2026-02-20

* **Claude Code** → para transformar instruções em inglês simples em código TypeScript.
* **Trigger.dev** → para rodar esse código automaticamente na nuvem (com agendamento, retries e monitoramento).

Aqui está o resumo direto ao ponto:

---

## 🔹 Ideia Principal

Você descreve uma automação em linguagem natural →
Claude Code escreve o código →
Você envia para o Trigger.dev →
A automação roda 24/7 na nuvem sozinha.

Sem precisar deixar seu computador ligado.

---

## 🔹 Por que usar Trigger.dev?

Ele permite:

* ⏰ Rodar tarefas em horários programados (cron)
* 🔁 Repetir automaticamente se der erro
* 🧩 Dividir workflows complexos em partes
* 👀 Monitorar execuções em tempo real
* 🧪 Separar ambiente de desenvolvimento e produção

---

## 🔹 Exemplos mostrados no guia

### 1️⃣ AI News Digest

* Verifica se um canal do YouTube postou vídeo novo
* Se sim, gera resumo, conceitos, quotes e estatísticas
* Se não, não faz nada

---

### 2️⃣ Company Research Agent (com ClickUp)

Um agente que:

* Fica monitorando uma lista no ClickUp
* Quando uma nova empresa é adicionada:

  * Faz pesquisa na web
  * Gera um relatório detalhado
  * Responde perguntas adicionais depois

Esse é um agente “não determinístico”, ou seja:
Ele decide sozinho quais ferramentas usar e quando parar a pesquisa.

---

## 🔹 Estrutura do Projeto

O projeto fica mais ou menos assim:

```.env                 → chaves de API
CLAUDE.md            → instruções para o Claude
trigger-ref.md       → referência da API do Trigger
src/trigger/         → tarefas em TypeScript```

Cada arquivo `.ts` é uma automação ou agente.

---

## 🔹 Passo a passo resumido

1. Criar projeto no VS Code
2. Baixar arquivos de configuração (CLAUDE.md e trigger-ref.md)
3. Dar um prompt para o Claude Code
4. Revisar o plano que ele cria
5. Configurar variáveis de ambiente (.env)
6. Conectar ao Trigger.dev
7. Testar no ambiente de desenvolvimento
8. Publicar para produção (via GitHub recomendado)

---

## 🔹 Conceitos importantes

### ✅ Determinístico

Fluxo fixo: passo 1 → 2 → 3 → 4

### 🤖 Não determinístico (Agente)

Tem múltiplas ferramentas e decide o que fazer.

---

## 🔹 Mensagem final do guia

Você não precisa mais escrever código manualmente.
Seu papel agora é:

* Dar instruções claras
* Revisar o plano
* Testar
* Garantir qualidade

O “skill” agora é saber orientar a IA corretamente.

---

**INEMA** · 2026-02-20

https://www.youtube.com/watch?v=SlNqHexxFl4
