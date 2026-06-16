# Memoria Permanente

> Tópico 4867 · 2 mensagens úteis de 9 totais

---

**INEMA** · 2026-04-09

🧠 Dando memória permanente ao Claude Code

Um dos maiores problemas dos agentes de IA no desenvolvimento é simples:
eles esquecem tudo entre as sessões.

Você fecha o Claude Code, volta no dia seguinte…
e precisa explicar novamente arquitetura, decisões e contexto do projeto.

O projeto Claude-Mem resolve exatamente isso.

Ele é um plugin open-source que adiciona memória persistente de longo prazo ao Claude Code (com suporte também ao Gemini CLI e gateways como OpenClaw).


🚀 O que o Claude-Mem faz

O plugin captura automaticamente o que acontece durante as sessões:

• prompts do usuário
• comandos executados
• alterações de arquivos
• uso de ferramentas
• decisões arquiteturais

Essas informações são então comprimidas semanticamente usando IA e armazenadas para uso futuro.

Na próxima sessão, o sistema injeta apenas o contexto relevante de volta no agente.

Resultado: o Claude continua exatamente de onde parou.


⚙️ Como a arquitetura funciona

O sistema possui alguns componentes interessantes:

🔄 Hooks automáticos

Observam eventos importantes da sessão:

• início
• envio de prompts
• uso de ferramentas
• parada
• encerramento

🧠 Compressão com IA

As interações são resumidas usando o Claude Agent SDK, reduzindo drasticamente o consumo de tokens.

🗄️ Armazenamento híbrido

• SQLite (FTS5) → busca textual rápida
• Chroma Vector DB → busca semântica

📊 Recuperação progressiva de contexto

O sistema busca memória em três níveis:

1️⃣ resumo leve
2️⃣ contexto cronológico
3️⃣ detalhes completos apenas quando necessário

Isso pode reduzir o consumo de tokens em até 10x.


🌐 Interface e ferramentas

O Claude-Mem também cria um servidor local com:

• painel web em tempo real
• histórico de observações
• API local para consultas de memória
• suporte a citações por ID


📊 Adoção do projeto

O projeto já ultrapassou:

⭐ 45k estrelas no GitHub
🍴 3k+ forks

E continua recebendo atualizações frequentes.


💡 Minha leitura

Estamos entrando em uma nova fase no uso de agentes de IA.

Não basta apenas ter modelos poderosos —
é preciso dar a eles memória e continuidade de contexto.

Projetos como o Claude-Mem são um passo importante para transformar agentes em verdadeiros colaboradores de longo prazo no desenvolvimento.

---

**INEMA** · 2026-04-09

https://github.com/thedotmack/claude-mem
