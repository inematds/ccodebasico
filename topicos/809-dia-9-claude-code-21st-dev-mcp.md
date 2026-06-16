# Dia 9 - Claude Code 21st.dev MCP

> Tópico 809 · 6 mensagens úteis de 20 totais

---

**INEMA** · 2025-09-08

## Hacks do Magic MCP

1. **Instalação instantânea com API Key embutida**

   * O comando copiado do site já inclui a chave de API.
   * Evita ter que configurar manualmente ou salvar variáveis de ambiente.

2. **Multitarefa com sessões paralelas**

   * Enquanto uma sessão gera o mockup inicial, você pode abrir outra para instalar/testar o MCP.
   * Acelera o fluxo sem precisar esperar cada etapa.

3. **Teste rápido do MCP**

   * Perguntar diretamente: *“Quais ferramentas do Magic MCP estão disponíveis agora?”*
   * É a forma mais simples de verificar se o servidor está de fato ativo (às vezes o `mcp list` engana).

4. **Inspiração vs. Builder**

   * Component Inspiration → gera HTML leve e direto para auditoria, fácil de reverter.
   * Component Builder → gera múltiplas variantes completas que podem ser aplicadas de imediato.
   * Hack: use Inspiration quando quiser testar rápido sem arriscar quebrar seu projeto.

5. **Chat with Variant**

   * Em vez de editar código, você conversa com cada variante e pede ajustes (cores, espaçamentos, fontes).
   * Funciona como um mini-Figma dentro do terminal.

6. **Open in MCP = aplicar sem copiar/colar**

   * Elimina o fluxo antigo (copiar → colar → depurar).
   * Um clique aplica as mudanças direto no seu projeto.

7. **Refiner para ajustes cirúrgicos**

   * Se só quer mudar detalhes (ex.: bordas, padding, tipografia), use o `component_refiner`.
   * Evita ter que refazer toda a tela.

8. **Logo Search automático**

   * Permite adicionar logos reais de empresas só digitando os nomes.
   * Hack prático para simular “clientes parceiros” ou criar páginas de credibilidade.

9. **Resiliência ao primeiro erro**

   * Primeiro redirecionamento muitas vezes falha — repetir o comando costuma resolver.
   * Saber disso evita perder tempo achando que está quebrado.

10. **Stack alignment**

* Informe no prompt qual framework você está usando (React, Next.js, Tailwind).
* Hack: isso reduz conflitos de código e retrabalho.

---

---

**INEMA** · 2025-09-08

vier fora do meu padrão?

* Peça realinhamento: “converter para meu stack X”, “padronizar tokens de design”, “remover CSS inline”, etc.

---

**INEMA** · 2025-09-08

Segue um passo a passo direto para usar o 21st.dev Magic MCP com Claude Code e refazer sua UI em minutos.

# Resumo rápido

Você vai instalar o Magic MCP, confirmar que o servidor está ativo, pedir variantes de UI, pré-visualizar no navegador e aplicar no projeto com um clique. Se algo falhar, reinicie a sessão e tente de novo.

# Passo a passo

1. Preparar o projeto

* Crie/abra seu projeto no Claude Code.
* Se quiser, peça um mockup inicial: descreva a página, elementos e interações que deseja.

2. Instalar o Magic MCP

* Acesse 21st.dev/mcp e escolha sua IDE/ferramenta.
* Copie o comando de instalação que o site gera.
* Abra um terminal novo e cole o comando.
* Reinicie a sessão do terminal quando terminar.

3. Verificar se o MCP está conectado

* Rode: claude mcp list
* Confirme que o servidor magic-mcp (21st.dev) aparece como conectado.

4. Conferir as ferramentas disponíveis

* Pergunte ao Claude: “Liste as ferramentas do Magic MCP e o que cada uma faz.”
* Você deve ver: component\_builder, logo\_search, component\_inspiration, component\_refiner.

5. Gerar inspirações rápidas de layout

* Peça: “Use component\_inspiration para trazer variações modernas desta página de coleta de ideias com barra de busca, elementos flutuantes e feedback visual.”
* O MCP retornará múltiplas propostas e/ou links de preview.

6. Criar variantes com o Component Builder

* Peça: “Use component\_builder para gerar 5 variantes completas desta tela.”
* Aguarde a geração; normalmente surgem 5 versões diferentes.

7. Pré-visualizar e ajustar

* Abra cada variante no navegador.
* Se quiser refinar sem mexer em código, clique em “Chat with variant” e peça ajustes de espaçamento, tipografia, cores, animações, etc.

8. Aplicar no projeto

* Quando escolher uma, clique em “Open in MCP”.
* O Magic MCP aplica as mudanças no seu projeto (por exemplo, atualizando index.html ou componentes).

9. Validar localmente

* Suba o servidor local do projeto.
* Revise acessibilidade, responsividade e pequenos detalhes.
* Se algo destoar do seu stack, peça ao MCP para alinhar ao framework usado.

10. Iterar rápido

* Se uma variante perdeu contexto, peça outra rodada (builder ou inspiration).
* Use o component\_refiner para melhorar elementos específicos sem trocar tudo.

# Exemplos de prompts úteis

