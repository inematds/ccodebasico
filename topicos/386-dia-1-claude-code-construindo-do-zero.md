# Dia 1: Claude Code Construindo do Zero

> Tópico 386 · 7 mensagens úteis de 19 totais

---

**INEMA** · 2025-08-25

sugestões.

23. checklist de término de fase

* hack: cada fase termina com: build local ok, screenshot salvo, commit, resumo do que mudou em 5 linhas.

hacks de recuperação rápida
24\) diffs e bissecção

* hack: se quebrou “do nada”, rode um diff do último bom para agora. Em casos ruins, use bissecção manual por metades de alterações.

25. rotina “volta ao estável”

* hack: mantenha um script npm run rescue que reseta node\_modules, limpa cache e reinstala.
* exemplo package.json:
  "rescue": "rimraf node\_modules .next dist && npm i"

perguntas rápidas com respostas e exemplos

1. e se o Playwright não listar as ferramentas após instalar?
   resposta: reinicie o terminal do Claude Code e rode a chamada mínima.
   exemplo: “liste ferramentas do MCP X e execute uma busca simples em Ref”.

2. como sabotar menos o plano com detalhes demais?
   resposta: defina requisitos visuais e de UX, não nome de libs.
   exemplo: “cards com hover suave” em vez de “Framer Motion X”.

3. cache insiste em mostrar site antigo.
   resposta: mude porta, feche sessões, limpe cache do dev server e reabra.
   exemplo: rodar em 3001 e matar processos em 3000.

4. como garantir commits úteis?
   resposta: force mensagens com causa, ação e impacto.
   exemplo: “fix(css): remove .hidden em .section-hero; conteúdo volta a renderizar no mobile”.

5. deploy falhou no Vercel, e agora?
   resposta: copie logs de erro, peça ao Claude “patch mínimo”, commite e redeploy.
   exemplo: “corrigir script build faltando ‘next build’ e adicionar dependência faltante”.

6. quando usar dangerously-skip-permissions?
   resposta: em branch de experimento. Na principal, aceite permissões e registre no .claude/ para evitar bloqueios silenciosos.

7. vale usar agente dedicado para UI?
   resposta: sim, após base estável. Ele roda screenshots e dá nota, indicando ajustes rápidos.

---

**INEMA** · 2025-08-25

Aqui vai um pacote de hacks práticos para acelerar e evitar dor de cabeça no fluxo com Claude Code, Cursor e MCPs. Curto, direto e acionável.

hacks de planejamento e setup

1. plano .md enxuto e à prova de erro

   * hack: descreva o que, não o como. Evite travar libs (ex.: Framer Motion) no início.
   * exemplo: “hero com CTA verde, seção serviços em cards, formulário de lead; sem animações por enquanto”.

2. arquivo de comando da sessão

   * hack: crie session-notes.md com decisões, pendências e links de erro. O Claude usa isso como memória leve.

3. modelos e chamadas prontos

   * hack: mantenha models-to-use.md com snippets de chamada de API que você realmente usa. Cola o trecho certo sem pesquisar de novo.

hacks de MCPs (Playwright, Exa, Ref)
4\) valide MCPs de verdade

* hack: depois de instalar, liste ferramentas e execute 1 chamada real. Se não retornar algo útil, reinicie o terminal e revalide.
* exemplo: peça ao Ref para buscar um parágrafo específico de doc e mostrar a citação.

5. chaves e limites

   * hack: salve as keys em .env.local e documente escopo/limite no session-notes.md. Evita “funcionava ontem”.

6. quando usar Exa vs web search do Claude

   * hack: Exa para docs e “deep dev search”; web search para páginas oficiais recentes. Se falhar, troque imediatamente.

hacks de modos do Claude
7\) ask mode primeiro, agent depois

* hack: peça plano e critérios de aceite no ask mode; só então mude para agent. Menos alucinação, mais previsibilidade.

8. perigos do dangerously-skip-permissions

   * hack: use só em branch descartável. Em projeto principal, aceite permissões na primeira rodada e grave no .claude/.

hacks de prompts realmente úteis
9\) prompt de fases com commit automático

