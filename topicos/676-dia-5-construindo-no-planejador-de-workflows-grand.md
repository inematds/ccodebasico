# Dia 5: Construindo no Planejador de Workflows (Grandes Atualizações)

> Tópico 676 · 14 mensagens úteis de 35 totais

---

**INEMA** · 2025-09-03

primeiros caracteres do body e stack do erro.

Onde guardar chaves?
Em .env local e variáveis no painel do Vercel; nunca commitar.

# Checklist final para replicar

1. Planeje 30–40 min: objetivos, critérios de sucesso, erros esperados.
2. Corrija UI base: botões, paddings, estados de carregamento.
3. Adicione auto-healing do Mermaid.
4. Configure GitHub + Vercel + Supabase; crie .env e ignore no Git.
5. Integre Web Speech API: microfone, parar, Esc para cancelar.
6. Separe modelos: GPT-5 Nano (texto/UX) e Claude Sonnet (JSON).
7. Crie o botão Let’s Build It e o fluxo de validação e download do JSON.
8. Suba função serverless no Vercel para chamadas à Anthropic.
9. Aumente max tokens e trate parsing de respostas.
10. Instrumente logs, teste em aba anônima e faça commits pequenos.
11. Limpe arquivos legados e padronize a estrutura do repo.
12. Teste ponta a ponta e publique no Vercel.

---

**INEMA** · 2025-09-03

# Passo a passo do que ele fez no vídeo (didático e claro)

1. Alinhou objetivos do dia
   Definiu que iria evoluir do Planejador (Dia 4) para algo mais usável:
   planejar → gerar diagrama Mermaid com auto-correção → botão para gerar JSON importável no n8n → ditado por voz → deploy.

2. Ajustou rapidamente a UI inicial
   Corrigiu sobreposição de botões no topo do diagrama e melhorou o espaçamento/padding para leitura do usuário.

3. Detectou e tratou erros do Mermaid
   Percebeu que às vezes o LLM gerava sintaxe inválida.
   Criou um ciclo de validação: se o diagrama falhar, capturar o erro, reenviar ao LLM com o erro e tentar até renderizar (self-healing).

4. Separou “planejamento” de “execução”
   Abriu uma nova sessão só para mudanças maiores.
   Usou modo de planejamento: listar tarefas, dependências e critérios de sucesso antes de escrever/alterar código.

5. Preparou infraestrutura e versionamento
   Criou/ligou repositório no GitHub.
   Configurou deploy no Vercel.
   Conectou Supabase e registrou MCPs (Vercel e Supabase) para facilitar operações.
   Definiu .env e garantiu que chaves não fossem commitadas.

6. Implementou entrada de voz
   Reaproveitou uma implementação anterior.
   Confirmou que o projeto usava Web Speech API do navegador (não Whisper).
   Documentou o passo a passo em um arquivo .md e integrou: botão de microfone ao lado do enviar, iniciar/parar, cancelar com Esc.

7. Definiu os modelos por função
   Usou GPT-5 Nano para planejamento/respostas longas e UX.
   Usou Claude 4 Sonnet para gerar o JSON final do workflow, por ser mais robusto em estruturas.

8. Criou o botão Let’s Build It
   Após o plano e o diagrama, adicionou um botão que:
   envia o plano ao Claude 4 Sonnet → recebe somente JSON → remove marcas indesejadas → valida JSON → oferece download para importar no n8n.

9. Aumentou limites de tokens e saneou parsing
   Evitou respostas truncadas ajustando o max output tokens.
   Tratou as respostas removendo aspas triplas, trechos extras e só então validando o JSON.

10. Contornou CORS com backend
    Viu que chamadas à Anthropic direto do browser falhavam por CORS.
    Moveu a chamada para uma função serverless no Vercel, usando a chave no servidor e retornando apenas o resultado ao frontend.

11. Instrumentou logs e testou corretamente
    Ligou logs detalhados de request/response/erros no Console.
    Testou em aba anônima para evitar cache e service workers atrapalhando.
    Fez commits pequenos e frequentes como checkpoints.

