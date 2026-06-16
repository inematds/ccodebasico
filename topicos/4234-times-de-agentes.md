# Times de Agentes

> Tópico 4234 · 3 mensagens úteis de 13 totais

---

**INEMA** · 2026-03-25

Direto ao ponto.

**1) Verifique a versão**
Agent Teams requer **Claude Code v2.1.32 ou superior**. ([Claude][1])

```claude --version```

**2) Habilite o recurso**
A Anthropic diz para ativar `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1` no ambiente ou no `settings.json`. ([Claude][1])

Opção rápida no terminal atual:

```export CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1```

Para deixar no projeto, crie/edite o arquivo de config:

```mkdir -p .claude
cat > .claude/settings.local.json <<'EOF'
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
EOF```

**3) Rodar o Claude**

```claude```

**4) Pedir um time de agentes**
Dentro do Claude Code, use linguagem natural. Exemplo prático: ([Claude][1])

```Crie um agent team com 3 teammates usando Sonnet.
Objetivo: construir uma landing page de startup de IA.

Teammate 1: Front-end developer
- cuidar de layout, componentes e animações
- entregar interface pronta

Teammate 2: Back-end developer
- cuidar de API mock, estrutura de dados e integrações
- entregar serviços necessários para a UI

Teammate 3: QA agent
- validar fluxo, achar bugs e devolver correções para os devs
- só marcar como concluído quando os problemas críticos forem resolvidos

Entregáveis finais:
- app rodando localmente
- relatório de testes
- resumo do que foi feito```

**5) Forçar modo simples no mesmo terminal**
Se quiser evitar split panes:

```claude --teammate-mode in-process```

O modo `in-process` funciona em qualquer terminal; split panes pedem `tmux` ou iTerm2. ([Claude][1])

**6) Usar com tmux**
Se quiser ver cada agente em um painel separado, a doc recomenda `tmux` e cita `tmux -CC` no iTerm2 como entrada sugerida. ([Claude][1])

Exemplo:

```tmux
claude```

Se precisar limpar sessão travada depois:

```tmux ls
tmux kill-session -t NOME_DA_SESSAO```

([Claude][1])

**7) Comandos úteis em linguagem natural**
Durante a execução, você pode pedir coisas assim: ([Claude][1])

```Use Sonnet para cada teammate.```

```Exija aprovação de plano antes de implementar.```

```Peça para o researcher teammate encerrar.```

```Clean up the team```

**8) Quando usar**
Use quando houver trabalho em paralelo, como frontend + backend + testes, pesquisa em paralelo, ou hipóteses concorrentes de debug. Para tarefas sequenciais, simples, ou com muita edição no mesmo arquivo, a própria doc recomenda sessão única ou subagents. ([Claude][1])

**Setup mínimo completo**

```mkdir -p .claude
cat > .claude/settings.local.json <<'EOF'
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
EOF

claude --teammate-mode in-process```

Depois, já dentro do Claude:

```Crie um agent team com 3 teammates usando Sonnet: front-end, back-end e QA. Objetivo: construir uma landing page completa e validar tudo antes de encerrar.```

Posso te passar agora um **template de prompt pronto** para usar em projeto React/Node.

[1]: https://code.claude.com/docs/en/agent-teams "Orchestrate teams of Claude Code sessions - Claude Code Docs"

---

**INEMA** · 2026-03-25

**Agent Teams no Claude Code** para obter resultados melhores do que com um único agente ou com subagentes simples.

**Resumo do conteúdo:**

Um **agent team** é formado por vários agentes especializados trabalhando juntos sob coordenação de um agente principal. No exemplo, um time com **front-end**, **back-end** e **QA**. Esses agentes trabalham **em paralelo**, compartilham uma lista de tarefas e podem **conversar entre si**, o que permite ciclos de revisão: os devs entregam para o QA, o QA encontra erros, e o trabalho volta para correção até ficar bom.

A principal diferença em relação a **subagentes** é que subagentes trabalham mais isolados e retornam resultados ao agente principal, enquanto **agent teams colaboram entre si diretamente**, como uma equipe real com funções complementares.

**Como ativar a função**, já que ela é experimental: basta adicionar uma variável/configuração no `settings.local.json` do projeto. Depois disso, recomenda-se criar uma **documentação local de referência** sobre agent teams dentro do projeto, para que o Claude consulte esse material com mais rapidez no futuro.

Na parte de **prompting**, sugere-se uma estrutura clara:

* definir primeiro o **objetivo geral**;
* informar **quantos agentes** haverá;
* escolher o **modelo**;
* descrever o papel de cada agente;
* dizer com quem cada um deve falar;
* e deixar explícitos os **entregáveis finais**.

Algumas boas práticas:

* cada agente deve ter **responsabilidade sobre arquivos ou entregas específicas**;
* é importante dar **contexto completo**, porque os agentes não começam com histórico;
* vale manter equipes pequenas, em geral **de 3 a 5 agentes**;
* e é melhor evitar agentes demais, porque isso aumenta custo e lentidão.

No terminal com **tmux**, fica mais fácil acompanhar visualmente o que cada agente está fazendo e até interagir com agentes específicos individualmente. Isso ajuda muito no monitoramento e correção de rumo.

Regras práticas para melhorar o uso:

* agentes devem ter **territórios bem definidos**;
* comunicação direta entre agentes é uma das maiores vantagens;
* o trabalho deve acontecer em **paralelo**, não apenas em sequência;
* todos herdam permissões, arquivos, skills e MCPs da sessão principal;
* e é possível usar um modo de **aprovação de planos** antes da execução.

Lista problemas comuns e soluções:

* muitas interrupções por permissão → pré-aprovar ferramentas/comandos;
* entregas confusas → definir donos de arquivos;
* agente ocioso → atribuir tarefas e dependências mais claras;
* custo alto → usar menos agentes;
* perda de trabalho → salvar resultados em arquivos temporários;
* aprovações ruins → deixar o humano aprovar até entender melhor o fluxo.

Por fim,  **quando usar agent teams**:

* quando o projeto é **complexo**;
* quando há áreas especializadas diferentes;
* quando tarefas precisam ser feitas **ao mesmo tempo**;
* quando agentes precisam **reagir uns aos outros**;
* e quando se busca maior qualidade.

E quando **não usar**:

* em tarefas simples;
* quando tudo é sequencial;
* quando todos precisam mexer no mesmo arquivo;
* ou quando o custo/tokens importa muito.

**Ideia central:**
Agent Teams são muito poderosos para trabalhos complexos e colaborativos, mas só entregam bem quando você define claramente **papéis, contexto, comunicação e entregáveis**. Eles custam mais e são mais lentos, então devem ser usados com critério.

---

**INEMA** · 2026-03-25

https://chatgpt.com/c/69c35600-82d0-8325-b55d-4b3af3f1e35c
