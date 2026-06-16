# 6 Top Plugins Skills

> Tópico 5537 · 20 mensagens úteis de 53 totais

---

**INEMA** · 2026-05-06

## 2. Claude Mem

Comandos:

```/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem```

O **Claude Mem** trabalha entre **sessões diferentes**.

Enquanto o Context Mode cuida da sessão atual, o Claude Mem tenta fazer Claude lembrar do projeto no futuro. Ele captura automaticamente coisas como edições de arquivos, decisões, correções de bugs e comandos executados. Depois comprime isso em resumos semânticos e salva em um banco SQLite local com busca vetorial. 

Na próxima sessão, ele injeta automaticamente os pedaços relevantes de memória, em vez de você ter que explicar tudo de novo. O material também diz que ele pode gerar e atualizar arquivos `CLAUDE.md` por pasta conforme você trabalha. 

Ele usa uma busca em três camadas: primeiro retorna um índice compacto de observações, depois busca uma linha do tempo ao redor do que importa, e só então puxa detalhes completos quando necessário. 

Atenção: o material avisa para **não usar `npm install`** nesse caso, porque isso instalaria só a biblioteca SDK e os hooks não seriam registrados. Use exatamente os dois comandos de plugin. 

Em resumo: **Claude Mem cria memória persistente entre sessões.**

---

A diferença simples:

```Context Mode = memória/limpeza da sessão atual
Claude Mem   = memória entre sessões futuras```

Eu instalaria os dois se você usa Claude Code em projetos longos: **Context Mode evita a sessão degradar hoje; Claude Mem evita você reexplicar tudo amanhã.**

---

**INEMA** · 2026-05-06

## 1. Context Mode

Comandos:

```/plugin marketplace add mksglu/context-mode
/plugin install context-mode@context-mode```

O **Context Mode** trabalha dentro da **sessão atual** do Claude Code.

A função dele é impedir que a conversa fique cheia de “lixo” técnico: logs enormes, snapshots do Playwright, respostas longas de ferramentas, issues, outputs crus etc. O material diz que, depois de certo tempo, uma parte grande da janela de contexto pode virar esse tipo de dado inútil, fazendo Claude esquecer arquivos editados, tarefas em andamento e o último pedido. 

Ele resolve isso roteando chamadas de ferramentas e buscas por uma espécie de sandbox. O código roda isolado, o output bruto é capturado, e só o trecho realmente útil volta para o contexto. Também registra eventos importantes em um banco SQL local, como edições de arquivos, tarefas, decisões e erros. Quando a conversa é compactada, ele reconstrói um snapshot da sessão para Claude continuar de onde parou. 

Depois de instalar, o material recomenda reiniciar o Claude Code. Ele também cita o comando:

```/context-mode:ctx-stats```

para ver estatísticas de redução de contexto. 

Em resumo: **Context Mode mantém a sessão atual limpa e recuperável.**

---

**INEMA** · 2026-05-06

`get-shit-done-cc` é o **instalador via `npx` do GSD**, um plugin/ferramenta para Claude Code.

No material, **GSD** aparece como uma solução para evitar “context rot” — quando uma sessão longa começa bem, mas depois Claude passa a esquecer requisitos, escrever código pior, pular etapas ou dizer que terminou algo que não terminou. O GSD resolve isso criando **subagentes com contexto limpo para cada tarefa**, mantendo a sessão principal mais organizada. 

O comando:

```npx get-shit-done-cc --claude --global```

significa, em termos simples:

`npx` executa o pacote sem você instalar manualmente antes.
`get-shit-done-cc` é o pacote/ferramenta do GSD.
`--claude` indica que ele será configurado para Claude Code.
`--global` instala/configura de forma global, para ficar disponível em todos os projetos.

Ele não é descrito como um plugin para economizar tokens. Na verdade, o documento diz que subagentes podem gastar mais tokens, mas economizam tempo porque reduzem retrabalho causado por Claude esquecer o que foi pedido. 

Depois de instalar, o material recomenda digitar:

```/gsd-help```

dentro do Claude Code para ver os comandos disponíveis.

---

**INEMA** · 2026-05-06

O **Superpowers** é uma skill/plugin que tenta fazer o Claude Code trabalhar com mais disciplina, como um desenvolvedor sênior.

Na prática, ele força um fluxo mais cuidadoso:

1. **Planejar antes de codar**
   Em vez de sair escrevendo código imediatamente, Claude primeiro entende o problema e monta um plano.

2. **Trabalhar em ambiente isolado**
   Ajuda a evitar que alterações quebrem direto o projeto principal.

3. **Escrever testes antes ou junto da implementação**
   Isso reduz a chance de entregar algo que “parece certo”, mas quebra quando roda.

4. **Revisar o próprio trabalho**
   Ele faz uma revisão para ver se a solução bate com o pedido e outra para avaliar qualidade do código.

5. **Evitar código apressado**
   O objetivo é reduzir soluções incompletas, bugs bobos, edge cases esquecidos e retrabalho.

Em resumo: **o GSD cuida melhor do contexto; o Superpowers cuida melhor do processo de desenvolvimento.**

Comando de instalação:

```/plugin install superpowers@claude-plugins-official```

---

**INEMA** · 2026-05-06

