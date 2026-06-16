# 10x Melhor Claude AIOS 2.1

> Tópico 6063 · 7 mensagens úteis de 20 totais

---

**INEMA** · 2026-05-23

O `/goal` é o comando que **aciona uma meta curta**.

Então fica assim:

```/goal Mission: Criar landing page. Outcome: A página /landing existe, carrega sem erro e contém título, oferta, formulário e botão de envio.```

Você cola isso no Claude Code, Hermes ou agente compatível. O importante é começar exatamente com:

```/goal ```

com a barra, a palavra `goal` e um espaço depois.

Já o **SuperGoal** normalmente não é acionado com `/goal`. Ele é uma **camada acima**:

1. Você define o **SuperGoal**
   Exemplo: “Lançar meu produto em 4 semanas”.

2. O agente usa o prompt de **Long-Term Goal** para transformar isso em uma missão.

3. Essa missão vira vários cards no **Mission Control**.

4. Cada card de agente gera um `/goal`.

Então a sequência é:

```SuperGoal
↓
Long-Term Goal
↓
Mission Control
↓
vários /goal```

Em outras palavras:

**/goal**** executa uma tarefa.**
**SuperGoal organiza um projeto maior.**

Exemplo:

```SuperGoal: Lançar meu curso em 4 semanas```

vira mini-metas como:

```/goal Mission: Criar página de vendas...
/goal Mission: Preparar sequência de emails...
/goal Mission: Gerar roteiro do vídeo...
/goal Mission: Criar posts de lançamento...```

Então, para acionar mesmo, você usa `/goal` nas tarefas pequenas. Para SuperGoal, você usa o prompt de **Long-Term Goal**, que cria a missão completa.

---

**INEMA** · 2026-05-23

A finalidade do **Long-Term Goal** é transformar uma meta grande, de até **4 semanas**, em uma missão organizada com várias mini-metas no **Mission Control**.

Ele é diferente do **Short-Term Goal** porque não serve para executar uma tarefa única agora. Ele serve para **planejar, dividir e acompanhar uma missão maior**.

## Finalidade do Long-Term Goal

Ele ajuda você a pegar uma ideia grande, por exemplo:

> “Quero lançar um produto em 4 semanas.”

E transformar isso em uma missão com 4 a 10 etapas menores, como:

1. Definir oferta
2. Criar página
3. Preparar emails
4. Gravar vídeo
5. Fazer divulgação
6. Acompanhar respostas
7. Ajustar lançamento

Algumas etapas podem ser feitas por IA. Outras precisam de você, como gravar vídeo, participar de uma reunião, assinar algo ou fazer uma ação física fora do chat.

## Diferença principal

| Tipo                             | Serve para                          |                            Duração | Resultado                       |
| -------------------------------- | ----------------------------------- | ---------------------------------: | ------------------------------- |
| **Short-Term Goal**              | Uma tarefa única e objetiva         |     Uma sessão, cerca de 20 turnos | Um `/goal` pronto para executar |
| **Long-Term Goal**               | Uma missão maior dividida em partes | 7 a 42 dias, normalmente 4 semanas | Um plano com 4 a 10 mini-metas  |
| **SuperGoals / Mission Control** | Organizar tarefas humanas + IA      |                   Projeto completo | Painel de acompanhamento        |

## Exemplo simples

**Short-Term Goal:**

> Criar uma landing page com formulário funcionando.

Isso cabe em uma sessão.

**Long-Term Goal:**

> Lançar um curso online em 4 semanas.

Isso é grande demais para uma sessão, então precisa virar várias mini-metas:

* IA pesquisa o público
* IA cria a copy da página
* IA prepara sequência de emails
* Você grava as aulas
* IA organiza os materiais
* Você publica
* IA ajuda no lançamento

## Em resumo

O **Short-Term Goal** é para **executar uma tarefa agora**.

O **Long-Term Goal** é para **organizar uma missão maior em etapas**, separando o que a IA pode fazer e o que você precisa fazer pessoalmente.

A grande vantagem é evitar que o agente se perca em um prompt gigante. Em vez disso, ele cria um plano controlado, com metas menores, verificáveis e acompanháveis.

---

**INEMA** · 2026-05-23

A função desse prompt é **transformar uma ideia vaga em uma meta executável para um agente de IA**, usando o comando `/goal`.

Ele serve como uma “skill” ou instrução-mestre para ensinar o agente a criar metas curtas, bem definidas e prontas para execução em ferramentas como Claude Code, Codex CLI ou Hermes Agent.

