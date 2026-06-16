# Basico de usar o Claude Code

> Tópico 2934 · 8 mensagens úteis de 17 totais

---

**Luiz Carlos** · 2026-02-10

Para facilitar o gerenciamento do Claude, use `/statusline` para personalizar sua barra de status e exibir sempre o uso do contexto e a branch atual do Git. Muitos de nós também usamos cores e nomes para as abas do terminal, às vezes com o tmux — uma aba por tarefa/árvore de trabalho.

Use a digitação por voz. Você fala 3 vezes mais rápido do que digita e, como resultado, suas instruções ficam muito mais detalhadas. (pressione fn duas vezes no macOS)


#8. Use subagentes

a. Adicione "use subagents" a qualquer solicitação em que você queira que Claude aloque mais poder computacional para resolver o problema.

b. Delegue tarefas individuais a subagentes para manter a janela de contexto do seu agente principal limpa e focada.

c. Direcione as solicitações de permissão para o Opus 4.5 por meio de um gancho — deixe-o verificar ataques e aprovar automaticamente os seguros (consulte https://code.claude.com/docs/en/hooks#permissionrequest )


#9. Use o Claude para dados e análises.

Peça ao Claude Code para usar a CLI "bq" para coletar e analisar métricas em tempo real. Temos uma skill do BigQuery integrada ao código-fonte, e todos na equipe a utilizam para consultas analíticas diretamente no Claude Code. Pessoalmente, não escrevi uma linha de SQL nos últimos 6 meses.

Isso funciona para qualquer banco de dados que possua uma CLI, MCP ou API.


#10. Aprendendo com Claude

Algumas dicas da equipe para usar o Claude Code para aprendizado:

a. Habilite o estilo de saída "Explicativo" ou "Aprendizado" em /config para que Claude explique o *motivo* por trás das alterações.

b. Peça ao Claude para criar uma apresentação visual em HTML explicando códigos desconhecidos. Os slides ficam surpreendentemente bons!

c. Peça a Claude para desenhar diagramas ASCII de novos protocolos e bases de código para ajudá-lo a entendê-los.

d. Desenvolva uma habilidade de aprendizagem por repetição espaçada: você explica seu entendimento, Claude faz perguntas adicionais para preencher as lacunas e armazena o resultado.

---

**Luiz Carlos** · 2026-02-10

Meu nome é Boris e sou o criador do Claude Code. 
Gostaria de compartilhar rapidamente algumas dicas de uso do Claude Code, diretamente da equipe do Claude Code. 
A forma como a equipe usa o Claude é diferente da minha. Lembre-se: não existe uma única maneira correta de usar o Claude Code -- a configuração de cada pessoa é diferente. Experimente para ver o que funciona melhor para você!

https://x.com/bcherny/status/2017742741636321619?s=20

#1. Faça mais em paralelo

Crie de 3 a 5 worktrees do Git simultaneamente, cada uma executando sua própria sessão do Claude em paralelo. É o maior ganho de produtividade e a principal dica da equipe. Pessoalmente, eu uso vários checkouts do Git, mas a maioria da equipe do Claude Code prefere worktrees -- e é por isso 
@amorriscode
 que incluímos suporte nativo para elas no aplicativo Claude Desktop!

Algumas pessoas também nomeiam suas árvores de trabalho e configuram aliases de shell (za, zb, zc) para poderem alternar entre elas com uma única tecla. Outras têm uma árvore de trabalho dedicada à "análise", usada apenas para ler logs e executar o BigQuery.


#2. Comece cada tarefa complexa no modo de planejamento. Dedique sua energia ao planejamento para que Claude possa executá-la de primeira.

Uma pessoa contrata um Claude para escrever o plano e, em seguida, aciona um segundo Claude para revisá-lo como engenheiro da equipe.

Outro diz que, no momento em que algo dá errado, eles voltam ao modo de planejamento e replanejam. Não insistam. Eles também instruem explicitamente Claude a entrar no modo de planejamento para as etapas de verificação, não apenas para a construção.


#3. Invista no seu http://CLAUDE.md . Após cada correção, termine com: "Atualize seu http://CLAUDE.md para não cometer esse erro novamente." Claude é assustadoramente bom em criar regras para si mesmo.

Edite impiedosamente seu http://CLAUDE.md ao longo do tempo. Continue iterando até que a taxa de erros de Claude diminua consideravelmente.

Um engenheiro diz a Claude para manter um diretório de notas para cada tarefa/projeto, atualizado após cada PR. Eles então apontam http://CLAUDE.md para ele.


#4. Crie suas próprias habilidades e as adicione ao Git. Reutilize-as em todos os seus projetos.

Dicas da equipe:
- Se você fizer algo mais de uma vez por dia, transforme isso em uma habilidade ou comando.
- Crie um comando de barra /techdebt e execute-o ao final de cada sessão para encontrar e eliminar código duplicado.
- Configure um comando de barra que sincronize 7 dias de Slack, Google Drive, Asana e GitHub em um único despejo de contexto.
- Criar agentes no estilo de engenheiros de análise que escrevam modelos dbt, revisem código e testem alterações em desenvolvimento.


#5. Claude corrige a maioria dos erros sozinho. Veja como fazemos isso:

Habilite o Slack MCP, cole uma conversa sobre um bug do Slack no Claude e simplesmente diga "corrigir". Não é necessário alternar entre contextos.

Ou simplesmente diga: "Vá corrigir os testes de CI que estão falhando." Não fique controlando cada detalhe do processo.

Mostre a Claude os logs do Docker para solucionar problemas em sistemas distribuídos -- ele é surpreendentemente capaz nisso.


#6. Aprimore suas sugestões

a. Desafie o Claude. Diga: "Me questione sobre essas mudanças e não faça um PR até que eu passe no seu teste." Faça do Claude seu revisor. Ou diga: "Prove que isso funciona" e peça ao Claude para comparar o comportamento entre a branch principal e a sua branch de recurso.

b. Após uma correção medíocre, diga: "Sabendo tudo o que você sabe agora, descarte isso e implemente a solução elegante."

c. Elabore especificações detalhadas e reduza a ambiguidade antes de entregar o trabalho. Quanto mais específico você for, melhor será o resultado.


#7. Configuração do Terminal e do Ambiente

A equipe adora o Ghostty! Várias pessoas gostam da renderização sincronizada, das cores de 24 bits e do suporte adequado a Unicode.

---

**INEMA** · 2026-02-08

## ✅ PASSO A PASSO DIRETO – WORKFLOW AGÊNTICO COM CLAUDE CODE

### 1️⃣ Instalar o ambiente

* Baixe **Visual Studio Code**
* Instale a extensão **Claude Code**
* Tenha um **plano pago do Claude** (Opus)

---

### 2️⃣ Criar um projeto

* Crie uma pasta no computador (ex: `agentic-workflows`)
* Abra essa pasta no VS Code
* Clique em **Claude Code Open**

---

### 3️⃣ Adicionar o arquivo `CLAUDE.md`

* Crie um arquivo chamado **`CLAUDE.md`** na raiz do projeto
* Cole nele as instruções do framework WAT
* Esse arquivo diz à IA:

  > “É assim que você deve trabalhar”

📌 Sem esse arquivo, o projeto fica caótico.

---

### 4️⃣ Deixar o Claude organizar o projeto

No chat do Claude Code, diga algo como:

> “Leia o `CLAUDE.md` e prepare a estrutura do projeto.”

Ele vai criar:

* `workflows/`
* `tools/`
* `.tmp/`
* `.env`

---

### 5️⃣ Escolher o modo correto

* Comece sempre em **Plan Mode**
* Isso evita execução errada

---

### 6️⃣ Descrever o objetivo (em linguagem natural)

Explique **o que você quer**, não como fazer.

Exemplo:

> “Quero coletar 200 vagas de emprego deste site e salvar em Excel.”

---

### 7️⃣ Responder perguntas do agente

O agente vai perguntar coisas como:

* Onde salvar o arquivo?
* Quantos resultados?
* Quais campos extrair?

👉 Responda de forma clara.

---

### 8️⃣ Revisar e aprovar o plano

O agente vai apresentar:

* Um **workflow**
* Uma ou mais **tools**
* Etapas de execução

Se estiver ok:

* Autorize
* Troque para **Auto Edit** ou **Bypass Permissions**

---

### 9️⃣ Deixar o agente executar

O agente vai:

* Criar tools (Python)
* Criar workflows (Markdown)
* Executar
* Corrigir erros sozinho
* Atualizar o sistema se algo falhar

Você só observa.

---

### 🔁 10️⃣ Reutilizar e melhorar

Da próxima vez que pedir algo parecido:

* Ele reutiliza workflows
* Ele melhora a qualidade
* Ele fica mais rápido

---

## 🧠 Regra de ouro (do vídeo)

Sempre defina:

* **Objetivo claro**
* **Critério de conclusão claro**

Exemplo ruim:

> “Quero leads.”

Exemplo certo:

> “Quero 100 leads de dentistas no Brasil, em Excel, com nome, telefone e site.”

---

## 🧭 Fluxo resumido em uma linha

**Objetivo → Perguntas → Plano → Aprovação → Execução → Auto-correção → Resultado**

---

**INEMA** · 2026-02-08

## 🧠 Resumo – Workflows Agênticos com Claude Code

### Ideia central

Os  **workflows agênticos mudam completamente a automação com IA**.
Em vez de construir fluxos rígidos passo a passo, você **define o objetivo**, e o agente:

* decide os passos,
* executa,
* corrige erros,
* aprende com o processo.

Tudo isso **sem precisar programar**.

---

## 🤖 O que são Workflows Agênticos

* **Automação tradicional**:
  Você define cada etapa manualmente (gatilhos, APIs, lógica, condições).
* **Workflows agênticos**:
  Você diz *o que quer*, e o agente descobre *como fazer*.

👉 Analogia principal:

* Automação tradicional = cozinhar seguindo receita
* Workflow agêntico = pedir um prato no restaurante

O agente pode fazer **perguntas de esclarecimento**, mas depois cuida de tudo.

---

## 🧱 Framework WAT

O vídeo gira em torno do framework **WAT**, composto por:

1. **Workflows**
   Instruções em linguagem natural (Markdown)
2. **Agent**
   A IA que pensa, planeja, decide e coordena
3. **Tools**
   Scripts (Python) que executam ações reais

Separar **decisão** de **execução** torna o sistema mais confiável.

---

## 🛠️ Ambiente (Claude Code)

O autor mostra que qualquer pessoa consegue usar:

* Visual Studio Code (gratuito)
* Extensão Claude Code
* Interface em formato de chat
* IA criando arquivos, ferramentas e workflows sozinha

Você **não precisa saber programar**.

---

## 📄 Arquivo CLAUDE.md

Um ponto-chave do vídeo.

O `CLAUDE.md`:

* é a **descrição de cargo da IA**
* ensina o agente a trabalhar dentro do WAT
* define regras, estrutura de arquivos e loop de melhoria

Sem ele, o projeto vira bagunça.

---

## 🔄 Modos de autonomia

O Claude Code pode operar em diferentes níveis:

* **Plan Mode** (só planeja)
* **Ask Before Edit**
* **Auto Edit**
* **Bypass Permissions** (autonomia total)

Boa prática: **sempre começar em Plan Mode**.

---

## 🌐 MCP (Model Context Protocol)

O MCP permite dar acesso a **serviços inteiros** (ex: Firecrawl), e o agente:

* escolhe quais ferramentas usar
* decide parâmetros
* combina ações sozinho

Analogia:

* MCP = supermercado
* Ferramentas individuais = lojas separadas

---

## 📊 Demonstrações práticas

O vídeo mostra o agente:

1. **Scraping de vagas de emprego**

   * Cria workflow + ferramenta
   * Exporta Excel estruturado
   * Aprende e reutiliza no futuro

2. **Busca filtrada de vagas**

   * Detecta limitação de dados
   * Propõe alternativas
   * Ajusta o plano sozinho

3. **Geração de leads (dentistas)**

   * Pesquisa fontes
   * Muda de estratégia quando falha
   * Corrige bugs
   * Atualiza ferramentas
   * Entrega Excel final completo

Tudo isso com **mínima orientação humana**.

---

## ⚠️ Erros comuns

O autor destaca dois erros principais:

1. **Objetivo vago**

   * “Quero um scraper de leads” é ruim
   * O certo é pedir ajuda para criar um PRD claro

2. **Não definir o que é “feito”**

   * O agente precisa saber quando parar
   * Entradas e saídas claras = resultados consistentes

---

## 🚀 Por que workflows agênticos são melhores

Segundo o vídeo:

* São **auto-corretivos**
* Não exigem conhecimento técnico
* Aprendem com o tempo
* Eliminam loops de debug
* Funcionam via linguagem natural

---

## ⚠️ Observação importante

* Automações **disparadas por humanos** têm agente presente → auto-correção em tempo real
* Automações **agendadas ou deployadas** usam só workflows e tools → sem auto-healing ao vivo

---

## 🎯 Mensagem final

Estamos saindo do papel de **executores** e virando **arquitetos de sistemas**.

Quem aprender a:

* definir bons objetivos,
* estruturar workflows,
* usar agentes corretamente,

vai sair na frente na nova era da automação.

---

### Em uma frase

> Como transformar IA em um agente autônomo, confiável e auto-evolutivo, usando linguagem natural em vez de código.

---

**INEMA** · 2026-02-08

## 🧩 O que é o arquivo (CLAUDE.md / CLAUDE_traduzido_ptbr.md)**

Esse arquivo **não é um tutorial** e **não é conteúdo educativo**.
Ele é um **documento de comando**.

👉 Em termos simples:
**ele define como a IA deve se comportar dentro do projeto.**

Se o PDF é a *aula* e o resumo é o *material de estudo*,
o **CLAUDE.md**** é o manual de trabalho da IA**.

---

## 🧠 Papel real desse arquivo

O `CLAUDE.md` funciona como:

* descrição de cargo do agente
* manual interno de operação
* regras de decisão
* contrato de comportamento

Quando esse arquivo existe em um projeto, a IA entende:

> “É assim que eu devo pensar, decidir, agir, errar e melhorar.”

---

## 🏗️ O que ele define, na prática

### 1️⃣ A arquitetura WAT

Ele deixa explícito que o projeto segue o modelo:

* **Workflows** → dizem *o que* deve ser feito
* **Agent** → decide *como* fazer
* **Tools** → executam *de forma determinística*

Isso impede a IA de:

* improvisar execução
* misturar decisão com código
* tentar “fazer tudo sozinha”

---

### 2️⃣ Qual é o papel do agente (da IA)

O arquivo diz claramente que a IA:

* **não é executora direta**
* é uma **orquestradora inteligente**
* deve:

  * ler instruções
  * escolher ferramentas
  * lidar com falhas
  * perguntar quando faltar informação

Ou seja:
👉 ela pensa como um **gestor técnico**, não como um script.

---

### 3️⃣ Como lidar com erros

Esse é um ponto-chave.

O arquivo obriga a IA a seguir um ciclo quando algo falha:

1. entender o erro
2. corrigir a ferramenta
3. testar a correção
4. atualizar o workflow
5. seguir adiante melhor do que antes

Isso cria **sistemas que aprendem**, não fluxos descartáveis.

---

### 4️⃣ O que a IA **não pode fazer**

O documento também impõe limites claros:

* não sobrescrever workflows sem permissão
* não criar bagunça na estrutura de arquivos
* não salvar segredos fora do `.env`
* não tratar arquivos locais como entregáveis finais

Essas regras evitam projetos frágeis e caóticos.

---

### 5️⃣ Organização do projeto

Ele define um padrão fixo de pastas:

* `workflows/` → instruções
* `tools/` → código
* `.tmp/` → lixo regenerável
* `.env` → segredos

Isso faz com que qualquer projeto:

* seja previsível
* seja escalável
* possa ser mantido por outra pessoa

---

## 🧭 Por que esse arquivo é tão importante

Sem esse arquivo:

* a IA improvisa
* a qualidade cai rápido
* erros se repetem
* cada tarefa vira algo descartável

Com esse arquivo:

* a IA trabalha com método
* projetos ficam reutilizáveis
* erros viram aprendizado
* o sistema melhora com o tempo

---

**INEMA** · 2026-02-08

## 🧠 Resumo  – Workflows Agênticos com Claude Code

### Ideia central

O documento ensina **o que são workflows agênticos** e por que eles são superiores à automação tradicional.
Em vez de programar cada passo, você **diz o objetivo** e o agente decide **como chegar lá**.

---

### 🤖 O que são Workflows Agênticos

* Na automação tradicional, você define **todas as etapas manualmente**
* Nos workflows agênticos:

  * Você define o **objetivo**
  * O agente planeja, executa, corrige erros e melhora o processo sozinho
  * Ele só faz perguntas quando precisa de esclarecimento

👉 Analogia principal:

* Automação tradicional = cozinhar seguindo receita
* Workflow agêntico = pedir um prato no restaurante

---

### 🧱 Framework WAT

O documento apresenta o **framework WAT**, composto por:

1. **Workflows**
   Instruções em linguagem natural (Markdown) dizendo *o que fazer*
2. **Agent**
   A IA que pensa, decide, coordena e aprende
3. **Tools**
   Scripts (Python) que executam ações concretas

Separar pensamento de execução aumenta muito a confiabilidade.

---

### 🛠️ Ambiente de Trabalho

O guia mostra como configurar:

* Visual Studio Code
* Extensão Claude Code
* Estrutura básica de projeto

Tudo é pensado para **quem não sabe programar**.

---

### 📄 Arquivo CLAUDE.md

Um ponto-chave do texto é o `CLAUDE.md`, que:

* Define como o agente deve operar
* Funciona como descrição de cargo da IA
* Permite reaproveitar o mesmo padrão em vários projetos

---

### 🔄 Modos de operação do Claude Code

O agente pode operar com diferentes níveis de autonomia:

* Planejamento apenas
* Pedir permissão antes de editar
* Editar automaticamente
* Autonomia total (com cautela)

Boa prática: **sempre começar em modo de planejamento**.

---

### 🌐 MCP (Model Context Protocol)

O MCP permite dar acesso a **serviços inteiros** (como Firecrawl), sem precisar explicar APIs.
O agente escolhe:

* Qual ferramenta usar
* Quando usar
* Como preencher parâmetros

---

### 📊 Exemplos práticos

O documento mostra vários casos reais:

* Scraping de vagas de emprego
* Filtros inteligentes de dados
* Geração de leads (dentistas)
* Correção automática de erros durante a execução

Esses exemplos mostram o agente:

* Reutilizando ferramentas
* Mudando de estratégia quando algo falha
* Aprendendo com erros

---

### ⚠️ Boas práticas e erros comuns

Destaques importantes:

* Sempre definir **objetivo claro**
* Sempre definir **quando o trabalho termina**
* Evitar prompts vagos
* Tratar a IA como um especialista, não como executor burro

---

### 🚀 Por que workflows agênticos são melhores

Segundo o documento:

* São auto-corretivos
* Não exigem conhecimento técnico
* Ficam mais inteligentes com o tempo
* Reduzem manutenção e retrabalho

---

## 🎯 Em uma frase

> O arquivo ensina como sair da automação rígida e entrar num modelo onde a IA pensa, decide, executa e melhora processos sozinha — com você apenas definindo objetivos claros.

---

**INEMA** · 2026-02-08

Basico de usar o Claude Code

---

**INEMA** · 2026-02-08

https://chatgpt.com/c/698718ac-ee90-8331-996c-5259db4db6a1
