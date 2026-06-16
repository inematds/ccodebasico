# Discussão

> Tópico 6 · 22 mensagens úteis de 38 totais

---

**Carlos** · 2026-04-08

Se vc puder pagar e for um usuário intenso no uso, altera para o Mac $100

---

**Rob** · 2026-04-08

boa!!!!
mas com relaçao ao uso de tokens , este $20 usd mes da pra trabalhar bem durante as 24h do dia?
pergunto isso pois achei interessante usar a Open Router por$10 usd , podendo ter ate 1.000 intercessões dia,  mas tambem sei que devem usar os antecessores do opus

---

**Carlos** · 2026-04-08

api fica caro. se vc puder, assine o plano pro, $20, e use o claude code com ele

---

**Rob** · 2026-04-08

O claude code 99%free, é muito bom fiz o procedimento que esta no topico aqui, recomendo e indico , para pesquisas e projetos mais simples, pois tem limite diario de 50 interessoes/dia

---

**Rob** · 2026-04-08

ola, uma duvida aqui, alguem do grupo tem a resposta?
o que ficaria mais barato, usar o claude atraves da OpenRouter atraves de creditos, ou usar API do claude, ou Pagar o plano mensal do Claude de $20 usd,   quem ja testou?   @INEMAtds @INEMAtds  ja fez este teste?

---

**Rob** · 2026-04-07

Ola,  alguém tem alguma dica site site ou repositório que temos skills do claude.
Quero montar uma equipe de marketing,  a ideia é  ter uma skill para cada um dos integrantes 
@INEMAtds @apoioinema ,  podem ajudar?

---

**Jefferson** · 2026-04-01

como estudo claude code, estou perdido aqui, nao sei como organizar as pastas

---

**Reginaldo** · 2026-03-25

@INEMAtds tudo bem, admirado em ver você construir todo esse ambiente aqui para ajudar essa galera desconectada haha... sou da area de TI +25 anos ai batendo cabeça ..... vc tem um contato direto para trocarmos ideia de projetos e ideias para por em pratica tenho alguns projetos e gostaria de mitigar ideias com você que pelos seus conteúdos é um entusiasta como eu de soluções e automações, aqui achei a comunidade muito dispersa não achei nenhum chat ativo para bater um papo com a galera que esta produzindo.... se for do seu interesse trocar ideias me indica ql chat é o melhor aqui na comunidade para debater ideias, ou um discord ou me chama na DM vamos maturar ideias.... Forte abraço e sucesso na comunidade.

---

**INEMA** · 2026-03-19

nao, voce pode usar a api tem um post  claude code ccr - free olha ali

---

**Gustavo** · 2026-03-19

E a melhor maneira de evitar isso seria conectando ele via MCP

---

**Gustavo** · 2026-03-19

Boa noite pessoal vi umas notícias sobre instalar o claude no metade via app na API está bloqueando contas alguém sabe se isso é verdade ?

---

**akagelks** · 2026-02-27

Boa noite, no vídeo de agora a pouco sobre converter web em app, não to achando o grupo de discussão, alguém poderia me ajudar?

---

**INEMA** · 2026-01-15

isso q vc faz é bom, mas o CCode esta muito melhor, tem atulizar ele e usar o opus 4.5

---

**Lu** · 2026-01-09

Ney, uso o CCode dentro do VSCODE, me ajudando a auditar o codigo do nocode.  Mas percebo que ele às vezes fica meio sem noção. Então, incluí o gemini e o chatgpt. E acabo fazendo uma “mesa redonda” pra desbugar algunas coisas. 
Vc sabe de algum caminho que agilize isso? Ouvi sobre um agente que desbuga automaticamente. Vc conhece?

---

**INEMA** · 2026-01-06

## 🧠 O QUE É O PROMPT AVANÇADO DE DEPURAÇÃO PARA CLAUDE

É um **prompt estruturado**, não um pedido simples do tipo “arrume esse bug”.

👉 Ele transforma o Claude em um **engenheiro de software sênior focado em debugging**, guiando a IA passo a passo para:

* Entender o **contexto completo**
* Identificar a **causa raiz** do problema
* Propor **correções seguras**
* Evitar soluções superficiais

