# /buddy e os Tamagochis

> Tópico 4478 · 2 mensagens úteis de 13 totais

---

**INEMA** · 2026-04-02

## 🚀 Como tirar proveito do `/buddy`

Pense nele como um **modo “trabalhar junto”**, não só “executar”.

### 1. Use como pair programming de verdade

Em vez de dar comandos secos, faça coisas como:

* “buddy, vamos refatorar esse código?”
* “buddy, qual a melhor forma de estruturar isso?”
* “buddy, explica antes de mudar”

👉 Isso força o Claude a:

* Raciocinar com você
* Não sair executando direto
* Te ensinar no processo

---

### 2. Peça planos antes de executar

Exemplo:

* “buddy, me mostra o plano antes de rodar”
* “buddy, quais são os riscos disso?”

👉 Isso evita cagadas (principalmente com arquivos e git)

---

### 3. Use para debugging guiado

* “buddy, vamos debuggar isso juntos”
* “buddy, o que você acha que está errado?”

👉 Ele começa a investigar contigo, não só dar resposta final

---

### 4. Combine com tarefas maiores

Funciona muito bem para:

* Refatoração grande
* Arquitetura de projeto
* Migração (ex: JS → TS)
* Setup de ambiente

---

## 🧸 Sobre “tamagotchis” no Claude Code

Esse termo não é oficial da Anthropic — normalmente a galera usa isso pra se referir a:

👉 **personas / modos de comportamento do agente**

No caso do Claude Code, isso inclui:

* `/buddy` (colaborativo)
* modo padrão (mais executor)
* possivelmente outros modos dependendo da versão/CLI

---

## 🔄 Como “mudar os tamagotchis”

Depende da versão do Claude Code, mas geralmente:

### ✔️ Você troca via comandos

Exemplo:

* `/buddy` → ativa modo colaborativo
* sair dele → volta ao modo normal

Em algumas versões:

* `/mode`
* `/persona`
* `/reset`

---

## 🧩 Como acessar “outros”

Hoje, oficialmente, o principal é:

* `/buddy`

Outros “modos” podem aparecer como:

* flags na CLI
* configurações no config
* atualizações do cc

👉 Não existe ainda (oficialmente) um sistema tipo “escolher personagem” completo

---

## ⚠️ Dica importante

Se você quer “simular outros tamagotchis”, dá pra fazer assim:

Exemplo:

* “buddy, aja como um arquiteto sênior”
* “buddy, seja crítico e questione tudo”
* “buddy, só sugira, não execute nada”

👉 Isso muda MUITO o comportamento

---

## ⚡ Resumão

* `/buddy` = modo colaborativo (pair programming)
* Melhor uso = pedir plano, discutir, iterar
* “Tamagotchis” = basicamente modos/personas
* Troca = via comandos tipo `/buddy` ou reset
* Dá pra customizar comportamento via prompt

---

**INEMA** · 2026-04-02

O `/buddy` no **Claude Code (cc)** da Anthropic é basicamente um **modo de colaboração assistida** — como se você tivesse um “par-programador” ativo dentro do terminal.

### 💡 Propósito principal

O `/buddy` serve para:

* **Guiar você passo a passo** em tarefas de código
* **Explicar decisões enquanto trabalha**
* **Sugerir melhorias em tempo real**
* **Ajudar a depurar (debug) de forma interativa**

---

### 🧠 Como ele funciona na prática

Quando você ativa o `/buddy`, o Claude deixa de ser só reativo e passa a agir mais como:

> “um colega de equipe que pensa junto com você”

Ele pode:

* Fazer perguntas antes de executar algo
* Explicar o que vai fazer e por quê
* Propor alternativas (“quer fazer assim ou assado?”)
* Ajudar a evitar erros antes de rodar comandos perigosos

---

### 🆚 Diferença para o modo normal

* **Modo normal:** você pede → ele executa/responde
* **/buddy****:** ele colabora → discute → sugere → executa com você

É mais **interativo e pedagógico**, menos “automático”.

---

### 🧑‍💻 Quando usar

Use `/buddy` quando:

* Está aprendendo algo novo
* Quer entender melhor o código (não só gerar)
* Está fazendo refatoração ou arquitetura
* Quer mais segurança antes de rodar comandos

Evite se:

* Só quer executar algo rápido e direto

---

### ⚡ Resumindo

O `/buddy` transforma o Claude Code em um **pair programmer ativo**, focado em **colaboração, explicação e decisões conscientes**, em vez de só execução.