* exemplo:
  “Implemente Fase 1: estrutura + layout base + formulário mock. Valide com Playwright (screenshot). Commit ‘F1 done’. Pare e reporte.”

10. prompt de inspeção visual

* exemplo:
  “Use Playwright para abrir localhost atual, tirar screenshot e descrever problemas de UI em tópicos com ações correção.”

11. prompt de rollback orientado

* exemplo:
  “Se erro crítico for detectado, reverta para último commit estável e gere diff explicando o que quebrou e por quê.”

hacks de debug veloz
12\) portas e cache

* hack: padronize 3001 para o projeto atual e mate o que estiver em 3000 antes de rodar. Limpe cache do dev server ao trocar branch.
* comandos úteis:
  mac/linux: lsof -i :3000; kill -9 PID
  windows: netstat -ano | findstr :3000 → taskkill /PID <pid> /F

13. CSS invisível

* hack: procure classes com display\:none/opacity:0/overflow/position absolute fora do viewport. Gere um “debug.css” temporário que destaca blocos com outline.

14. incompatibilidades por plano detalhista

* hack: se quebrou após “seguir o plano”, remova nomes de libs do plano e deixe o Claude escolher o equivalente nativo/simples.

15. screenshots como verdade

* hack: confie no que o Playwright vê, não no que você acha. Se screenshot mostra outra app, é cache/porta errado.

hacks de versionamento e segurança
16\) commits de marco

* hack: 1 commit por fase com mensagem clara. Se possível, 1 branch por fase e PR para a main.

17. mensagens ricas

* hack: force o Claude a escrever mensagens de commit com causa/efeito: “fix: remove animação X que ocultava .hero em mobile”.

18. checkpoints manuais

* hack: marque versões “boas” com tags leves: v0.1-landing-ok, v0.2-form-ok.

hacks de deploy
19\) vercel sem susto

* hack: antes do deploy, rode npm run build local. Se falhar local, vai falhar no Vercel.
* se der erro no Vercel: copie o trecho do log, cole no Claude e peça “patch mínimo” com commit.

20. autosync estável

* hack: só faça deploy automático da main; use branches para features e PRs para manter histórico limpo.

hacks de produtividade
21\) output style sob medida

* hack: peça “explique como para 12 anos; esconda código a não ser que eu peça; sempre liste próximos 3 passos”. Reduz ruído.

22. agente inspetor de UI

* hack: crie um script que roda Playwright, salva 3 screenshots (desktop/tablet/mobile) e o Claude pontua 0–10 com

---

**INEMA** · 2025-08-25

Playwright para abrir o localhost e tirar um screenshot ao final. Faça commit com a mensagem ‘Fase 1 concluída’.”

Diagnóstico de porta ocupada

* Verifique qual porta está em uso; se necessário, suba em 3001 e feche processos antigos.

Commit e push

```git add .
git commit -m "Fase X: descrição clara do marco"
git push origin main```

Deploy Vercel

* Painel do Vercel: Import → selecione o repo → Deploy.
* Se erro de dependência: leia os logs do build, ajuste package.json ou scripts, commit e redeploy.

# Perguntas rápidas (com respostas)

1. Como evito quebrar tudo com libs de animação?
   Resposta: não fixe libs específicas no plano inicial. Construa o layout base; só depois teste animações.

2. Como sei se a porta está ocupada?
   Resposta: se o localhost não mostra seu projeto, mude para 3001 ou encerre o processo antigo antes de subir.

3. O Playwright é obrigatório?
   Resposta: não, mas acelera o feedback visual (screenshots) e ajuda a detectar problemas cedo.

4. Quando usar dangerously-skip-permissions?
   Resposta: apenas quando estiver seguro do que o agente fará; ele pulará confirmações e pode alterar/deletar arquivos.

5. Por que commits frequentes?
   Resposta: para reverter facilmente se algo quebrar; trate cada fase como um marco versionado.

6. O que fazer se o deploy no Vercel falhar?
   Resposta: abra os logs, corrija dependências/configs, commit e redeploy. Normalmente é ajuste de build.

