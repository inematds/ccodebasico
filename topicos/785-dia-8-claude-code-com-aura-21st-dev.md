# Dia 8 - Claude Code com Aura & 21st.dev

> Tópico 785 · 10 mensagens úteis de 21 totais

---

**INEMA** · 2025-09-08

Reforçando algumas **explicações e aprendizados** que servem como orientação para não se perder. Aqui está o que ele fala e explica ao longo da prática:

---

### 1. Diferença entre **criar do zero** e **usar templates**

* Criar um site do zero no Claude → rápido, mas o resultado fica feio/incompleto.
* Usar template pronto (Aura.build) → muito mais eficiente.
* Explicação: “É mais fácil começar de um design pronto e só trocar cores/textos do que tentar remodelar algo que já saiu errado.”

---

### 2. O problema dos **tokens no Claude**

* Quando Claude tenta regurgitar todo um código de 800+ linhas, bate no limite de 32K tokens.
* Solução: aumentar o limite para 64K com `export CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000`.
* Explicação: “O Claude não consegue cuspir tudo de uma vez se o limite for baixo. É preciso expandir a janela de saída.”

---

### 3. A importância do **Plan Mode**

* Ele insiste em não sair mudando tudo no impulso.
* No Plan Mode você planeja as mudanças → Claude gera diffs limpos em vez de reescrever tudo.
* Explicação: “Se você não planeja, o Claude tende a alucinar e refazer coisas desnecessárias.”

---

### 4. O erro de **deletar e recomeçar**

* Ele mostra que apagar componentes e recriar do zero gera inconsistências (layouts quebrados, animações que somem).
* Explicação: “Sempre preserve o código base. Se deletar, Claude perde referência e inventa coisas.”

---

### 5. **Component Targeting** no 21st.dev

* Você pode aplicar estilos em elementos específicos (ex.: “aplique este botão glass no id=get-consultation”).
* Explicação: “Direcionar é essencial. Se você não diz onde aplicar, ele espalha o estilo em botões aleatórios.”

---

### 6. Diferença Aura.build vs 21st.dev

* Aura.build → gera **sites inteiros** com templates e temas.
* 21st.dev → foca em **componentes individuais** (botões, cards, efeitos).
* Explicação: “Aura é para começar com base, 21st é para polir detalhes e fazer upgrades pontuais.”

---

### 7. Uso de **screenshots para feedback**

* Ele mostra que tirar print e mandar para Claude ajuda o modelo a entender onde está o erro no layout.
* Explicação: “Claude precisa de contexto visual para corrigir falhas específicas como áreas em branco ou animações sumidas.”

---

### 8. Filosofia de trabalho “comece simples”

* Primeiro, implemente um template sem mexer.
* Depois, altere apenas o necessário (cores, textos, pequenos componentes).
* Explicação: “É muito mais rápido chegar a um site bonito em 20 minutos se você não brigar com o modelo.”

---

**INEMA** · 2025-09-08

Aqui estão os hacks mais úteis e práticos e a prática com Claude Code + Aura.build + 21st.dev revelam:

---

### Hacks para ganhar velocidade

1. **Sempre começar do template pronto (****Aura.build****)**

   * Copie o código base e implemente sem alterar.
   * Só depois ajuste cores/textos → evita bugs e alucinações.

2. **Duplicar limite de tokens do Claude**

   * Se bater no erro de 32K tokens:
     `export CLAUDE_CODE_MAX_OUTPUT_TOKENS=64000`
   * Isso dobra a saída para 64K e evita que o código seja cortado.

3. **Plan Mode antes de alterar**

   * Use plan mode para definir o que vai mudar → garante diffs limpos e previsíveis.

---

### Hacks para reduzir erros

4. **Não apagar blocos inteiros**

   * Deletar e reescrever arquivos gera alucinação. Prefira mudar cores, textos ou classes específicas.

5. **Componentes cirúrgicos com ****21st.dev**

   * Copie o prompt de um componente e adicione contexto:
     “aplique apenas no botão get-consultation”
   * Isso evita mudanças aleatórias no site inteiro.

6. **Usar screenshots como guia**

   * Se o Claude errar no layout ou sumir animação, envie screenshot marcando a área com problema.

---

### Hacks para economizar créditos

7. **Copiar código/prompt manualmente**

   * Em vez de gastar créditos no 21st.dev/Aura, copie o código ou prompt e cole no Claude ou Gemini.
   * Eles aplicam as mudanças sem custo extra.

