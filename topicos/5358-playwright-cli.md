# Playwright CLI

> Tópico 5358 · 4 mensagens úteis de 12 totais

---

**INEMA** · 2026-04-26

rio principal para escolher uma ferramenta seria equilibrar:

* eficiência de tokens;
* capacidade de clicar e navegar corretamente;
* facilidade de integração com Claude Code;
* qualidade da automação;
* capacidade de melhorar scripts com base em falhas.

O autor diz que, no momento, tem usado principalmente Playwright CLI, mas pretende testar outras opções.

---

## 15. Mensagem principal

A mensagem central é que browser automation com Claude Code e Playwright CLI permite criar agentes capazes de executar tarefas reais no navegador.

O processo mais importante é:

1. criar um script de automação;
2. rodar no navegador;
3. observar falhas;
4. corrigir o script;
5. repetir;
6. transformar o fluxo em uma skill;
7. agendar a execução quando fizer sentido.

A grande vantagem não está apenas em automatizar cliques, mas em criar processos reutilizáveis, iterativos e cada vez mais confiáveis.

---

## Resumo final em uma frase

Claude Code com Playwright CLI pode automatizar testes, coleta de dados, interações em sites logados e tarefas recorrentes no navegador, desde que os scripts sejam refinados por ciclos de tentativa, erro e melhoria contínua.

---

**INEMA** · 2026-04-26

ativa não foi perfeita. O Google bloqueou parte da automação, então o script mudou a estratégia e passou a usar DuckDuckGo.

Depois de algumas iterações, a automação conseguiu encontrar números de telefone de clínicas odontológicas. O autor ressalta que esse tipo de automação melhora conforme o script aprende com as falhas anteriores.

---

## 8. Automação em sites onde o usuário está logado

O terceiro caso de uso responde a uma pergunta importante: é possível automatizar ações em sites que exigem login?

A resposta demonstrada é sim.

Algumas abordagens possíveis:

* usar um perfil persistente do navegador;
* fazer login manual uma vez e reaproveitar a sessão;
* conectar a automação a um navegador já aberto;
* salvar cookies e dados de sessão.

Testa isso com uma comunidade na plataforma Skool. Ele faz login manualmente uma vez, e depois o navegador automatizado consegue abrir a plataforma já autenticado.

---

## 9. Curtir posts automaticamente em uma comunidade

Depois de persistir a sessão logada, o autor pede para o agente entrar em um canal chamado “wins” e curtir posts.

A primeira tentativa tem problemas:

* o bot clica várias vezes no botão de curtir;
* ele acaba curtindo e descurtindo o mesmo post;
* recebe aviso de estar curtindo rápido demais;
* tem dificuldade para identificar corretamente o estado do botão.

Depois, o autor dá instruções mais específicas:

* entrar no canal correto;
* ordenar os posts por mais recentes;
* verificar se o ícone de curtida está amarelo ou cinza;
* pular posts que já foram curtidos;
* curtir apenas os que ainda não foram.

Com essas orientações, a automação melhora e passa a funcionar corretamente.

---

## 10. As automações não são perfeitas de primeira

Um tema recorrente é que browser automations normalmente falham nas primeiras tentativas.

Elas podem errar seletores, clicar no botão errado, confundir estados da interface, repetir ações, travar ou não entender exatamente onde estão os elementos.

Mas o ponto defendido é que isso é normal. O valor aparece quando o agente observa o erro, ajusta o script e tenta novamente.

Cada execução melhora o processo.

---

## 11. Uso com tarefas agendadas

Na parte final, o autor conecta browser automation com tarefas agendadas.

Ele mostra que é possível criar automações que rodam diariamente ou em horários específicos, especialmente usando o aplicativo desktop.

Exemplos mencionados:

* engajar diariamente com posts da comunidade;
* publicar resumos de notícias de IA;
* responder notificações;
* responder comentários em posts;
* fazer posts automáticos;
* interagir como um bot dentro de uma comunidade.

O autor mostra um bot chamado “AIS agent”, que publica e responde dentro da comunidade de forma autônoma.

---

## 12. Agentes que criam novas ferramentas durante o uso

Um ponto interessante é que o agente pode encontrar novas situações e criar scripts adicionais para lidar com elas.

Exemplo: alguém pediu para o bot votar em uma enquete. O agente não sabia inicialmente como votar, então precisou descobrir onde clicar, entender a interface e transformar esse novo comportamento em uma ferramenta reaproveitável.

Isso mostra uma evolução do sistema: a automação começa simples, mas vai acumulando capacidades conforme encontra novos cenários.

---

## 13. Limitações e cuidados

O autor deixa claro que esse tipo de automação ainda não é perfeito.

Problemas citados ou demonstrados:

* o bot pode responder pessoas duas vezes;
* pode esquecer de marcar notificações como lidas;
* pode clicar rápido demais;
* pode curtir e descurtir sem perceber;
* pode precisar de várias iterações até funcionar bem;
* algumas plataformas são pouco amigáveis para automação;
* sites podem bloquear bots;
* a interface pode mudar e quebrar os scripts.

Mesmo assim, ele considera a abordagem poderosa porque o agente consegue aprender com os erros e adaptar os scripts.

---

## 14. Comparação entre ferramentas de automação

O vídeo menciona que Playwright CLI não é a única opção. Existem outras ferramentas e CLIs para automação de navegador ou computador.

O crité

---

**INEMA** · 2026-04-26

Como combinar **Claude Code** com **Playwright CLI** para automatizar ações em um navegador, criando scripts capazes de testar sites, coletar dados, interagir com páginas logadas e transformar esses fluxos em processos repetíveis usando skills.

### 1. Ideia central

A proposta principal é que, ao dar ao Claude Code acesso a um navegador por meio do Playwright CLI, ele passa a conseguir automatizar praticamente qualquer tarefa feita manualmente em sites.

Exemplos citados:

* testar aplicações web;
* tirar screenshots;
* baixar relatórios de sites sem API;
* buscar contatos na internet;
* interagir com plataformas onde o usuário já está logado;
* responder notificações;
* curtir posts;
* criar rotinas automáticas recorrentes.

A ideia não é apenas executar uma automação uma vez, mas criar scripts que possam ser melhorados com o tempo e reaproveitados como skills.

---

## 2. Por que usar Playwright CLI em vez de MCP de navegador

O autor comenta que inicialmente testou outras abordagens, como Chrome DevTools MCP, mas percebeu que ferramentas MCP de navegador podem consumir muitos tokens porque expõem muitas ferramentas e descrições ao modelo.

O Playwright CLI aparece como uma alternativa mais leve e eficiente em termos de contexto. Ele permite controlar o navegador por scripts, sem carregar tantos recursos no prompt.

O fluxo inicial foi:

1. abrir um projeto vazio;
2. pedir ao Claude Code para instalar o Playwright CLI;
3. inicializar o projeto;
4. criar um script de teste;
5. abrir uma página;
6. tirar screenshot;
7. confirmar que a automação funcionava.

---

## 3. Automação de QA em uma aplicação web

O primeiro caso de uso é a criação e teste automático de uma aplicação web.

Pede ao Claude Code para construir um site de formulário de onboarding, com uma pergunta por página. O formulário inclui campos como:

* nome;
* sobrenome;
* telefone;
* empresa;
* e-mail;
* cargo;
* tamanho da empresa;
* setor;
* fonte de indicação;
* objetivo principal;
* site;
* observações finais.

Depois que o site é criado, o autor não testa manualmente. Ele pede ao Claude Code para usar o navegador automatizado para preencher o formulário, avançar pelas etapas, detectar bugs e corrigir o próprio código.

---

## 4. Headed browser vs headless browser

Diferença entre dois modos de execução do navegador:

**Headed browser** é quando o navegador aparece na tela, permitindo assistir ao bot clicando, digitando e navegando.

**Headless browser** é quando a automação roda em segundo plano, sem abrir uma janela visível.

No exemplo de QA, usa headed browser para acompanhar visualmente o que o agente está fazendo.

---

## 5. O ciclo de testar, detectar erro, corrigir e testar de novo

Durante o teste do formulário, o bot preenche os campos, avança pelas páginas e tira screenshots. Ele encontra alguns problemas, como:

* o campo de texto final não avançava corretamente ao pressionar Enter;
* a página de revisão não carregava;
* alguns botões eram interceptados por sobreposições antigas da interface.

Depois disso, o Claude Code usa as evidências do próprio teste para corrigir o site. Em seguida, ele roda o teste novamente para validar se os bugs foram resolvidos.

Esse é um ponto central do vídeo: a automação não apenas executa ações, mas também pode criar um ciclo iterativo de melhoria.

---

## 6. Transformar automações em skills

Depois que uma automação funciona bem, o próximo passo é transformá-la em uma skill.

A lógica seria algo como:

1. quando quiser fazer QA, rode o script de teste;
2. colete os erros e screenshots;
3. analise os problemas;
4. corrija o código;
5. rode o teste novamente;
6. repita até passar.

Com isso, uma tarefa que antes era manual vira um processo consistente e reutilizável.

---

## 7. Busca automática de dentistas e contatos

O segundo exemplo é uma automação para buscar dentistas na internet e capturar números de telefone.

O plano inicial era:

1. abrir o navegador;
2. pesquisar por dentistas;
3. acessar resultados;
4. visitar sites;
5. procurar informações de contato;
6. coletar telefones.

A primeira

---

**INEMA** · 2026-04-26

https://chatgpt.com/c/69ee9497-4a50-8327-bed6-7453fbc35602
