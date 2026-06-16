# 32 Hacks CCode

> Tópico 5390 · 6 mensagens úteis de 20 totais

---

**INEMA** · 2026-04-28

context`               | Ver exatamente o que está consumindo seu orçamento de tokens.                          |
| `/compact`               | Comprimir o histórico da conversa. Permite adicionar instruções sobre o que preservar. |
| `/clear`                 | Limpar a conversa, mantendo `claude.md` e arquivos de apoio.                           |
| `Shift + Tab`            | Alternar entre modos. Sempre começar no modo de planejamento.                          |
| `/rewind`                | Voltar para um ponto anterior da conversa.                                             |
| `/hooks`                 | Configurar notificações, como alertas sonoros ao concluir.                             |
| `/loop`                  | Tarefa recorrente dentro de uma sessão, com máximo de 3 dias.                          |
| `ultrathink`             | Alocar cerca de 32.000 tokens de raciocínio para problemas difíceis.                   |
| `claude-worktree <nome>` | Criar um workspace paralelo isolado em sua própria branch.                             |

## V. Princípios centrais para levar com você

Algumas mentalidades aparecem em quase todos os hacks. Internalize estas e o restante ficará mais fácil:

1. **Contexto é seu recurso mais escasso.** Mantenha-o pequeno, monitore-o e corte agressivamente.
2. **Planeje antes de executar.** Modo de planejamento, perguntas de esclarecimento e a regra dos 95% de confiança reduzem ciclos desperdiçados.
3. **Trate o Claude como um colega de equipe, não como uma máquina de respostas.** Dê problemas a ele, deixe-o raciocinar e questione saídas fracas.
4. **Inclua verificações de qualidade no trabalho.** Autocapturas de tela, verificação com DevTools e etapas de validação na lista de tarefas pegam problemas antes de você.
5. **Capture aprendizados.** Atualize o `claude.md` e seu diretório de skills sempre que o Claude descobrir algo novo.
6. **Escolha o modelo e a ferramenta certos para cada caso.** Haiku para trabalho paralelo barato, Opus para síntese, APIs diretas quando o overhead do MCP for pesado.

---

**INEMA** · 2026-04-28

pre ativas

* Execute o Claude Code em um servidor remoto para que ele continue rodando mesmo quando seu laptop estiver fechado.
* Acesse via SSH para interagir, ou conecte ao Telegram para controle por chat.
* Perfeito para tarefas longas em que você não quer ficar monitorando um terminal local.

### 27. Controle remotamente pelo celular

* O Claude Code agora permite controlar sessões locais pelo celular ou por qualquer navegador.
* Comece uma tarefa na sua mesa, saia, e continue orientando pelo celular.
* Seu código nunca sai da sua máquina local. Apenas a conexão de controle remoto fica no celular.
* Inicie algo pesado, pegue um café ou dê uma caminhada, e continue construindo do bolso.

### 28. Análise de dados sem SQL

* Conecte ferramentas de linha de comando, como o CLI do BigQuery, ao Claude Code.
* Faça perguntas em linguagem natural, como:
  “Quais foram nossas 10 maiores fontes de receita no último trimestre?”
* O Claude traduz a pergunta para a consulta correta, executa e retorna a resposta. Não é necessário saber SQL.
* Esse padrão funciona para qualquer ferramenta baseada em CLI, não apenas BigQuery.

### 29. Ultrathink

* Quando o Claude precisar raciocinar sobre um problema difícil — decisões de arquitetura, depuração complexa, grandes refatorações — ou quando não estiver entregando a saída correta depois de alguns prompts, digite a palavra `ultrathink`.
* O terminal fica colorido e o Claude aloca o orçamento máximo de pensamento, cerca de 32.000 tokens, antes de responder.
* Não use isso para correções simples. Use quando as decisões afetarem o sistema inteiro ou quando prompts normais não estiverem funcionando.

### 30. Edite permissões para autonomia segura

* Muitos usuários, incluindo Nate, já demonstraram `--dangerously-skip-permissions` para deixar o Claude executar sem pedidos de aprovação. É rápido, mas se chama “perigoso” por um motivo.
* A abordagem mais inteligente: abra suas permissões e permita explicitamente os comandos que você sabe que são seguros, e negue explicitamente qualquer coisa destrutiva, como deletes e removes.
* Você ganha a mesma velocidade e autonomia com muito menos risco.
* Importante: a lista de negação tem prioridade sobre a lista de permissão.

### 31. Use equipes de agentes

* Subagentes rodam em paralelo com contexto novo, mas não conseguem conversar entre si. Equipes de agentes conseguem.
* Os membros da equipe compartilham uma lista de tarefas, comunicam-se uns com os outros e até atribuem trabalho entre si.
* Você pode falar diretamente com agentes individuais, em vez de passar tudo por um agente principal.
* É mais caro e demora mais que subagentes, mas produz uma saída muito mais coesa para projetos grandes.

### 32. Context 7 MCP

* Instale o servidor MCP Context 7. Quando precisar de documentação atualizada, basta pedir ao Claude para usá-lo.
* O problema que ele resolve: os dados de treinamento do Claude têm uma data de corte, então às vezes ele sugere funções ou APIs que foram renomeadas, descontinuadas ou removidas.
* O Context 7 possui documentação atualizada e específica por versão, além de exemplos de código ao vivo de milhares de bibliotecas populares, como Next.js, React, MongoDB e outras.
* Ele busca documentação atual e injeta no contexto da conversa antes que o Claude escreva qualquer código. Um único comando de instalação, e todo agente de programação passa a trabalhar com informações muito mais frescas. Um enorme ganho de qualidade.

## IV. Guia rápido de comandos

| Comando                  | Finalidade                                                                             |
| ------------------------ | -------------------------------------------------------------------------------------- |
| `/init`                  | Escanear um projeto e gerar um `claude.md`.                                            |
| `/statusline`            | Adicionar um painel ao vivo no terminal: porcentagem de contexto, modelo, custo.       |
| `/voice`                 | Entrada nativa de voz para código.                                                     |
| `/

