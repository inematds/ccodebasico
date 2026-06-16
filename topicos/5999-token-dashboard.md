# Token-Dashboard

> Tópico 5999 · 6 mensagens úteis de 17 totais

---

**INEMA** · 2026-05-22

use os recurso de skill para salvar e limpar a sessao  o /session-handoff

---

**INEMA** · 2026-05-22

**Para que isto serve**
Ver quais dos seus prompts são caros (surpresa: geralmente envolvem resultados grandes de ferramentas).
Comparar uso de tokens entre projetos em que você trabalhou.
Identificar padrões desperdiçadores — o mesmo arquivo lido vinte vezes em uma sessão, uma chamada de ferramenta retornando 80k tokens.
Entender o que um "cache hit" realmente economiza.
Se você está no Pro ou Max, confirmar que está tendo retorno do dinheiro em dólares equivalentes à API.

---

**INEMA** · 2026-05-22

**Token Dashboard**
Um dashboard local que lê as transcrições JSONL que o Claude Code grava em `~/.claude/projects/` e as transforma em análise de custo por prompt, mapas de calor de ferramentas/arquivos, atribuição de subagentes, análise de cache, comparação entre projetos e um motor de dicas baseado em regras.**

Tudo roda localment**e. Nenhum dado sai da sua máquina — sem telemetria, sem chamadas de API com seus dados, sem login.

---

**INEMA** · 2026-05-22

ajuste os limites de acesso para seguranca, deixei todo aberto para facilitar os testes

---

**INEMA** · 2026-05-22

`git clone https://github.com/nateherkai/token-dashboard.git
cd token-dashboard
python3 cli.py dashboard`

---

**INEMA** · 2026-05-22

https://github.com/inematds/token-dashboard
