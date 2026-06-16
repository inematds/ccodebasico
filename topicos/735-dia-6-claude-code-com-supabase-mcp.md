# Dia 6 - Claude Code Com Supabase MCP

> Tópico 735 · 9 mensagens úteis de 22 totais

---

**INEMA** · 2025-09-08

Aqui estão alguns **hacks práticos** para facilitar e acelerar a implementação do Supabase com MCP, evitando armadilhas comuns:

---

### 1) Simplificação do token

* Em vez de colar o Access Token direto no `mcp.json`, exporte como variável de ambiente:

  * Linux/macOS:
    `export SUPABASE_ACCESS_TOKEN=SEU_TOKEN`
  * Windows (PowerShell):
    `setx SUPABASE_ACCESS_TOKEN "SEU_TOKEN"`
* No JSON, use:

  ```  "--access-token", "$SUPABASE_ACCESS_TOKEN"
  ```

Assim você evita expor o token no código e pode trocá-lo rápido sem editar arquivos.

---

### 2) Reset rápido de conexão MCP

* Sempre que mudar schema ou `mcp.json`, reinicie o cliente MCP.
* Atalho: se estiver usando Claude Code, feche a aba do projeto e reabra para forçar reload.

---

### 3) Validação “verdadeira” da conexão

* Não confie só em “Supabase connected”.
* Hack: rode o comando para listar **funções disponíveis**; se não aparecer nada, a integração falhou.

---

### 4) Criação de schema turbo

* Em vez de pedir tabela por tabela, descreva todas de uma vez em **prompt estruturado** (como no passo que te passei antes).
* Hack: peça índices já no pedido inicial (GIN para JSON, index para session\_id). Assim não precisa criar depois.

---

### 5) Autoteste sem dor

* O MCP consegue rodar queries sozinho.
* Hack: sempre peça ao Claude:
  “Insira um registro de teste em cada tabela e depois faça um SELECT LIMIT 1 para validar”.
  Isso já garante que o fluxo está inteiro funcionando.

---

### 6) Safe area para testes

* Use janela anônima do navegador depois de mudar schema.
* Hack: evita cache e garante que o frontend carrega as mudanças mais recentes do backend.

---

### 7) Frontend conectado sem gambiarra

* Hack: crie funções genéricas no frontend (ex.: `saveToSupabase(table, data)`), e reaproveite para todas as tabelas.
* Reduz código duplicado e facilita manutenção.

---

### 8) Debug rápido no Supabase

* Painel → **Table Editor** → clique na tabela → aba **Data** → visualize inserts sem abrir SQL.
* Hack: use consultas SQL só quando precisa validar índices ou performance.

---

---

**INEMA** · 2025-09-08

limit 3;
select * from conversations order by created_at desc limit 5;
select * from mermaid_diagrams order by created_at desc limit 3;
select action, metadata, created_at from user_actions order by created_at desc limit 5;
```

```

9. Checklist de depuração rápida

* MCP sem funções listadas: token errado/cliente não reiniciado/JSON inválido.
* Inserts falhando com 401/403: revise RLS e chaves usadas; para desenvolvimento, use operações via servidor ou crie políticas compatíveis.
* Botões sem ação: reinicie o servidor local; confira ligações dos handlers; veja erros no console.
* Dados não aparecem: rode as consultas acima; revise session\_id sendo passado aos inserts.

10. Próximos passos sugeridos

* Carregar histórico por sessão ao abrir a conversa.
* Autenticação de usuário com Clerk (ou Supabase Auth) em módulo posterior.
* Índices adicionais conforme consultas mais frequentes.
* Exportar diagramas e histórico para análise.

---

**INEMA** · 2025-09-08

Aqui vai um passo a passo claro, direto e prático.

1. Preparar o ambiente

* Ter conta no Supabase.
* Node.js instalado (npx disponível).
* Um cliente MCP (ex.: Claude Code/Cloud Code/Cursor) que leia mcp.json.
* Projeto web rodando localmente (ex.: Vite/Next/React).

2. Criar token e configurar o MCP
   a) Criar Access Token