12. Limpou o repositório e consolidou a entrega
    Removeu arquivos legados/rascunhos.
    Padronizou estrutura e manteve .env fora do Git.
    Verificou: diagrama com auto-healing, explicação em primeira pessoa, voz funcionando, botão Let’s Build It gerando JSON válido, deploy no Vercel.

# Exemplos rápidos por etapa

Etapa 3 – Auto-healing Mermaid
Exemplo: capturar “Mermaid syntax error at line 23”, reenviar o trecho com erro ao LLM e tentar até renderizar.
Resultado: o usuário não fica preso em tela vazia; vê o diagrama final.

Etapa 6 – Voz com Web Speech API
Exemplo: botão microfone do lado do enviar; segurar para gravar, soltar para enviar; pressionar Esc para cancelar.
Resultado: experiência sem fricção e sem dependência de serviços pagos.

Etapa 8 – Let’s Build It → JSON n8n
Exemplo: enviar o plano da automação para o Claude, exigir só JSON, validar e oferecer o download.
Resultado: arquivo pronto para importar no n8n em um clique.

Etapa 10 – Função serverless
Exemplo: criar endpoint /api/generate-json no Vercel, chamar a Anthropic com a key do servidor e devolver JSON.
Resultado: sem CORS e sem expor credenciais no cliente.

# Perguntas essenciais com respostas curtas

Por que separar modelos?
Para maximizar qualidade: GPT-5 Nano no texto/UX; Claude Sonnet no JSON estruturado.

Como garantir JSON válido?
Sanitizar saída, validar com parser; se falhar, reenviar com o erro até passar.

Como evitar “não atualiza na tela”?
Aba anônima, limpar cache/service worker e versionar assets corretamente.

O que logar no Console?
Endpoint, status, tempo,

---

**INEMA** · 2025-09-03

offscreen/try-catch e só mostrar se ok.
    Pergunta comum: e se o LLM insistir errado?
    Resposta: reduza temperatura, forneça contraexemplos, aplique regex sanitizadora e adicione “respond only with JSON”.

12. Estados de UI explícitos
    O que é: loading, corrigindo, pronto, erro; sempre mostrar o que está acontecendo.
    Exemplo: “Gerando diagrama…”, “Corrigindo sintaxe… tentativa 2/4”, “JSON validado. Baixar”.
    Pergunta comum: isso não polui?
    Resposta: use toasts discretos/inline; melhora percepção de qualidade.

13. Botão de voz com controle de fluxo
    O que é: iniciar/parar gravação, enviar automático opcional, tecla Esc para sair.
    Exemplo: segurar para gravar; soltar para enviar; Esc para cancelar sem enviar.
    Pergunta comum: e acessibilidade?
    Resposta: adicione atalhos de teclado e aria-labels.

14. Backoff e limites de token
    O que é: aumentar max output tokens quando truncar; usar retries com backoff para APIs.
    Exemplo: setar 10k–50k tokens de saída nos prompts longos; retries 3–5 com 250ms→2s.
    Pergunta comum: como detectar truncamento?
    Resposta: padrões como “…”/corte abrupto; some com verificação de JSON incompleto.

15. Documentação mínima viva
    O que é: criar .md curto com como instalar, rodar e onde estão os pontos críticos.
    Exemplo: CLOUD\_WEB\_SPEECH.md com snippet, dependências e “erros comuns e correções”.
    Pergunta comum: o time lê?
    Resposta: sim, se curto e ligado a tarefas: “1 min de leitura, salva 1 hora de debug”.

Lista curtinha dos hacks em 2 palavras cada
Planejamento primeiro
Reuso código
Aba anônima
Logs completos
Auto-healing
Proxy serverless
Commits micro
Segredos .env
Triple quotes
Modelos divididos
Validação saída
UI estados
Voz com Esc
Backoff/tokens
Doc mínima

---

**INEMA** · 2025-09-03

Aqui vão hacks detalhados, cada um com exemplo aplicado e perguntas/respostas rápidas.