7. Preciso do GitHub desde o começo?
   Resposta: ajuda muito. O histórico de commits vira seu “checkpoint” para desfazer erros.

8. Cache confundindo versões?
   Resposta: feche instâncias antigas, limpe cache, reinicie o server correto, e valide a porta ativa.

9. Posso usar outro IDE?
   Resposta: sim. O passo a passo continua válido (VS Code/Windsurf funcionam).

10. Quando ativar agentes extras (validador de UI etc.)?
    Resposta: após a base estável; cada agente adiciona complexidade e custo de contexto.

---

**INEMA** · 2025-08-25

Aqui vai um checklist passo a passo, prático e direto, para repetir o que o  fez (com dicas para evitar as mesmas dores).

# Passo a passo – do zero ao deploy

1. Preparar o ambiente

* Tenha: Node.js, npm, Git, conta no GitHub e no Vercel, um IDE (Cursor recomendado).
* Instale/abra o Claude Code no IDE.
* Verifique versões:

```node -v
npm -v
git --version```

2. Criar o projeto e o planejamento

* Crie uma pasta vazia para o projeto.
* No IDE, crie website-plan.md com: objetivo do site, páginas, paleta de cores, componentes, formulário de lead (nome, sobrenome, empresa, o que faz, e-mail, telefone, botão AUDIT MY BUSINESS).
* Mantenha o plano em alto nível. Evite forçar bibliotecas específicas (ex.: Framer Motion) nesta fase.

3. Inicializar o Claude Code com o plano

* No terminal do Claude Code:

/```init
```
* Ele lerá o website-plan.md e criará um arquivo de orientação do projeto (ex.: claude.md).

4. Conectar o repositório GitHub e versionar

* No terminal do Claude Code:

/g```it

```* Autentique o GitHub, crie um repositório para o projeto e faça o primeiro commit.
* Garanta commits a cada marco que o Claude completar.

5. Adicionar MCPs e validar

* Adicione MCP Playwright (testes e screenshots), Exa (busca), RefTools (docs).
* Pegue as chaves de API (Exa e Ref.tools) e configure-as.
* Valide se os MCPs estão visíveis/ativos e listam ferramentas.
* Se precisar, feche/reabra o terminal do Claude Code após instalar.

6. Definir modo de trabalho do Claude

* Use Ask mode para planejar e revisar; Agent mode para executar.
* Só use dangerously-skip-permissions quando souber o que está fazendo (pula confirmações e pode apagar/alterar arquivos sem perguntar).

7. Construir a base do site

* Peça ao Claude (Agent mode) para:

  1. Criar estrutura do projeto,
  2. Implementar layout inicial e estilos,
  3. Implementar o formulário de lead (mock, sem funcionalidade),
  4. Configurar Playwright para abrir o localhost e tirar screenshots a cada marco,
  5. Fazer commits ao final de cada fase.

8. Rodar localmente e checar

* O servidor subirá em localhost (3000, 3001, etc.).
* Se a porta estiver ocupada, mude para outra ou encerre processos antigos.
* Use o Playwright para validar visualmente e detectar erros de CSS/DOM.

9. Depurar problemas comuns

* Página “quebrada” ou feia: verifique classes CSS que escondem conteúdo.
* Cache teimoso: feche sessões antigas, limpe cache, reinicie o servidor do projeto certo (ex.: 3001).
* Conflitos de libs: se algo que você especificou no plano quebrar (ex.: animações), remova e volte ao alto nível.

10. Preparar para deploy

* Confirme que build e start funcionam:

npm``` run build
npm start

*``` Faça push para a branch main com histórico limpo de commits.

11. Deploy no Vercel

* No Vercel: New Project → importe o repositório.
* Deploy. Se falhar, abra os logs, ajuste dependências/configs, faça novo commit e redeploy.
* Ao finalizar, você terá uma URL pública e pushs futuros na main redeployam automaticamente.

12. Pós-deploy e próximos passos

* Abra a URL pública e valide.
* Se quiser, adicione domínio customizado.
* Opcional: crie um models-to-use.md com snippets de chamada de modelos, e considere agentes auxiliares (validador de UI, auditor de CSS, etc.) para iterações futuras.

