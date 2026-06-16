# MultiAgentes

> Tópico 5439 · 4 mensagens úteis de 27 totais

---

**Lu** · 2026-05-05

Estou montando a minha equipe multiagentica com a composição de Ruflo, Obsidian, graphify, skills do claude para MKT/design e o bot do telegram pro maestro. Mas ta demorando mais do que eu gostaria. Alguma dica?

---

**INEMA** · 2026-05-03

**3 prompts/modelos de prompt** no vídeo:

## 1. Prompt da demo inicial: criar uma equipe para uma landing page

Algo como:

> Crie uma equipe chamada **Neuroflow** com **3 teammates usando Sonnet**.
> O primeiro é um **front-end developer**.
> O segundo é um **backend developer**.
> O terceiro é um **QA agent**.
> Construa uma **landing page para uma startup fictícia de IA**.

O resultado foi uma equipe em que front-end e back-end trabalharam, depois mandaram para o QA, o QA encontrou problemas e devolveu para correção.

---

## 2. Prompt para criar documentação local sobre agent teams

Depois de habilitar o recurso, ele recomenda “treinar” o projeto com a documentação oficial. O prompt foi mais ou menos:

> Crie para mim um **master reference guide** para **agent teams** em uma pasta chamada `docs`.
> Isso será usado para ajudar você a construir agentes melhores e mais eficazes no futuro.

A ideia era fazer o Claude ler a documentação e criar um guia local em Markdown com instruções, melhores práticas, hooks, modos de exibição, gerenciamento de tarefas etc.

---

## 3. Prompt completo para app full stack com 3 agentes

Exemplo mais estruturado. A estrutura:

> **Goal:** Build a working full stack app with a REST API and a React front end.
> The end result should be a running app that I can view on localhost.
> It should have users and post functionality, plus a QA test report confirming that everything works.
>
> Create a team of **three teammates using Sonnet**.
>
> The first teammate is a **backend developer**.
> It should build the REST API, data model, endpoints, and backend logic.
>
> The second teammate is a **frontend developer**.
> It should wait for the backend developer’s message, then build the React frontend that connects to the API.
>
> The third teammate is a **QA agent**.
> It should test the completed app, check whether the front end and backend work together, identify bugs, and produce a QA report.
>
> When the backend developer is done, it should message the frontend developer.
> When the frontend developer is done, it should send the work to QA.
> QA should report pass/fail results and any critical issues.
>
> Final deliverables:
> a running app,
> a pass/fail test report,
> and a document explaining what was built, key decisions, and how to run it moving forward.

---

## 4. Prompt da equipe de pesquisa para limpar o workspace

Um exemplo com uma equipe chamada **research team**:

> The goal is to help me clean up the workspace.
> Create a team of **three agents called research team using Sonnet**.
>
> The first agent is a **researcher**.
> It should read through the project and create a structured inventory of what exists.
>
> The second agent is a **strategist**.
> It should use the researcher’s findings to identify what should be improved, reorganized, or documented.
>
> The third agent is a **critic**.
> It should review the researcher and strategist’s work, check for gaps, and challenge anything inaccurate or incomplete.
>
> The researcher should send its inventory to both the strategist and critic.
> The strategist should send its recommendations to the critic.
> The critic should produce the final review.

---

## Modelo geral recomendado

O formato é este:

```Goal: [explique o objetivo final e o resultado esperado]

Create a team of [número] teammates using [modelo].

Teammate 1 is [papel].
It should [responsabilidades].
It owns [arquivos/áreas].
When done, message [outro agente].

Teammate 2 is [papel].
It should [responsabilidades].
It should wait for [dependência] before starting/finishing.

Teammate 3 is [papel].
It should [responsabilidades].
It should review/test/critique the work from the other teammates.

Final deliverables:
- [entregável 1]
- [entregável 2]
- [relatório ou documentação final]```

O ponto principal é: não usar prompts vagos. Ele define **objetivo, papéis, comunicação entre agentes, donos de arquivos e entregáveis finais**.

---

**INEMA** · 2026-05-03

Como usar **equipes de agentes no Claude Code** para criar resultados melhores em tarefas complexas.

A ideia principal é que, em vez de usar um único agente ou subagentes isolados, você cria uma **equipe com papéis especializados**, como desenvolvedor front-end, desenvolvedor back-end e agente de QA. Esses agentes trabalham em paralelo, compartilham uma lista de tarefas e conseguem conversar entre si. Isso permite ciclos de revisão, correção e melhoria, como quando o QA encontra problemas e devolve o trabalho para os outros agentes ajustarem.

Para usar esse recurso, é preciso habilitar uma variável de configuração no projeto, pois a funcionalidade ainda é experimental. Recomendo criar uma documentação local sobre “agent teams” dentro do projeto, para que o Claude tenha uma referência rápida e use o recurso com mais eficiência.

Bons prompts são essenciais. Um prompt eficaz deve incluir:

* o objetivo final do projeto;
* quantos agentes serão criados;
* qual modelo cada agente usará;
* o papel específico de cada agente;
* quais arquivos ou entregáveis cada um deve produzir;
* com quem cada agente deve se comunicar;
* quais são os resultados finais esperados.

Também são apresentados cuidados importantes. Cada agente deve ter uma área clara de responsabilidade para evitar que um sobrescreva o trabalho do outro. É melhor usar de **2 a 5 agentes**, não grandes “enxames”, porque isso aumenta muito o custo e a complexidade. Recomenda-se usar equipes apenas quando a tarefa realmente exige colaboração paralela, especialização e revisão de qualidade.

Diferença entre **agent teams** de **subagentes**. Subagentes funcionam melhor para tarefas independentes e sequenciais. Já equipes de agentes são mais úteis quando há dependências entre partes do trabalho, necessidade de comunicação constante e validação cruzada.

Também que, usando o Claude Code no terminal com tmux, é possível ver os agentes trabalhando em painéis separados e até interagir diretamente com cada um. Isso ajuda a acompanhar melhor o processo e corrigir agentes que estejam indo na direção errada.

A conclusão é que equipes de agentes são muito poderosas, mas devem ser usadas com critério. Elas são mais lentas e mais caras, então fazem sentido principalmente para projetos complexos, com várias áreas especializadas, onde qualidade e colaboração importam mais do que velocidade ou economia de tokens.

---

**INEMA** · 2026-05-03

https://chatgpt.com/c/69f6c421-9854-832c-b6ad-24afdf6cde38
