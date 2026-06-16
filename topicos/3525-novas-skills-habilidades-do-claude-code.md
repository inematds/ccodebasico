# Novas Skills - Habilidades do Claude Code

> Tópico 3525 · 11 mensagens úteis de 27 totais

---

**INEMA** · 2026-03-05

https://youtu.be/BSjXJAYWXPw

---

**INEMA** · 2026-03-05

https://github.com/anthropics/skills/tree/main/skills/skill-creator

---

**INEMA** · 2026-03-05

https://github.com/anthropics/skills/tree/main/skills

---

**INEMA** · 2026-03-05

https://github.com/anthropics/skills

---

**INEMA** · 2026-03-05

A Anthropic descreve exatamente isso: escrever evals, rodar benchmarks e guardar resultados localmente/CI.

## Como eu rodo na prática (Claude Code)

### 1) Instale o Skill Creator (plugin)

* Instale o plugin **Skill Creator** no Claude Code. Ele é “Anthropic Verified” e funciona por **modos**: Create, Eval, Improve, Benchmark. 

### 2) Rode o Skill Creator via comando

No Claude Code, você usa:

* **`****/skill****-creator`** e escolhe o modo (Eval / Benchmark / Improve). 

> Dica: qualquer skill pode ser chamada manualmente com **`****/nome****-da-skill`**. 

---

## Validar uma skill (fluxo recomendado)

### A) Rodar **Evals** (validação funcional)

1. Digite: **`****/skill****-creator`**
2. Escolha **Eval**
3. Peça algo do tipo: **“Run evals on my <nome-da-skill>”** (o plugin sugere esse exemplo) 
4. O fluxo te guia para:

   * definir **prompts de teste** (e arquivos, se precisar)
   * dizer **“o que é bom”** (critérios)
   * rodar e ver se passa/falha 

O plugin faz isso com agentes internos (Executor/Grader/Comparator/Analyzer) para executar e julgar os resultados. 

### B) Rodar **Benchmark** (validação com números)

Depois que os evals existem, faça:

1. **`****/skill****-creator` → Benchmark**
2. Peça: **“Benchmark my skill across 10 runs and show variance.”** 

O benchmark mede:

* **pass rate**
* **tempo**
* **tokens** 

---

## “O creator skill fica ativo e ele avalia?”

* **Ele não fica avaliando “em background” automaticamente.** Você **chama** o Skill Creator quando quer avaliar/otimizar. 
* O que dá pra fazer é: depois de criar seus evals, você pode **guardar os evals/resultados localmente, integrar num dashboard ou plugar em CI** (a própria notícia sugere isso).

---

## Quando vale a pena rodar?

* **Sempre que você editar a skill** → rode evals + benchmark.
* **Quando sair modelo novo** (ou atualizar infra) → rode benchmark para pegar regressões. 
* Se for “capability uplift”, rode evals **sem a skill** também: se o modelo base passar, talvez a skill ficou redundante.

---

**INEMA** · 2026-03-05

## O que a Anthropic melhorou no **skill-creator**

A ideia central é: **skills agora podem ser tratadas como software**, com **testes, métricas e iteração**, sem você precisar programar. A própria Anthropic diz que isso ajuda autores a **verificar que a skill funciona**, **pegar regressões** e **melhorar descrições** para disparar melhor. ([Claude][1])

---

## 1) Dois tipos de skills (e por que isso importa)

A Anthropic separa skills em duas categorias: ([Claude][1])

### A) **Capability uplift**

É quando a skill “ensina técnica” para o Claude fazer algo **melhor do que só no prompt** (ex.: skills de criação de documentos). ([Claude][1])
**Risco:** com modelos novos, isso pode virar desnecessário (o modelo “aprende sozinho”).

### B) **Encoded preference**

É quando o Claude já sabe fazer as partes, mas a skill **organiza o workflow no jeito do seu time** (sequência, critérios, formato, fontes de dados). ([Claude][1])
**Risco:** não é “obsoleta” tão fácil, mas pode parar de refletir seu processo real.

➡️ Por isso os testes (evals) são úteis para **motivos diferentes** em cada tipo: ver quando o modelo “ultrapassou” a uplift, ou checar fidelidade do workflow na encoded preference. ([Claude][1])

---

## 2) “Evals”: testes para saber se a skill funciona mesmo

O **skill-creator agora ajuda você a escrever evals**, que são testes do tipo: ([Claude][1])

* **defina prompts de teste** (e arquivos, se precisar)
* **descreva o que é um resultado bom**
* rode e veja se a skill passa/falha

### Dois usos principais dos evals

* **Pegar regressões:** algo que funcionava mês passado pode mudar com modelo/infra e começar a falhar — eval te dá sinal cedo. ([Claude][1])
* **Saber quando a skill ficou desnecessária:** se o **modelo base** começa a passar nos testes **sem** a skill, a skill não está quebrada — só ficou redundante. ([Claude][1])

### Exemplo do post: **PDF skill**

