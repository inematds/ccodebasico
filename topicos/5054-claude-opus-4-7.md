# Claude OPUS 4.7

> Tópico 5054 · 9 mensagens úteis de 25 totais

---

**INEMA** · 2026-04-17

**Análise do Opus 4.7 - O que é real versus o que é hype
**
Resumindo: tanto faz - se alguém lhe disser que este modelo muda tudo, pode ignorar.

Esta é a minha análise imparcial do Opus 4.7 e se você realmente precisa migrar do 4.6.

Também explico 'como' avaliar um modelo e determinar se ele realmente traz algo novo.

A primeira coisa que sempre verifico é: este é um novo modelo base ou uma versão retreinada da mesma arquitetura?
→ É o mesmo modelo base com aprendizado por reforço, re-treinamento e ajustes de peso.
→ Não se trata de um novo paradigma, apenas de uma melhoria incremental em áreas específicas.

A maior mudança da qual a maioria das pessoas não fala: tokenização.

→ A forma como representa palavras, código e cadeia de pensamento mudou fundamentalmente.
→ A prosa em inglês custa de 15 a 30% mais fichas
→ o código é aproximadamente 1,5x
→ Isso significa um raciocínio melhor, pois dispõe de representações mais ricas, mas o contexto é consumido mais rapidamente.

Realizei três comparações diretas entre as versões 4.6 e 4.7:

Síntese do deck do tabuleiro:
→ A versão 4.7 realiza mais referências cruzadas e toma a iniciativa.
→ A saída do PowerPoint ficou visivelmente mais limpa e com melhor formatação, sem necessidade de configurações adicionais.
→ 4.6 A saída era apertada, padronizada, com elementos sobrepostos.

Revisão de contratos com fornecedores:
→ 4.6 encontrou 4 cláusulas bloqueadoras, 4.7 encontrou 7 mais uma cláusula oculta
→ 4.7 verificou cada citação com precisão em relação à fonte, 4.6 parafraseou algumas incorretamente
→ ⚠️ 4.7 é mais opinativo e lidera com confiança mesmo quando deveria ser cauteloso - cuidado com opiniões disfarçadas de fatos

Triagem em lote de tickets (80 tickets):
→ A versão 4.6 precisava ser agrupada em lotes de 20, enquanto a versão 4.7 processava todos os 80 em linha.
→ A versão 4.7 era mais disciplinada com as chamadas de ferramentas — não disparava chamadas desnecessárias como a versão 4.6 às vezes fazia.


Novidades que vale a pena conhecer:

→ O nível de esforço X-Alto fica entre Alto e Máximo - ideal para tarefas difíceis de verificar, revisão jurídica e bugs sutis.
→ /ultra-review transfere a revisão de código para a nuvem (consome tokens, use com moderação)
→ /recap fornece um resumo da sua sessão
→ melhor seguimento de instruções implícitas, mas isso significa que dicas preguiçosas são punidas mais severamente.


Quando usar cada um:

→ 4.7: trabalho longo de várias horas, depuração árdua, revisão com muitas verificações, liderança de equipe de agentes, análise densa
→ 4.6: trabalho em pipeline, tarefas onde a tokenização antiga pode ser mais eficiente, menor queima de tokens
→ Sonnet: ainda a ferramenta principal para iteração rápida, Excel, PowerPoint

Para voltar à versão 4.6: /model claude-opus-4-6

Resumindo, se alguém no YouTube disser que isso multiplicou por 55 o Código Claude deles, essa pessoa está mentindo para você.

---

**INEMA** · 2026-04-16

O **Claude Opus 4.7** foi lançado como uma versão mais avançada do 4.6, com melhorias reais em código, visão e precisão — mas **não é o modelo mais poderoso da Anthropic**.

👉 O mais avançado é o **Mythos Preview**, que não está disponível ao público.

---

## Ideia principal do artigo

O Opus 4.7 não é só um upgrade — ele é usado como um **“modelo de teste”**.

A Anthropic está usando ele para:

* testar **limites de segurança**
* validar **controles contra uso perigoso (principalmente cibersegurança)**
* aprender como liberar modelos mais poderosos no futuro

👉 Ou seja: ele é uma “ponte” para algo mais avançado.

---

## O que ele melhora

