# /loop - Novo Comando do CC2

> Tópico 3614 · 3 mensagens úteis de 12 totais

---

**INEMA** · 2026-03-07

https://youtu.be/u6zzEFYJvFU

---

**INEMA** · 2026-03-07

# Resumo – Nova feature do Claude Code (Loop + Scheduled Tasks)

## 1. Nova capacidade do Claude Code

O Claude Code agora pode:

* **Criar lembretes automáticos**
* **Verificar tarefas ou projetos periodicamente**
* **Executar ações automaticamente por até 3 dias**
* Trabalhar **sem intervenção do usuário**

Exemplo:

* “Me lembre às 10:23 de verificar meu projeto”
* “A cada 10 minutos verifique meu ClickUp”

---

# 2. Nova funcionalidade: **Loop**

O **Loop** permite criar tarefas repetitivas automaticamente.

### O que ele faz

* Executa comandos em intervalos definidos
* Pode rodar por até **3 dias**
* Usa **cron jobs** internamente

Exemplos:

* Verificar deploy a cada 5 minutos
* Rodar uma skill a cada 20 minutos
* Checar logs ou progresso de projeto

### Intervalos possíveis

* A cada 5 minutos
* A cada 10 minutos
* A cada hora
* Qualquer intervalo definido pelo usuário

---

# 3. Lembretes únicos

Também é possível criar **lembretes de uma vez só**.

Exemplo:

* “Às 15h me lembre de sair”
* “Em 45 minutos me lembre de revisar algo”

Quando executado:

* O cron é criado
* O lembrete dispara
* Depois **é automaticamente removido**

---

# 4. Como funciona tecnicamente

O sistema usa três ferramentas principais:

### 1️⃣ `cron create`

Cria o agendamento.

### 2️⃣ `cron list`

Lista tarefas agendadas.

### 3️⃣ `cron delete`

Cancela tarefas.

Tudo pode ser feito com **linguagem natural**.

---

# 5. Execução por sessão

Os loops são **vinculados à sessão atual**.

Isso significa:

* Cada aba ou terminal tem suas tarefas próprias
* Uma sessão **não vê tarefas de outra**
* Se a sessão fechar → **as tarefas são canceladas**

---

# 6. Limitações do Loop

### ⏳ Expiração automática

Loops duram **máximo de 3 dias**.

Motivo:

* evitar loops esquecidos consumindo recursos.

---

### ❌ Sem persistência

Se quiser continuar depois de 3 dias:

* precisa recriar o loop.

---

### ❌ Sem catch-up

Se a tarefa deveria rodar enquanto o app estava fechado:

* ela **não executa depois**.

---

### ❌ Terminal fechado = tarefas canceladas

Se fechar a sessão:

* todos os cron jobs são removidos.

---

# 7. Diferença: Loop vs Scheduled Tasks

| Loop                     | Scheduled Tasks             |
| ------------------------ | --------------------------- |
| Até 3 dias               | Pode durar indefinidamente  |
| Sessão atual             | Persistente                 |
| Sem catch-up             | Tem catch-up                |
| Para tarefas temporárias | Para automações permanentes |

---

### Quando usar **Loop**

Para tarefas temporárias:

* monitorar deploy
* acompanhar progresso de projeto
* checar logs
* monitorar e-mails urgentes
* sprint de 3 dias

---

### Quando usar **Scheduled Tasks**

Para automações contínuas:

* tarefas diárias
* tarefas semanais
* relatórios automáticos
* rotinas permanentes

---

# 8. Exemplos práticos de uso

Possibilidades citadas no vídeo:

* Checar e-mails importantes a cada 5 minutos
* Monitorar deploy
* Verificar progresso da equipe
* Monitorar logs
* Acompanhar mudanças em arquivos
* Automatizar revisões de PR
* Criar um **assistente executivo automatizado**

---

# Conclusão

A nova função **Loop** transforma o Claude Code em algo mais próximo de um **agente autônomo**, capaz de:

* executar tarefas automaticamente
* monitorar projetos
* agir proativamente

Enquanto **Scheduled Tasks** serve para automações permanentes, o **Loop** é ideal para **trabalho intensivo de curto prazo (até 3 dias)**.

---

**INEMA** · 2026-03-07

https://chatgpt.com/c/69aca868-5ad0-8330-bc97-1c9251b3b151
