# Exemplo de Um Projeto do Zero - Leilao Cavalos

> Tópico 498 · 7 mensagens úteis de 20 totais

---

**INEMA** · 2025-08-29

3

com esse passo a passo, você já tem um sistema prático onde qualquer pessoa pode perguntar em português e receber análises sobre o leilão de cavalos.
a força do projeto está em **definir perguntas claras, organizar dados simples e ensinar a ia com exemplos**.

---

**INEMA** · 2025-08-29

**capítulo 3** em detalhes, com o passo a passo prático completo.

---

# capítulo 3 — passo a passo com o exemplo do leilão de cavalos

este é o guia prático: aqui você vai ver como transformar as definições (capítulo 2) em um projeto funcional dentro do **claude code**.

---

## 3.1 definir as perguntas no claude

abra o claude code e escreva para ele quais perguntas você quer que funcionem.
isso ajuda a ia a ter clareza desde o início.

exemplo de perguntas iniciais:

* mostre todos os filhos do cavalo storm cat.
* quais cavalos venceram corridas aos 2 anos?
* quais cavalos vendidos por mais de 500 mil tiveram ganhos abaixo de 100 mil?
* quais descendentes de galileo correram em pista de grama?

---

## 3.2 preparar os dados em csv

crie três arquivos simples:

**horses.csv**

```id,name,sire,dam,starts,wins,earnings,best_race,surface,age_first_win
1,Young Star,Galileo,Blue Moon,8,2,154000,Allowance,Turf,2
2,Desert Wind,Frankel,Sahara Sun,5,1,62000,Maiden,Dirt,3
3,Lightning Bolt,Into Mischief,Storm Girl,7,3,410000,Graded Stakes,Dirt,2```

**auctions.csv**

```id,horse_id,price,date
1,1,550000,2022-05-10
2,2,520000,2022-05-10
3,3,600000,2022-05-11```

**lineage.csv**

```horse_id,ancestor_id
1,10
2,11
3,12```

---

## 3.3 criar o banco no supabase

no editor sql, cole o esquema:

```create table horses (
  id serial primary key,
  name text,
  sire text,
  dam text,
  starts int,
  wins int,
  earnings numeric,
  best_race text,
  surface text,
  age_first_win int
);

create table auctions (
  id serial primary key,
  horse_id int references horses(id),
  price numeric,
  date date
);

create table lineage (
  horse_id int references horses(id),
  ancestor_id int references horses(id)
);```

importe os csvs no painel do supabase.

---

## 3.4 conectar o claude ao banco (mcp postgres)

crie o arquivo `mcp.config.json`:

```{
  "servers": {
    "postgres": {
      "type": "postgres",
      "host": "db.xxxxx.supabase.co",
      "port": 5432,
      "database": "postgres",
      "user": "postgres",
      "password": "sua_senha",
      "ssl": true
    }
  }
}```

guarde suas credenciais em `.env` e não compartilhe publicamente.

---

## 3.5 ensinar o claude com claude.md

esse é o arquivo mais importante.
nele, você dá as **regras e exemplos** que a ia vai seguir.

exemplo:

```# projeto leilão de cavalos 🐎

você está conectado a um banco postgres com dados de cavalos, leilões e pedigree.  
sua função é transformar perguntas em sql e responder em português claro.  

regras:  
- "bom cavalo" = pedigree consistente ou vitórias aos 2 anos ou ganhos acima da média.  
- "mau negócio" = preço alto em leilão e ganhos baixos.  
- sempre use as tabelas horses, auctions e lineage.  

exemplos:  
usuário: mostre todos os filhos do cavalo storm cat  
sql:
select h.name
from horses h
join lineage l on h.id = l.horse_id
join horses p on p.id = l.ancestor_id
where p.name = 'Storm Cat';

usuário: quais cavalos venceram corridas aos 2 anos?  
sql:
select name, wins, best_race
from horses
where age_first_win = 2;```

---

## 3.6 conversar e testar

abra o claude code e pergunte:

* “quais cavalos foram maus negócios?”

esperado (sql que o claude deve gerar):