1. Planejar antes de codar
   O que é: 30–40 min de planejamento claro (objetivo, entradas, saídas, erros esperados, checkpoints).
   Exemplo: antes de implementar voz e JSON, escrever “checklist de sucesso”: diagrama rende sem erro; JSON baixa e importa no n8n; botão de voz inicia/para com Esc; logs aparecem no Console.
   Pergunta comum: isso não atrasa?
   Resposta: reduz retrabalho. No vídeo, o plano evitou horas perdidas em bugs de CORS e parsing.

2. Reaproveitar código como “cheat code”
   O que é: copiar trechos testados de projetos anteriores e adaptar.
   Exemplo: portar a lógica do botão de ditado baseada em Web Speech API de um app anterior; documentar num .md para reuso.
   Pergunta comum: não carrega dívidas técnicas?
   Resposta: só se copiar “às cegas”. Padronize, isole em função e teste em sandbox.

3. Testar em aba anônima para matar cache
   O que é: sempre abrir a versão local/produção em janela anônima quando a UI “não muda”.
   Exemplo: ícone de microfone “feio e travado” funcionou na aba anônima; na aba normal, o cache segurava CSS/JS antigo.
   Pergunta comum: quando usar?
   Resposta: toda vez que “eu mudei, mas não apareceu”. Também limpe Service Workers quando houver.

4. Logar tudo no Console
   O que é: instrumentar prints claros do ciclo completo: request, payload, response, erros.
   Exemplo: logar status e body da resposta do GPT-5 Nano e do Claude; copiar todo o Console quando quebrar e colar no prompt do agente.
   Pergunta comum: o que logar?
   Resposta: endpoint, parâmetros essenciais, tempo da chamada, código de status, primeiros 200–500 chars do body e stack do erro.

5. Auto-healing de Mermaid e JSON
   O que é: validar saída; se falhar, reenviar com o erro e tentar novamente até render/parsear.
   Exemplo: ao detectar “Mermaid syntax error at line X”, reenviar ao LLM com o trecho problemático; para JSON, remover aspas triplas, validar com JSON.parse e refazer em caso de falha.
   Pergunta comum: quantas tentativas?
   Resposta: 3–6 com backoff exponencial; mostre estado “corrigindo diagrama…” para não parecer travado.

6. Proxy serverless para contornar CORS
   O que é: nunca chamar Anthropic/OpenAI direto do browser quando CORS bloquear; use função serverless (Vercel/Netlify).
   Exemplo: criar /api/generate-json no Vercel que recebe o plano, chama Claude Sonnet com a key do servidor e devolve o JSON válido.
   Pergunta comum: é seguro?
   Resposta: muito mais seguro que expor chave no cliente. Combine com .env e rate limit.

7. Commits pequenos e frequentes como checkpoints
   O que é: granularidade de commit por feature/fix, com mensagens claras.
   Exemplo: “feat(voice): adiciona Web Speech API + Esc para parar”; “fix(mermaid): auto-heal em 3 tentativas”.
   Pergunta comum: quando versionar .env?
   Resposta: nunca. Use .env.example sem chaves reais.

8. .env e separação de segredos
   O que é: variáveis em .env; Git ignora; app lê via process.env; em produção, usar painel de env do Vercel.
   Exemplo: CLAUDE\_API\_KEY, OPENAI\_API\_KEY, SUPABASE\_URL, SUPABASE\_ANON\_KEY.
   Pergunta comum: como compartilhar?
   Resposta: entregue .env.example e docs curtos “onde colar as chaves”.

9. Triple quotes em prompts no Python
   O que é: strings multilinha com """ … """ para evitar quebrar aspas ao editar.
   Exemplo: system\_prompt = """regras…"""; user\_prompt = """conteúdo…""".
   Pergunta comum: e performance?
   Resposta: nenhuma diferença; só evita bugs de sintaxe e facilita manutenção.

10. Divisão de modelos por tarefa
    O que é: usar um modelo para raciocínio/UX e outro para saída estruturada.
    Exemplo: GPT-5 Nano para planejar e redigir explicações; Claude 4 Sonnet para gerar JSON do n8n.
    Pergunta comum: por que separar?
    Resposta: maximiza qualidade de JSON e reduz alucinação em estruturas.

11. Validação de saída antes de exibir
    O que é: nunca renderizar direto; validar primeiro.
    Exemplo: para JSON, tentar JSON.parse e schema opcional; para Mermaid, renderizar em

