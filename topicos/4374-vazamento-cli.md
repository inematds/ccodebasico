# Vazamento CLI

> Tópico 4374 · 5 mensagens úteis de 18 totais

---

**INEMA** · 2026-03-31

ue reescreve suas memórias sozinho**

---

## 🧑‍🤝‍🧑 9. Sistema de múltiplos agentes

Ele sugere que existe algo tipo “exército de agentes”:

* um líder
* vários executores
* tarefas divididas

👉 isso ainda vai evoluir mais

---

## 🚀 10. UltraPlan (muito interessante)

Fluxo:

1. você chama UltraPlan
2. sessão é enviada pra nuvem
3. roda em modo leitura
4. cria plano completo
5. volta pra você
6. você aprova
7. execução acontece local

👉 ideia:
**pensar na nuvem, executar na sua máquina**

---

## 🐞 11. Ultra Review

* agente remoto
* encontra bugs
* valida se são reais

👉 tipo QA automático com IA

---

## 🔮 12. Silent Forks

* cria processos invisíveis
* tenta prever seu próximo prompt

👉 tipo:
“o sistema já está pensando antes de você pedir”

---

## 📚 13. Magic Docs

* arquivos que se atualizam sozinhos
* aprendem com uso do projeto

👉 documentação viva

---

## 🐾 14. Buddy System (parte curiosa)

* “pets” com personalidade (duck, dragon, capybara…)
* cada um com estilo (debug, caos, etc.)
* tipo RPG

👉 provavelmente:
**forma de mudar comportamento da IA + gamificação**

---

## ⚠️ Insight final (o mais importante do vídeo)

Ele deixa claro:

👉 Isso tudo é poderoso
👉 Mas NÃO é o principal

O principal ainda é:

> **o modelo (Claude)**

Porque:

* você pode copiar o sistema
* mas não a inteligência

---

## 🧠 Resumo estilo frase do vídeo

> “Isso é o sistema operacional da IA… mas o cérebro ainda é o modelo.”

---

**INEMA** · 2026-03-31

## 🧠 1. Como a conversa realmente funciona (o loop interno)

Ele explica que não é “pergunta → resposta” simples.

É um **loop contínuo**:

1. Você digita algo
2. O sistema injeta:

   * system prompt
   * contexto da sessão
   * skills disponíveis
3. Isso vai pra API do Claude (streaming, não espera tudo pronto)
4. O modelo responde **parcialmente**
5. Se precisar → chama uma tool
6. A tool executa (ex: ler arquivo, rodar comando)
7. O resultado volta pro modelo
8. O modelo continua pensando
9. Isso repete até “achar que terminou”

👉 Ou seja:
**o modelo vai pensando + agindo ao mesmo tempo**

---

## 🔁 2. Query Loop (coração do sistema)

Ele destaca que isso roda tipo um motor:

* chama API
* executa tools
* valida segurança
* verifica contexto
* compacta se necessário
* repete

E isso pode acontecer várias vezes numa única resposta.

👉 Por isso parece “inteligente” — não é uma resposta só, é um processo.

---

## 🧰 3. Tools (bem mais complexas do que parecem)

Ele mostra que cada tool não é só “executar comando”.

Tem uma pipeline:

1. `call()` → executa
2. valida input (schema)
3. checa permissões (`settings.json`)
4. decide:

   * pode rodar em paralelo?
   * precisa aprovação?
   * é read-only?
5. pode ser interrompida (ESC/cancel)
6. pode rodar sob demanda

👉 Isso é tipo um mini-sistema operacional dentro do CLI.

---

## 🤖 4. Como ele cria agentes (clonagem)

Ele explica que os agentes são criados copiando o “estado”:

### 🔹 Standard

* começa do zero
* sem contexto
* independente

### 🔹 Fork

* copia o contexto do agente principal
* cria um “ramo paralelo”
* compartilha prefixo (economiza custo de API)

👉 isso é tipo “abrir outra aba com a mesma conversa”

### 🔹 Teammate (Agent Mode)

* roda em outro processo/terminal
* se comunicam via JSON (tipo caixa de mensagens)