* Melhor em **programação**
* Grande avanço em **visão (imagens mais detalhadas)**
* Melhor **memória em tarefas longas**
* Mais precisão ao seguir instruções (menos interpretação)
* Melhor desempenho em áreas como **finanças e direito**

---

## Segurança (ponto chave)

* O modelo tem **restrições deliberadas**
* Bloqueia automaticamente usos perigosos em cibersegurança
* Profissionais legítimos precisam passar por **verificação** para usar nesses casos

👉 A empresa limitou o modelo de propósito

---

## Custo e impacto

* Preço por token continua igual ao 4.6
* Mas pode consumir **mais tokens** (novo tokenizer + mais raciocínio)

👉 na prática, pode sair mais caro dependendo do uso

---

## Conclusão

O Opus 4.7:

* é mais capaz e mais confiável que o 4.6
* mas foi lançado de forma **controlada e limitada**
* serve como um **campo de testes para segurança**
* prepara o caminho para modelos mais poderosos no futuro

---

**INEMA** · 2026-04-16

Aqui vai um **resumo direto e prático** do artigo:

---

## Best practices – Claude Opus 4.7 com Claude Code (resumo)

### 1. Seja mais específico no prompt

O 4.7 segue instruções **mais literalmente**, então:

* diga exatamente o que quer
* evite ambiguidade
  👉 prompts vagos = resultados mais fracos 

---

### 2. Use tarefas maiores (menos microgerenciamento)

O modelo foi otimizado para **trabalhos longos e complexos**:

* pode delegar mais etapas de uma vez
* menos necessidade de corrigir a cada passo
  👉 funciona melhor como “executor”, não só assistente 

---

### 3. Confie mais, mas valide outputs críticos

Ele agora:

* verifica o próprio trabalho
* comete menos erros em fluxos longos

Mas ainda assim:

* revise resultados importantes (principalmente código e dados)

---

### 4. Ajuste o nível de esforço (effort)

Use níveis mais altos (ex: `high` ou `xhigh`) quando:

* for código complexo
* envolver múltiplas etapas
* exigir precisão alta

👉 mais qualidade, porém mais custo/tempo 
---

### 5. Estruture tarefas em blocos claros

Funciona melhor quando você:

* define objetivo
* define contexto
* define formato de saída

Exemplo mental:

> objetivo → contexto → restrições → output

---

### 6. Use arquivos e contexto ao máximo

Claude Code é forte em:

* ler código inteiro
* manter contexto grande
* trabalhar com múltiplos arquivos

👉 quanto mais contexto relevante você dá, melhor o resultado

---

### 7. Evite depender de “intuição do modelo”

O 4.7:

* improvisa menos
* “adivinha” menos

👉 isso aumenta precisão, mas exige prompts melhores

---

### 8. Ideal para workflows contínuos

Melhor uso:

* refatoração grande
* debugging complexo
* criação de sistemas completos
* automação com múltiplas etapas

👉 menos indicado para tarefas rápidas e simples

---

## Conclusão (essência)

O Opus 4.7 com Claude Code funciona melhor quando você trata ele como:

👉 **um engenheiro que executa tarefas completas com instruções claras**
(e não como um chatbot que improvisa)

---

**INEMA** · 2026-04-16

https://claude.com/blog/best-practices-for-using-claude-opus-4-7-with-claude-code

---

**INEMA** · 2026-04-16

O **Claude Opus 4.7** foi lançado como uma evolução do 4.6, com foco em melhorar qualidade, precisão e consistência. Ele promete:

* Melhor desempenho em tarefas complexas (especialmente programação)
* Maior aderência a instruções
* Menos erros e “alucinações”
* Capacidade de revisar e corrigir o próprio raciocínio
* Melhor visão, criatividade e análise de documentos
* Melhor desempenho em contextos longos (até 1 milhão de tokens)

Uma grande novidade é o nível de esforço **“xhigh”**, que permite raciocínio mais profundo, além do modo de pensamento adaptativo.

---

### Problema anterior (Opus 4.6)

Antes do 4.7, muitos usuários reclamaram que o modelo piorou porque:

* Estava “pensando menos”
* Pulava etapas importantes (como ler arquivos antes de editar)
* Gerava respostas mais superficiais
* Cometia mais erros e abandonava tarefas
* Consumía muitos tokens sem entregar qualidade