```select h.name, a.price, h.earnings
from horses h
join auctions a on a.horse_id = h.id
where a.price > 500000 and h.earnings < 100000;```

pergunta:

* “quais descendentes de galileo venceram aos 2 anos?”

esperado:

```select h.name, h.wins, h.best_race
from horses h
join lineage l on h.id = l.horse_id
join horses p on p.id = l.ancestor_id
where p.name = 'Galileo' and h.age_first_win = 2;```

---

## 3.7 corrigir e refinar

se as respostas não estiverem certas:

* ajuste o schema (nomes de campos),
* adicione mais exemplos no `claude.md`,
* ensine regras novas de negócio.

---

## 3.8 evoluir o projeto

quando o básico funcionar:

* crie scripts para atualizar os dados automaticamente,
* adicione filtros mais complexos no claude.md,
* crie um painel web para clientes acessarem sem precisar abrir o claude code.

---

## conclusão do capítulo

---

**INEMA** · 2025-08-29

**capítulo 2** com mais clareza e exemplos práticos.

---

# capítulo 2 — o que levantar antes do projeto

antes de abrir o claude code e sair testando, é essencial **levantar algumas informações**.
isso garante que a ia entenda o seu contexto e saiba responder as perguntas corretamente.

---

## 2.1 definir as perguntas-alvo

primeiro, escreva de forma simples as perguntas que você quer que o sistema responda.
isso serve como **bússola do projeto**.

exemplo (leilão de cavalos):

* quais cavalos venceram corridas aos 2 anos?
* quais descendentes de storm cat foram vendidos em leilão?
* quais cavalos vendidos por mais de 500 mil tiveram ganhos abaixo de 100 mil?
* quais cavalos correram mais de 10 vezes e tiveram poucas vitórias?

se você não souber as perguntas certas, o projeto fica sem foco.

---

## 2.2 listar os dados disponíveis

anote quais dados você já possui e em qual formato eles estão (planilha, csv, pdf, site).
pense em colunas/tabelas.

exemplo (cavalos):

* horses: nome, pai, mãe, corridas, vitórias, ganhos, pista, idade da 1ª vitória.
* auctions: cavalo\_id, preço, data.
* lineage: cavalo\_id, ancestral\_id.

se os dados não existirem ainda, você precisará extraí-los (ex.: baixar pdfs do site do leilão).

---

## 2.3 traduzir regras do domínio

muitas vezes usamos termos abertos que a ia não entende.
por isso, defina **critérios claros** que o claude pode seguir.

exemplo:

* “bom cavalo” = vitórias aos 2 anos OU ganhos acima da média do lote.
* “mau negócio” = preço de venda alto E ganhos baixos.
* “precocidade” = vitória registrada até os 2 anos.

essas regras irão para o `claude.md`.

---

## 2.4 planejar a atualização dos dados

decida como vai manter os dados atualizados.
se não houver atualização, as respostas ficam defasadas.

formas possíveis:

* **manual**: importar csv atualizado uma vez por semana.
* **semi-automática**: rodar um script que baixa novos pdfs e atualiza o banco.
* **automática**: agendar no servidor uma coleta diária.

exemplo: no leilão de cavalos, toda vez que sair um novo catálogo, rodar o parser e atualizar o banco.

---

## 2.5 definir critérios de sucesso

como saber se o projeto está funcionando?
crie um checklist simples com métricas de acerto.

exemplo:

* o sistema deve responder corretamente 80% das perguntas-alvo.
* cada resposta deve vir acompanhada do sql gerado (para auditoria).
* tempo de resposta máximo: 5 segundos.

se os critérios forem cumpridos, o projeto está pronto para uso real.

---

## 2.6 resumo do capítulo

antes de abrir o claude, você precisa ter em mãos:

1. perguntas-alvo claras,
2. lista de dados disponíveis,
3. regras do domínio traduzidas em lógica,
4. plano de atualização,
5. critérios de sucesso.

com esses 5 pontos definidos, o próximo passo é abrir o claude code e seguir o **passo a passo prático** (capítulo 3).

---

**INEMA** · 2025-08-29

**capítulo 1** para deixá-lo mais educativo e com mais exemplos práticos.

---

# capítulo 1 — a ideia

