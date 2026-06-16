# Universal Prompt Claude.md

> Tópico 5772 · 8 mensagens úteis de 19 totais

---

**INEMA** · 2026-05-14

Para Entender Diferenca no Agente e Skill

**Agente** = sistema que tem objetivo, contexto, memória, ferramentas e um loop de decisão/ação.
Ele executa uma tarefa de ponta a ponta, tomando decisões ao longo do caminho.

**Skill** = uma capacidade reutilizável, empacotada como um procedimento ou módulo.
Ela não é “o agente inteiro” no sentido completo; é mais como uma competência que pode ser chamada de novo.

Então, quando diz que “o agente pode virar uma skill”, o sentido mais preciso é:

> Depois que você constrói um fluxo de agente que funciona bem, você pode transformar esse processo em uma skill reutilizável.

Por exemplo:

Um **agente de prospecção** faz:

1. pesquisa leads;
2. coleta contatos;
3. gera mensagens;
4. monta dashboard;
5. agenda blocos no calendário.

Depois de validado, esse fluxo pode virar uma **skill de prospecção**, chamada sempre que você quiser rodar o mesmo processo de novo.

O que seria errado é dizer que uma skill, sozinha, é sempre um agente completo. Ela pode ser apenas uma função especializada. O agente é quem pode usar essa skill dentro de um fluxo maior.

Uma forma mais clara de resumir seria:

> Um agente bem construído pode ser convertido em uma skill reutilizável, ou seja, um processo validado que pode ser chamado novamente por Claude Code para repetir aquela capacidade com consistência.

Ou ainda mais simples:

> Agente é o operador. Skill é uma habilidade que o operador aprende e reutiliza.

---

**INEMA** · 2026-05-14

um **dashboard HTML** com:

Lista de leads.

Informações de contato.

Mensagens prontas.

Status de cada oportunidade.

Agenda de execução.

A ideia é transformar dados soltos em uma interface clara e acionável.

---

### 10. Transformar o agente em uma skill

Depois que o agente funciona bem, ele pode ser transformado em uma **skill reutilizável**.

Assim, sempre que o usuário quiser rodar o mesmo processo novamente, basta chamar a skill. Ela pode também evitar duplicação de leads e manter um banco de dados local com os contatos já encontrados.

---

### 11. Princípios operacionais

O processo segue alguns princípios importantes:

**Data-first:** definir entrada e saída antes de construir.

**Mudanças cirúrgicas:** alterar apenas o necessário.

**Simplicidade primeiro:** evitar lógica desnecessária.

**Orientado ao objetivo:** tudo deve apontar para o resultado final.

**Ritmo por tarefa:** explorar, planejar, codar e registrar progresso.

---

### 12. Ideia central

O ponto principal é que criar um agente de IA não começa com código, mas com **estrutura**.

Um bom agente precisa de:

Memória para aprender.

Loop para agir de forma contínua.

Ferramentas para executar tarefas reais.

Contexto para seguir regras.

E um arquivo como `CLAUDE.md` para servir como constituição do projeto.

---

**INEMA** · 2026-05-14

### 1. O que é um agente de IA

Um agente de IA é apresentado como um sistema com **quatro partes essenciais**:

**Memória:** tudo o que o agente aprende e mantém registrado, como fatos, decisões, informações anteriores, clientes, reuniões e lições.

**Loop:** o ciclo de ação do agente. Diferente de um chatbot, que espera comandos, o agente observa o estado atual, decide a próxima ação, executa, avalia o resultado e continua até cumprir o objetivo.

**Ferramentas:** são as capacidades externas do agente, como acessar Gmail, calendário, internet, planilhas, APIs, CRM, LinkedIn, Notion ou sistemas de scraping.

**Contexto:** são as regras que orientam o comportamento do agente: o que ele deve fazer, o que não deve fazer, qual tom usar e quais limites seguir.

---

### 2. Diferença entre modelo e ambiente

**Modelo:** o “motor” inteligente, como Claude, ChatGPT ou Gemini.

**Ambiente/IDE:** o lugar onde o agente trabalha, como Claude Code, VS Code, Cursor, terminal ou outras ferramentas.

A ideia é que o modelo é como o **piloto**, enquanto o ambiente é o **carro de corrida** onde a execução acontece.

---

### 3. Por que agentes importam

Agentes são importantes porque criam **alavancagem**: uma pessoa consegue executar tarefas que antes exigiam várias pessoas, como pesquisar, estruturar dados, gerar mensagens, criar dashboards e automatizar agendas.

O tema central é que agentes permitem transformar ideias em sistemas práticos, mesmo sem grande experiência técnica.

---

### 4. O framework B.L.A.S.T.

O método apresentado para construir agentes é o **B.L.A.S.T.**, dividido em cinco fases:

**Blueprint:** definir a visão, o objetivo final, as regras e a lógica do projeto.

**Link:** conectar o agente às ferramentas necessárias, como Gmail, Google Calendar, Firecrawl, Apify ou outras APIs.