---

**INEMA** · 2026-04-28

as vezes, o Claude produz uma saída muito melhor na segunda tentativa quando o nível de exigência é maior e ele sabe o que evitar.
* Passo essencial: quando uma versão melhor surgir, diga ao Claude para atualizar a si mesmo, seja em uma skill ou no `claude.md`, para que o mesmo erro não se repita.

### 18. Use `/rewind` para desfazer rapidamente

* Se você tomar um rumo errado, digite `/rewind` e o Claude volta a um ponto anterior da conversa.
* Não é preciso começar de novo. Super rápido e limpo.

### 19. Use hooks para notificações

* Digite `/hooks` para configurar um hook de notificação, ou simplesmente descreva em linguagem natural e deixe o Claude Code configurá-lo.
* Uso comum: acionar um alerta sonoro quando o Claude terminar uma sessão ou conversa.
* Isso libera você para trabalhar em outra coisa, ou até executar 15 sessões paralelas do Claude Code e reagir apenas quando uma precisar da sua intervenção.

### 20. Use capturas de tela

* O Claude consegue ver imagens, o que é um grande desbloqueio.
* Envie mensagens de erro, sites de inspiração ou referências de design.
* Execute um ciclo de autoverificação:
  “Tire uma captura de tela do site e diga se o layout parece correto.”
  O Claude analisa visualmente a página e aponta o que está errado.
* Fluxo prático: desenhar, capturar tela, implementar mudanças, repetir. Três passadas antes da V1 produzem uma primeira versão de qualidade muito maior.

### 21. Use o Chrome DevTools

* O Claude pode abrir um navegador, interagir com um app e verificar funcionalidades.
* É parecido com o ciclo de captura de tela, mas para comportamento real do app, botões e formulários, em vez de design estático.
* Excelente para front-end e útil para preencher formulários ou resumir fluxos quando uma API explícita não está disponível.
* Funciona melhor quando você já está logado em algum lugar e o Claude só precisa navegar, clicar e preencher.

### 22. Clone sites de inspiração

* Tire capturas de tela de sites que você gosta, envie ao Claude e diga:
  “Faça parecer com isso.”
* O Claude recria padrões de design sem produzir aquele resultado genérico de IA.
* Você também pode enviar o HTML e o estilo reais da fonte como inspiração.
* Use o resultado como template e depois acrescente seu próprio toque.

## III. Hacks avançados: território de usuário avançado

Para usuários que querem levar o Claude Code ao limite.

### 23. Execute sessões paralelas com Git Worktrees

* Duas sessões na mesma pasta podem sobrescrever uma à outra. Worktrees resolvem isso criando cópias paralelas eficientes do projeto.
* Digite `claude-worktree <nome-da-feature>` para criar um workspace isolado em sua própria branch.
* Abra outro terminal, repita com um nome de feature diferente, e você terá dois agentes de programação trabalhando em paralelo sem interferirem um no outro.
* Você pode executar três, quatro ou cinco ao mesmo tempo, depois mesclar as branches de volta como em qualquer fluxo de trabalho Git.

### 24. Use endpoints de API em vez de servidores MCP quando fizer sentido

* Servidores MCP são convenientes porque expõem todas as ferramentas, mas carregam todas essas definições de ferramenta no seu contexto.
* Se os tokens estiverem apertados, use diretamente o endpoint da API.
* Exemplo: você só precisa ler uma base de dados do Notion. Pule o MCP completo do Notion e codifique diretamente aquele endpoint específico. Você economiza uma enorme quantidade de contexto.