skill-criator ajuda voce criar as Skills melhorando o conteudo e ja gravando na pastas .claude\skills

---

**INEMA** · 2026-05-06

1. **Skill Creator**
   Cria outras skills a partir de instruções em linguagem natural.

2. **Superpowers**
   Força o Claude Code a trabalhar com planejamento, testes e revisão, como um desenvolvedor sênior.

3. **GSD — Get Shit Done**
   Usa subagentes com contexto limpo para executar tarefas sem degradar a sessão.

4. **/review**
   Revisão local rápida de código para encontrar bugs, edge cases e problemas de design.

5. **/ultra****-review**
   Revisão avançada em sandbox na nuvem com vários agentes revisores.

6. **Context Mode**
   Mantém a sessão limpa, reduz lixo no contexto e reconstrói o estado da sessão.

7. **Claude Mem**
   Cria memória entre sessões, salvando decisões, edições, bugs corrigidos e comandos.

8. **Frontend Design**
   Melhora o visual de sites, interfaces, slides e artefatos criados no Claude Code.

Comandos principais:

```/plugin install skill-creator@claude-plugins-official

/plugin install superpowers@claude-plugins-official

npx get-shit-done-cc --claude --global

/review

/ultra-review

/plugin marketplace add mksglu/context-mode
/plugin install context-mode@context-mode

/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem

/plugin install frontend-design@claude-plugins-official```

---

**INEMA** · 2026-05-06

**6 habilidades/plugins principais para Claude Code** — focadas em resolver problemas reais de negócios: economizar tempo, reduzir custos e evitar erros humanos.

### Ideia central

A tese principal é que empresas não pagam por automações “bonitas” ou complexas. Elas pagam por soluções simples que geram resultado direto: menos trabalho manual, menos erro e mais eficiência.

### As principais ferramentas

**1. Skill Creator**
Serve para criar outras skills a partir de instruções em linguagem natural. Em vez de escrever arquivos técnicos manualmente, você descreve o que quer e Claude ajuda a montar, testar e empacotar a skill.

**2. Superpowers**
Faz Claude trabalhar como um desenvolvedor sênior: primeiro planeja, depois testa, revisa e só então implementa. Ajuda a evitar código apressado e mal estruturado.

**3. GSD**
Resolve o problema de “context rot”, quando Claude começa a esquecer requisitos ou piorar a qualidade depois de muito tempo na mesma sessão. Ele cria subagentes com contexto limpo para cada tarefa.

**4. ****/review**** e ****/ultra****-review**
São comandos de revisão de código. `/review` faz uma análise local rápida. `/ultra-review` envia a branch para um sandbox em nuvem com vários agentes revisores, buscando bugs confirmados antes de merge.

**5. Context Mode**
Mantém a sessão limpa. Ele evita que logs, snapshots e dados brutos encham a janela de contexto. Também registra eventos importantes em um banco SQL local para reconstruir o estado da sessão depois.

**6. Claude Mem**
Cria memória entre sessões. Armazena decisões, edições, bugs corrigidos e comandos em um banco local com busca vetorial, permitindo que Claude continue projetos antigos sem precisar de explicações repetidas.

**Bônus: Frontend Design Skill**
Melhora a aparência de interfaces, sites, slides e artefatos visuais feitos no Claude Code, evitando aquele visual genérico de “design feito por IA”.

### Como vender isso

Você não deve vender “skills” ou “plugins”. Deve vender o resultado:

Economizar horas por semana, reduzir erros administrativos, responder leads mais rápido, melhorar processos e liberar o dono do negócio para focar no que dá lucro.

### Caminho recomendado

Comece com uma skill só, aprenda bem, crie alguns fluxos práticos e demonstre para empresários usando exemplos de valor real. Depois, combine as ferramentas para criar automações melhores, mais rápidas e mais baratas.

---

**INEMA** · 2026-05-06

/plugin install frontend-design@claude-plugins-official

---

**INEMA** · 2026-05-06

/plugin install claude-mem

---

**INEMA** · 2026-05-06

/plugin marketplace add thedotmack/claude-mem

---

**INEMA** · 2026-05-06

/plugin marketplace add mksglu/context-mode

/plugin install context-mode@context-mode

---

**INEMA** · 2026-05-06

Podemos ter um plugin q contola as informacoes salvem em um banco e recupera quando precisamos

---

**INEMA** · 2026-05-06

use o  /statusline ou o projeto iccmonit para monitorar

---

**INEMA** · 2026-05-06

use o PLAN no Superpoderes, o GSD na Execução e o /ultrareview em revisao

---

**INEMA** · 2026-05-06

Entao tem o /review ou o /ultrareview q roda no nuvem

---

**INEMA** · 2026-05-06

npx get-shit-done-cc --claude --global

/GSD-help

---

**INEMA** · 2026-05-06

Com isso Voce tem Ficar Gerenciando isso ou pode usar Skills  para gerenciar pro voce

---

**INEMA** · 2026-05-06

Alternativa é fazer q se rode em subagentes pois nao polui sua janela de Contexto 1

---

**INEMA** · 2026-05-06

O problema de quando a janela de Contexto aumenta mais de 40%

---

**INEMA** · 2026-05-06

/plugin install superpowers@claude-plugins-official