---

### Hacks de design rápido

8. **Troca de cores com hex codes**

   * Especifique hex exato (ex.: #1E3A8A e #9CA3AF) → Claude não “inventa” tons.

9. **Remixar no ****Aura.build**** antes de levar ao Claude**

   * Troque cores/temas direto no Aura.build → já exporta pronto e com menos risco de erro.

10. **MCP Server para mockups instantâneos**

* Ative o 21st.dev Magic MCP → ele gera 6–7 mockups prontos.
* Você escolhe o melhor e aplica direto sem ter que testar na unha.

---

---

**INEMA** · 2025-09-08

(rápido e seguro)

1) Comece com template do Aura.build e implemente “como está”.
2) Ajuste cores e textos em plan mode.
3) Aplique componentes pontuais do 21st.dev onde precisar brilho extra.
4) Quando quiser explorar visuais novos, use o Magic MCP para gerar mockups e aplicar o preferido.
5) Teste responsividade e acessibilidade a cada passo.

7. Checklist de QA e performance

* Responsividade: mobile, tablet, desktop ultrawide.
* Layout: min-h-screen no body/main, container e gaps consistentes.
* Acessibilidade: contraste de cores, labels e aria-\* em botões/links.
* Performance: imagens otimizadas, preload de fontes, Lighthouse mínimo 90/90/90.
* Código: diffs curtos, sem reescrever arquivos inteiros sem necessidade.

8. Solução de problemas comuns

* Só 70% da tela aparece: verifique meta viewport, remova height fixa no body, adicione min-h-screen, overflow-x-hidden e width: 100vw no container principal.
* Animação sumiu após edição: restaure a seção original do template e peça para “preservar a animação orbital; apenas trocar cores/cópia”.
* Excedeu 32K tokens: aumente para 64K como no passo 3.3. Se ainda falhar, peça para escrever em arquivos por partes (header.tsx, hero.tsx, features.tsx).
* shadcn/ui não aplicado: rode o init do shadcn e reimporte estilos globais; gere o Button pelo CLI para garantir tokens de cor e variantes.

9. Prompts prontos para copiar

* Implementar template sem mudanças:
  implemente exatamente este template, sem alterações. crie os arquivos, importe estilos, rode o dev server em localhost e mantenha rodando. depois me mostre o diff das criações
* Trocar paleta com segurança:
  altere apenas tokens de cor Tailwind para primária #1E3A8A e cinza #9CA3AF; preservando animações e classes existentes. nada de remoções
* Aplicar componente 21st.dev específico:
  aplique o estilo Liquid Glass Button do 21st.dev somente no elemento com id="get-consultation" no header. não crie novos botões; apenas estilize o existente
* Gerar mockups via Magic MCP:
  gere 6–7 mockups com estética glassmorphism, hero animado e tipografia moderna. liste as opções; aplique a opção 3 mantendo a estrutura e rotas atuais

10. Hacks úteis

* Comece do design e só depois ajuste conteúdo. Isso encurta o ciclo para menos de 20 minutos.
* Sempre peça diffs pequenos e explique as linhas alteradas. Isso reduz alucinações.
* Se precisar economizar créditos, copie o código/prompt do 21st.dev e peça para o Claude aplicar localmente.
* Ao mexer em animações, trave o seletor e a keyframe original; peça apenas mudança de cores/blur/duração.
* Para grandes colagens de código, divida por arquivos e peça gravação incremental (crie src/components/Hero.tsx; agora Features.tsx; etc.).

---

**INEMA** · 2025-09-08

Passo a passo completo para deixar seu app/site do Claude Code bonito rápido, usando Aura.build, 21st.dev e 21st.dev Magic MCP

1. Pré-requisitos rápidos

* Claude Code instalado e com terminal funcionando.
* Node.js LTS e um gerenciador (npm, pnpm ou yarn).
* Projeto React/Vite ou Next + Tailwind + shadcn/ui. Se não tiver:
  Prompt para o Claude Code:
  crie um projeto React + Vite + TypeScript com Tailwind e shadcn/ui; rode o servidor em localhost e mantenha o dev server ativo para cada mudança

2. Criação do projeto base no Claude Code

* Abra uma pasta vazia.
* Prompt direto:
  quero um site simples de consultoria em IA. gere a estrutura com React + Vite + TS + Tailwind + shadcn/ui. suba em localhost automaticamente e mantenha rodando