* Supabase → Account settings → Access Tokens → New access token.
* Copie o token na hora da criação.

b) Criar/editar mcp.json no projeto

```{
  "mcpServers": {
    "supabase": {
      "command": "npx",
      "args": [
        "-y",
        "@supabase/mcp-server-supabase@latest",
        "--access-token",
        "SEU_TOKEN_AQUI"
      ]
    }
  }
}```

3. Proteger credenciais antes do primeiro commit

* No .gitignore, adicione:

```mcp.json
MCP.json```

4. Reiniciar o cliente MCP e validar a conexão

* Feche e reabra o cliente (Claude/Cloud Code).
* Peça para listar servidores MCP e conferir que o supabase aparece com funções listadas.
* Sinal verde: aparece supabase e uma lista de funções.
* Sinal amarelo: aparece só “connected” sem funções → revise o token/JSON e reinicie.

5. Subir o app local e checar

* Rode o projeto (exemplos):

  * Vite: npm run dev
  * Next.js: npm run dev
* Abra o localhost informado e confirme que a UI carrega.

6. Criar o schema via MCP
   Envie ao agente este prompt único:

U```se o servidor MCP do Supabase para criar as tabelas abaixo, com chaves primárias UUID, FKs, timestamps created_at (timestamptz default now()) e updated_at, e índices por session_id:

1) sessions
   - id
   - created_at

2) initial_prompts
   - id
   - session_id -> sessions.id on delete cascade
   - prompt text
   - created_at

3) voice_inputs
   - id
   - session_id -> sessions.id on delete cascade
   - transcript text
   - confidence float8
   - recognition_instance text
   - created_at

4) conversations
   - id
   - session_id -> sessions.id on delete cascade
   - role text  -- ex.: user/assistant/system
   - content text
   - model text
   - created_at

5) mermaid_diagrams
   - id
   - session_id -> sessions.id on delete cascade
   - diagram text
   - created_at

6) user_actions
   - id
   - session_id -> sessions.id on delete cascade
   - action text
   - metadata jsonb
   - created_at
   - criar índice GIN em metadata

Ao concluir, responda success=true somente quando as tabelas estiverem criadas no Supabase.
```
* Verifique resposta success=true.
* Abra o painel do Supabase e confirme as tabelas.

7. Ligar frontend ao banco (handlers mínimos)
   Peça ao agente para criar/ajustar handlers e chamadas de persistência. Prompt sugerido:

Co```necte o frontend às tabelas do Supabase criadas via MCP:
- Criar funções saveInitialPrompt(sessionId, text)
- saveVoiceInput(sessionId, transcript, confidence, recognitionInstance)
- saveConversation(sessionId, role, content, model)
- saveMermaid(sessionId, diagram)
- logUserAction(sessionId, action, metadata)

Ligue:
- handleInitialSubmit -> saveInitialPrompt
- handleVoiceInput -> saveVoiceInput
- envio/recebimento de chat -> saveConversation
- geração de diagrama -> saveMermaid
- cliques de botões -> logUserAction

Após implementar, execute consultas de verificação via MCP para garantir que cada insert chegou ao banco.

```Se preferir, peça para o agente também criar a função createSession() que retorna o id da sessão e armazená-lo em memória/estado.

8. Testes ponta a ponta

* Texto: envie um prompt → consulte no Supabase initial\_prompts e sessions.
* Voz: dite algo → verifique transcript/confidence em voice\_inputs.
* Conversa: faça 2–3 trocas → confira em conversations.
* Diagrama: gere o workflow → copie o campo diagram e cole em mermaid.live para renderizar.
* Ações: clique em botões da UI → veja registros em user\_actions.
* Dica: após alterar schema/código, teste em janela anônima para evitar cache.

SQLs rápidos de validação (no painel do Supabase)