---

## 🎯 POR QUE ELE É DIFERENTE DE “DEBUG NORMAL”

❌ Prompt comum:

> “Meu código não funciona, conserte.”

✅ Prompt avançado:

* Define p**apel da IA
*** Fornece o**bjetivo claro
*** Isola s**intomas vs causa
*** Exige r**aciocínio explícito
*** Força va**lidação da solução

**Isso reduz drasticamente:

* Alucinação
* Correções erradas
* Retrabalho

---

## 🧩 COMO ELE USADO

O prompt é usado **implicitamente** quando pede coisas como:

* “Analise o erro”
* “Explique por que isso está acontecendo”
* “Corrija sem quebrar outras partes”
* “Verifique localmente se funciona”

Esses pedidos seguem um **template mental fixo**, que é justamente o prompt avançado.

---

## 🧪 ESTRUTURA DO PROMPT (RESUMIDA)

O prompt avançado de depuração tem 6 blocos:

### 1️⃣ Papel

> “Você é um engenheiro de software sênior especializado em debugging.”

### 2️⃣ Contexto

* Stack usada
* Ferramentas (Anti-Gravity, Supabase, GitHub)
* O que o sistema deveria fazer

### 3️⃣ Problema observado

* O que está quebrado
* Mensagens de erro
* Comportamento inesperado

### 4️⃣ Restrições

* Não quebrar outras partes
* Manter arquitetura
* Não simplificar demais

### 5️⃣ Processo de análise

> “Explique a causa raiz antes de corrigir.”

### 6️⃣ Saída esperada

* Correção clara
* O que foi alterado
* Como validar

---

## 🧠 EXEMPLO DE PROMPT (VERSÃO CURTA)

Voc```ê é um engenheiro de software sênior especializado em depuração.

Contexto:
Este é um dashboard SaaS rodando em Anti-Gravity, conectado ao Supabase.
O objetivo é exibir métricas de uso corretamente.

Problema:
Os dados não atualizam ao trocar o filtro de 30 para 90 dias.

Tarefa:
1. Identifique a causa raiz.
2. Explique por que o erro ocorre.
3. Corrija sem quebrar outras funcionalidades.
4. Explique como validar a correção.

-```--

## 🚀 POR QUE ISSO É UM “HACK”

Porque:

* 90% das pessoas nã**o estruturam prompts
*** Claude responde muito melhor a papé**is + processo
* F**unciona como um deb**ug SOP reutilizável
* **Escala para qualquer linguagem ou stack

👉 É o mesmo princípio do repositório UDPC qu**e vo**cê citou antes.

---

## ✅ CONCLUSÃO

* ✅ O  prompt avançado de depuração (mesmo sem dar esse nome formal)
* 🧠 Ele usa Claude como e**ngenheiro de debugging,** não como chatbot
* 🔥 Esse prompt é um **diferencial técnico real**

---

**INEMA** · 2026-01-06

https://github.com/inematds/udpc

---

**Micael** · 2025-11-12

Nós para usar o Claude no Windows   Temos que ter uma chave de api certo ? Temos que carregar a nossa conta a console Claude ?

---

**INEMA** · 2025-09-18

[https://www.youtube.com/live/mhfrWIhmqps?si=rqipKBe4mqrE41k9](https://www.youtube.com/live/mhfrWIhmqps?si=rqipKBe4mqrE41k9)

---

**INEMA** · 2025-09-18

[https://www.youtube.com/live/oR7vkdgnPus?si=-ESWdw2lrNHW4BqC](https://www.youtube.com/live/oR7vkdgnPus?si=-ESWdw2lrNHW4BqC)

---

**INEMA** · 2025-09-18

https://www.youtube.com/live/2jvitDHRy48?si=eqhiYlHgH3W-g0Fb

---

**Carlos** · 2025-09-17

As lives estão todas abertas no YouTube. Só você ir lá e procurar por INEMA.TDS

---

**Dudu** · 2025-09-17

Por favor Nei, coloca a suas live deste tema aqui pra gente ? Vou ter assistir fora do horário da live
