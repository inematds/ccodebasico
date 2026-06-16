# Dia 11:Claude Code - Construindo GPTs

> Tópico 931 · 7 mensagens úteis de 19 totais

---

**INEMA** · 2025-09-14

**hacks práticos** para você usar nesse fluxo de criação de GPTs personalizados no Claude Code (com base em Markdown + MyMemories + Knowledge Base).

---

## Hacks de Estrutura

1. **Prompt único e limpo**

   * Coloque todas as regras no `slide_generator.md`.
   * Sempre inclua a hierarquia: `MyMemories.md → Knowledge Base → Prompt`.
   * Hack: Peça ao Claude “liste as fontes aplicadas” antes de gerar, para forçar o uso correto.

2. **MyMemories como “banco de preferências”**

   * Tudo que você corrigir ou pedir, salve nesse arquivo.
   * Hack: Peça para o Claude atualizar automaticamente o `MyMemories.md` após cada feedback.

3. **Knowledge Base modular**

   * Separe cada tema em um `.md` (design, copywriting, TED, Jobs etc.).
   * Hack: Nomeie arquivos com prefixos claros, ex.: `01_design.md`, `02_copy.md` → isso ajuda a IA a priorizar.

---

## Hacks de Geração

4. **ASCII Layouts**

   * Peça “com ASCII” para ter wireframes simples de cada slide.
   * Hack: Depois exporte esse ASCII para um editor visual (ex.: excalidraw) e já tem um protótipo.

5. **Prompt dinâmico**

   * Ao invés de “10–15 slides”, use:

     * “Gere 5 versões com estilos diferentes” → você escolhe o melhor.
   * Hack: Misture Jobs no início, TED no meio e Kawasaki no final.

6. **Simulação de público**

   * Acrescente: “Otimize os slides para um público X (ex.: executivos, alunos, investidores)”.
   * Hack: Guarde públicos frequentes em `MyMemories.md` para reuso.

---

## Hacks de Produtividade

7. **Init.md**** como “comando rápido”**

   * Escreva um guia em 3 linhas:

     * 1. Use slide\_generator.md
     * 2. Leia Knowledge Base
     * 3. Consulte MyMemories.md
   * Hack: Sempre abra a pasta e só copie/cole esse init.

8. **Exportação rápida para PowerPoint**

   * Gere em `.md` → converta com Pandoc:

     * `pandoc saida.md -o saida.pptx`
   * Hack: Se pedir “inclua marcadores \[SLIDE X]”, Pandoc já separa automaticamente.

9. **Feedback iterativo curto**

   * Em vez de “refaça tudo”, peça: “refaça apenas slides 3, 7 e 9 com estas regras”.
   * Hack: Faz a IA aprender mais rápido, e suas memórias ficam mais fiéis.

---

## Hacks de Integração

10. **Converter PDFs para Markdown**

    * Peça ao Claude: “Transforme este PDF em .md e adicione à Knowledge Base”.
    * Hack: Assim você cria repositórios temáticos (vendas, TI, saúde).

11. **Usar Pinecone MCP só quando precisa**

    * Se quiser arrastar PDFs grandes, use Pinecone Assistant.
    * Hack: Quando ele falhar, registre no `MyMemories.md` a forma correta de consulta.

12. **Multi-Stack simplificado**

    * Crie versões diferentes do mesmo prompt (ex.: storytelling, técnico, workshop).
    * Hack: Basta trocar um arquivo `.md`, sem mexer na estrutura.

---

**INEMA** · 2025-09-14

principal.
   * Ao gerar slides, consulte memories/MyMemories.md e toda a pasta knowledge\_base/.
3. Peça a apresentação:

   * Tópico: Como grandes empresas devem adotar ChatGPT
   * Gere 20 slides com resumo executivo no slide 2 e wireframes em ASCII.
4. Refine:

   * Deixe o tom mais executivo nos slides 5–8.
   * Aplique modelo TED no slide 3 e Jobs no slide 6.
   * Reduza texto no slide 9 para 2 linhas.

## 7) Refinando e reutilizando

