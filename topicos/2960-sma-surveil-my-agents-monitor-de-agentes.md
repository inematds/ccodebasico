# SMA - Surveil My Agents - Monitor de Agentes

> Tópico 2960 · 7 mensagens úteis de 20 totais

---

**INEMA** · 2026-02-08

## **O que é o *Agent Teams***

**Agent Teams** é um recurso **nativo da Anthropic no Claude Opus 4.6**.
Uma funcionalidade que foi introduzida oficialmente nessa versão do Claude Code.

👉 Ou seja:

* O *Agent Teams* **faz parte da API e da arquitetura do Opus 4.6**;
* Ele permite criar grupos de agentes que **trabalham juntos, se comunicam entre si e coordenam tarefas complexas**.
* Essa funcionalidade é diferente dos *subagents*, que apenas executam tarefas isoladas sem conversar entre si.

---

## **O que o autor implementou**

O autor **não criou o conceito de Agent Teams**, mas construiu algo **em cima desse recurso nativo**:

### O que foi desenvolvido pelo autor:

✔ Um **dashboard de vigilância em tempo real** (Agent Surveillance)
✔ Uma **skill que automatiza a ativação do painel**
✔ A leitura contínua dos **arquivos JSON gerados pelos agentes**
✔ Integração com um **UI local (localhost:3847)**
✔ Armazenamento de histórico em **SQLite**
✔ Uma interface visual com:

* Kanban de tarefas
* Fluxo de mensagens
* Histórico de sessões
* Representação dos agentes e suas interações

Esse dashboard **não faz parte do Claude Code por padrão** — ele foi **projetado e implementado pelo autor** para tornar o uso de Agent Teams **mais transparente e fácil de auditar**.

---


## **Como funciona o Agent Teams (nativo)**

O Agent Teams no Opus 4.6 funciona assim:

1. Você solicita ao Claude:
   👉 *“Create an agent team to X”*
2. A feature cria um **Team Lead + outros agentes**
3. O Team Lead gerencia a estratégia e as conversas
4. Os agentes:

   * se comunicam entre si
   * criam tarefas
   * atualizam tarefas
   * coordenam a execução dos objetivos
5. O sistema persiste enquanto o objetivo não é concluído

Essa estrutura **suporta comunicação bidirecional entre agentes**, ao contrário dos subagents.

---

## **Diferença entre Agent Teams e subagents**

🔹 **Subagents**

* Não se comunicam entre si
* Trabalham isoladamente
* Retornam apenas resultado final para você

🔹 **Agent Teams**

* Há comunicação cruzada entre agentes
* Existe um líder (Team Lead) que coordena
* Todos podem trocar mensagens
* Há um fluxo de trabalho colaborativo

---

## **Conclusão**

✅ *Agent Teams* é **um recurso do próprio Claude Opus 4.6**.
✳️ O autor **construiu em cima desse recurso** um dashboard e uma skill para tornar o monitoramento mais fácil, visual e auditável, mas o Agent Teams em si é fornecido pela Anthropic.

---

**INEMA** · 2026-02-08

tabela de usuários
* Volta para API
* API valida
* UI testa
* Time Lead aprova

Esse tipo de coordenação **não é possível com subagentes**.

---

## Casos ideais de uso de Agent Teams

O autor destaca:

1. **Code review paralelo**

   * Segurança
   * Performance
   * Cobertura de testes
2. **Features cross-layer**

   * Frontend + Backend + DB
3. **Debugging complexo**

   * Debate entre agentes
   * Um pode discordar do outro
   * Chegam a consenso
4. **Pesquisa avançada**

   * Comitês de pesquisa
   * Descobertas científicas
   * RFPs, propostas, brainstorming

---

## Problemas e limitações (gotchas)

* Custo altíssimo de tokens
* Agentes podem:

  * sobrescrever arquivos uns dos outros
  * gerar código redundante
* Team Lead às vezes:

  * começa a codar em vez de delegar
* Sem automação, é difícil recriar exatamente o mesmo time depois que ele termina

---

## Visualização e infraestrutura

O sistema é todo baseado em:

* JSONs de configuração
* Inboxes individuais por agente
* Protocolos de mensagens (tipo WhatsApp / Telegram com “lido”)
* Ciclo de vida de tarefas (criar, atualizar, concluir)
* Dashboard com:

  * modo ao vivo
  * histórico
  * kanban
  * threads de mensagens

Nada “novo” foi inventado — o dashboard **apenas visualiza o que já existe** no sistema do Claude Code.