# Exemplos úteis por etapa

Planejamento (.md)

* Estrutura mínima:

Obje```tivo: Site de consultoria em IA com captura de leads.
Páginas: Home, Serviços, Sobre, Contato/Lead.
Formulário: nome, sobrenome, empresa, o que faz, e-mail, telefone, botão "AUDIT MY BUSINESS".
Paleta: fundo claro, destaque verde no CTA, tipografia moderna.
Requisitos: design limpo, responsivo, sem libs de animação obrigatórias.

Pr```ompt (Ask mode) para gerar o plano detalhado

* Exemplo:
  “Revise website-plan.md e gere um plano de execução em fases. Não escreva código ainda. Liste marcos, critérios de aceite, checkpoints do Playwright e commits esperados.”

Prompt (Agent mode) para construir

* Exemplo:
  “Implemente a Fase 1: estrutura do projeto, layout base e página Home com o formulário mock. Configure

---

**INEMA** · 2025-08-25

## Resumo – Claude Code: Construindo um site do zero

### Objetivo da aula

* Mostrar que qualquer pessoa, mesmo sem background técnico, pode sair do zero e construir algo com Claude Code.
* Construir em público, sem cortes, incluindo erros e dificuldades, para quebrar a ideia de que tudo sai perfeito logo na primeira vez.
* O projeto escolhido: **site de consultoria em IA** com formulário de captura de leads e possibilidade de rodar um mini “AI audit”.

---

### Etapas principais

1. **Preparação inicial**

   * Uso do **Cursor** como IDE (mas pode ser outro).
   * Configuração dos servidores MCP (Playwright, Exa, RefTools).
   * Criação de um arquivo de planejamento em **.md** para estruturar o projeto (páginas, cores, elementos, etc.).
   * Uso dos modos do Claude:

     * *Ask mode*: só planeja e gera conteúdo.
     * *Agent mode*: executa ações (cria, edita, roda código).
     * *YOLO / dangerously skip permissions*: ignora permissões e roda direto (arriscado).

2. **Construção do site**

   * Início com **estrutura básica em HTML/CSS**.
   * Uso do **Playwright** para rodar localmente e tirar screenshots.
   * Identificação de problemas como:

     * Conflito de portas (3000 vs 3001).
     * Cache mostrando versão antiga do projeto.
     * Incompatibilidade com **Framer Motion + CSS**, causando erros críticos.
     * CSS ocultando elementos ao invés de exibi-los.

3. **Depuração**

   * Sessão de debug de quase 40 minutos para identificar incompatibilidades.
   * Descoberta de que o problema não estava na execução, mas no **plano inicial errado** (componentes incompatíveis).
   * Ajustes feitos removendo instruções técnicas específicas do plano.

4. **GitHub e versionamento**

   * Conexão com repositório GitHub.
   * Uso de **commits a cada fase** para manter histórico.
   * Revisão das alterações feitas pelo Claude automaticamente.

5. **Deploy**

   * Escolha do **Vercel** (mas também comparado com Netlify, Render, DigitalOcean).
   * Primeira tentativa falhou por falta de dependências.
   * Ajuste feito a partir dos logs → sucesso no segundo deploy.
   * Site no ar, agora totalmente personalizável e sem dependência de plataformas externas.

---

### Lições principais

* **Planejamento em .md** é fundamental: clareza evita erros e retrabalho.
* **Validação contínua** com Playwright e commits no GitHub garante controle.
* **Evitar planos técnicos muito detalhados** no início, pois pode gerar incompatibilidades.
* **Erros fazem parte do processo**: depuração real é diferente do que tutoriais polidos mostram.
* **Benefício final**: possuir o próprio código, com controle total e aprendizado sobre o que quebra e por quê.

---

---

**INEMA** · 2025-08-25

Dia 1: Claude Code Construindo do Zero

---

**INEMA** · 2025-08-25

https://chatgpt.com/c/68abe3ba-5e7c-8331-8f81-038616acf9df