Na prática, ele faz o agente:

1. **Perguntar o que você quer entregar em uma sessão**

   Exemplo: “Quero criar uma página de captura”, “Quero arrumar o checkout”, “Quero gerar um relatório”.

2. **Verificar se a meta é clara o suficiente**

   Ele checa se o objetivo é:

   * mensurável;
   * pequeno o bastante para caber em cerca de 20 turnos;
   * possível de executar com os arquivos, acessos e informações disponíveis.

3. **Fazer perguntas se estiver faltando algo**

   Se a meta estiver vaga, ele deve fazer uma pergunta objetiva antes de criar o `/goal`.

4. **Gerar um prompt final pronto para copiar e colar**

   O resultado começa obrigatoriamente com `/goal`, por exemplo:

```/goal Mission: Criar página de captura. Outcome: A página /captura existe, carrega corretamente e contém título, formulário de email e botão de envio funcional.```

5. **Evitar que o agente trabalhe no escuro**

   O prompt manda o agente pausar e perguntar quando precisar de decisão humana, ajuste de gosto, tom, escolha visual ou informação faltante.

6. **Limitar o trabalho**

   Ele define um limite de 20 turnos e manda salvar um resumo final em um arquivo.

Em resumo: **esse prompt cria metas curtas, objetivas e verificáveis para agentes autônomos executarem sem se perderem no meio do caminho**. Ele não executa a tarefa diretamente; ele cria o comando `/goal` ideal para outro agente executar.

---

**INEMA** · 2026-05-23

O Claude Code ficou 10 vezes melhor (Agentic OS)

Claude Code acaba de lançar o recurso de metas.
Hermes também.

Vou mostrar a vocês como dominá-lo e qual é a sua maior limitação.
E não é só isso, vou te mostrar como multiplicar por 10 com o SuperGoals.
Essas metas abrangentes combinam tarefas humanas e de IA.
Este é o Chief Wigum 2.0: o sistema para criar metas que realmente importam.
⚡ Metas de curto prazo
📅 Metas de longo prazo divididas em sprints de 3 a 4 semanas
🤝 Aperto de mãos entre humanos e IA para que você saiba exatamente o que fazer
💼 Painel de controle da missão que monitora tudo
Também abordo como criar metas que não falham.

---

**INEMA** · 2026-05-23

Resumindo, temos **dois tipos de prompts/metas**:

## 1. Short-Term Goal — Meta de curto prazo

Serve para **uma tarefa específica**, feita em uma única sessão com o agente.

Exemplo:

> Criar uma landing page, corrigir um bug, gerar um relatório, configurar checkout, criar um formulário.

Características:

* dura cerca de **20 turnos**;
* precisa ter resultado **sim/não**;
* o agente precisa ter tudo que precisa para executar;
* começa com `/goal`;
* é para **fazer uma entrega agora**.

Em resumo: **uma tarefa fechada para executar em uma sessão.**

---

## 2. Long-Term Goal — Meta de longo prazo

Serve para **uma missão maior**, normalmente de até 4 semanas, que não cabe em uma sessão só.

Exemplo:

> Lançar um produto, criar um curso, montar uma campanha, validar uma oferta, organizar um projeto completo.

Características:

* dura de **7 a 42 dias**;
* vira **4 a 10 mini-metas**;
* mistura tarefas da IA com tarefas humanas;
* usa o **Mission Control** para acompanhar;
* cada mini-meta pode virar um `/goal`.

Em resumo: **um projeto grande dividido em etapas controláveis.**

---

## A lógica completa

Você tem um sistema em camadas:

**Long-Term Goal**
→ quebra uma missão grande em várias partes.

**Mission Control**
→ mostra essas partes em um painel.

**Short-Term Goal `****/goal****`**
→ executa cada parte pequena com o agente.

**Humano + IA**
→ a IA faz o que dá para fazer no chat; você faz o que exige presença, decisão real, gravação, reunião, assinatura ou ação fora do chat.

## Frase simples

O **Long-Term Goal planeja a missão**.
O **Short-Term Goal executa uma tarefa**.
O **Mission Control acompanha tudo**.

---

**INEMA** · 2026-05-23

10x Melhor Claude AIOS 2.1

---

**INEMA** · 2026-05-23

https://chatgpt.com/c/6a121cd5-ce94-8325-a86c-9087dd850c7a