### 25. Use `/loop` para tarefas recorrentes

* Diga ao Claude algo como:
  “A cada 5 minutos, verifique o deployment.”
  O Claude reexecuta esse prompt a cada 5 minutos dentro da mesma sessão.
* Use para monitorar um PR, verificar logs de erro ou acompanhar um build. Ele só interrompe quando algo precisa da sua atenção.
* Lembretes únicos também funcionam:
  “Lembre-me às 15h de falar com a equipe sobre X.”
* Observação: loops duram apenas 3 dias. Para agendas mais longas, use tarefas agendadas do desktop. Note que execuções de tarefas agendadas começam em sessões novas, sem memória anterior.

### 26. Hospede em um VPS para sessões

---

**INEMA** · 2026-04-28

a ferramenta de fazer perguntas ao usuário.
* Diga ao Claude:
  “Faça perguntas continuamente até estar 95% confiante de que entende exatamente o que eu preciso e o que você deve fazer.”
* Esse alinhamento inicial evita três ou quatro rodadas de revisão depois.

### 10. Inclua autoverificação na lista de tarefas

* Quando o Claude gerar uma lista de tarefas, inclua etapas de verificação diretamente nela.
* Exemplo de sequência:

  1. Construir o site.
  2. Tirar uma captura de tela e verificar se tudo parece correto.
  3. Abrir o Chrome DevTools e confirmar que não há erros de funcionalidade.
* As verificações de qualidade passam a fazer parte do plano de execução, então o Claude não apenas constrói e entrega, mas também verifica o próprio trabalho.
* Acrescente a regra:
  “Não avance para a próxima tarefa até estar 95% confiante de que a atual está boa.”
  Chegar a 90% em uma tentativa única é muito melhor do que 60%.

## II. Hacks intermediários: avance mais rápido

Para usuários que já se sentem confortáveis com o Claude Code e querem entregar mais, mais rapidamente.

### 11. Use subagentes para trabalho paralelo

* No seu prompt, diga à sessão principal para usar subagentes ao trabalhar em problemas complexos.
* O Claude cria subagentes isolados, cada um com sua própria janela de contexto e, opcionalmente, seu próprio modelo.
* Subagentes trabalham em paralelo pesquisando, escrevendo testes ou explorando abordagens diferentes, e depois reportam à sessão principal.
* Combine isso com o hack de modelo nº 13 para que subagentes rodem no Haiku, usando tokens mais baratos, enquanto sua thread principal permanece no Opus.

### 12. Crie skills personalizadas

* Crie arquivos de prompt reutilizáveis no diretório `.claude/skills`.
* Exemplos: `techdebt.md` diz ao Claude exatamente como procurar dívida técnica; `code-review.md` define exatamente como revisar sua base de código.
* Invoque uma skill em linguagem natural ou com um comando de barra, e o mesmo fluxo de trabalho será executado de forma consistente todas as vezes.
* Faça commit delas no GitHub para que toda a sua equipe use os mesmos procedimentos operacionais.

### 13. Use Haiku para subagentes

* Você pode definir o modelo de cada subagente criado.
* Para tarefas simples ou processamento de grandes volumes de dados, use Haiku. Ele é mais barato e ainda dá conta do recado.
* Exemplo: um subagente processa centenas de milhares de tokens de artigos no Haiku e envia um pequeno resumo para seu agente principal no Opus.
* Feito corretamente, isso mantém os custos baixos sem sacrificar qualidade onde ela realmente importa.

### 14. Atualize constantemente seu `claude.md`

* Atualize o `claude.md` sempre que houver uma nova descoberta, nova skill, novo padrão, pegadinha ou convenção.
* Na próxima sessão, o Claude já saberá tudo isso, evitando erros repetidos e tornando-o mais inteligente sobre você, seu negócio e seu projeto ao longo do tempo.
* Cuidado com o inchaço: o `claude.md` é carregado em toda conversa como prompt de sistema e consome contexto.
* Mantenha-o focado. Um limite prático é de 150 a 200 linhas. Se passar disso, corte.

### 15. Faça o `claude.md` direcionar para outros arquivos

* Mantenha o `claude.md` enxuto criando links para arquivos separados de guias de estilo, contexto de negócio e documentos de referência.
* Aponte para esses arquivos para que o Claude saiba onde procurar sem carregar tudo a cada turno.
* O prompt de sistema não precisa do status exato de cada projeto. Ele só precisa saber onde encontrar essas informações.

### 16. Interrompa cedo e peça novamente

* Se o Claude começar a seguir o caminho errado, não espere ele terminar.
* Pressione **Esc**, corrija o rumo e faça um novo prompt.
* Cada token gasto na direção errada é contexto desperdiçado. Oriente de forma precisa e cedo.

