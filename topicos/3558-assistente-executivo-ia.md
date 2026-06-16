# Assistente Executivo IA

> Tópico 3558 · 3 mensagens úteis de 13 totais

---

**INEMA** · 2026-03-06

Esse sistema **se atualiza de três formas principais**: contexto, decisões e memória. Vou explicar de forma simples.

---

# 1️⃣ Atualização automática (Memória da IA)

O Claude Code mantém **memória persistente entre conversas**.

Ou seja, ele aprende:

* suas preferências
* padrões de trabalho
* estilo de escrita
* decisões recorrentes

Exemplo:

Você diz:

> “Lembre que eu sempre quero respostas em bullet points.”

Ele salva isso automaticamente.

Na próxima conversa ele **já aplica isso**.

---

# 2️⃣ Atualização manual de contexto

Alguns arquivos você atualiza manualmente quando sua realidade muda.

### 📂 `context/current-priorities.md`

Atualize quando seu foco mudar.

Exemplo:

```# Prioridades atuais

1. Lançar novo curso
2. Contratar assistente virtual
3. Automatizar atendimento```

---

### 📂 `context/goals.md`

Atualização **a cada trimestre**.

Exemplo:

```Q2 2026

Meta 1: faturar 200k
Meta 2: lançar produto X
Meta 3: crescer lista de e-mail```

---

# 3️⃣ Registro de decisões

Toda decisão importante vai aqui:

📂 `decisions/log.md`

Exemplo:

```[2026-03-05]

DECISÃO: usar ClickUp como gestor principal
RAZÃO: melhor integração com automações
CONTEXTO: organização da equipe```

Isso cria **memória estratégica do negócio**.

---

# 4️⃣ Atualização de projetos

Cada projeto tem uma pasta:

```projects/
   curso-ia/
   contratacao-va/```

O README dentro do projeto é atualizado conforme o progresso.

---

# 5️⃣ Skills (automação)

Quando você percebe algo repetitivo, cria uma **skill**.

Exemplo:

```.claude/skills/criar-post-linkedin/
SKILL.md```

Isso vira **automação reutilizável**.

---

# 6️⃣ Resumo de sessões

Após trabalhar com a IA, você pode registrar:

📂 `templates/session-summary.md`

Exemplo:

```O que foi feito
Decisões
Próximos passos```

---

# 📊 Resumo rápido

| Atualização       | Como acontece     |
| ----------------- | ----------------- |
| Memória           | automática        |
| Prioridades       | manual            |
| Metas trimestrais | manual            |
| Decisões          | manual            |
| Projetos          | manual            |
| Skills            | quando necessário |

---

💡 **A lógica do sistema é esta:**

Memória automática + contexto + decisões =
**um assistente que fica cada vez mais inteligente.**

---

---

**INEMA** · 2026-03-06

# O que esse prompt faz

Ele instrui o Claude Code a criar um **assistente executivo pessoal estruturado em 3 fases**.

### Fase 1 — Criar a estrutura do projeto

Ele cria um repositório com uma arquitetura organizada para armazenar:

* Contexto sobre você
* Contexto do seu trabalho
* Projetos
* Decisões
* Templates
* Regras de comportamento da IA
* Habilidades (skills)

Exemplo da estrutura:

```CLAUDE.md
context/
projects/
decisions/
templates/
references/
archives/
.claude/
   rules/
   skills/```

A ideia é transformar isso em um **“segundo cérebro” persistente**.

---

# O papel de cada pasta

### `context/`

Informações sobre você e seu trabalho.

Arquivos:

* `me.md` → quem você é
* `work.md` → seu negócio
* `team.md` → equipe
* `current-priorities.md` → foco atual
* `goals.md` → metas trimestrais

---

### `projects/`

Cada projeto ativo ganha uma pasta própria com um README.

Exemplo:

```projects/
   lançamento-curso/
   hiring-va/
   redesign-site/```

---

### `decisions/log.md`

Registro permanente de decisões importantes.

Formato:

```[2026-03-05] DECISION: ...
REASONING: ...
CONTEXT: ...```

Isso cria **memória estratégica**.

---

### `templates/`

Modelos reutilizáveis.

Exemplo:

`session-summary.md`

Serve para fechar sessões de trabalho com IA.

---

### `.claude/rules/`

Regras de comportamento da IA.

Exemplos:

* estilo de comunicação
* padrões de escrita
* convenções da empresa

---

### `.claude/skills/`

Onde serão criadas **automação de tarefas**.

Exemplos de skills futuras:

* criar post de conteúdo
* planejar semana
* revisar estratégia
* organizar tarefas

---

# Fase 2 — Entrevista

O Claude faz uma **entrevista com você**.

Pergunta sobre:

1. Quem você é
2. Seu negócio
3. Sua equipe
4. Projetos e prioridades
5. Estilo de comunicação
6. O que você quer automatizar

Com essas respostas ele personaliza tudo.

---

# Fase 3 — Construção do “cérebro”

Ele gera:

* todos os arquivos de contexto
* regras da IA
* estrutura de projetos
* arquivo principal `CLAUDE.md`

Esse arquivo é o **cérebro do assistente**.

---

# O que o CLAUDE.md define

Ele diz para a IA:

* quem você é
* qual é sua prioridade
* onde está cada informação
* como usar memória
* como registrar decisões
* como criar novas skills

---

# Resultado final

Você passa a ter um **assistente executivo personalizado que:**

* conhece seu negócio
* lembra decisões
* entende prioridades
* organiza projetos
* aprende com o tempo
* automatiza tarefas

Ou seja:

**não é um chatbot genérico — é um sistema operacional pessoal.**

---

**INEMA** · 2026-03-06

https://chatgpt.com/c/69aa3a51-92cc-8327-8ad3-0fc486d30e89
