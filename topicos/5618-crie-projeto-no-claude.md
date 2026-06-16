# Crie Projeto no Claude

> Tópico 5618 · 4 mensagens úteis de 11 totais

---

**INEMA** · 2026-05-06

Next.js 15, app router, TypeScript
- Supabase, autenticação + banco de dados
- Vercel
- Rodar: `pnpm dev`
- Respostas do coach: `app/api/coach/route.ts`

## D · Decisões
- 2026-04-12 — Supabase em vez de Firebase. RLS permite evitar um backend.
- 2026-04-22 — feed social removido do lançamento. Retenção > viralidade para hábitos.
- 2026-04-29 — coach trocado de GPT-4 para Sonnet 4.6. As respostas soam menos genéricas.

## E · Mapa de Memória
- project-brief.md — briefing de lançamento de março, congelado
- current-strategy.md — foco de maio: retenção D7, não cadastro
- decisions.md — raciocínio completo por trás de cada decisão da seção D
- next-actions.md — widget para Apple Watch, resumo semanal, indicação
- session-summaries.md — últimos 10 resumos
- bugs-and-risks.md — oscilação de autenticação no iOS 18.2, atenção ao limite de taxa do Supabase

## F · Referências
- Repositório: github.com/inematds/imkt4
- Notion: Playbook da Semana de Lançamento do IMKT4
- Slack: #imkt4-build
- Produção: imkt4.app
```
---

## Três regras

**Mantenha abaixo de 200 linhas.** Depois disso, o Claude começa a passar os olhos por cima. Se uma seção crescer, mova os detalhes para `memory/` e crie um link para ela.

**Atualize a data.** Um briefing desatualizado é pior do que nenhum briefing. Mexeu no arquivo → atualize a data.

**Um por pasta, não por repositório.** Monorepos recebem vários — um em cada subpasta significativa. O Claude lê o mais próximo do arquivo que você está editando.

---

## Como usar

1. Copie o modelo
2. Cole em um novo `CLAUDE.md` na raiz do seu projeto
3. Preencha as seções — escreva `TBD` para qualquer coisa que você ainda não saiba
4. Crie a pasta `memory/` ao lado dele
5. Abra o Claude Code, OpenClaw ou cole no ChatGPT — ele lê o briefing antes de responder
```
```
```

---

**INEMA** · 2026-05-06

Exemplo:

```# Manual Operacional do Projeto

> Um `CLAUDE.md` de copiar e colar para colocar na raiz de qualquer pasta de projeto. Ele informa ao Claude Code, OpenClaw, ChatGPT — qualquer ferramenta — o que é aquela pasta, o que há nela e onde procurar informações. Um por pasta. Pode adaptar livremente.

---

## Por que um por pasta

Quando uma IA abre uma pasta, ela lê o `CLAUDE.md` na raiz antes de tocar no seu código. Sem ele, você precisa reexplicar o projeto em cada sessão. Com ele, o modelo já entra informado: sabe o propósito da pasta, sua estrutura e onde fica a memória de longo prazo.

Esta é a camada intermediária do sistema de memória em 3 níveis. Sua identidade global — quem você é, como escreve, voz e tom — fica um nível acima, em `~/.claude/CLAUDE.md`. Este arquivo é apenas sobre esta pasta.
```

~/projects/seu-projeto/
CLAUDE.md          ← este arquivo
memory/
decisions.md
current-strategy.md
next-actions.md
session-summaries.md
src/

```
---

## As 6 coisas que todo `CLAUDE.md` de pasta precisa

|  | Seção | O que responde |
| --- | --- | --- |
| **A** | O que é esta pasta | A função da pasta, em um parágrafo |
| **B** | O Objetivo | Por que ela existe. Como fica quando estiver concluída |
| **C** | Stack | Com o que foi construída |
| **D** | Decisões | Decisões já tomadas — para não discutir tudo de novo |
| **E** | Mapa de Memória | O que existe em cada arquivo dentro de `memory/` |
| **F** | Referências | Onde mais este projeto existe |

> [!callout] G · Opcional — *substituições específicas do projeto*

> Se esta pasta precisa de regras que substituem sua identidade global — por exemplo, este repositório usa Python, embora você normalmente escreva em TypeScript — adicione uma seção G curta. Caso contrário, pule. **Voz e tom pertencem ao seu `~/.claude/CLAUDE.md` global, não aqui.**

---

## O Modelo

```markdown
# {{Nome do Projeto}} — CLAUDE.md
*Última atualização: {{AAAA-MM-DD}} · Responsável: {{seu nome}}*