* Ajuste MyMemories.md sempre que der feedback; a IA lerá primeiro.
* Acrescente novos arquivos .md na knowledge\_base para temas diferentes (vendas, produto, dados, segurança).
* Crie variantes do slide\_generator.md para estilos distintos (técnico, storytelling, workshop).

## 8) Exportação opcional

* Peça à IA para salvar a saída em um arquivo .md de resultado.
* Se usar Pandoc localmente, você pode converter .md em .pptx:

  * `pandoc saida.md -o saida.pptx`
  * Requer Pandoc instalado no seu sistema.

## 9) Opcional: integrar um MCP (quando fizer sentido)

* Use apenas quando realmente precisar ler fontes externas dinâmicas.
* Exemplo: Pinecone Assistant para consultar PDFs:

  * Arraste PDFs para um repositório indexado pelo assistant.
  * Peça ao Claude Code para consultar o assistant e incorporar trechos.
* Se falhar, documente no MyMemories.md o comando que funcionou depois do ajuste.

---

# Exemplos prontos

Exemplo 1 – comando inicial

```Use prompt/slide_generator.md. Gere 15 slides sobre “Estratégia de IA em PMEs”, com wireframes ASCII e foco minimalista. Resumo executivo no slide 2. Aplique Jobs no slide 6 e TED no slide 10.```

Exemplo 2 – refação parcial

R```efaça os slides 3, 7 e 11:
- 3: torne a mensagem-chave mais concreta (resultado mensurável).
- 7: troque bullets por 3 linhas de impacto.
- 11: adicione próximos passos práticos.
```
Exemplo 3 – troca de estilo

Ma```ntenha o conteúdo, mas aplique “10/20/30” do Guy Kawasaki. Reduza texto a no máximo 3 linhas por slide e aumente a força dos títulos.

```---

# Perguntas rápidas e respostas

O que torna essa abordagem confiável?

* Tudo está em arquivos .md locais, fáceis de auditar, versionar e portar. Sem dependência de servidor externo.

Como garanto que a IA use minhas preferências?

* Ela lê primeiro memories/MyMemories.md. Atualize esse arquivo sempre que der feedback e peça para “reler memórias”.

Posso adicionar fontes específicas do meu negócio?

* Sim. Crie arquivos na pasta knowledge\_base com regras, cases e dados internos. O prompt já manda consultar essa pasta.

E se a IA ignorar a knowledge\_base?

* Reforce no comando: “antes de gerar, liste quais arquivos da knowledge\_base serão aplicados e como”.

Como peço layouts?

* Acrescente “com ASCII” para cada slide. Se preferir, peça só para slides críticos.

Como reaproveitar para outros temas?

* Duplique a pasta do projeto, troque os arquivos da knowledge\_base e ajuste o MyMemories.md às novas preferências.

---

**INEMA** · 2025-09-14

# Passo a passo para criar um “custom GPT” no Claude Code usando Markdown

## 1) Preparar o projeto

1. Crie a pasta do projeto.

   * Windows PowerShell: `mkdir claudecode-demo && cd claudecode-demo`
   * Linux/macOS: `mkdir -p claudecode-demo && cd claudecode-demo`
2. Estrutura inicial de pastas e arquivos:

```claudecode-demo/
  prompt/
    slide_generator.md
  knowledge_base/
    design_minimalista.md
    copy_apresentacoes.md
    jobs_ted_guy.md
  memories/
    MyMemories.md
  init.md```

## 2) Escrever o prompt principal (prompt/slide\_generator.md)

Cole o conteúdo abaixo no arquivo.

