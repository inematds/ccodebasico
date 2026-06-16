# Remote Control

> Tópico 3382 · 6 mensagens úteis de 18 totais

---

**INEMA** · 2026-02-25

Para **desativar o Remote Control depois de conectado**, você tem algumas opções simples:

---

# ✅ 1️⃣ Encerrar a sessão no terminal (forma principal)

No terminal onde o Claude Code está rodando:

### 👉 Opção A: Fechar a sessão

Pressione:

```Ctrl + C```

Isso encerra a sessão completamente — o remote morre junto.

---

### 👉 Opção B: Usar comando dentro da sessão

Se estiver dentro da interface do Claude Code, você pode tentar:

```/exit```

ou simplesmente fechar o processo.

---

# ✅ 2️⃣ Fechar o terminal

Se você:

* Fechar o terminal
* Encerrar o processo do Claude
* Desligar o computador
* Perder conexão por ~10 minutos

👉 A sessão remota será automaticamente desconectada.

---

# ✅ 3️⃣ Encerrar pelo navegador/app

Na interface web ou no celular:

* Saia da sessão
* Ou feche a aba

⚠️ Isso só desconecta o cliente remoto.
Se o terminal continuar rodando, a sessão ainda existe.

---

# 🔐 Importante (segurança)

Se você compartilhou o link ou QR code por engano:

👉 **Encerre o processo no terminal imediatamente (Ctrl + C)**
Isso invalida a sessão.

---

# 🎯 Resumo rápido

Quer matar o Remote Control de vez?

➡️ **Ctrl + C no terminal onde ele foi iniciado.**

Pronto.

---

**INEMA** · 2026-02-25

### 📌 O que é o *Remote Control*

*Remote Control* é um recurso que permite **continuar uma sessão do Claude Code rodando localmente no seu computador a partir de outro dispositivo** (telefone, tablet ou navegador) — mantendo tudo sincronizado. Ele funciona pela **interface web do Claude ou app móvel**, mas a execução do código continua acontecendo **na sua máquina**. 

### 🧠 Principais ideias

**Como funciona**

* Você inicia uma sessão com `claude remote-control` ou usando o comando interno `/remote-control` dentro de uma sessão existente no Claude Code CLI.
* O terminal mostra um **URL de sessão e um QR code** que permite conectar de outro dispositivo.
* Ao conectar, a sessão aparece na interface do **claude.ai/code** ou no **app do Claude (iOS/Android)** e você pode enviar mensagens, ver saídas e interagir. 
**O que isso permite**

* Continuar tarefas iniciadas no computador no seu **celular ou outro dispositivo**. 
* A sessão fica **sincronizada** entre terminal e dispositivo remoto. ([Claude][1])
* Os processos continuam rodando **na sua máquina**, usando seu ambiente local (filesystem, ferramentas, etc.). 

### ⚙️ Requisitos e condições

* Disponível como **prévia de pesquisa** para planos **Pro e Max** (não está disponível em todos os planos). 
* Sua máquina deve continuar conectada à internet e o terminal com o Claude Code em execução.

### 🔐 Segurança & Conexão

* A conexão remota é feita **sem abrir portas no seu computador**; o terminal faz **requisições HTTPS de saída** e a Anthropic gerencia o túnel seguro entre o cliente remoto e sua sessão local. 

### 📊 Diferença para Claude Code na web

* **Remote Control** mantém tudo rodando localmente no seu computador, com acesso remoto para interação.
* **Claude Code on the web** roda na infraestrutura da Anthropic no cloud, não na sua máquina. 

Se você quiser, posso também te dar os **comandos exatos para começar uma sessão remota** ou explicar as **limitações** desse recurso!

---

**INEMA** · 2026-02-25

claude remote-control

---

**INEMA** · 2026-02-25

https://venturebeat.com/orchestration/anthropic-just-released-a-mobile-version-of-claude-code-called-remote

---

**INEMA** · 2026-02-25

https://code.claude.com/docs/en/remote-control

---

**INEMA** · 2026-02-25

Remote Control CC