---

## A · O que é esta pasta
{{Um parágrafo. O que existe aqui, quem trabalha nela, em que estado está.
Estágio: ideia / sandbox / lançado / pausado / encerrado.}}

## B · O Objetivo
- **Por que existe:** {{o problema que resolve}}
- **Concluído significa:** {{o estado de sucesso, em português claro}}
- **Fora do escopo:** {{coisas que deliberadamente não serão construídas}}

## C · Stack
- **Linguagens:** {{}}
- **Frameworks:** {{}}
- **Hospedagem / infraestrutura:** {{}}
- **Serviços principais:** {{}}
- **Rodar localmente:** `{{o comando principal}}`
- **Arquivos importantes:** `{{caminho/para/arquivo.importante}}`

## D · Decisões
*Uma linha cada. Data · o que · por quê.*
- `{{AAAA-MM-DD}}` — {{decisão}} porque {{motivo}}
- `{{AAAA-MM-DD}}` — ...

## E · Mapa de Memória
O que existe dentro de `/memory`:
- `project-brief.md` — briefing original, congelado
- `current-strategy.md` — estado atual, editado semanalmente
- `decisions.md` — explicação longa por trás de cada entrada da seção D
- `next-actions.md` — lista de próximas ações
- `session-summaries.md` — resumos de sessões, com datas
- `bugs-and-risks.md` — problemas abertos e pontos de atenção

## F · Referências
- **Repositório:** {{}}
- **Notion:** {{}}
- **Linear / Jira:** {{}}
- **URL de produção:** {{}}
- **Dashboards:** {{}}

## G · Substituições específicas do projeto *(opcional — pule se o global já cobre isso)*
- {{ex.: este repositório usa Python 3.12, não TypeScript}}
- {{ex.: esta pasta é enviada para um ambiente regulado; trate segredos com cuidado}}```

---

## Exemplo preenchido

```markdown
# Glaido — CLAUDE.md
*Atualizado: 2026-05-01*

## A · O que é esta pasta
Aplicação web da IMKT4. Next.js + Supabase. Atualmente em modo de crescimento após o esforço de lançamento em março. O app iOS fica em uma pasta irmã; esta é apenas para web.

## B · O Objetivo
- Por quê: a maioria dos apps de hábitos não entrega nada personalizado. A IMKT4 entrega.
- Concluído: usuários ativos semanalmente atingindo suas próprias metas de sequência sem insistência
- Fora do escopo: feed social, ranking de amigos

## C · Stack
-

---

**INEMA** · 2026-05-06

**Manual de operação do projeto** em formato `CLAUDE.md`.

Na prática, é um arquivo que você coloca na raiz de uma pasta/projeto para orientar uma IA — como Claude Code, OpenClaw ou ChatGPT — sobre **o que é aquele projeto, como ele funciona, onde estão as informações importantes e quais decisões já foram tomadas**. 

Ele serve para evitar que você precise explicar tudo de novo a cada sessão. Quando a IA abre a pasta, ela lê esse arquivo primeiro e já entende:

* qual é o objetivo do projeto;
* qual stack/tecnologia ele usa;
* quais arquivos são importantes;
* quais decisões já foram tomadas;
* onde ficam as memórias do projeto;
* links úteis como repo, Notion, Jira, dashboards etc.

A ideia central é tratar esse arquivo como uma **memória intermediária do projeto**: não é sobre sua identidade pessoal ou estilo global, mas sim sobre **aquela pasta específica**.

Exemplo simples:

```# Meu Projeto — CLAUDE.md

## O que é
Aplicação web para gerenciar reservas.

## Objetivo
Permitir que usuários criem, editem e acompanhem reservas.

## Stack
Next.js, TypeScript, Supabase e Vercel.

## Decisões
- Usar Supabase para autenticação.
- Não criar app mobile nesta fase.

## Memória
- current-strategy.md: estratégia atual
- next-actions.md: próximas tarefas```

Resumindo: é um **briefing fixo para IA trabalhar melhor dentro de um projeto**, com contexto suficiente para ela não se perder nem repetir perguntas básicas.

---

**INEMA** · 2026-05-06

Crie Projeto no Claude