---

**INEMA** · 2025-09-03

Aqui estão os principais hacks que ele usou no processo:

1. Planejar antes – gastar \~40 min planejando economiza horas de correção.
2. Reaproveitar código – usar implementações antigas como “cheat code”.
3. Testar em aba anônima – evita cache e erros invisíveis.
4. Logar tudo – console como “raio-x” do app.
5. Auto-healing – diagramas/JSON se corrigem sozinhos.
6. Proxy serverless – contornar CORS com Vercel functions.
7. Commits frequentes – checkpoints para não perder progresso.
8. .env seguro – nunca versionar chaves de API.
9. Simplificar prompts – usar GPT-5 Nano para texto e Claude Sonnet só para JSON.
10. Triple quotes – evitar erros ao editar prompts longos no Python.

---

**INEMA** · 2025-09-03

1. Botões/espaço
2. Auto-correção Mermaid
3. Voz/WebSpeech
4. Botão/JSON
5. GPT-5 Nano
6. Tokens/limite
7. CORS/backend
8. Logs/console
9. GitHub/Vercel/Supabase
10. Limpeza/.env

---

**INEMA** · 2025-09-03

Lista simples do que ele fez:

1. Corrigiu botões sobrepostos e ajustou espaçamento no diagrama.
2. Criou sistema de auto-correção (self-healing) para diagramas Mermaid.
3. Adicionou entrada de voz com Web Speech API (microfone, parar com Esc).
4. Implementou botão “Let’s Build It” que gera e baixa JSON válido para n8n.
5. Usou GPT-5 Nano para texto/planejamento e Claude 4 Sonnet para JSON.
6. Aumentou limite de tokens de saída para evitar cortes nas respostas.
7. Resolveu erro de CORS movendo chamadas da API para backend/Vercel.
8. Ativou logs completos no Console para depuração.
9. Criou repositório GitHub, integrou Vercel e Supabase.
10. Organizou repositório: limpou arquivos antigos e criou .env para chaves.

---

**INEMA** · 2025-09-03

frequentes.

Higiene do repositório
Exemplo: remoção de app-old.js, testes/rascunhos; .env ignorado; estrutura limpa para clonar/deploy.
Pergunta: como compartilhar com segurança?
Resposta: nunca commitar chaves; documentar onde colocar credenciais localmente.

Modelos e limites
Exemplo: GPT-5 Nano para texto/planejamento; Claude 4 Sonnet para JSON; ajuste de tokens para não truncar.
Pergunta: quando trocar de modelo?
Resposta: usar Claude para saídas estruturadas (JSON/diagramas) e manter Nano para UI/razão longa.

---

**INEMA** · 2025-09-03

Transformou o protótipo do Dia 4 em uma ferramenta mais usável para planejar e começar a “construir” workflows, adicionando voz, diagrama Mermaid com auto-correção, geração e download de JSON para importar no n8n, e um fluxo de depuração/logs bem mais robusto. Também preparou o ambiente com GitHub, Vercel e Supabase, organizou o repositório e resolveu bloqueios de CORS via backend.

Resumo do que ele fez

1. Melhorias de UI e experiência
   • Corrigiu sobreposição e espaçamento dos botões sobre o diagrama.
   • Alinhou o botão de microfone ao botão enviar e colocou ao lado do campo de mensagem.
   • Evitou explicações repetitivas: agora a explicação detalhada do diagrama é opcional.

2. Diagrama Mermaid com auto-healing
   • Detecta erro de sintaxe ao renderizar.
   • Reenvia automaticamente para o LLM com a mensagem de erro até corrigir e renderizar.
   • Adicionou sinais de estado para o usuário entender que está “corrigindo em silêncio”.

3. Entrada de voz sem fricção
   • Implementou ditado via Web Speech API (nativa do navegador).
   • Permitiu interromper com Esc e evitou envio automático indesejado.
   • Reaproveitou lógica de um projeto anterior, documentando o passo a passo em .md.