Isso aconteceu principalmente por mudanças de configuração (redução do esforço), não necessariamente no modelo em si.

---

### O que mudou no 4.7

O 4.7 basicamente resolve essas críticas:

* Volta a pensar mais profundamente
* Executa tarefas com mais rigor
* Produz respostas mais estruturadas e úteis
* Melhora a confiabilidade geral

---

### Pontos de atenção

* Pode consumir **mais tokens** (logo, mais custo)
* Nem todos os ganhos são comprovados fora de benchmarks
* Ainda existem dúvidas se parte da melhora vem de ajustes que já poderiam existir antes

---

### Conclusão

O Opus 4.7 parece ser um avanço real e mais confiável que o 4.6, especialmente para tarefas complexas.
Mas o desempenho na prática ainda depende de testes reais — benchmarks sozinhos não garantem tudo.

---

**INEMA** · 2026-04-16

# Atualizações da versão 2.1.111

## Modelo

**Comando:** `/model`

* Modelo mantido como **Opus 4.7 (1M context)** *(padrão)*

---

## Novidades principais

* **Claude Opus 4.7 xhigh** agora está disponível
  Use `/effort` para ajustar o equilíbrio entre velocidade e inteligência.

* **Modo Auto** agora está disponível para assinantes **Max** ao usar **Opus 4.7**.

* Novo nível de esforço **xhigh** para **Opus 4.7**
  Fica entre **high** e **max**. Disponível via:

  * `/effort`
  * `--effort`
  * seletor de modelo
    Outros modelos continuam usando **high** como fallback.

---

## Melhorias no comando `/effort`

* Quando chamado sem argumentos, `/effort` agora abre um **slider interativo**.
* Navegação com as **setas do teclado**.
* Confirmação com **Enter**.

---

## Tema e interface

* Novo tema **“Auto (match terminal)”**
  Ajusta automaticamente entre modo claro/escuro de acordo com o terminal.
  Disponível em `/theme`.

* O menu `/skills` agora permite **ordenar por contagem estimada de tokens**
  Pressione **t** para alternar a ordenação.

* **Ctrl+U** agora limpa **todo o buffer de entrada**
  Antes, apagava apenas até o início da linha.
  Use **Ctrl+Y** para restaurar.

* **Ctrl+L** agora:

  * limpa a entrada do prompt
  * força um **redesenho completo da tela**

* O rodapé da visualização de transcript agora mostra atalhos:

  * `[` → exportar para scrollback
  * `v` → abrir no editor

* O marcador **“+N lines”** para colagens longas truncadas agora aparece como uma **linha horizontal de largura total**, facilitando a leitura.

---

## Novos recursos e skills

* Novo skill **`****/less****-permission-prompts`**
  Analisa transcripts em busca de chamadas comuns de Bash somente leitura e ferramentas MCP, propondo uma allowlist priorizada para `.claude/settings.json`.

* Novo comando **`****/ultrareview****`**
  Faz revisão completa de código na nuvem usando análise paralela com múltiplos agentes.

  * Sem argumentos: revisa a branch atual
  * `/ultrareview <PR#>`: busca e revisa um PR específico do GitHub

---

## Auto mode

* O **Auto mode** não exige mais `--enable-auto-mode`.

---

## Windows, Linux e macOS

* **Windows:** a ferramenta **PowerShell** está sendo liberada gradualmente.
  Para ativar ou desativar:

  * `CLAUDE_CODE_USE_POWERSHELL_TOOL`

* **Linux e macOS:** também é possível ativar com:

  * `CLAUDE_CODE_USE_POWERSHELL_TOOL=1`

  Requer `pwsh` disponível no `PATH`.

---

## Permissões e prompts

* Comandos Bash somente leitura com **glob patterns**
  Exemplo: `ls *.ts`

* Comandos iniciados com:

  * `cd <project-dir> && ...`

Agora **não disparam prompt de permissão**.

---

## Correções e melhorias de uso

* Agora o sistema sugere o **subcomando mais próximo** quando `claude <word>` é usado com erro de digitação.
  Exemplo:

  * `claude udpate` → sugestão: **“Did you mean claude update?”**

* Os arquivos de plano agora recebem nomes baseados no prompt
  Exemplo:

  * `fix-auth-race-snug-otter.md`
    Em vez de nomes puramente aleatórios.