---

## Conclusão

O vídeo ensina que:

* **Agent Teams são poderosíssimos**, mas caros
* Devem ser usados com **intencionalidade**
* Subagentes ainda têm um papel essencial
* Monitorar tudo é a chave para usar bem
* Pensar como um **founder bootstrapado** ajuda a decidir quando “contratar” agentes

---

**INEMA** · 2026-02-08

Aqui está um **resumo completo, estruturado e fiel aos detalhes** do vídeo **“How to Use Claude Code Agent Teams Like a Pro”**, em português:

---

## Visão geral do vídeo

O vídeo é um **deep dive prático** sobre como funcionam os **Agent Teams** introduzidos no **Claude Code com Opus 4.6**, explicando **quando usar**, **como configurar**, **como monitorar** e **como evitar desperdício de tokens**. O autor também apresenta um **dashboard de vigilância em tempo real** (Agent Surveillance Dashboard) criado por ele para observar toda a atividade dos agentes.

---

## O que são Agent Teams e por que eles importam

Antes do Opus 4.6, o Claude usava principalmente **subagentes**:

* Eles trabalham em paralelo
* Não se comunicam entre si
* Apenas retornam um resumo final ao usuário

Com **Agent Teams**:

* Existe um **Team Lead** (líder do time)
* Os agentes **se comunicam entre si**
* Há **coordenação sequencial**
* Todo o processo pode ser **auditado passo a passo**
* Os times **persistem até a tarefa ser concluída**

Isso muda completamente o modelo mental:
👉 você deixa de ser o “intermediário” de tudo e passa a ter um **líder de time gerenciando os outros agentes**.

---

## O dashboard de vigilância (Agent Surveillance)

O autor criou uma **skill** que:

* Inicia automaticamente um **dashboard web em localhost:3847**
* Monitora os **arquivos JSON** usados pelos agentes
* Mostra:

  * mensagens entre agentes
  * tarefas pendentes, em progresso e concluídas (Kanban)
  * histórico completo das execuções
* Armazena tudo em um **SQLite local**
* Encerra automaticamente quando o time termina

O objetivo é **total transparência**:

* Ver o que cada agente está fazendo
* Auditar decisões
* Entender por que algo deu certo ou errado
* Controlar custos de tokens

---

## Por que monitorar é essencial

O autor destaca um ponto crítico:
⚠️ **Agent Teams consomem tokens muito rapidamente**

* Um único projeto pode consumir **80k a 300k tokens**
* Usar times “só porque é legal” é um erro
* Eles devem ser usados **apenas para tarefas realmente complexas**

Por isso, **monitorar em tempo real** é fundamental para:

* Evitar uso excessivo
* Corrigir desvios cedo
* Garantir que os agentes estejam alinhados

---

## Como habilitar Agent Teams (inclusive para não técnicos)

Para usar Agent Teams é necessário ativar um **feature flag**.

Para usuários não técnicos, o autor sugere:

* Copiar a documentação oficial
* Colar no Claude Code ou no **Warp (terminal inteligente)**
* Pedir para ele:

  * verificar configurações
  * instalar corretamente
  * validar se os Agent Teams estão ativos

Depois:

* Reiniciar o Claude Code
* Perguntar diretamente:
  👉 *“Você tem acesso a agent teams?”*
  Se ele responder listando ferramentas de times, está tudo certo.

---

## Diferença prática: Subagentes vs Agent Teams

### Subagentes

* Não conversam entre si
* Bons para:

  * pesquisa rápida
  * exploração de código
  * tarefas administrativas
  * preservar contexto principal
* Mais baratos em tokens

### Agent Teams

* Comunicação cruzada
* Coordenação real
* Bons para:

  * tarefas complexas
  * múltiplas camadas (frontend, backend, banco)
  * decisões estratégicas
  * revisões profundas
* Muito mais caros em tokens

**Heurística simples**:

1. Os agentes precisam conversar entre si?

   * ❌ Não → use subagentes
   * ✅ Sim → próxima pergunta
2. A tarefa é complexa o suficiente para justificar o custo?

   * ❌ Não → sessão normal
   * ✅ Sim → agent team

---

## Como os Agent Teams funcionam internamente

Fluxo típico:

1. Você pede: *“Crie um agent team para X”*
2. O **Team Lead** analisa o problema
3. Ele cria de **3 a 5 agentes**, cada um com um papel
4. Os agentes:

   * planejam juntos
   * pedem aprovação ao líder
   * executam tarefas
   * trocam mensagens entre si