* Se o layout ocupar só parte da tela ou quebrar em monitores wide, peça:
  ajuste auto-layout e responsividade: min-h-screen, max-w-\[...], container px-4 md\:px-6, overflow-x-hidden, meta viewport correta

3. Método 1 — Aplicar um template completo do Aura.build
   3.1 Escolha e copie o template

* Em aura.build, abra um componente/template trending com animações.
* Clique em Code e copie o código completo.

3.2 Cole e implemente sem alterações

* Prompt no Claude Code:
  implemente este código exatamente como está, sem alterações. crie todos os arquivos necessários. rode em localhost agora
  \[cole as \~886 linhas do template]

3.3 Se der erro de limite de tokens (32K)

* macOS/Linux no terminal do Claude Code:
  export CLAUDE\_CODE\_MAX\_OUTPUT\_TOKENS=64000
* Windows PowerShell:
  setx CLAUDE\_CODE\_MAX\_OUTPUT\_TOKENS 64000
  feche e reabra o terminal do Claude Code.
* Alternativa via arquivo de ambiente: crie/edite .claude/env com a linha
  CLAUDE\_CODE\_MAX\_OUTPUT\_TOKENS=64000
  reinicie o workspace.

3.4 Personalize sem “derrubar” o template

* Entre em plan mode e peça apenas mudanças de cópia e paleta:
  mude a primária para azul real #1E3A8A e cinza #9CA3AF; não altere estrutura, só cores e textos
* Se uma animação sumir (ex.: orbital):
  restaure a seção original do template e peça:
  preserve a seção de animação orbital; só ajuste cores e textos

Boas práticas neste método

* Comece do template pronto, depois personalize. Evita refatoração pesada e alucinações.
* Não apagar grandes blocos. Prefira diffs pequenos e localizados.

4. Método 2 — Melhorias cirúrgicas com 21st.dev (nível de componente)
   4.1 Garantir base compatível

* shadcn/ui e Tailwind ativos. Se faltar, peça ao Claude para executar:
  npx shadcn\@latest init
  npx shadcn\@latest add button card input
  configure tailwind.config e importe estilos globais.

4.2 Copiar prompt do 21st.dev e aplicar em um alvo

* No 21st.dev, escolha um componente (ex.: Liquid Glass Button).
* Clique em Copy Prompt → selecione Claude Code → Add context:
  aplicar ao botão Get consultation no header (canto superior direito)
* Cole o prompt no Claude Code. Ele deve:
  instalar dependências se necessário, criar/atualizar o componente e aplicar classes/estilos.

4.3 Se o efeito cair no lugar errado

* Use DevTools para obter seletor/id/class do alvo.
* Envie um screenshot e peça:
  aplique o estilo do componente somente no elemento com id="get-consultation", mantendo semântica e acessibilidade

4.4 Enfileire mudanças

* Você pode colar vários prompts de componentes (botões, cards, hero, chat) um após o outro.
* Sempre peça commits pequenos:
  faça um patch mínimo; mostre o diff e explique as linhas alteradas

5. Método 3 — 21st.dev Magic MCP server (mockups com IA)
   5.1 Instalação

* No site do 21st.dev, abra Magic MCP → Installation.
* Escolha Claude Code, copie o comando sugerido (inclui ID do provedor e sua API key) e rode no terminal do Claude Code.
* Reinicie o terminal quando solicitado.

5.2 Uso

* Com o projeto aberto, peça:
  gere 6–7 mockups com foco em glassmorphism e hero com animação orbital. liste as opções com thumbs e aplique a opção escolhida mantendo minha estrutura atual
* Escolha um mockup e mande aplicar.
* Ajuste textos e paleta em plan mode, mantendo diffs pequenos.

6. Fluxo de trabalho recomendado

---

**INEMA** · 2025-09-08