4. Geração de JSON para n8n
   • Criou o botão Let’s Build It após o diagrama/explicação.
   • Envia o plano do workflow para o Claude 4 Sonnet, que retorna apenas JSON.
   • Limpa marcas não-JSON (p.ex., aspas triplas), valida e, se inválido, refaz até ficar parseável.
   • Disponibiliza o JSON para download e importação direta no n8n.

5. Modelos e limites de tokens
   • Usou GPT-5 Nano para raciocínio de interface/planejamento e textos longos.
   • Usou Claude 4 Sonnet para gerar o JSON final.
   • Ajustou max output tokens para evitar respostas cortadas.

6. Infra/DevOps e CORS
   • Criou repositório GitHub, integrou Vercel para deploy contínuo e conectou Supabase.
   • Configurou MCPs (Vercel e Supabase) no ambiente.
   • Moveu chamadas à Anthropic para backend/serverless (Vercel functions) para contornar CORS.
   • Criou .env e garantiu que chaves não vão para o Git.

7. Depuração e observabilidade
   • Ligou logs detalhados no Console do navegador e do servidor.
   • Passou a testar em janela anônima para eliminar cache/estado.
   • Fez commits frequentes como checkpoints e limpou arquivos legados do repo.

8. Entrega final
   • App planejador com: perguntas de refinamento, diagrama Mermaid auto-corretivo, explicação em primeira pessoa, ditado por voz, botão Let’s Build It e download de JSON válido.
   • Deploy no Vercel funcionando; repositório limpo e documentado.

Tópicos com exemplos e respostas objetivas

Planejamento e checkpoints
Exemplo: 40 min de planejamento antes de escrever código, definindo tarefas, estados e validações.
Pergunta: por que investir tanto em planejamento?
Resposta: reduz retrabalho, antecipa erros de integração e acelera a implementação.

Auto-correção de Mermaid
Exemplo: ao falhar o render, capturar o erro, reenviar para o LLM e repetir até renderizar.
Pergunta: como evitar tela “vazia” quando falha?
Resposta: mostrar estado de processamento e mensagem discreta de auto-correção.

Entrada de voz
Exemplo: botão de microfone do lado do enviar, interrompível com Esc, sem envio automático involuntário.
Pergunta: precisa de Whisper?
Resposta: não; Web Speech API resolve no cliente e simplifica o stack.

JSON para n8n
Exemplo: Let’s Build It envia o plano ao Claude 4 Sonnet, retorna JSON limpo e validado para download.
Pergunta: como garantir JSON válido?
Resposta: sanitizar resposta, validar JSON; se inválido, refazer pedindo correção com o erro.

CORS e chamadas de API
Exemplo: chamadas diretas à Anthropic no browser falharam; passou por função serverless.
Pergunta: qual o padrão recomendado?
Resposta: proxy/backend (Vercel functions) para chamadas a provedores que bloqueiam CORS.

Logs e debugging
Exemplo: copiar todo o Console quando algo quebra e anexar ao pedido de correção do agente.
Pergunta: como acelerar diagnóstico?
Resposta: logar tudo, testar em aba anônima e versionar com commits pequenos e

---

**INEMA** · 2025-09-03

estrutura; se inválido, reenviar com o erro até gerar JSON parseável.

Modelos e tokens
Exemplo: GPT-5 Nano para raciocínio de interface e textos; Claude 4 Sonnet para o JSON final.
Pergunta: e se cortar a resposta?
Resposta: aumentar max output tokens e dividir em partes quando necessário.

CORS e Anthropic
Exemplo: chamadas diretas do browser falham por CORS; mover para função serverless no Vercel.
Pergunta: como contornar CORS?
Resposta: criar endpoint proxy no backend que faz a chamada à API e retorna ao frontend.

Depuração e observabilidade
Exemplo: copiar o Console completo quando algo quebra e anexar ao pedido de correção do agente.
Pergunta: quais práticas ajudam mais?
Resposta: logar tudo, testar em aba anônima, commits frequentes, checkpoints claros.

UI e UX
Exemplo: alinhar altura do botão de voz e enviar; evitar loops de explicação repetitiva; sinalizar estados de processamento.
Pergunta: como reduzir frustração do usuário?
Resposta: feedback visual claro, cancelamento fácil do ditado, botões coerentes e discretos.