T```ítulo: Slide Generator – Sistema Enxuto

Papel
Você é um designer de apresentações e estrategista de conteúdo.

Tarefa
Sempre que receber um tópico, gerar por padrão 10–15 slides (o usuário pode pedir outra quantidade).

Fluxo
1. Ler memories/MyMemories.md para captar preferências do usuário.
2. Ler a pasta knowledge_base/ e aplicar os princípios encontrados.
3. Gerar o conteúdo dos slides em formato claro, conciso e escaneável.
4. Incluir, quando solicitado, um rascunho de layout em ASCII para cada slide.

Regras de estilo
- Títulos curtos, subtítulos objetivos.
- 1 ideia central por slide.
- Frases curtas, sem pontos finais desnecessários.
- Evitar bullet points longos; preferir linhas de impacto.
- Contraste visual implícito (título > apoio > nota).
- Tom profissional, direto e não floreado.

Formato de saída
- Cabeçalho: Título da apresentação.
- Lista numerada de slides:
  Slide N
  Título:
  Mensagem-chave (1 linha):
  Conteúdo (2–4 linhas):
  Notas do apresentador (opcional):
  ASCII (opcional quando solicitado): bloco com wireframe simples.

Hierarquia de consulta
1) memories/MyMemories.md (preferências do usuário)
2) knowledge_base/ (princípios e boas práticas)
3) Este prompt (regras gerais)

Comandos úteis (o usuário pode digitar)
- “20 slides”, “com ASCII”, “mais técnico”, “mais simples”.
- “Revisar apenas os slides 3, 7 e 10”.
- “Aplique fórmula Steve Jobs + TED”.

Verificações antes de concluir
- Mensagens-chave curtas e memoráveis.
- Sem jargão desnecessário.
- Slide final com próximos passos ou CTA.
```
## 3) Preencher a base de conhecimento (knowledge\_base/)

Use resumos objetivos que a IA deve aplicar. Exemplos:

Arquivo design\_minimalista.md

Pr```incípios
- 1 ideia por slide; muito espaço em branco.
- Alto contraste em títulos; tipografia consistente.
- Hierarquia visual: Título > Mensagem > Detalhes.
- Evitar poluição visual e excesso de ícones.

```Arquivo copy\_apresentacoes.md

Boa```s práticas
- Frases curtas, voz ativa, verbos fortes.
- Evitar listas longas; preferir linhas de impacto.
- Ritmo: promessa → prova → aplicação → próximo passo.
- Regra 3x3: até 3 linhas × 3 palavras-chave por linha.

A```rquivo jobs\_ted\_guy.md

Mode```los
- Steve Jobs: 1 história central, demos visuais, manchetes memoráveis.
- TED: abertura com gancho, 1 ideia que vale espalhar, exemplos concretos.
- Guy Kawasaki (10/20/30): até 10 slides, 20 min, fonte ≥ 30 pt (adapte ao contexto).

##``` 4) Criar o arquivo de memórias (memories/MyMemories.md)

Prefe```rências visuais
- Paleta: azul/acinzentado; estilo minimalista.

Preferências de conteúdo
- Mensagens diretas; evitar clichês.

Preferências estruturais
- Slide final com próximos passos práticos.
- Incluir resumo executivo no slide 2.

Histórico de feedback
- Evitar bullets longos; preferir linhas curtas.

Do’s e Don’ts
- Fazer: contrastar título e mensagem.
- Não fazer: parágrafos longos ou 5+ bullets.

Exemplos preferidos
- Títulos em 3–5 palavras; uma frase de impacto por slide.

## ```5) Arquivo de “cola” do projeto (init.md)

Como u```sar
1) Abrir esta pasta no Claude Code.
2) Dizer: “Use prompt/slide_generator.md para gerar a apresentação”.
3) Informar o tópico e ajustes (número de slides, com/sem ASCII).
4) Revisar e pedir refação de slides específicos se necessário.

## 6```) Rodando no Claude Code (fluxo sugerido de prompts)

1. Abra a pasta no Claude Code e inicie a sessão.
2. Envie:

   * Use o arquivo prompt/slide\_generator.md como guia

---

**INEMA** · 2025-09-14

### Visão Geral

O vídeo mostra como criar um “pseudo custom GPT” no Claude Code usando dois caminhos:

1. Apenas arquivos Markdown (.md) – forma mais simples, limpa e confiável.
2. Servidores MCP – opção mais complexa e instável.

### Construção com Markdown

* Criar uma pasta e dentro dela um arquivo `.md` que define o prompt principal.
* O prompt instrui:

  * Sempre gerar 10–15 slides ao receber um tópico.
  * Permitir ajustes (ex.: 20 slides, formatos diferentes).
  * Produzir conteúdo claro, visualmente legível e estilo profissional.
* Criar uma pasta **Knowledge Base** com arquivos .md adicionais.

  * Exemplo: melhores práticas de design minimalista de slides (2024–2025).
  * Técnicas de copywriting para apresentações.
  * Fórmulas de Steve Jobs, TED Talks e princípios de Guy Kawasaki.