[**21st.dev**](https://21st.dev/)

---

**INEMA** · 2025-09-08

https://aura.build/

---

**INEMA** · 2025-09-08

Resumo

### Propósito

Ensinar como deixar qualquer site ou app feito no Claude Code mais bonito e rápido de forma prática, mesmo sem ser designer.

---

### Principais pontos

1. **Três abordagens apresentadas**

   * **Aura.build**: templates completos de sites, com animações e código pronto para copiar.
   * **21st.dev**: biblioteca de componentes (botões, efeitos de vidro, morphism etc.), prompts prontos para Claude Code.
   * **21st.dev**** MCP Server**: nível avançado, gera de 6 a 7 mockups com IA e permite escolher e implementar direto.

2. **Exemplo prático**

   * Criação de site de consultoria em IA.
   * Problemas comuns: layout incompleto, uso ineficiente de tokens, perda de animações.
   * Solução: começar sempre pelo template pronto → depois personalizar cores e conteúdos.

3. **Problema dos tokens**

   * Claude tem limite de 32K tokens de saída.
   * Correção: export CLAUDE\_CODE\_MAX\_OUTPUT\_TOKENS=64000 → dobra a capacidade.

4. **Boas práticas descobertas**

   * Nunca apagar e reconstruir do zero (gera alucinações).
   * Melhor começar pelo design-base e depois ajustar (diferenças menores, menos erros).
   * Usar plan mode para planejar alterações antes de aplicar.

5. **Uso de ****21st.dev**

   * Permite copiar prompts prontos para componentes.
   * Dá para direcionar mudanças em elementos específicos (ex.: botão “Get consultation”).
   * Possível combinar com Claude/Gemini sem gastar créditos do 21st.dev, copiando só o código ou prompt.

6. **Preview do próximo passo (MCP server)**

   * Instalação simples no Claude Code.
   * Mostra vários mockups prontos.
   * Escolha e aplicação automáticas → agiliza ainda mais a etapa de design.

---

### Resultado final

Em cerca de 20 minutos é possível passar de um site básico para um design limpo, moderno e com efeitos de vidro, usando Aura.build + 21st.dev, com ajustes rápidos e menos frustração.

---

**INEMA** · 2025-09-08

Claude Code Dia 8: Deixando Seus Apps Bonitos com Aura & 21st.dev
Seu código secreto para parar de construir aplicativos feios.

Transformar projetos Claude Code de sem-graça de desenvolvedor para lindos de designer usando três abordagens diferentes.

Três métodos para melhorar instantaneamente sua UI, incluindo:

* Aura.build para templates completos de sites
* 21st.dev para design em nível de componentes
* 21st.dev MCP server para mockups com IA (prévia de amanhã)

Método 1: Aura.build (Templates de Site Inteiro)

* Navegar por componentes em alta com animações
* Copiar toda a base de código (886 linhas)
* O problema do limite de 32K tokens e a solução
* Exportar CLAUDE\_CODE\_MAX\_OUTPUT\_TOKENS=64000
  Lição crítica aprendida:
  Começar do zero com código de template: 10 minutos
  Adaptar site existente: 1+ hora de dor
  Sempre comece com o template de design, DEPOIS modifique.

Método 2: 21st.dev (Biblioteca de Componentes)

* Botões de glass morphism
* Efeitos de vidro líquido
* Recurso de copiar prompt para Claude Code
* Direcionar elementos específicos
  A correção do limite de tokens:
  Quando o Claude diz "resposta excedeu o máximo de 32.000 tokens de saída"
  Execute: export CLAUDE\_CODE\_MAX\_OUTPUT\_TOKENS=64000
  Isso dobra sua capacidade de saída para 64K tokens.

Fluxo de trabalho profissional descoberto:

1. Pegue o código do template do Aura.build
2. Implemente como está primeiro (sem modificações)
3. Depois mude cores/conteúdo no modo de planejamento
4. Resultado: diffs limpos, menos alucinações

Direcionamento de componentes com 21st.dev:

* Copie o prompt do 21st.dev
* Adicione contexto: "Aplicar ao botão obter consulta"
* Coloque várias atualizações de componentes na fila
* Veja a mágica acontecer

Armadilhas comuns mostradas:

* Não delete e reconstrua (causa alucinações)
* Template tem 886 linhas? Aumente o limite de tokens antes
* Faltando 30% da tela? Problema de auto-layout
* Animação orbital desapareceu? Comece do zero

Prévia de amanhã: 21st.dev MCP server

* Veja 6-7 mockups instantaneamente
* Escolha o seu favorito
* Implementação automática no Claude Code

Resultado: De um site de consultoria básico para uma beleza com glass-morphism em menos de 20 minutos (quando feito corretamente).

---

**INEMA** · 2025-09-08

Dia 8 -Claude Code com Aura & 21st.dev

---

**INEMA** · 2025-09-08

https://chatgpt.com/c/68be62c4-b934-8321-8584-8d3da4b99caa