Eles citam que a skill de PDF tinha dificuldade em formulários “não preenchíveis” (sem campos), porque precisava colocar texto em coordenadas. Com evals, isolaram a falha e corrigiram ancorando posição em coordenadas extraídas do texto. ([Claude][1])

---

## 3) “Benchmark mode”: medir com números (não só “parece melhor”)

Além de testar, agora dá para rodar **benchmark padronizado** usando seus evals, e medir: 

* **pass rate** (quantos testes passaram)
* **tempo total**
* **tokens**

Isso é ótimo quando:

* saiu um **modelo novo**
* você editou a skill e quer provar que melhorou

---

## 4) Multi-agent evals: mais rápido e mais “limpo”

Rodar eval um por um pode:

* ser lento
* “vazar contexto” (um teste influenciar o outro)

Agora o skill-creator pode **rodar evals em paralelo**, cada um com contexto limpo, com métricas de tokens e tempo por agente.

E tem **comparators** para A/B:

* versão A vs versão B
* com skill vs sem skill
  Eles julgam sem saber qual é qual, para evitar viés. 

---

## 5) Trigger tuning: fazer a skill disparar na hora certa

Mesmo uma skill perfeita é inútil se não dispara.

O post diz que, conforme você tem muitas skills, a descrição precisa ser calibrada:

* **muito ampla** → dispara errado (false triggers)
* **muito estreita** → nunca dispara (false negatives)

O skill-creator agora analisa a descrição com prompts de exemplo e sugere ajustes para reduzir ambos. Eles testaram em skills públicas de criação de documentos e viram melhoria em 5 de 6. 

---

## 6) “O futuro”: skill vs especificação pode virar a mesma coisa

A Anthropic sugere que hoje um `SKILL.md` é quase um “plano de implementação” com passos detalhados.
No futuro, **uma descrição em linguagem natural** pode ser suficiente e o modelo “descobre como fazer”. E eles dizem que o framework de evals é um passo nessa direção.

---

**INEMA** · 2026-03-05

A **notícia oficial** no blog da Anthropic/Claude, publicada em **3 de março de 2026**. 

### Resumo da notícia (o que mudou no Skill Creator)

* O **skill-creator** agora ajuda autores a **escrever evals**, **rodar benchmarks** e **manter skills funcionando** conforme os modelos evoluem. As atualizações já estão disponíveis no **Claude.ai** e **Cowork**, e também como **plugin para Claude Code** e no **repo oficial**. 

* A Anthropic percebeu que a maioria dos autores de skills são **especialistas no assunto (SMEs)**, não engenheiros, e por isso faltavam ferramentas para saber se a skill **ainda funciona**, **se dispara na hora certa**, e **se melhorou após uma edição**. 

* A notícia reforça os **dois tipos de skills**:

  * **Capability uplift** (melhora uma capacidade do modelo; pode ficar desnecessária conforme o modelo melhora)

  * **Encoded preference** (documenta um workflow/processo do time; tende a ser mais durável)

* **Evals**: agora o skill-creator ajuda a criar testes (prompts + critérios do que é “bom”) para verificar se a skill está correta. O post cita o caso da **PDF skill**, que melhorou ao “ancorar” posicionamento em coordenadas extraídas de texto.

* **Benchmarks**: modo que roda uma avaliação padronizada e mede **taxa de sucesso (pass rate)**, **tempo decorrido** e **tokens** — útil após updates do modelo ou iterações da skill. 

* **Multi-agent evals**: para acelerar e evitar “contaminação” de contexto, o skill-creator roda evals **em paralelo** com agentes independentes; e adiciona agentes “comparadores” para **A/B** (ex.: versão A vs versão B, ou com skill vs sem skill).

* **Trigger tuning**: como disparar a skill na hora certa depende muito da descrição, o skill-creator agora ajuda a ajustar descrições para reduzir **falsos positivos** e **falsos negativos** (disparar errado vs não disparar). 

* **Visão de futuro**: a Anthropic sugere que a linha entre “skill” e “especificação” pode se misturar; no futuro, uma descrição em linguagem natural pode bastar, e os **evals** seriam um passo nessa direção.

---

**INEMA** · 2026-03-05

https://claude.com/blog/improving-skill-creator-test-measure-and-refine-agent-skills

---

**INEMA** · 2026-03-05

**As habilidades do Claude Code ficaram ainda melhores**

O Claude Code acabou de lançar uma grande atualização na forma como as habilidades (skills) funcionam. O novo **Skill Creator** ajuda você a criar habilidades melhores do zero, executar **avaliações (evals)** para testar o desempenho delas, **otimizar habilidades existentes** para maior precisão e **acioná-las de forma mais confiável**.

 Olha  **tudo o que mudou** e  uma **a criação completa de uma nova habilidade **, para que você possa ver exatamente como funciona.

Se você está **começando agora no Claude Code** ou **já vem criando habilidades**, essa atualização torna **todo o fluxo de trabalho muito melhor**. 🚀

---

**INEMA** · 2026-03-05

Novas Skills - Habilidades do Claude Code

---

**INEMA** · 2026-03-05

https://chatgpt.com/c/69a9e40d-eb9c-832f-91a3-b34876c364c4