5. O líder consolida tudo
6. O time se encerra automaticamente

Tudo isso é visível no dashboard.

---

## Exemplo prático: autenticação

* Agente UI cria a interface
* Percebe que precisa de uma API
* Agente API cria endpoint de login
* Percebe que precisa de banco
* Agente DB cria

---

**INEMA** · 2026-02-08

https://www.youtube.com/watch?v=1jlKUxqRQAw

---

**INEMA** · 2026-02-08

O autor passou os últimos dias explorando profundamente um dos recursos novos favoritos do **Opus 4.6**, chamado **agent team feature** (times de agentes). A partir disso, ele desenvolveu uma **skill** que cria automaticamente um **dashboard de monitoramento em tempo real**, apresentado em um vídeo no YouTube lançado no mesmo dia. Quem acompanha o conteúdo recebe acesso a essa skill.

Essa skill é ativada quando o usuário diz algo como **“surveil my agents”**. A partir desse comando, o sistema **inicia automaticamente um painel** que permite observar continuamente tudo o que os agentes estão fazendo.

Ele demonstra o funcionamento criando um **time de agentes de exemplo** (um “dental agent team”) apenas para validar que a skill de vigilância está funcionando corretamente. O painel roda localmente em **localhost:3847**, algo que já está embutido diretamente na skill, sem necessidade de configuração manual a cada sessão.

O motivo pelo qual o dashboard funciona é que, nos bastidores, os agentes se comunicam por meio de **arquivos JSON**, que registram mensagens, estados e tarefas. À medida que novas tarefas aparecem no terminal, esses mesmos dados são lidos e refletidos **em tempo real no dashboard**, que é iniciado no momento certo.
Isso elimina o problema comum de ter que iniciar manualmente um servidor local e depois “lembrar” cada sessão do Claude Code de usá-lo. A skill já inclui:

* a **infraestrutura**,
* o **código para iniciar o painel**,
* e a **ordem correta de operações**, garantindo que as tarefas pendentes apareçam no momento certo.

No painel, é possível:

* clicar em qualquer agente (por exemplo, **pesquisador, redator e líder do time**),
* ver exatamente o que cada um está fazendo em tempo real,
* acompanhar a **comunicação cruzada** entre os agentes,
* monitorar o progresso das tarefas conforme avançam.

Além do modo ao vivo, há um **modo de histórico**. Todo o histórico das execuções é armazenado localmente em um **banco de dados SQLite** no computador do usuário. Isso permite revisar execuções passadas, ver notificações, tarefas concluídas e entender exatamente o que aconteceu em cada sessão.

Enquanto o time de agentes está ativo, o painel continua exibindo o progresso até que todas as tarefas sejam concluídas. Assim que o trabalho termina, o **dashboard se encerra automaticamente**, sem necessidade de intervenção manual. Isso torna a ferramenta útil tanto para **monitorar** quanto para **garantir que os agentes estejam fazendo o que deveriam**.

O autor enfatiza que o projeto foi um verdadeiro **“labor of love”** (feito com muito cuidado e dedicação), e por isso **não é gratuito**.

---

**INEMA** · 2026-02-08

**Painel de Monitoramento de Agentes para Times do Opus 4.6 (skill incluída)**

O recurso de times de agentes, Monitorando com um Skill.

Essa skill inicia um painel em tempo real que observa o que seus agentes estão fazendo o tempo todo.

Basta dizer **“surveil my agents”** e ela:

→ Inicia automaticamente um painel em localhost
→ Lê os arquivos JSON que os agentes usam para se comunicar
→ Exibe todas as tarefas pendentes assim que elas aparecem no seu terminal
→ Mostra a comunicação cruzada entre líder do time, pesquisador, redator e outros agentes

A skill inclui tanto o código de infraestrutura **quanto** a ordem de operações, para que você não precise lembrar como configurar tudo a cada sessão.

Você pode clicar em qualquer agente para ver exatamente o que ele está fazendo em tempo real, e o histórico é armazenado em um banco de dados SQLite local no seu computador, permitindo revisar execuções anteriores.

Quando o time de agentes conclui o trabalho, o painel é encerrado automaticamente.

Foi um projeto feito com muito carinho do Mark, por isso não é gratuito — mas vocês, pessoas maravilhosas, têm acesso a ele.

---

**INEMA** · 2026-02-08

https://chatgpt.com/c/698893b3-fd30-8329-9d54-bbb3d14aa85e