```sql
select * from sessions order by created_at desc limit 3;
select * from initial_prompts order by created_at desc limit 3;
select * from voice_inputs order by created_at desc

---

**INEMA** · 2025-09-08

incluem adicionar **histórico carregado por sessão** no frontend e implementar **autenticação**, que será feita em vídeos futuros com o **Clerk**. O Supabase também permite autenticação, mas sua configuração (como OAuth com Google) pode ser mais complexa.

---

**INEMA** · 2025-09-08

Conteúdo completo estruturado nos 5 capítulos :

---

### Capítulo 1 — Configuração inicial

O objetivo central é integrar o **Supabase** ao projeto utilizando o **servidor MCP** (Model Context Protocol), permitindo criar e manipular bancos de dados de forma automática, sem precisar copiar e colar comandos SQL manualmente.

O primeiro passo é configurar o arquivo **MCP.json**. Nele, deve ser adicionada a entrada para o Supabase, chamando o pacote via `npx` e passando o argumento **--access-token**, que é obrigatório para autenticar a comunicação.

Para obter o token de acesso, é necessário entrar nas **Configurações da conta do Supabase**, criar um novo **Access Token** e copiá-lo imediatamente (ele não poderá ser visualizado novamente depois).

Por segurança, o arquivo **mcp.json** deve ser adicionado ao **.gitignore** antes de qualquer commit, evitando que credenciais sensíveis sejam expostas em repositórios públicos.

---

### Capítulo 2 — Verificação e preparação

Com o MCP configurado, é preciso **verificar a conexão**. Isso é feito pedindo ao agente (Claude ou outro cliente compatível) que liste os servidores MCP e confirme as funções disponíveis.
Se aparecer apenas “Supabase connected” sem listar funções, significa que a conexão não está realmente funcional.

Em seguida, deve-se subir a aplicação local em **localhost**, garantindo que as portas corretas estejam abertas. Esse passo permite validar que o frontend está rodando e preparado para receber as conexões do backend via Supabase.

Um detalhe importante: algumas configurações podem funcionar apenas localmente, mas falhar no servidor real. Por isso, sempre faça a checagem completa de ponta a ponta.

---

### Capítulo 3 — Criação do schema

Após a preparação, entra em cena o **planejamento das tabelas** necessárias para a aplicação. O exemplo usado no vídeo definiu um conjunto de tabelas que cobrem todo o fluxo do app Workflow Maker:

* **sessions** – rastrear sessões de usuário
* **initial\_prompts** – guardar o primeiro input de cada sessão
* **voice\_inputs** – salvar transcrições da Web Speech API
* **conversations** – manter o histórico completo dos chats
* **mermaid\_diagrams** – armazenar os diagramas gerados
* **user\_actions** – registrar cliques e interações do usuário

Com o Supabase via MCP, não é necessário escrever SQL. O agente é instruído a **criar todas as tabelas de uma vez** e aplica a migração automaticamente. A confirmação de sucesso vem no retorno com `success=true` e pode ser validada diretamente no painel do Supabase.

---

### Capítulo 4 — Integração backend ↔ frontend

Com o banco pronto, o próximo passo é conectar o **frontend** às tabelas criadas. Isso é feito ajustando os **handlers JavaScript** da aplicação, como `handleInitialSubmit` e `handleVoiceInput`.

Cada handler é associado a uma função de persistência, como `saveInitialPrompt` ou `saveVoiceInput`, que recebe os dados da interface e os grava no banco.
Esse processo garante que inputs de texto, ditados de voz ou ações do usuário sejam salvos corretamente em suas respectivas tabelas.

Uma vantagem extra do MCP é que ele consegue **testar automaticamente as inserções**, executando consultas SQL de validação para verificar se os registros chegaram no banco.

---

### Capítulo 5 — Testes, benefícios e próximos passos

A etapa final consiste em **testes ponta a ponta**:

* Enviar um prompt de texto e conferir o registro em `initial_prompts`.
* Usar entrada de voz e confirmar a transcrição em `voice_inputs`.
* Gerar um diagrama e validar o código salvo em `mermaid_diagrams` (testável em sites como mermaid.live).
* Conferir se o histórico completo aparece em `conversations`.

O benefício do MCP é claro: em vez do ciclo tradicional (gerar SQL → colar → testar → repetir), basta descrever o que se deseja e o servidor cria, aplica e valida automaticamente. Isso acelera o desenvolvimento e reduz erros.

Para depuração, se a interface quebrar (botões que não funcionam, envios que não gravam), basta reiniciar o servidor local, revisar os handlers e repetir o teste.

Os próximos passos

---

**INEMA** · 2025-09-08

Esta sessão tem como propósito **explicar, de forma clara e prática, como integrar o Supabase a um projeto utilizando o servidor MCP (Model Context Protocol)**.

A ideia central é mostrar que, em vez de escrever manualmente consultas SQL, copiar e colar no editor do Supabase e depois testar — um processo demorado e sujeito a erros — o servidor MCP permite **descrever o que se quer em linguagem natural** e deixar que o agente (Claude Code, no exemplo) faça toda a configuração automaticamente.

### O que foi apresentado na sessão

1. **Configuração inicial**

   * Criar um token de acesso no Supabase (Access Token).
   * Configurar o arquivo `mcp.json` para incluir o Supabase com o argumento `--access-token`.
   * Proteger esse arquivo adicionando-o ao `.gitignore`, evitando expor credenciais.

2. **Verificação da conexão**

   * Testar se o MCP realmente reconhece o Supabase e lista funções disponíveis.
   * Atenção: se aparecer apenas “Supabase connected” sem funções listadas, a integração não está completa.

3. **Criação do schema**

   * Planejar e criar tabelas automaticamente (sessions, prompts, voice\_inputs, conversations, mermaid\_diagrams, user\_actions).
   * Confirmar no painel do Supabase que as tabelas e colunas foram criadas corretamente.

4. **Integração frontend ↔ backend**

   * Conectar funções do código (ex.: `handleInitialSubmit`, `handleVoiceInput`) às tabelas criadas.
   * O MCP valida as operações sozinho, verificando se os dados enviados chegam ao banco.

5. **Testes e benefícios**

   * Testar entradas de texto, voz, diagramas e histórico de conversas, confirmando que tudo está salvo.
   * Comparar o método tradicional (copiar/colar SQL) com o MCP, que funciona como um “atalho” ou “cheat code” para simplificar todo o processo.
   * Apontar próximos passos, como implementar autenticação de usuários.

### Em resumo

A sessão explica que o **MCP com Supabase torna a integração de banco de dados rápida, automática e confiável**, facilitando a vida de quem está desenvolvendo aplicações. Ela mostra tanto os aspectos técnicos (configuração e segurança) quanto os práticos (testes e validação), servindo como guia para quem nunca fez esse tipo de integração.

---

**INEMA** · 2025-09-08

O propósito desta sessão foi **mostrar como integrar o Supabase a um projeto usando o servidor MCP de forma prática e segura**, eliminando a necessidade de escrever ou colar comandos SQL manualmente.

Em resumo:

* Como configurar corretamente o **MCP.json** com o Supabase e o uso obrigatório do **Access Token**.
* A importância de proteger credenciais adicionando o arquivo ao **.gitignore** antes de qualquer commit.
* Como **validar a conexão** para garantir que o servidor MCP realmente reconhece e expõe funções do Supabase.
* O processo de **criação automática de tabelas** (sessions, prompts, voice inputs, conversations, diagrams, actions) sem precisar escrever SQL.
* A forma de **conectar backend e frontend**, ligando funções do app às tabelas criadas.
* A realização de **testes ponta a ponta** (texto, voz, diagramas, histórico) para confirmar que os dados fluem corretamente.
* E, por fim, os **benefícios do MCP** em relação ao método tradicional, além de indicar próximos passos como autenticação e carregamento de histórico de sessões.

Em essência, a sessão serviu para mostrar que o **Supabase MCP funciona como um “atalho” poderoso**, simplificando a criação, integração e validação de banco de dados em projetos que usam Claude Code e workflows automatizados.

---

**INEMA** · 2025-09-08

Dia 6 - Claude Code Com Supabase MCP

---

**INEMA** · 2025-09-08

https://chatgpt.com/c/68bc0cf2-e264-8331-9d35-dc73a10fc399