👉 isso é literalmente multi-agente real

---

## 🧠 5. Prompt caching (parte importante)

Ele comenta algo avançado:

* agentes filhos reutilizam partes do contexto do pai
* compartilham “bytes idênticos”
* economiza custo e tempo

👉 isso explica:

* por que é rápido
* por que às vezes herda erros (tipo “alucinação”)

---

## 🔒 6. Segurança (camadas tipo “cebola”)

Ele fala que tem várias camadas:

1. sandbox → tudo roda isolado
2. permissões → allow / deny / ask
3. proteção de bash → comandos perigosos
4. proteção de código

👉 ideia:
**mesmo que o modelo queira fazer algo perigoso, ele é barrado**

Mas ele alerta:

> agora que isso vazou, pode ter gente tentando explorar

---

## 🧠 7. Contexto (parte MUITO importante)

Aqui ele entra em detalhe interessante:

O sistema **remove coisas ativamente**:

* resultados antigos de tools
* outputs de bash
* leituras antigas de arquivos

E faz:

* microcompactação (tempo/conteúdo)
* corte de histórico (snipping)
* auto-compactação

👉 conclusão:
**ele não guarda tudo — ele limpa agressivamente**

---

## 🧬 8. Memória (como ele “aprende”)

Ele divide em camadas:

### Tipos:

* usuário → quem você é
* feedback → erros e acertos
* projeto → tarefas atuais
* referência → links externos

### AutoDream:

* lê logs da sessão
* extrai “aprendizados úteis”
* remove ruído
* mantém `memory.md` com ~200 linhas

👉 isso é tipo:
**um cérebro que reescreve suas memórias sozinho**

---

## 🧑‍🤝‍🧑 9. Sistema de múltiplos agentes

Ele sugere que existe algo tipo “exército de agentes”:

* um líder
* vários executores
* tarefas divididas

👉 isso ainda vai evoluir mais

---

## 🚀 10. UltraPlan (muito interessante)

Fluxo:

1. você chama UltraPlan
2. sessão é enviada pra nuvem
3. roda em modo leitura
4. cria plano completo
5. volta pra você
6. você aprova
7. execução acontece local

👉 ideia:
**pensar na nuvem, executar na sua máquina**

---

## 🐞 11. Ultra Review

* agente remoto
* encontra bugs
* valida se são reais

👉 tipo QA automático com IA

---

## 🔮 12. Silent Forks

* cria processos invisíveis
* tenta prever seu próximo prompt

👉 tipo:
“o sistema já está pensando antes de você pedir”

---

## 📚 13. Magic Docs

* arquivos que se atualizam sozinhos
* aprendem com uso do projeto

👉 documentação

---

**INEMA** · 2026-03-31

Explicando cada recurso:

---

## ⚙️ 1. Query Engine (motor de conversa)

**Como funciona:**

* Recebe sua mensagem → adiciona contexto + prompt → chama API → executa tools → repete em loop

**Para que serve:**

* Orquestrar toda a conversa até resolver a tarefa

---

## 🧰 2. Tools (ferramentas)

**Como funciona:**

* Cada tool tem: execução (`call`), validação, permissões e controle
* Pode rodar em paralelo ou ser interrompida

**Para que serve:**

* Ler arquivos, rodar comandos, editar código, buscar dados

---

## 🤖 3. Subagentes

**Como funciona:**

* **Standard:** começa do zero
* **Fork:** copia contexto e cria ramificação
* **Teammate:** roda separado e se comunica via mensagens

**Para que serve:**

* Dividir tarefas e acelerar execução

---

## 🧠 4. Context Management

**Como funciona:**

* Remove dados antigos automaticamente
* Compacta histórico (microcompact + auto)

**Para que serve:**

* Evitar limite de contexto e manter performance

---

## 🧬 5. Memory (memória)

**Como funciona:**

* Tipos:

  * usuário (preferências)
  * feedback (erros/acertos)
  * projeto (tarefas atuais)
  * referência (links/dados externos)
* AutoDream resume tudo

