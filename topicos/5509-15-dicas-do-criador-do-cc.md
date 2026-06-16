# 15 Dicas do Criador do CC

> Tópico 5509 · 4 mensagens úteis de 12 totais

---

**INEMA** · 2026-05-04

paralelizável.

🚀 **Dica 12: `--bare` para acelerar a inicialização do SDK em até 10x**
Ao rodar `claude -p` — ou os SDKs de TypeScript/Python — o Claude procura arquivos locais `CLAUDE.md`, configurações e MCPs por padrão. Para uso não interativo, quase nunca é isso que você quer. Desative com `--bare` e passe explicitamente o que precisar via `--system-prompt`, `--mcp-config` etc. Boris diz que isso foi uma falha de design e que uma versão futura deve inverter o padrão.

📁 **Dica 13: `--add-dir` para trabalhar com vários repositórios**
Ao trabalhar em múltiplos repositórios, Boris inicia o Claude em um deles e usa `--add-dir` ou `/add-dir` para dar acesso aos outros. Isso informa o Claude sobre o repositório e concede as permissões corretas, sem precisar ficar alternando entre sessões separadas.

🤖 **Dica 14: `--agent` para prompts de sistema e ferramentas personalizados**
Agentes personalizados são uma primitiva poderosa que a maioria das pessoas ignora. Coloque um arquivo `.md` em `.claude/agents` e depois rode `claude --agent=<nome-do-seu-agent>`. Você ganha controle total sobre o prompt de sistema e o conjunto de ferramentas daquela sessão.

🎙️ **Dica 15: `****/voice****` para entrada por voz**
Boris faz a maior parte da programação falando com o Claude, não digitando. Rode `/voice` no CLI e segure a barra de espaço, toque no botão de voz no Desktop ou habilite a ditado nas configurações do iOS.

---

**INEMA** · 2026-05-04

**15 recursos ocultos e pouco utilizados do Claude Code**


Boris Cherny é o cara que **criou o Claude Code**.

Ele acabou de publicar uma thread com seus recursos ocultos e subutilizados favoritos.

Preparei um TL;DR bem direto para você.

Aqui vai cada dica 👇

📱 **Dica 1: Existe um app mobile**
Abra o app Claude no iOS ou Android e toque na aba **Code** à esquerda. Você pode rodar sessões completas do Claude Code pelo celular. A maioria das pessoas nem sabe que isso existe.

🔄 **Dica 2: Teletransporte entre dispositivos**
Use `claude --teleport` ou `/teleport` para retomar uma sessão na nuvem na sua máquina local. Use `/remote-control` para controlar uma sessão local pelo celular ou navegador. Boris deixa a opção **“Enable Remote Control for all sessions”** ativada por padrão no `/config`.

⏰ **Dica 3: `****/loop****` e `****/schedule****`**
Dois dos recursos mais poderosos do Claude Code. Você pode agendar o Claude para rodar automaticamente em intervalos definidos por até uma semana. Boris usa isso para acompanhar PRs, resolver automaticamente comentários de code review e abrir PRs com feedbacks do Slack a cada 30 minutos. O truque é transformar seus melhores fluxos de trabalho em **skills** e depois colocá-los em loop.

⚙️ **Dica 4: Hooks**
Rode lógica determinística em qualquer ponto do ciclo de vida do agente. Carregue contexto no início da sessão (`SessionStart`), registre cada comando bash que o Claude executa (`PreToolUse`), envie solicitações de permissão para o WhatsApp para aprovação remota (`PermissionRequest`) ou incentive o Claude a continuar quando ele parar (`Stop`). A maioria das pessoas nunca mexeu em hooks. É ali que está a verdadeira alavancagem.

🖥️ **Dica 5: Cowork Dispatch**
Boris usa o Dispatch todos os dias quando não está no computador. É um controle remoto seguro para o app Claude Desktop: ele acompanha Slack e e-mail, gerencia arquivos e faz coisas no laptop enquanto Boris está longe. Usa todos os seus MCPs, seu navegador, tudo.

🌐 **Dica 6: A extensão do Chrome para frontend**
A dica mais importante para usar o Claude Code é dar ao Claude uma forma de verificar o próprio resultado. Boris usa a extensão do Chrome sempre que trabalha com código web. Pense como se fosse qualquer outro engenheiro: se você não der um navegador para ele, o resultado visual provavelmente não vai ficar bom. Dê um navegador ao Claude e ele vai iterar até ficar bom. Na experiência dele, funciona com mais confiabilidade do que MCPs parecidos.

🖥️ **Dica 7: Deixe o app Desktop rodar e testar seu servidor web**
O app Desktop já vem com a capacidade de fazer o Claude subir automaticamente seu servidor web e testá-lo em um navegador embutido. Dá para replicar isso no CLI ou no VSCode usando a extensão do Chrome, mas no app Desktop isso já vem pronto.

🌿 **Dica 8: Faça um fork da sua sessão**
Há duas formas de criar um fork de uma sessão existente: execute `/branch` dentro da sessão ou, pelo CLI, rode `claude --resume <session-id> --fork-session`. Útil quando você quer explorar uma direção diferente sem perder o ponto em que estava.

💬 **Dica 9: `****/btw****` para perguntas paralelas**
Faça uma pergunta rápida ao Claude no meio de uma tarefa sem quebrar o fluxo. Boris usa isso o tempo todo. É uma interação de turno único, sem chamadas de ferramentas, mas o Claude tem todo o contexto do que está fazendo, então a resposta continua bem fundamentada.

🌿 **Dica 10: Git worktrees**
O Claude Code tem suporte nativo profundo a worktrees. Rode `claude -w` para iniciar uma sessão em um novo worktree, ou marque a opção de worktree no app Desktop. Boris mantém dezenas de Claudes rodando em paralelo o tempo todo — é assim que ele faz isso. Usuários de sistemas de controle de versão que não sejam Git podem usar o hook `WorktreeCreate` para adicionar lógica personalizada.

📦 **Dica 11: `****/batch****` para changesets enormes**
O `/batch` entrevista você e depois distribui o trabalho para quantos agentes em worktrees forem necessários — dezenas, centenas ou até milhares. Boris usa isso para grandes migrações de código e qualquer tipo de trabalho

---

**INEMA** · 2026-05-04

15 Dicas do Criador do CC

---

**INEMA** · 2026-05-04

https://chatgpt.com/c/69f90c55-c130-8328-a371-d1b379472346