## 1.1 o que é o claude code

o **claude code** é um ambiente de desenvolvimento onde você conversa com a ia como se fosse um colega de equipe. ele entende linguagem natural e consegue:

* escrever código,
* conectar em bancos de dados,
* rodar consultas,
* e explicar os resultados.

a grande diferença é que você não precisa ser programador para usar. basta estruturar bem seus dados e ensinar a ia quais perguntas devem ser respondidas.

---

## 1.2 o papel do mcp (model context protocol)

o **mcp** é o “cabo de energia” que conecta o claude ao mundo externo.

* sem mcp, o claude só conversa em texto.
* com mcp, ele pode **usar ferramentas reais**, como um banco de dados ou uma api.

no nosso caso, usamos o **mcp postgres**:

* isso permite ao claude escrever sql, rodar consultas no banco e trazer resultados em tempo real.

---

## 1.3 as partes principais do projeto

1. **dados estruturados (csv/sql)**

   * os dados precisam estar minimamente organizados (em tabelas).
   * exemplo: cavalos, leilões, linhagens.

2. **supabase/postgres**

   * onde os dados ficam guardados.
   * o claude acessa esse banco via mcp.

3. **mcp.config.json**

   * arquivo que aponta para o banco.
   * contém host, usuário, senha e ssl.

4. **claude.md**

   * manual de instruções para a ia.
   * define regras, exemplos de consultas e termos do domínio.

5. **conversa com o claude**

   * é aqui que a mágica acontece: você faz perguntas, ele gera sql, roda no banco e devolve a resposta.

---

## 1.4 o que você pode construir com isso

o claude code pode ser usado para qualquer projeto em que você tenha dados estruturados. alguns exemplos:

* **negócios**: consultar vendas, clientes e faturamento.
* **educação**: responder perguntas sobre desempenho de alunos.
* **esportes**: analisar estatísticas de jogadores e partidas.
* **pesquisa**: explorar dados científicos organizados em tabelas.

no nosso caso, aplicamos no **leilão de cavalos**:

* os dados de pedigree e leilões ficam em tabelas.
* o claude gera consultas automaticamente.
* você pode descobrir “bons cavalos” ou “maus negócios” em segundos.

---

## 1.5 exemplo rápido (sem detalhes técnicos)

pergunta do usuário:
“quais cavalos vendidos acima de 500 mil tiveram ganhos abaixo de 100 mil?”

o claude faz:

```select h.name, a.price, h.earnings
from horses h
join auctions a on h.id = a.horse_id
where a.price > 500000 and h.earnings < 100000;```

resposta do claude:

* lightning bolt — preço: 600.000 / ganhos: 54.000
* desert wind — preço: 520.000 / ganhos: 80.000

---

## 1.6 conclusão do capítulo

o claude code funciona como um **tradutor inteligente** entre você e os seus dados.

* você fala em português,
* ele traduz para sql,
* consulta o banco,
* e responde de volta de forma clara.

com essa base, qualquer pessoa pode criar um projeto útil sem programar.

---

**INEMA** · 2025-08-29

refinar

se a query não funcionar:

* revise o schema,
* adicione exemplos no claude.md,
* corrija os nomes dos campos.

### 8. evoluir o projeto

* automatize a atualização dos dados,
* crie um painel para clientes,
* pense em monetização (assinatura).

---

## conclusão

com esses 3 capítulos, qualquer pessoa consegue usar o claude code para:

1. entender a ideia,
2. definir o que precisa antes,
3. seguir o passo a passo com dados reais.

no exemplo do leilão de cavalos, perguntas complexas sobre pedigree e desempenho se transformam em respostas rápidas e úteis, sem precisar programar.

---

**INEMA** · 2025-08-29

# manual de uso do claude code com mcp postgres

## capítulo 1 — a ideia

o claude code permite criar projetos que respondem perguntas em **linguagem natural** usando dados estruturados. você não precisa programar: o claude gera o sql, conecta ao banco e explica os resultados.

partes principais do claude code:

* **mcp (model context protocol):** conexão entre o claude e ferramentas externas (ex.: postgres).
* **mcp postgres:** servidor que permite ao claude escrever e executar sql direto no banco.
* **claude.md****:** arquivo onde você ensina as regras do seu projeto (como interpretar termos e exemplos de consultas).
* **mcp.config.json:** arquivo de configuração que aponta para o seu banco supabase/postgres.

com essa base, qualquer pessoa pode transformar dados em conhecimento útil.

exemplo de uso:
no **leilão de cavalos**, você pode perguntar:

* “quais cavalos ganharam corridas aos 2 anos?”
* “quais descendentes de galileo tiveram vitórias precoces?”
* “quais cavalos vendidos por mais de 500 mil tiveram ganhos abaixo de 100 mil?”

---

## capítulo 2 — o que levantar antes do projeto

antes de começar no claude code, você deve definir:

1. **perguntas-alvo**
   escreva 5 a 10 perguntas que o sistema precisa responder.
   exemplo: listar filhos de um cavalo, encontrar maus negócios, vitórias aos 2 anos.

2. **dados disponíveis**
   quais colunas e formatos você tem (csv/sql).
   exemplo: horses.csv, auctions.csv, lineage.csv.

3. **regras do domínio**
   traduza conceitos abertos em critérios lógicos.
   exemplo: “bom cavalo” = vitórias precoces ou ganhos acima da média.

4. **atualização**
   como os dados serão carregados e mantidos.
   exemplo: baixar pdfs do site do leilão 1x por semana.

5. **critérios de sucesso**
   como validar se está funcionando.
   exemplo: responder corretamente 80% das perguntas-alvo.

---

## capítulo 3 — passo a passo com o exemplo do leilão de cavalos

### 1. definir as perguntas

exemplo:

* listar filhos de um cavalo específico.
* mostrar cavalos com vitórias aos 2 anos.
* identificar maus negócios (preço alto, ganhos baixos).

### 2. preparar os dados

três tabelas mínimas:

* **horses**: id, nome, pai, mãe, corridas, vitórias, ganhos, pista, idade\_da\_primeira\_vitória.
* **auctions**: id, cavalo\_id, preço, data.
* **lineage**: cavalo\_id, ancestral\_id.

salve como `horses.csv`, `auctions.csv`, `lineage.csv`.

### 3. criar o banco no supabase

rode no editor sql:

```create table horses (
  id serial primary key,
  name text,
  sire text,
  dam text,
  starts int,
  wins int,
  earnings numeric,
  best_race text,
  surface text,
  age_first_win int
);

create table auctions (
  id serial primary key,
  horse_id int references horses(id),
  price numeric,
  date date
);

create table lineage (
  horse_id int references horses(id),
  ancestor_id int references horses(id)
);```

importe os csvs no painel.

### 4. conectar o claude (mcp postgres)

crie `mcp.config.json`:

```{
  "servers": {
    "postgres": {
      "type": "postgres",
      "host": "db.xxxxx.supabase.co",
      "port": 5432,
      "database": "postgres",
      "user": "postgres",
      "password": "sua_senha",
      "ssl": true
    }
  }
}```

### 5. ensinar o claude (`claude.md`)

```# projeto leilão de cavalos 🐎

você está conectado a um banco postgres com dados de cavalos, leilões e pedigree.  
sua função é transformar perguntas em sql e responder com clareza.

regras:  
- "bom cavalo" = pedigree consistente ou vitórias precoces ou ganhos acima da média.  
- "mau negócio" = preço alto em leilão e ganhos baixos.  
- sempre use as tabelas horses, auctions e lineage.  

exemplo:  
usuário: mostre todos os filhos do cavalo storm cat  
sql:
select h.name
from horses h
join lineage l on h.id = l.horse_id
join horses p on p.id = l.ancestor_id
where p.name = 'Storm Cat';```

### 6. conversar e testar

abra o claude e pergunte:

* “quais cavalos foram maus negócios?”
* “quais descendentes de galileo venceram aos 2 anos?”

ele vai gerar sql, rodar no banco e devolver a resposta.

### 7. corrigir e

---

**INEMA** · 2025-08-29

https://chatgpt.com/c/68b0d327-bde4-8328-a5ce-2857a9ac40d4
