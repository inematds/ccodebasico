# Routines

> Tópico 5029 · 3 mensagens úteis de 13 totais

---

**INEMA** · 2026-04-15

Detalhes práticos e “pegadinhas” de uso:

* **Diferença entre rotina local e remota**: as locais rodam na sua máquina; as remotas rodam na nuvem.

* **Três formas de disparo**: por agendamento, chamada de API ou evento do GitHub.

* **Configuração da tarefa**: nome, prompt, modelo, repositório, ambiente de nuvem, cadência, conectores e permissões.

* **Cadência mínima**: pelo que ele testou, a menor frequência parece ser **1 hora**.

* **Conectores**: dá para ligar serviços como Slack, Gmail e outros, ou usar APIs diretamente com chaves.

* **Permissões/autonomia**: como a rotina roda sozinha, o ideal é que seja um prompt de execução única, sem depender de perguntas ao usuário.

Problemas reais:

* Ao migrar automações, **nem tudo funcionou de primeira**.
* Como o ambiente remoto usa apenas o repositório clonado, ele **não enxerga o arquivo `.env` local**.
* Por isso, foi preciso colocar segredos em **variáveis de ambiente do cloud environment**.
* Em alguns casos, ele precisou dizer explicitamente no prompt para o Claude **usar a variável de ambiente**, e não tentar procurar no `.env`.
* Para um teste com ClickUp, ele só conseguiu fazer funcionar ao trocar o acesso de rede para **full**, porque no modo **trusted** o acesso era bloqueado.

Sobre limitações importantes:

* **Não há acesso a cookies locais nem sessões do navegador**.
* Automações baseadas em navegador podem falhar se dependerem de login já salvo localmente.
* Se algo não estiver no GitHub, numa API ou em um conector acessível, **a rotina não consegue usar**.
* Cada execução remota é efêmera: o ambiente é criado, roda, e depois é destruído.

Sobre persistência:

* O ambiente temporário é apagado ao fim da execução.
* Mas o **histórico das execuções** fica salvo.
* Se a automação mexer no código, ela pode **criar branch** ou gerar saídas persistentes no repositório.

Sobre segurança e infraestrutura:

* O modo **trusted** só acessa serviços previamente aprovados.
* O modo **full** abre mais liberdade, mas aumenta o risco caso o agente leia conteúdo malicioso e tente enviar dados para fora.
* Existe opção de **custom** para liberar domínios específicos.
* Dá para usar **setup scripts** para instalar dependências antes da execução principal.

Comparando com outras formas de automação:

* **Routines**: rodam na nuvem, sem precisar deixar a máquina ligada.
* **Desktop scheduled tasks**: rodam localmente.
* **/loop**: também local, e não sobrevive a reinícios da sessão.

Na comparação, ele destaca:

* rotina remota **sobrevive sem máquina ligada**;
* tarefas locais têm **acesso a arquivos locais**;
* rotina remota é **mais autônoma**;
* tarefas locais podem ter intervalos menores, até de minutos.

Limites de uso:

* plano **Pro**: algo como **5 execuções por dia**;
* plano **Max**: **15 execuções por dia**;
* plano **Team/Enterprise**: **25 por dia**;
* pode haver cobrança excedente em alguns contextos;
* cada rotina na nuvem roda com cerca de **4 vCPUs, 16 GB de RAM e 30 GB de disco**.

Nos pontos mais conceituais, isso é interessante porque mantém a parte **agente + workflow + ferramentas** funcionando junta, em vez de virar só um script automatizado simples. Isso permite que o agente:

* leia contexto do projeto;
* escolha ações;
* se autocorrija em caso de erro;
* deixe rastros ou resultados úteis entre execuções, mesmo sendo stateless.

E no fim  dúvidas comuns:

* não precisa saber **cron**;
* dá para **escolher o modelo**;
* dá para **acompanhar a execução em tempo real**;
* você pode **interromper ou interagir** com a execução;
* pode usar **MCP/conectores**;
* as rotinas parecem ser **ligadas à conta individual**;
* o custo entra no **uso normal da assinatura**;
* quando falha, o histórico mostra o motivo;
* o ideal é **testar várias vezes antes de colocar em produção**.

---

**INEMA** · 2026-04-15

A nova funcionalidade de **routines (rotinas) no Claude Code**, que permite criar automações que rodam na nuvem, sem precisar deixar o computador ligado.

A ideia central é que uma rotina funciona como um **prompt automatizado**: você define uma instrução uma vez e ela pode ser executada automaticamente em horários definidos, por eventos (como GitHub) ou via API. Essas execuções acontecem em servidores na nuvem, tornando o processo mais prático e independente da máquina local.

Para configurar, é necessário conectar a rotina a um **repositório no GitHub**, pois é dali que o sistema lê arquivos, scripts e contexto. Como dados sensíveis não ficam no repositório, as **chaves de API precisam ser adicionadas como variáveis de ambiente** dentro do ambiente em nuvem. Também é possível configurar permissões de rede (restritas ou completas), dependendo do que a automação precisa acessar.

Um ponto importante é que essas automações são **stateless (sem estado)**: cada execução começa do zero e não tem acesso a dados locais (como cookies ou arquivos do computador). Isso pode exigir ajustes, especialmente em automações que dependem de login ou sessão. Nesses casos, é necessário usar APIs ou métodos de autenticação adequados.

Os prompts precisam ser **bem específicos**, já que a rotina deve funcionar sozinha, sem interação humana. Se não estiver claro o suficiente, a automação pode falhar.

Entre as vantagens:

* Não precisa deixar o computador ligado
* Pode ser acionado por eventos, API ou agendamento
* Mantém o comportamento “inteligente” de agente (capaz de corrigir erros durante a execução)
* Permite integração com ferramentas externas (como Slack, ClickUp, etc.)

Há também limitações:

* Execução mínima de 1 em 1 hora
* Limite diário de execuções dependendo do plano
* Sem acesso a arquivos locais
* Recursos computacionais limitados por execução

Comparado a automações locais, o grande diferencial é rodar totalmente na nuvem, mas com a desvantagem de perder acesso direto ao ambiente local.

Por fim, boas práticas como:

* Testar as rotinas antes de ativar
* Usar prompts claros e completos
* Evitar expor dados sensíveis
* Criar repositórios específicos para cada automação, se necessário

Em resumo, essa atualização torna muito mais fácil criar **agentes automatizados na nuvem**, combinando flexibilidade, automação e inteligência em um único fluxo.

---

**INEMA** · 2026-04-15

https://chatgpt.com/c/69ded490-635c-8330-91ea-f96867529219
