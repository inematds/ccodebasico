# ClaudeClaw v1 - Assistente Pessoal Local

> Tópico 3359 · 7 mensagens úteis de 22 totais

---

**INEMA** · 2026-02-27

https://youtu.be/AujrjZwrsQ4

---

**INEMA** · 2026-02-27

**Análise Detalhada de ClaudeClaw V2 - Guia Completo, Memória, Habilidades 💎 🦞
**
Este é o guia completo de como o ClaudeClaw funciona internamente e como tirar o máximo proveito dele (continuação da primeira publicação aqui: [ClaudeClaw V1](https://www.skool.com/earlyaidopters/introducing-v1-of-claudeclaw-your-cli-assistant-via-telegram?p=be44af9c)[ ](https://www.skool.com/earlyaidopters/introducing-v1-of-claudeclaw-your-cli-assistant-via-telegram?p=be44af9c)).

Antes de mais nada, o repositório está sendo atualizado ativamente, então certifique-se de acompanhá-lo no GitHub.

→ novos comandos de barra como /respin (inicia automaticamente um novo chat com base nas suas últimas 20 interações)

→ Integração com o Slack adicionada com instruções passo a passo completas no arquivo README.

Como a memória funciona em três camadas:

→ Camada 1: janela de contexto normal, igual a qualquer conversa do Código Claude

→ Camada 2: memória de longo prazo em um banco de dados SQLite com degradação de 2% ao dia (menciona a necessidade de aumentá-la novamente)

→ Camada 3: suas habilidades e personalidade via [CLAUDE.md](http://claude.md/)[ ](http://claude.md/)- não é necessário um ensaio sobre sua personalidade, três frases são suficientes.

Como criar uma skill do zero usando a API do Gumroad como exemplo.
→ Deu a Claude a documentação da API
→ Abriu meu navegador através do Claude no Chrome
→ tokens criados
→ Configurar OAuth
→ Desenvolvi a habilidade em 15 minutos sem nenhuma intervenção minha.
→ Fiz o mesmo para o Gmail e o Google Agenda, fornecendo a documentação bruta da API em vez de depender das integrações limitadas do n8n/MCP.


Essa é a mudança de mentalidade: você não está mais limitado às 6 a 8 ações que uma plataforma como n8n ou Zapier oferece.

→ Se o endpoint da API existir, você pode criar uma skill para ele e acessá-lo pelo Telegram.

🔗 https://github.com/earlyaidopters/claudeclaw

O controle remoto MCP da Anthropic complementa o ClaudeClaw, não o substitui.
→ O controle remoto é específico para a pasta do projeto; ClaudeClaw tem acesso a todo o seu computador.

---

**INEMA** · 2026-02-25

Aqui vai um **resumo direto do guia visual do ClaudeClaw** :

ClaudeClaw é um “bridge” (ponte) que conecta seu **Claude Code rodando no desktop** ao seu **telefone via Telegram**, usando o Agent SDK oficial. Em vez de criar um assistente separado ou usar soluções como OpenClaw (que violavam os termos ao extrair OAuth), você simplesmente faz seu Claude Code virar seu assistente móvel.

A ideia central:
Você já tem tudo — skills, MCP servers, CLAUDE.md, memória, sistema de arquivos, web search e sessões persistentes.
Você só adiciona uma ponte de ~200 linhas.
Pronto: seu Claude Code passa a funcionar no seu bolso.

O fluxo técnico (mostrado no diagrama):
Mensagem no Telegram → bot recebe → processa mídia (voz, foto, vídeo) → injeta memória relevante → Agent SDK inicia o CLI oficial do Claude → formata resposta → envia de volta. Tudo em poucos segundos.

Memória funciona em 3 camadas:

1. Resumo de sessão (continuidade via session ID).
2. Banco SQLite com FTS5 (memória semântica + episódica com decaimento).
3. Injeção automática de contexto antes de cada resposta.

O diferencial importante:
Não extrai token.
Não usa API hackeada.
Chama o binário oficial do Claude via SDK.
Token fica local em `~/.claude/`.

O mega prompt (900 linhas) permite gerar o sistema inteiro respondendo 4 perguntas:

* Plataforma (Telegram/Discord/iMessage)
* Voz (STT/TTS/nenhuma)
* Memória (full/simples/nenhuma)
* Recursos extras (scheduler, WhatsApp, vídeo, auto-start)

Setup leva cerca de 5 minutos:
Clonar repo → rodar wizard → npm start → mandar mensagem no Telegram.

Mensagem final do guia:
Pare de reconstruir tudo.
Construa uma ponte.
Use seu Claude Code de qualquer lugar.
Hoje Claude Code. Amanhã qualquer CLI de IA.

---

**INEMA** · 2026-02-25

É um **mega-prompt para reconstruir o ClaudeClaw do zero**.

Basicamente, o arquivo  é um guia completo que:

* Define o papel do assistente como **onboarding + construtor do projeto**
* Explica o que é o ClaudeClaw (assistente que roda localmente e é controlado por Telegram/Discord/iMessage)
* Descreve todas as funcionalidades possíveis:

  * Execução do Claude Code via SDK
  * Memória persistente (simples ou avançada com FTS e decaimento)
  * Voz (STT via Groq/OpenAI, TTS via ElevenLabs)
  * Análise de vídeo (Gemini)
  * Scheduler com cron
  * Ponte com WhatsApp
  * Serviço em background (launchd/systemd)
* Especifica toda a arquitetura do sistema
* Lista a estrutura de pastas e arquivos obrigatórios
* Define exatamente como cada arquivo deve ser implementado
* Explica o setup wizard interativo
* Inclui regras técnicas críticas (ex: usar `fileURLToPath`, evitar poluir `process.env`, usar `bypassPermissions`)
* Determina a ordem de build e validações finais

Em resumo:

É um manual técnico detalhado que ensina um agente Claude a gerar automaticamente um clone completo do ClaudeClaw, com configuração personalizada baseada nas escolhas do usuário.

---

**INEMA** · 2026-02-25

### 🔹 O que é o ClaudeClaw V1

* Assistente que roda **nativamente no seu computador**.
* Controlado via **Telegram**.
* Faz praticamente tudo que o OpenClaw fazia, mas local.
* Usa suas **skills globais do Claude Code** (ex: Gemini skill).

---

### 🔹 Funcionalidades Principais

* 📹 Envio de **vídeos** para análise (via Gemini).
* 🎙️ Envio de **áudios** com resposta em texto ou voz.
* 🖼️ Envio de imagens.
* 📝 Geração de posts (ex: LinkedIn a partir de vídeos).
* 📋 Integração com **Obsidian** (ex: `/todo`).
* 💬 Controle de **WhatsApp via Telegram** (opcional).
* 🔁 Multimodal completo (texto, imagem, vídeo, voz).

---

### 🔹 Comandos Importantes

* **ConvoLife** → mostra quanto da janela de contexto já foi usada.
* **Checkpoint** → salva o estado da conversa para reutilizar depois.
* **/todo** → acessa tarefas do Obsidian.
* **/LinkedIn** → transforma vídeo em post.
* Outros comandos personalizados podem ser adicionados.

---

### 🔹 Contexto e Modelos

* Recomenda usar **Sonnet 1M tokens** para contexto estendido (pago).
* Também funciona com Sonnet normal ou Haiku.
* Contexto é mantido por **Session ID**.
* Checkpoint cria um “resumo compactado” para manter memória entre sessões.

---

### 🔹 Voz e Processamento

* Transcrição via **Groq (com Q)**.
* Resposta em áudio via **11 Labs**.
* Detecta comandos por palavras-gatilho no áudio.

---

### 🔹 Gemini Skill

Permite:

* Geração de texto
* Compreensão multimodal
* Outputs estruturados
* Cache de contexto
* Integração com modelos Gemini

---

### 🔹 Instalação e Onboarding

* Clone o repositório.
* Rode `ClaudeClaw`.
* Responda perguntas de setup (voz, vídeo, WhatsApp etc.).
* Funciona melhor no **MacOS** (Windows ainda precisa de testes).
* Pode usar autenticação Claude ou API key.
* Instalação via `npm install`.

---

### 🔹 Filosofia do Projeto

* V1 ainda evoluindo.
* Criado para uso pessoal diário do autor.
* Código aberto para melhorias e sugestões.
* Arquitetura documentada no repositório.

---

### 🔹 Diferencial Principal

Tudo roda localmente, aproveitando suas próprias skills e ferramentas já configuradas, transformando o Telegram em um controle remoto do seu computador com IA multimodal.

---

**INEMA** · 2026-02-25

Apresentando a V1 do ClaudeClaw – Seu Assistente de CLI via Telegram

O ClaudeClaw V1 chegou — e é tudo o que eu queria que um assistente pessoal de IA fosse:
→ roda nativamente no seu computador
→ é totalmente controlado pelo Telegram
→ aproveita todas as suas habilidades já configuradas no Claude Code e apps autenticados

Veja o que ele pode fazer (se você tiver as skills certas):

* Enviar notas de voz e receber respostas em áudio
* Enviar vídeos para análise via Gemini
* Gerenciar sua lista de tarefas no Obsidian
* Gerar posts para o LinkedIn a partir de vídeos
* Verificar o uso da sua janela de contexto
* Até controlar mensagens do WhatsApp pelo Telegram

A skill do Gemini é uma ótima base para cuidar de muitas dessas funções:
https://github.com/google-gemini/gemini-skills/blob/main/skills/gemini-api-dev/SKILL.md

As demais skills podem ser quaisquer GLOBAL skills que você configurar na sua instância do Claude Code.

O multimodal é real:
→ Enviei um vídeo meu gravando e ele entendeu exatamente o que eu estava fazendo
→ Notas de voz são transcritas via Groq, e as respostas voltam em áudio usando 11 Labs
→ Imagens, vídeos e texto — tudo tratado nativamente pela skill do Gemini

Dica profissional: se couber no seu orçamento, rode isso com Sonnet de 1M tokens para ter contexto estendido
→ Caso contrário, o Sonnet regular ou até mesmo o Haiku funcionam bem, já que tudo roda localmente na sua máquina

Comandos integrados incluem:

* ConvoLife (verifica quanto resta da janela de contexto)
* Checkpoint (salva o estado da conversa para a próxima sessão)
* /to-do
* /LinkedIn
* e mais

O repositório tem um fluxo completo de onboarding (passos 1–8), mas tentei deixar o mais simples possível:
→ clone o repositório → rode o ClaudeClaw → responda algumas perguntas de sim/não na configuração → e pronto, já está funcionando

🔗 https://github.com/earlyaidopters/claudeclaw

⚠️ Desenvolvido e testado no MacOS — usuários de Windows, por favor, deem feedback
→ usem a thread deste post para relatar bugs ou solicitar funcionalidades
→ esta é a V1 e estou usando diariamente, então as melhorias virão rapidamente

---

**INEMA** · 2026-02-25

https://chatgpt.com/c/699f6721-8f8c-8333-bd44-808651b1cca8