Versionamento e segurança
Exemplo: .env ignorado no Git; integração GitHub+Vercel com deploy só após teste local.
Pergunta: como compartilhar o projeto com segurança?
Resposta: nunca versionar chaves; fornecer instruções para o usuário inserir suas credenciais localmente.

Reaproveitamento de código
Exemplo: importar a lógica de ditado de outro app; converter em guia .md para replicar.
Pergunta: quando vale reaproveitar?
Resposta: quando economiza tempo sem introduzir dependências desnecessárias; sempre revisar diferenças de contexto.

Boas práticas consolidadas do vídeo

• Planeje primeiro, execute depois; 40 minutos de plano economizam horas de correção.
• Logue tudo e use o Console como verdade operacional.
• Não deixe uma IA ditar arquitetura para outra; prefira contratos simples e funções mínimas.
• Use proxy serverless para chamadas de APIs que bloqueiam CORS.
• Valide e auto-corrija outputs do LLM (Mermaid e JSON).
• Teste em janela anônima e faça commits frequentes como checkpoints.
• Mantenha o repositório limpo, com .env e estrutura previsível para clonar e publicar.

---

**INEMA** · 2025-09-03

Resumo completo e direto do conteúdo

Visão geral

A evolução do Planejador de Workflows do Dia 4 para um protótipo mais usável: planejamento, geração de diagrama Mermaid com auto-correção, botão “Let’s Build It” para gerar um JSON importável no n8n e entrada de voz via Web Speech API. O autor prioriza planejamento longo, logs detalhados e ciclos de depuração rápidos para superar falhas de UI, erros de sintaxe no Mermaid, CORS para chamadas da API da Anthropic e parsing de respostas de modelos.

Linha do tempo e o que foi feito

1. Ajustes rápidos de UI e sintaxe
   – Espaçamento e sobreposição de botões no topo do diagrama foram corrigidos.
   – Erros de sintaxe do Mermaid surgiram; criou-se um loop de validação e auto-correção silenciosa do diagrama.
   – Evitou-se excesso de explicações repetitivas: a explicação detalhada só aparece quando o usuário quer.

2. Preparação de ambiente e planejamento
   – Adoção de modo de planejamento antes de executar: definição de tarefas, revisão de premissas e checkpoints de commit.
   – Criação/integração do repositório GitHub; Vercel para deploy; Supabase para dados; MCPs de Vercel e Supabase configurados.
   – Organização de prompts e documentação em arquivos .md para orientar o Claude 4 Sonnet na geração de JSON.

3. Entrada de voz
   – Reaproveitamento de implementação anterior; descoberta de que o projeto usa Web Speech API nativa do navegador (não Whisper).
   – Melhoria da usabilidade do microfone: tamanho alinhado ao botão enviar, posicionamento ao lado, possibilidade de parar/gravar e evitar “envio forçado”.

4. Modelos e limites
   – Frontend usa GPT-5 Nano para planejamento/razão e geração de texto com janela grande de saída; JSON final é gerado pelo Claude 4 Sonnet.
   – Ajuste de tokens de saída para evitar truncamentos.
   – Resolução de parsing: extração do JSON puro das respostas, removendo aspas/triple-quotes e validando antes de disponibilizar.

5. CORS e chamadas de API
   – Detecção de bloqueio CORS nas chamadas diretas do navegador para a Anthropic.
   – Orientação para intermediar chamadas via serverless/proxy (Vercel functions) em vez de chamar a API diretamente no cliente.

6. Telemetria e depuração
   – Logar tudo no console e inspecionar a aba Console do navegador sistematicamente.
   – Testar em janela anônima para evitar cache e estados antigos.
   – Commits frequentes como pontos de restauração.

7. Limpeza e padronização do repositório
   – Remoção de arquivos antigos e experimentais; criação de .env ignorado pelo Git.
   – Estrutura simplificada para clonagem e deploy contínuo no Vercel.

8. Resultado final
   – Planejamento guiado por perguntas, diagrama Mermaid com auto-healing, explicação em primeira pessoa, botão “Let’s Build It” que gera e baixa JSON válido para importação no n8n, ditado por voz funcional, deploy no Vercel.
   – Pendências menores: feedback visual mais claro durante o auto-healing e ajustes finos no fluxo de explicações.

