# AGENT VIEW - Gestão de Terminais

> Tópico 5683 · 3 mensagens úteis de 13 totais

---

**INEMA** · 2026-05-12

No **Agent View**, você tem dois grupos de comandos: os **comandos de shell** para gerenciar sessões e os **atalhos dentro da tela**.

## Comandos no shell

```claude agents```

Abre o Agent View.  

```claude --bg "sua tarefa aqui"```

Cria uma sessão em background direto do terminal.  

```claude attach <id>```

Entra/anexa em uma sessão específica.

```claude logs <id>```

Mostra a saída recente da sessão.

```claude stop <id>```

Para uma sessão. Também aceita `claude kill`.

```claude respawn <id>```

Reinicia uma sessão parada mantendo a conversa.

```claude respawn --all```

Reinicia todas as sessões paradas.

```claude rm <id>```

Remove a sessão da lista. ([Claude][1])

## Comandos dentro de uma sessão Claude Code

```/bg```

ou

```/background```

Manda a sessão atual para o background e faz ela aparecer no Agent View.

Também pode mandar uma última instrução antes de backgroundar:

```/bg run the tests and fix any failures```

([Claude][1])

## Atalhos dentro do Agent View

| Atalho                    | Ação                                                                              |
| ------------------------- | --------------------------------------------------------------------------------- |
| `↑` / `↓`                 | navegar entre sessões                                                             |
| `Enter`                   | anexar na sessão selecionada ou disparar uma nova tarefa se houver texto no input |
| `Space`                   | abrir/fechar preview da sessão                                                    |
| `Shift + Enter`           | disparar uma nova sessão e já anexar nela                                         |
| `→`                       | anexar na sessão selecionada                                                      |
| `Alt + 1` até `Alt + 9`   | anexar direto na Nª sessão do grupo                                               |
| `Tab`                     | navegar por subagents ou aplicar sugestão                                         |
| `Ctrl + S`                | alternar agrupamento por status ou diretório                                      |
| `Ctrl + T`                | fixar/desfixar sessão                                                             |
| `Ctrl + R`                | renomear sessão                                                                   |
| `Ctrl + G`                | abrir o prompt no editor `$EDITOR`                                                |
| `Ctrl + X`                | parar sessão; apertar de novo em até 2s deleta                                    |
| `Shift + ↑` / `Shift + ↓` | reordenar sessão                                                                  |
| `Esc`                     | fechar preview, limpar input ou sair                                              |
| `Ctrl + C`                | limpar input; apertar duas vezes sai                                              |
| `?`                       | mostrar todos os atalhos                                                          |

([Claude][1])

## Filtros no input do Agent View

Você também pode digitar filtros no campo de input:

```a:<nome>```

Mostra sessões rodando com aquele agent.

```s:<estado>```

Filtra por estado, por exemplo:

```s:blocked```

Mostra sessões que precisam de input.

```#<número>```

ou uma URL de PR para encontrar a sessão trabalhando naquele pull request.

---

**INEMA** · 2026-05-12

Para ativar o **Agent View** no Claude Code, faça assim:

1. **Atualize o Claude Code** e confira se está na versão exigida:

```claude --version```

O Agent View exige **Claude Code v2.1.139 ou superior**. 

2. **Abra o Agent View pelo terminal:**

```claude agents```

Isso abre a tela central onde aparecem as sessões em background. Se estiver vazio, é normal: ele só mostra sessões depois que você cria ou envia alguma para background. 

3. **Crie uma nova sessão direto no Agent View:**

Dentro da tela do `claude agents`, digite uma tarefa no campo de input e pressione `Enter`.

Exemplo:

```investigue os testes quebrando e proponha correções```

4. **Ou envie uma sessão atual para o Agent View:**

Dentro de uma sessão normal do Claude Code, rode:

```/bg```

ou:

```/bg rode os testes e corrija as falhas```

Também dá para iniciar direto do shell:

```claude --bg "investigue o teste instável"```

Depois disso, a sessão aparece no `claude agents`. 

Atalhos principais dentro do Agent View:

```↑ / ↓       navegar entre sessões
Space       ver preview ou responder
Enter / →   entrar na sessão
←           voltar para a lista
Esc         sair do Agent View
?           ver todos os atalhos```

Observação importante: se o Agent View não abrir, pode ser por versão antiga ou porque ele foi desativado na configuração com `disableAgentView` ou pela variável `CLAUDE_CODE_DISABLE_AGENT_VIEW`.  

[1]: https://code.claude.com/docs/en/agent-view "Manage multiple agents with agent view - Claude Code Docs"

---

**INEMA** · 2026-05-12

https://chatgpt.com/c/6a0288db-bdd0-832a-b94e-9b61fb262296