* “Use component\_inspiration para buscar 4 referências de UI para uma página de sugestões com barra de busca em gradiente, cartões flutuantes e microinterações de foco/clique.”
* “Use component\_builder para gerar 5 variantes do layout com header compacto, grid de cartões, dark mode opcional e botão primário destacado.”
* “Refine com component\_refiner: reduzir padding do header, aumentar contraste dos cards, suavizar sombras e padronizar raio de borda em 12px.”
* “Aplique esta variante no projeto com Open in MCP e mantenha meu framework atual.”
* “Adapte tudo para Tailwind, preservando semântica e acessibilidade ARIA.”

# Dicas e solução de problemas

* Reinício de sessão: depois da instalação, crie uma nova sessão do terminal para o MCP de fato responder.
* Verificação rápida: se desconfiar, pergunte “quais ferramentas do Magic MCP estão disponíveis agora?” Se não listar, reinicie.
* Limite do plano: se atingir o free tier, faça upgrade ou reduza o número de variantes por rodada.
* Conflitos de framework: informe o stack no prompt (“projeto com React + Vite” ou “Next.js + Tailwind”) e peça para remover resíduos do layout anterior.
* Link/redirect falhou: repita o comando/ação; na segunda tentativa costuma funcionar.
* Controle de mudanças: antes de aplicar, peça “mostre o diff proposto” ou “aplique em branch separada”.

# Perguntas rápidas

O que é melhor usar primeiro?

* component\_inspiration para ver direções de design; depois component\_builder para variantes completas.

Como edito sem copiar/colar código?

* Use “Chat with variant” para ajustes e “Open in MCP” para aplicar direto no projeto.

Posso manter minha barra de busca e só melhorar o resto?

* Sim. Diga explicitamente para preservar a search bar e usar o refiner para o restante.

E se a variante

---

**INEMA** · 2025-09-08

### Resumo

O vídeo mostra como usar o **21st.dev**** Magic MCP** para transformar rapidamente um projeto simples e “feio” em algo mais bonito e funcional, sem precisar copiar e colar código manualmente.

1. **Criação do projeto**

   * Novo projeto no Cloud Code.
   * Pedido para gerar um mockup de aplicação web de coleta de ideias, com interface atraente (barra com gradiente, elementos flutuantes, feedback visual).

2. **Instalação do Magic MCP**

   * Acesso ao site 21st.dev/mcp.
   * Copiar comando de instalação (já inclui chave API).
   * Reiniciar sessão do terminal e verificar com `claude mcp list`.

3. **Ferramentas do Magic MCP**

   * Component Builder: cria novos componentes de UI com múltiplas variantes.
   * Logo Search: adiciona logotipos de empresas.
   * Component Inspiration: busca componentes prontos para inspiração.
   * Component Refiner: refina e melhora componentes existentes.

4. **Primeiros testes**

   * Usando Component Inspiration, gerou múltiplas variações de interface.
   * Resultados: design minimalista, neon escuro, clean e outros.
   * Cada variante pode ser visualizada e aberta no navegador.

5. **Uso do Component Builder**

   * Após limite do plano gratuito, fez upgrade.
   * Gerou 5 variantes diferentes de interface.
   * Cada variante pode ser editada (“chat with variant”) ou aplicada diretamente em “Open in MCP”.
   * Diferença: Inspiration gera HTML leve para auditoria; Builder aplica direto no projeto principal.

6. **Conclusão**

   * Com Magic MCP, o processo de redesign é interativo e rápido.
   * Fluxo final: pedir redesign → ver variantes → escolher → aplicar → ajustar no editor.

-

---

**INEMA** · 2025-09-08

Claude Code Dia 9: 21st.dev Magic MCP - UI em Minutos 🪄

Este super truque prático funciona em qualquer lugar que aceite um servidor MCP.

Em cerca de 10 minutos você vai de feio para bonito usando o servidor Magic MCP do 21st.dev – o mais próximo que existe de ter um designer dentro do seu terminal.

O que você vai ver: geração de UI ao vivo com mockups movidos por IA, incluindo:

* Instalação e configuração do Magic MCP
* Uso do Component Builder para múltiplas variantes
* Component Inspiration para pré-visualizações rápidas
* Iteração em tempo real sem precisar copiar código

Ferramentas do Magic MCP explicadas:

* Component Builder: cria 5-6 variantes de UI para você visualizar
* Logo Search: adiciona logotipos de empresas automaticamente
* Component Inspiration: busca designs no 21st.dev
* Component Refiner: melhora componentes de UI já existentes

Processo de configuração mostrado:

* Copiar o comando de instalação do 21st.dev/mcp
* Já inclui a chave de API automaticamente
* Reiniciar a sessão do terminal após a instalação
* Verificar com: claude mcp list

Diferença no fluxo de trabalho:
Ontem: Copiar código → Colar → Depurar → Chorar
Hoje: Pedir redesign → Pré-visualizar 5 variantes → Escolher uma → Aplicar

Resultados de um Demo:

* Começou com um app de ideias “feio” e confuso
* Gerou 5 designs completamente diferentes
* Cada variante podia ser visualizada no navegador
* “Open in MCP” aplicava as mudanças instantaneamente

Problemas comuns abordados:

* Primeiro redirecionamento pode falhar (mas retry funciona)
* Conflitos de framework são possíveis (mas raros)
* Algumas variantes podem perder contexto (basta iterar)

Por que isso importa:
Nada mais de copiar código de sites de design. Nada mais de limites de tokens.
Basta descrever o que você quer, visualizar opções e aplicar.

---

**INEMA** · 2025-09-08

Dia 9 - Claude Code 21st.dev MCP
