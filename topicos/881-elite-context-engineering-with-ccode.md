# Elite Context Engineering with CCode

> Tópico 881 · 7 mensagens úteis de 18 totais

---

**INEMA** · 2025-09-12

**hacks práticos** que o vídeo mostrou sobre Context Engineering com Claude Code, organizados para você aplicar:

---

### Hacks de Redução (Reduce)

1. **Nunca use **`default mcp.json`**

**   * Hack: delete esse arquivo para liberar até 20k tokens.
   * Se precisar, carregue MCP manualmente com `claude --mcp-config`.

2. **Contexto enxuto em memória (`claw.md`)**

   * Hack: reduza ao mínimo indispensável.
   * Use **context priming** (`/prime`) em vez de carregar sempre 20k+ tokens de memória.

3. **Contexto sempre verificado**

   * Hack: use `/context` ou `claude now context` constantemente para monitorar.
   * Meta: manter acima de 90% livre no boot.

---

### Hacks de Delegação (Delegate)

4. **Sub-agents para trabalhos pesados**

   * Hack: tarefas como web scraping ou leitura de docs devem ser feitas por sub-agents (`/load AI docs`), não pelo agente principal.
   * Assim, cada sub-agent consome sua própria janela de contexto sem poluir a principal.

5. **Background agents para sair do loop**

   * Hack: use `/background` para rodar planos ou tarefas longas em paralelo.
   * Exemplo: gerar um plano completo enquanto você continua no fluxo.

6. **Delegar sempre que possível**

   * Hack: se a tarefa pode ser isolada, crie um agente especializado.
   * Lembre-se: “um agente focado é um agente performático”.

---

### Hacks Avançados

7. **Context Bundles para continuidade**

   * Hack: use `/loadbundle` para reprime um agente no mesmo ponto em que outro parou, sem carregar o lixo do contexto antigo.
   * Economiza tempo e tokens.

8. **Prime focado por tarefa**

   * Hack: crie `/prime bug`, `/prime feature`, `/prime chore` etc., para cada tipo de trabalho.
   * Isso dá precisão e evita poluição no contexto.

9. **Logs e trilhas inteligentes**

   * Hack: habilite bundles e report files para ter histórico leve (70% do contexto essencial).
   * Útil para debug, retomada e análise de fluxo.

---

### Hacks Estratégicos

10. **Sempre medir antes de escalar**

    * Hack: domine **um agente bem focado** antes de tentar multi-agents.
    * Senão, você só multiplica o desperdício.

11. **Delegação progressiva**

    * Hack: comece com sub-agents, depois avance para multi-agents com CLI/SDK.
    * Cada passo aumenta controle e escalabilidade.

12. **Context Engineering é aposta segura**

    * Hack: investir tempo em reduzir e delegar contexto **sempre paga** em performance, custo e tempo.

---

---

**INEMA** · 2025-09-12

**Elite Context Engineering with Claude Code**:

### Comandos Relacionados a MCP

* `claude now context` → verificar o consumo do contexto.
* `clade --mcp-config` → carregar manualmente uma configuração MCP específica.
* `strict-mcp-config` → sobrescrever globais ao iniciar MCP.
* `flashcontext` → checar contexto reduzido após carregar apenas um MCP.

### Comandos de Memória e Contexto

* `/context` → mostrar o estado atual do contexto.
* `/prime` → comando de **context priming** (inicializa contexto com um prompt dedicado).
* `clld` → alias usado para resetar/reinicializar o agente.
* `slashcontext` (equivalente a `/context`, usado no exemplo).

### Comandos de Sub-Agents e Delegação

* `/prime bug`, `/prime chore`, `/prime feature`, `/prime cc` → exemplos de context priming focado em diferentes tarefas.
* `/load AI docs` → carregar documentação com sub-agents.
* `Doc scraper` (executado via sub-agent para web scraping).

### Comandos de Context Bundles

* `/prime` → gera um bundle durante a execução.
* `/loadbundle` → carregar um **context bundle** para reprime/reinicializar agente com histórico.

### Comandos de Delegação Avançada

* `/background` → cria um **background agent** que roda fora do loop principal.
* `YOLO mode` (ex.: `claude opus YOLO mode`) → modo de execução mais solto para testes.

---

**INEMA** · 2025-09-12

**Elite Context Engineering with Claude Code**:

### Importância da Context Engineering

* O contexto é o recurso mais valioso dos agentes (Claude Code, por exemplo).
* A performance de um agente depende de quão bem o contexto é gerenciado.
* Dois pilares para isso: **R\&D = Reduce (reduzir) e Delegate (delegar)**.

### Níveis de Context Engineering

1. **Iniciante (Reduce)**

   * Erro comum: carregar MCP servers desnecessários que consomem milhares de tokens.
   * Solução: não usar `default mcp.json`, carregar MCPs somente quando realmente precisar.
   * Outro problema: `claw.md` muito grande (memória sempre carregada).
   * Solução: **context priming** (usar prompts específicos e leves para inicializar contexto em vez de arquivos enormes e estáticos).

2. **Intermediário (Delegate com Sub Agents)**

   * Sub-agents funcionam com **system prompts**, não pesam no contexto principal.
   * Permitem delegar tarefas pesadas (ex: web scraping, leitura de docs).
   * Mantêm o contexto do agente principal limpo e reduzem desperdício de tokens.
   * Risco: gestão complexa de múltiplos agentes → é preciso isolar bem cada sub-agent e sua função.

3. **Avançado (Context Bundles)**

   * Uso de **context bundles** (logs do que o agente fez).
   * Permite reprime ou reiniciar agentes com o histórico condensado, sem carregar todo o contexto de novo.
   * Dá continuidade ao trabalho quando o contexto “explode” (fica muito grande).
   * Garante eficiência e consistência entre execuções.

4. **Agêntico (Multi-Agent Delegation)**

   * Criação de agentes primários que gerenciam outros agentes (multi-agent systems).
   * Possível rodar **background agents** que executam tarefas fora do loop principal.
   * Isso tira o usuário da necessidade de ficar “babysitting” cada instância.
   * Padrão: criar agentes especializados, cada um focado em uma função clara, e orquestrá-los.
   * Tendência: cada vez mais “compute orquestrando compute, agentes orquestrando agentes”.

### Técnicas-Chave

* **Reduzir desperdício**: não carregar contextos enormes ou irrelevantes.
* **Delegar trabalho**: usar sub-agents e multi-agents para dividir tarefas.
* **Context Priming**: prompts focados para inicializar apenas o necessário.
* **Bundles**: reaproveitar contexto de sessões anteriores sem poluir o atual.
* **Background Agents**: rodar agentes autônomos em paralelo, liberando o principal.

### Conclusão

* O foco deve ser **agentes especializados e bem definidos**: “Um agente focado é um agente performático”.
* Mais importante do que economizar tokens é **usá-los bem**, evitando erros e retrabalho.
* O futuro é orquestrar múltiplos agentes, cada um fazendo uma tarefa específica de forma eficiente.
* Apostar em **context engineering** é um caminho seguro para escalar e melhorar automações com agentes.

---

---

**INEMA** · 2025-09-12

Assista o video, tem alguns Comando q a trascricao fez diferente

---

**INEMA** · 2025-09-12

https://www.youtube.com/watch?v=Kf5-HWJPTIE

---

**INEMA** · 2025-09-12

Elite Context Engineering with CCode - Claude Code

---

**INEMA** · 2025-09-12

https://chatgpt.com/c/68c394a3-0164-832f-baf2-774a70ade8e9