* Melhorias em **`****/setup****-vertex`** e **`****/setup****-bedrock`**:

  * mostram o caminho real de `settings.json` quando `CLAUDE_CONFIG_DIR` está definido
  * reutilizam modelos já fixados em execuções futuras
  * oferecem opção **“with 1M context”** para modelos compatíveis

---

## Logs, debugging e estabilidade

* O modo headless com `--output-format stream-json` agora inclui **`plugin_errors`** no evento inicial quando plugins são rebaixados por dependências não satisfeitas.

* Nova variável de ambiente:

  * `OTEL_LOG_RAW_API_BODIES`
    Permite emitir requisições e respostas completas da API como eventos de log OpenTelemetry para depuração.

* Foram suprimidas mensagens espúrias relacionadas a:

  * descompressão
  * rede
  * erros transitórios
    que podiam aparecer no TUI durante uso normal.

* Foi revertido o limite introduzido na **v2.1.110** sobre tentativas de fallback sem streaming
  Motivo: a mudança reduzia esperas longas, mas aumentava falhas totais durante sobrecarga da API.

---

**INEMA** · 2026-04-16

transient error messages that could appear in the TUI during normal operation
     · Reverted the v2.1.110 cap on non-streaming fallback retries — it traded long waits for more outright failures during API overload

---

**INEMA** · 2026-04-16

❯ /model                                                                                                                                                                                      
  ⎿  Kept model as Opus 4.7 (1M context) (default)
                                                                                                                                                                                              
❯ /release-notes                                                                                                                                                                              
  ⎿  Version 2.1.111:                                                                                                                                                                     
     · Claude Opus 4.7 xhigh is now available! Use /effort to tune speed vs. intelligence                                                                                                     
     · Auto mode is now available for Max subscribers when using Opus 4.7                                                                                                                   
     · Added xhigh effort level for Opus 4.7, sitting between high and max. Available via /effort, --effort, and the model picker; other models fall back to high                             
     · /effort now opens an interactive slider when called without arguments, with arrow-key navigation between levels and Enter to confirm                                                   
     · Added "Auto (match terminal)" theme option that matches your terminal's dark/light mode — select it from /theme                                                                        
     · Added /less-permission-prompts skill — scans transcripts for common read-only Bash and MCP tool calls and proposes a prioritized allowlist for .claude/settings.json                   
     · Added /ultrareview for running comprehensive code review in the cloud using parallel multi-agent analysis and critique — invoke with no arguments to review your current branch, or    
     /ultrareview <PR#> to fetch and review a specific GitHub PR                                                                                                                              
     · Auto mode no longer requires --enable-auto-mode
     · Windows: PowerShell tool is progressively rolling out. Opt in or out with CLAUDE_CODE_USE_POWERSHELL_TOOL. On Linux and macOS, enable with CLAUDE_CODE_USE_POWERSHELL_TOOL=1 (requires
     pwsh on PATH)                
     · Read-only bash commands with glob patterns (e.g. ls *.ts) and commands starting with cd <project-dir> && no longer trigger a permission prompt
     · Suggest the closest matching subcommand when claude <word> is invoked with a near-miss typo (e.g. claude udpate → "Did you mean claude update?")
     · Plan files are now named after your prompt (e.g. fix-auth-race-snug-otter.md) instead of purely random words
     · Improved /setup-vertex and /setup-bedrock to show the actual settings.json path when CLAUDE_CONFIG_DIR is set, seed model candidates from existing pins on re-run, and offer a "with 1M
      context" option for supported models
     · /skills menu now supports sorting by estimated token count — press t to toggle
     · Ctrl+U now clears the entire input buffer (previously: delete to start of line); press Ctrl+Y to restore
     · Ctrl+L now forces a full screen redraw in addition to clearing the prompt input
     · Transcript view footer now shows [ (dump to scrollback) and v (open in editor) shortcuts
     · The "+N lines" marker for truncated long pastes is now a full-width rule for easier scanning
     · Headless --output-format stream-json now includes plugin_errors on the init event when plugins are demoted for unsatisfied dependencies
     · Added OTEL_LOG_RAW_API_BODIES environment variable to emit full API request and response bodies as OpenTelemetry log events for debugging
     · Suppressed spurious decompression, network, and

---

**INEMA** · 2026-04-16

Claude OPUS 4.7