**Para que serve:**

* Fazer a IA “lembrar” e melhorar ao longo do tempo

---

## 🔒 6. Segurança

**Como funciona:**

* Sandbox (ambiente isolado)
* Permissões (allow/deny/ask)
* Proteções no bash
* Barreiras no código

**Para que serve:**

* Evitar comandos perigosos ou acesso indevido

---

## 🔗 7. Bridge

**Como funciona:**

* Conecta CLI com browser/IDE via WebSocket

**Para que serve:**

* Integrar com VS Code, navegador e outras interfaces

---

## 🧑‍🤝‍🧑 8. Multi-agentes (Army Mode)

**Como funciona:**

* Um agente principal coordena vários agentes menores

**Para que serve:**

* Resolver tarefas complexas em paralelo

---

## 🚀 9. UltraPlan (não lançado)

**Como funciona:**

* Envia tarefa para um agente remoto na nuvem
* Ele planeja → devolve → você aprova → executa local

**Para que serve:**

* Planejamento avançado sem usar sua máquina

---

## 🐞 10. Ultra Review

**Como funciona:**

* Agente remoto analisa código e verifica bugs

**Para que serve:**

* Revisão automática de código

---

## 🔮 11. Silent Forks

**Como funciona:**

* Cria processos invisíveis que preveem seu próximo prompt

**Para que serve:**

* Sugerir ou antecipar o que você vai pedir

---

## 📚 12. Magic Docs

**Como funciona:**

* Arquivos que se atualizam automaticamente com novos aprendizados

**Para que serve:**

* Documentação viva do projeto

---

## 🐾 13. Buddy System

**Como funciona:**

* “Personas” tipo pets (duck, dragon, etc.) com estilos diferentes

**Para que serve:**

* Mudar comportamento da IA (debug, criatividade, etc.) de forma gamificada

---

## 🧠 RESUMO FINAL

Tudo isso junto forma um sistema onde:
👉 o modelo pensa
👉 o CLI organiza
👉 as tools executam
👉 os agentes escalam
👉 a memória aprende

---

**INEMA** · 2026-03-31

O **código do Claude Code CLI vazou acidentalmente** por causa de um arquivo `.map`, e que isso revelou bastante sobre como a ferramenta funciona internamente. Segundo ele, o material mostra a arquitetura do sistema, como conversas rodam, como agentes são criados, como contexto e memória são gerenciados e quais recursos escondidos ainda não lançados existem. 

### Resumo 

* uma conversa funciona em ciclo: você digita, o sistema injeta prompt/contexto/skills, chama a API, executa tools, devolve resultados ao modelo e repete até concluir; 
* o Claude Code tem um conjunto padronizado de ferramentas com validação, permissões, paralelismo e controle de interrupção; 
* ele cria agentes de três formas: **standard**, **fork** e **teammate/agent mode**; 
* o gerenciamento de contexto é agressivo: remove resultados antigos de tools, leituras velhas, outputs de bash e faz compactação automática; 
* a memória é dividida em tipos como memória do usuário, feedback, projeto e referência, com um sistema chamado **AutoDream** para consolidar tudo; 
* a segurança tem várias camadas: sandbox, permissões, proteções no bash e barreiras para proteger o código; 

### Recursos “secretos” que foi encontrado

* **UltraPlan**: manda o planejamento para uma sessão remota na nuvem e depois traz de volta para aprovação/execução; 
* **Ultra Review**: um caçador remoto de bugs; 
* sugestões de prompt que tentam prever sua próxima mensagem; 
* **Magic Docs**: documentação que se atualiza com novos aprendizados; 
* **Buddy System**: companheiros virtuais tipo “pet” para gamificar a experiência. 

### Ideia principal

A conclusão é: **o vazamento expõe a engenharia e a arquitetura do produto**, o que pode ajudar concorrentes, mas **o diferencial maior ainda seria o modelo em si**, não apenas o código do CLI.

---

**INEMA** · 2026-03-31

https://chatgpt.com/c/69cc1504-78bc-832a-8916-4f01ab66a9cb