Tópicos com exemplos e respostas objetivas

Planejamento antes de codar
Exemplo: gastar 40 minutos detalhando tarefas, dependências e checagens de erro.
Pergunta: por que planejar longo?
Resposta: reduz retrabalho e acelera implementação; define critérios de validação e pontos de rollback.

Auto-correção de diagramas Mermaid
Exemplo: ao falhar o render, capturar o erro, reenviar para o LLM com o erro e reprocessar até renderizar.
Pergunta: como evitar que o usuário fique sem diagrama?
Resposta: implementar um estado de carregamento e uma rotina silenciosa de correção, exibindo aviso discreto de “corrigindo sintaxe”.

Entrada de voz com Web Speech API
Exemplo: botão de microfone ao lado do enviar, transcrevendo em tempo real e permitindo cancelar com Esc.
Pergunta: é preciso Whisper?
Resposta: não necessariamente; a Web Speech API resolve no navegador e reduz custo/complexidade.

Geração de JSON para n8n
Exemplo: após o diagrama e a explicação, o botão “Let’s Build It” chama Claude 4 Sonnet com o plano e retorna apenas JSON válido.
Pergunta: como garantir JSON válido?
Resposta: limpar trechos não-JSON, validar

---

**INEMA** · 2025-09-03

Claude Code Dia 5: Construindo no Planejador de Workflows (Grandes Atualizações)

Esta é a sessão maratona. 1 hora e 16 minutos de desenvolvimento real para você, mas 4 horas nos bastidores – do tipo em que nada funciona até que, de repente, tudo funciona.

Se você quer ver como realmente é construir com Claude Code quando as coisas dão errado, é aqui.

Publiquei este repositório para todos clonarem e desenvolverem: Repositório no GitHub.

O que você vai assistir: construção de uma ferramenta completa de planejamento de workflow com exportação em JSON, incluindo:

* Mais de 4 horas de desenvolvimento real comprimidas em 76 minutos
* Implementação do Claude 4 Sonnet para geração de JSON
* Adição da Web Speech API para entrada de voz
* Diagramas Mermaid AUTO-CORRETIVOS e validação de JSON
* Falhas de API e como corrigi-las
* O momento em que tudo finalmente se encaixa

A jornada da construção:
 – Fase de planejamento (sim, 40 minutos só de planejamento)

* Configurando Supabase e Vercel MCPs
* Criando arquivos de documentação para APIs
* Reaproveitando implementação de voz de projetos anteriores
* Configurando variáveis de ambiente

 – Fase da luta

* Botão de voz “feio pra caramba” e não funcionando
* Falhas em requisições de API mesmo com chaves corretas
* Política de CORS bloqueando chamadas da API do Claude
* Depuração no console para achar os erros reais

 – O avanço

* Finalmente interpretando corretamente as respostas da API
* Diagramas auto-corretivos funcionando silenciosamente
* Exportação JSON com o botão “Let’s Build It”
* Repositório limpo e implantação em produção

Lições críticas aprendidas:

* Registre TUDO no console para depuração
* Planejar 40 minutos economiza 4 horas de correção
* Não deixe a IA ditar para outra IA (classes/funções)
* Teste no modo anônimo para eliminar problemas de cache
* Faça commits com frequência – você vai precisar desses pontos de restauração

Funcionalidades finais entregues:

* Entrada de voz com Web Speech API
* Geração de diagramas de workflow com auto-correção
* Exportação JSON para importação no N8N
* Explicações em primeira pessoa da lógica do workflow
* Implantado no Vercel com integração ao GitHub

Estrutura do repositório (organizada):

* Removidos: app-old.js, testAPI.py, test-improvements.md
* Adicionado: arquivo .env para chaves de API
* Organizado: Estrutura de arquivos apropriada para clonagem

---

**INEMA** · 2025-09-03

Dia 5: Construindo no Planejador de Workflows (Grandes Atualizações)

---

**INEMA** · 2025-09-03

https://chatgpt.com/c/68b65e7f-00c8-832a-aa00-fc79705471f4