**Architect:** estruturar a arquitetura do projeto, separando lógica, decisões e ferramentas.

**Stylize:** melhorar a apresentação final, como dashboards HTML, mensagens, layouts e entregáveis visuais.

**Trigger:** definir como o agente será acionado: manualmente, por agenda, webhook, comando ou automação recorrente.

---

### 5. As cinco perguntas de descoberta

Antes de criar o agente, o Claude deve perguntar:

1. Qual é o resultado único que significa sucesso?
2. Quais integrações e ferramentas externas serão usadas?
3. Onde está a fonte principal dos dados?
4. Onde e como o resultado final deve ser entregue?
5. Quais regras de comportamento o agente deve seguir?

Essas perguntas impedem que o agente comece a construir sem entender o objetivo.

---

### 6. Estrutura de arquivos do projeto

O projeto deve criar arquivos de memória e organização, como:

`CLAUDE.md` — a constituição do projeto, com regras e instruções principais.

`/memory/task_plan.md` — plano de tarefas.

`/memory/findings.md` — descobertas e pesquisas.

`/memory/progress.md` — progresso, erros, testes e resultados.

`/memory/decisions.md` — decisões tomadas e seus motivos.

Essa estrutura ajuda o agente a manter continuidade e não se perder durante o projeto.

---

### 7. Exemplo prático: agente de prospecção

O exemplo construído é um agente para encontrar leads comerciais.

Ele deve:

Pesquisar empresas-alvo.

Coletar dados como site, e-mail, telefone e redes sociais.

Criar mensagens personalizadas para LinkedIn.

Criar rascunhos de e-mail.

Montar um dashboard HTML com os leads.

Reservar blocos na agenda para o usuário fazer o outreach.

O exemplo usado envolve encontrar empresas de Salão de Beleza e oferecer a criação de um site gratuito como proposta de valor.

---

### 8. Conexão com ferramentas

O agente pode ser conectado a várias ferramentas:

Google Calendar para criar blocos de agenda.

Gmail para e-mails.

Firecrawl para pesquisar e extrair informações da web.

Apify para scraping de sites, Google Maps, redes sociais e outras fontes.

Conectores personalizados via MCP quando a ferramenta não aparece diretamente no Claude.

---

### 9. Dashboard e entrega final

O resultado ideal não é apenas texto. O agente pode criar uma entrega mais visual, como

---

**INEMA** · 2026-05-14

A ideia central é que o Claude atue como **System Pilot**, seguindo o método **B.L.A.S.T.**:

**B — Blueprint:** entender o objetivo, integrações, fonte de dados, entrega final e regras de comportamento antes de programar.
**L — Link:** verificar conexões, APIs e credenciais antes de construir lógica.
**A — Architect:** separar o projeto em três camadas **A.N.T.**: arquitetura, navegação e ferramentas.
**S — Stylize:** refinar a entrega final, interface e formato dos resultados.
**T — Trigger:** colocar em produção, configurar automações e criar um ciclo de correção quando algo falhar.

Também exige uma estrutura padrão de arquivos:

`CLAUDE.md` como Constituição do Projeto,
`/memory/` para plano, descobertas, progresso e decisões,
`/architecture/` para procedimentos e regras,
`/execution/` para scripts,
`/.tmp/` para arquivos temporários.

O princípio mais importante é: **não escrever código antes de definir claramente o Blueprint, os dados de entrada/saída e as regras do projeto**.

---

**INEMA** · 2026-05-14

## O que você recebe de volta

Uma Constituição de Projeto `CLAUDE.md` com a identidade do System Pilot, o Protocolo 0 obrigatório de pausa até a aprovação do Blueprint, a espinha dorsal em cinco fases **B.L.A.S.T.** — Blueprint · Link · Architect · Stylize · Trigger — preenchida com as suas respostas, a construção em 3 camadas **A.N.T.** — Architecture · Navigation · Tools — conectada à Fase A, verificação de integração incorporada à Fase L, verificação de saída na Fase S e o ciclo de reparo autoajustável na Fase T. Além disso, `/memory/` com task_plan, findings, progress e decisions; `/architecture/` para SOPs; `/execution/` para scripts; e `/.tmp/` para arquivos temporários.

---

**INEMA** · 2026-05-14

# Protocolo Universal [CLAUDE.md](http://claude.md/)

> Cole o prompt abaixo no Claude Code no início de qualquer novo projeto. O Claude fará cinco perguntas de descoberta e, em seguida, escreverá uma Constituição do Projeto `CLAUDE.md` na raiz, seguindo o protocolo **B.L.A.S.T.** — Blueprint, Link, Architect, Stylize, Trigger — e a construção em 3 camadas **A.N.T.** — Architecture · Navigation · Tools. Com menos de 300 linhas no resultado. Pronto para usar em qualquer projeto — site, aplicativo, agente ou automação.

---

**INEMA** · 2026-05-14

Universal Prompt Claude md

---

**INEMA** · 2026-05-14

https://chatgpt.com/c/6a052832-37b8-8331-8ce8-3e5be4d26cb2
