# Claude Code 2.0 (Scheduled Tasks)

> Tópico 3599 · 4 mensagens úteis de 11 totais

---

**INEMA** · 2026-03-07

https://youtu.be/X-AquUT2L14

---

**INEMA** · 2026-03-07

# Resumo – Claude Code 2.0 (Scheduled Tasks)

## 1. Novo recurso principal: Scheduled Tasks

* Claude Code agora permite **tarefas automáticas agendadas**.
* O agente pode rodar **automaticamente em horários definidos** (hora, dia, semana).
* Funciona como um **“funcionário de IA 24/7”**.

Exemplo:

* Rodar uma tarefa todo dia às **6:00 da manhã**.

---

# 2. Como criar uma tarefa agendada

Existem duas formas:

### 1️⃣ Pela aba Schedule

* Clique em **Schedule → New Task**
* Defina:

  * Nome da tarefa
  * Descrição
  * Prompt
  * Modelo
  * Modo de execução
  * Pasta do projeto
  * Horário (cron)

### 2️⃣ Pelo comando

```/schedule```

---

# 3. Como a automação funciona

Quando chega o horário:

1. Claude inicia uma nova sessão
2. Lê o prompt
3. Analisa os arquivos do projeto
4. Executa a tarefa
5. Finaliza automaticamente

---

# 4. Diferença importante: workflow agentic

Ao contrário de scripts tradicionais:

### Scripts tradicionais

* Determinísticos
* Passo 1 → passo 2 → passo 3
* Se erro → falha

### Claude Agent

* **Autônomo**
* Tenta resolver erros
* Testa alternativas
* Pode **melhorar seu próprio processo**

---

# 5. Automação determinística ainda é possível

Se quiser controle total:

* Faça Claude executar apenas um **script Python ou TypeScript**
* A tarefa agendada apenas roda esse script.

---

# 6. Exemplo real

Task: **Morning Coffee**

Todo dia às **6:00 AM**:

Claude:

* Analisa compromissos
* Analisa projetos
* Resume atualizações
* Planeja o dia

Antes precisava rodar manualmente.

Agora roda automaticamente.

---

# 7. Limitações atuais

## 1️⃣ Computador precisa estar ligado

* Desktop app precisa estar aberto
* Se o PC estiver desligado → não executa.

Mas:

* Quando abrir o PC, Claude verifica **tarefas perdidas nos últimos 7 dias**.

---

## 2️⃣ Permissões precisam ser controladas

Como roda sozinho:

Pode:

* editar arquivos
* rodar comandos

Recomendação:

* bloquear comandos perigosos

Exemplo:

* impedir `delete`
* impedir `rm`

---

## 3️⃣ Tarefas são stateless

Cada execução:

* abre **uma sessão nova**
* não lembra da execução anterior

---

# 8. Como criar memória entre execuções

Um método:

Criar um arquivo de estado.

Exemplo:

```task_status.md```

Cada execução:

1. Lê o arquivo
2. Executa tarefa
3. Atualiza o arquivo

Conteúdo pode incluir:

* última execução
* duração
* problemas
* melhorias
* status

Assim a próxima execução tem contexto.

---

# 9. Estratégia de melhoria automática

Três níveis de auto melhoria:

### 1️⃣ Código

Se erro → editar o próprio script.

### 2️⃣ Prompt

Se pode melhorar → reescrever prompt.

### 3️⃣ Memória

Registrar histórico em arquivo.

---

# 10. Notificações quando tarefa termina

Opções:

### Desktop notification

Limitada.

### Hook com som

Pode configurar:

```play sound when task finishes```

### Notificação externa

Exemplo sugerido:

* enviar mensagem no **ClickUp**
* enviar mensagem Slack
* enviar email

---

# 11. Limitação atual do Desktop App

Scheduled Tasks só funcionam no:

* **Claude Code Desktop App**

Ainda não funciona em:

* terminal
* VS Code extension
* IDE plugins

Mas provavelmente será liberado em breve.

---

# 12. Onde ficam os arquivos das tarefas

As tarefas são salvas como **arquivos locais**.

Claude pode:

* ler
* editar

Mas **não pode criar novas tarefas**, pois o cron pertence ao app desktop.

---

# 13. Potencial do sistema

Com Claude Code:

É possível automatizar:

* pesquisa
* criação de conteúdo
* análise de projetos
* operações
* organização de tarefas
* relatórios automáticos
* agentes que melhoram com o tempo

---

# Conclusão

Claude Code agora permite criar **agentes autônomos agendados** que:

* executam tarefas automaticamente
* acessam todo o projeto
* se adaptam a erros
* podem melhorar continuamente.

Isso aproxima a IA de funcionar como um **assistente executivo automatizado**.

---

**INEMA** · 2026-03-07

Claude Code 2.0 (Scheduled Tasks)

---

**INEMA** · 2026-03-07

https://chatgpt.com/c/69abcb7e-c874-8327-8b2b-9d049dda0ed1
