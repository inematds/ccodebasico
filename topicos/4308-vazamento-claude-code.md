# Vazamento Claude Code

> Tópico 4308 · 14 mensagens úteis de 38 totais

---

**INEMA** · 2026-03-31

As pessoas estão usando o Codex para converter o código, então não há problemas de direitos autorais.

O agente do Codex de IA é quem está fazendo a "cópia em ambiente controlado", portanto não há base legal para direitos autorais se estiver em uma nova linguagem como Python ou Rust.

---

**INEMA** · 2026-03-31

https://github.com/inematds/claw-code

---

**INEMA** · 2026-03-31

**Análise detalhada do vazamento do código-fonte de Claude Code - Recursos ocultos 🔒
**
Todo o código-fonte do Claude Code CLI foi acidentalmente incluído em um arquivo .map esta manhã, e eu revisei todos os cerca de 2.000 arquivos para que você não precise fazer isso.

Eis como uma conversa realmente funciona nos bastidores:
→ você digita algo
→ prompt do sistema + habilidades + contexto são injetados
→ acessa a API do Claude para transmitir uma resposta
→ quaisquer chamadas de ferramentas são invocadas
→ O processo alterna entre a execução da ferramenta e as chamadas à API até que a tarefa seja verificada como concluída.
O sistema gera agentes de três maneiras:
→ padrão (recomeço, contexto zero, totalmente independente)
→ bifurcação (ramificações a partir do agente principal com prefixo idêntico, como /fork ou /branch)
→ Modo de colega de equipe (processo de terminal separado, coordenadas via sistema de caixa de correio JSON)

A gestão de contexto é mais agressiva do que a maioria das pessoas imagina:

→ Remove proativamente os resultados e metadados de ferramentas antigas
→ Remove leituras de arquivos obsoletas e saídas do bash
→ executa microcompactação baseada em tempo em segundo plano
→ O auto-dream mantém seu arquivo [memory.md ](http://memory.md/)com menos de 200 linhas, consolidando e removendo conteúdo desnecessário.
O modelo de segurança possui quatro camadas de profundidade:
→ ambiente de teste geral para todos os comandos
→ Sistema de permissões (permitir/negar/perguntar em settings.json)
→ Ferramentas de proteção do Bash para operações em nível de sistema
→ limites de código protegidos

Funcionalidades não lançadas que encontrei escondidas no código:

→ UltraPlan: teletransporta sua sessão para um agente remoto na nuvem para planejamento somente leitura e, em seguida, envia a implementação completa de volta para sua máquina para aprovação.
→ Ultra Review: caçador de bugs remoto que encontra e verifica bugs
→ Garfos silenciosos prevendo sua próxima instrução antes que você a digite
→ Documentos mágicos que se atualizam automaticamente com novos aprendizados, funcionando como documentação viva.
→ Um "Sistema de Companheiros" com companheiros de IA atribuíveis (pato, dragão, capivara) que podem gamificar diferentes modos de uso do Claude Code.
⚠️ A inteligência do modelo ainda é o verdadeiro diferencial aqui - você não pode simplesmente substituir o modelo existente por um de código aberto e obter os mesmos resultados.
→ mas espere que as equipes do Codex e do Gemini estudem isso atentamente

Estou anexando a análise um arquivo MD e o link do GitHub a esta publicação para que você possa explorá-la por conta própria.

---

**INEMA** · 2026-03-31

O **modelo** é o “cérebro”. O que **vazou** foi mais a “engenharia ao redor do cérebro”.

Em termos práticos:

**Modelo**

* É a IA em si.
* É o que entende seu pedido, raciocina, escreve, programa e decide o que responder.
* Inclui coisas como treinamento, pesos, capacidades, comportamento e qualidade real das respostas.

**O que vazou**

* Foi o **código do produto/CLI**, isto é, a camada que organiza o uso do modelo.
* Coisas como:

  * fluxo de conversa,
  * chamadas de API,
  * uso de tools,
  * gerenciamento de contexto,
  * agentes paralelos,
  * permissões,
  * sandbox,
  * features escondidas.

Uma analogia boa:

* **modelo** = o motor de um carro
* **vazamento** = painel, câmbio, software do carro, sistema de navegação e regras de segurança

Ou outra:

* **modelo** = o chef
* **vazamento** = a cozinha, os processos, os utensílios e a forma como os pedidos são organizados

Então o ponto do post é:

* concorrentes podem aprender bastante com a **arquitetura do produto** que vazou;
* mas isso **não significa** que agora eles têm a mesma inteligência do Claude;
* porque a parte mais valiosa ainda pode ser o **modelo em si**, que não é a mesma coisa que o código do app/CLI.

Resumindo em uma frase:

**Vazou o “como usar e orquestrar a IA”, não necessariamente a própria IA.**

---

**INEMA** · 2026-03-31

https://github.com/inematds/claude-code-kuber

---

**INEMA** · 2026-03-31

https://github.com/inematds/claude-code

---

**INEMA** · 2026-03-31

O quinto ponto é o **Undercover Mode**, uma abordagem em que edições feitas por IA em repositórios não apareceriam explicitamente como produzidas por IA, parecendo mudanças feitas por uma pessoa. O texto trata isso mais como um sinal da direção estratégica da Anthropic: agentes cada vez mais autônomos, discretos e integrados ao fluxo de trabalho.

---

**INEMA** · 2026-03-31

O quarto é o sistema de memória chamado **Dream**, voltado a resolver um problema central do Claude: a falta de memória persistente entre sessões. A proposta é consolidar informações úteis, remover duplicatas e apagar dados obsoletos, para que o sistema retenha decisões arquiteturais, preferências da equipe e histórico de debugging ao longo do tempo.

---

**INEMA** · 2026-03-31

O terceiro é o **Buddy System**, uma camada gamificada no terminal. O usuário teria um “companheiro virtual” estilo Tamagotchi, com espécies, raridades, traços de personalidade e atributos como debugging, paciência, caos, sabedoria e sarcasmo. Esse recurso parece ter mais foco em engajamento e retenção no ecossistema.

---

**INEMA** · 2026-03-31

O segundo é o **Ultra Plan**, um modo de planejamento profundo em nuvem. Em vez de responder rápido com análises superficiais, o sistema poderia dedicar cerca de 30 minutos para pensar em tarefas complexas, como migração de banco, decomposição de microsserviços ou arquitetura de produção, e depois retornar com um plano mais robusto.

---

**INEMA** · 2026-03-31

O primeiro é o **Kyros**, um agente “sempre ativo” que monitoraria projetos e repositórios de forma contínua, detectando bugs, acompanhando PRs, enviando notificações e até sugerindo correções de forma proativa, mesmo sem interação direta do usuário. A ideia central é sair do modelo reativo de uso e caminhar para agentes autônomos.

---

**INEMA** · 2026-03-31

Vazamento do Claude Code

---

**INEMA** · 2026-03-31

https://chatgpt.com/c/69cc1504-78bc-832a-8916-4f01ab66a9cb

---

**INEMA** · 2026-03-31

https://chatgpt.com/c/69cc3c10-18a8-832c-b99f-274ed8339f65