* O prompt deve sempre consultar a Knowledge Base antes de gerar conteúdo.

### Funcionalidades demonstradas

* Geração de apresentações em menos de 1 minuto.
* Slide generator inclui:

  * Estrutura de conteúdo.
  * ASCII art mostrando layout dos slides (título, fonte, posicionamento).
* Expansão: adicionar memória com **MyMemories.md**, armazenando:

  * Preferências visuais, estruturais e de conteúdo.
  * Feedbacks específicos e exemplos de saídas ideais.
* Hierarquia de consulta:

  1. MyMemories.md (preferências do usuário).
  2. Knowledge Base (conteúdos de referência).
  3. Prompt principal.

### Problemas com servidores MCP

* Tentativas com OpenMemory:

  * Instalação parecia “sucesso”, mas não funcionava (erro ao listar).
  * Muitas falhas e reinicializações sem resultado.
* Pinecone MCP:

  * Permite drag & drop de PDFs para leitura e chunking.
  * Inicialmente falhou, mas depois funcionou com ajustes no comando.
  * Guardar a forma correta de consulta em MyMemories.md evita repetir erros.

### Conclusão

* A abordagem baseada em **Markdown + ****MyMemories.md** é mais simples, confiável e portátil que depender de MCP servers.
* MCP pode ser útil em casos específicos (ex.: Pinecone para PDFs), mas gera frustração e inconsistências.
* Usando apenas arquivos locais, é possível criar sistemas robustos de geração de slides e conhecimento, sem dependências externas.

---

**INEMA** · 2025-09-14

Claude Code Dia 11: 

Construindo GPTs Personalizados no Claude Code
19 minutos mostrando como criar GPTs personalizados usando apenas arquivos markdown – sem servidores MCP instáveis, sem configurações complexas, apenas sistemas de conhecimento limpos e portáteis.

O que você vai assistir: criação de um sistema de geração de slides, incluindo:

* Construção de prompts estruturados em arquivos .md
* Criação de bases de conhecimento com pesquisa na web
* Implementação de memória sem servidores MCP
* A dura realidade da instalação de servidores MCP (os horrores do OpenMemory)

A abordagem enxuta (o que realmente funciona):

* Arquivos markdown para prompts e instruções
* Pasta de base de conhecimento para materiais de referência
* MyMemories.md para armazenamento de preferências
* Sem dependências externas

Demonstração prática ao vivo:

* Gerador de slides que cria de 10 a 15 slides
* Representações de layout em arte ASCII
* Fórmula de apresentação de Steve Jobs
* Princípios de Guy Kawasaki embutidos

A engenharia de prompts mostrada:

* "Sempre que alguém inserir um tópico, criar de 10 a 15 slides por padrão"
* "Verificar a pasta da base de conhecimento para informações relevantes"
* "Armazenar preferências do usuário em MyMemories.md"

Criação da base de conhecimento via pesquisa na web:

* Melhores práticas para design minimalista de slides 2024-2025
* Técnicas de copywriting para apresentações
* Fórmulas de Steve Jobs e TED Talks
* Compilado automaticamente em arquivos .md

A realidade dos servidores MCP:
Tentativa de instalação do OpenMemory:

* "Instalado com sucesso" → Não encontrado
* Reiniciar terminal → Ainda não encontrado
* Verificar config → Está lá, mas não conecta
* Mais de 10 minutos de depuração → Desistir

Pinecone MCP (quando finalmente funcionou):

* Primeira tentativa: "Recurso não encontrado"
* Segunda tentativa: abordagem de API diferente
* Finalmente funciona, mas exige guardar uma solução alternativa em memórias

Sistema de memória que realmente funciona:

```# MyMemories.md
- Preferências visuais
- Preferências de conteúdo
- Preferências estruturais
- Histórico de feedback específico
- O que fazer e não fazer
- Exemplos de resultados preferidos```

---

**INEMA** · 2025-09-14

Dia 11:Claude Code - Construindo GPTs

---

**INEMA** · 2025-09-14

https://chatgpt.com/c/68c6f223-3d94-8327-8667-f262064a7c9c