### 17. Questione as respostas agressivamente

* Se o Claude entregar algo apenas “ok”, pressione. Tente:
  “Descarte isso, faça uma versão mais elegante”
  ou
  “Isso não está bom o suficiente, tente novamente com uma abordagem completamente diferente.”
* Muit

---

**INEMA** · 2026-04-28

# 32 Hacks do Claude Code: do Iniciante ao Usuário Avançado

Este guia resume os 32 hacks de produtividade para o Claude Code apresentados no vídeo, organizados por nível de habilidade para que você possa evoluir de forma sistemática. Os hacks 1 a 10 constroem sua base, os 11 a 22 ajudam você a trabalhar mais rápido, e os 23 a 32 levam o Claude Code ao limite.

## I. Hacks para Iniciantes: construa sua base

Estes são os movimentos fundamentais que todo usuário do Claude Code deve dominar antes de se aprofundar.

### 1. Execute `/init` em todo projeto

* Para uma base de código existente, digite `/init` para que o Claude escaneie suas pastas, arquivos e arquitetura.
* O Claude gera um arquivo `claude.md` que funciona como uma folha de referência, mapeando convenções e arquivos importantes.
* Isso elimina a necessidade de reexplicar seu projeto no início de cada sessão.
* Para projetos totalmente novos, peça ao Claude Code para ajudar você a criar o `claude.md`, descrevendo o objetivo do projeto, a stack tecnológica, as regras e as pastas principais.

### 2. Configure uma linha de status

* Digite `/statusline` e diga ao Claude o que você quer que seja exibido: modelo, porcentagem de contexto, custo etc.
* O Claude gera um pequeno script que fica na parte inferior do seu terminal como um mini painel.
* Isso permite monitorar continuamente o contexto restante para evitar degradação por excesso de contexto.

### 3. Use entrada por voz

* O Claude Code agora vem com o comando nativo `/voice`, para que você possa falar com o terminal e fazê-lo programar para você.
* Se a voz ainda não estiver habilitada na sua conta, use um aplicativo de ditado por voz de terceiros para falar e fazer as palavras aparecerem em qualquer lugar da tela.

### 4. Mantenha seu contexto pequeno

* Não despeje toda a sua base de código em uma conversa. Dê ao Claude apenas o que ele precisa para a tarefa atual.
* Divida problemas grandes em etapas pequenas e focadas.
* Menos ruído na janela de contexto significa melhor desempenho do Claude. Simples, mas a maioria das pessoas ignora isso.

### 5. Use `/context` para encontrar excesso de tokens

* Execute `/context` para ver exatamente o que está consumindo seus tokens.
* O Claude divide prompts de sistema, conteúdo de arquivos, servidores MCP e outros itens em porcentagens.
* Se uma sessão parecer pesada, use isso para diagnosticar onde está o problema e reorganizar a abordagem.

### 6. Compacte em 60% e limpe entre tarefas

* Quando o contexto atingir cerca de 60%, execute `/compact` para que o Claude comprima o histórico da conversa sem perder detalhes importantes.
* Você pode passar instruções, por exemplo:
  `/compact but keep all API integration decisions and database schema`
  O Claude reduz o restante, preservando o que importa.
* Vai mudar para uma tarefa completamente nova? Use `/clear` para limpar a conversa. Seu `claude.md` e arquivos de apoio permanecem intactos, então você não começa do zero.

### 7. Sempre comece no modo de planejamento

* Pressione **Shift + Tab** para alternar entre modos, ou selecione manualmente o **Plan Mode**.
* No modo de planejamento, o Claude ainda pode ler e pesquisar, mas não altera nada até você aprovar.
* O Claude descreve etapas, faz perguntas de esclarecimento e mapeia a abordagem antes de escrever uma única linha de código.
* Depois de aprovar o plano, saia do modo de planejamento e peça para ele executar. Isso reduz drasticamente as idas e vindas de correção.

### 8. Trate o Claude como um desenvolvedor júnior

* Nem sempre dê comandos diretos como “escreva uma função que faça X”.
* Em vez disso, apresente problemas. Pergunte coisas como: “Como devemos lidar com o acompanhamento de crescimento?” e deixe o Claude raciocinar sobre a abordagem.
* Quando o Claude faz suas próprias suposições e as explica, a qualidade da saída melhora de forma perceptível. Pense nisso como o modo de planejamento levado um nível adiante.

### 9. Faça o Claude fazer perguntas

* O modo de planejamento muitas vezes faz isso nativamente, mas você pode invocar explicitamente a

---

**INEMA** · 2026-04-28

https://chatgpt.com/c/69ef93a2-5914-832f-ae17-4b1dbf0858bd
