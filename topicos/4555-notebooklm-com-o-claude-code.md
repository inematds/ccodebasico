# NotebookLM com o Claude Code

> Tópico 4555 · 6 mensagens úteis de 17 totais

---

**INEMA** · 2026-04-03

Aqui está o **passo a passo** do que o vídeo ensina: 

1. **Baixar a skill de integração com NotebookLM**
   O autor fornece uma skill pronta para conectar o Claude ao NotebookLM. A ideia é instalar essa skill primeiro no Claude Code. 

2. **Enviar a skill para o Claude e executar**
   No Claude, você arrasta o arquivo da skill e pede algo como “execute esta skill”. Isso inicia o processo de instalação. 

3. **Fazer login no NotebookLM**
   Durante a instalação, abre-se o navegador para você entrar na sua conta do NotebookLM. A skill captura a autenticação necessária para que o Claude consiga interagir com seus notebooks. 

4. **Testar se a conexão funcionou**
   Depois da autenticação, você pode pedir ao Claude algo como: listar seus últimos notebooks ou baixar um ativo gerado no NotebookLM. Se ele conseguir fazer isso, a integração está funcionando. 

5. **Gerar uma versão da skill para o Claude Co-work**
   Como Claude Code e Co-work são ambientes diferentes, o vídeo mostra pedir ao Claude Code para criar um arquivo de skill compatível com o Co-work. 

6. **Subir essa skill no Claude Co-work**
   No Co-work, você vai em **Skills > Manage Skills > Upload a Skill** e envia o arquivo gerado. Depois disso, o Co-work também passa a acessar o NotebookLM. 

7. **Usar o NotebookLM para enriquecer projetos**
   Em uma conversa ou projeto, você pede ao Claude para criar um novo notebook com base na conversa, no contexto do projeto e em outros materiais disponíveis. Depois, pede que ele devolva insights resumidos e ações práticas. 

8. **Abrir o notebook criado e verificar as fontes**
   O vídeo recomenda conferir se o NotebookLM realmente importou os materiais e pesquisas. Se algo falhar ou der timeout, basta pedir ao Claude para garantir a importação antes de continuar. 

9. **Usar o NotebookLM para gerar ativos**
   Além de resumir e pesquisar, você pode pedir ao Claude para usar o NotebookLM para criar coisas como infográficos, apresentações, materiais de apoio e outros ativos visuais. 

10. **Instalar a segunda skill, chamada “wrap-up”**
    Essa skill serve para salvar conversas longas no NotebookLM como memória de longo prazo. A lógica é: terminou uma sessão importante, ativa o wrap-up. 

11. **Criar um notebook central, tipo “seu cérebro”**
    O vídeo sugere manter um notebook principal, onde os resumos das sessões vão sendo armazenados. Assim, decisões, contexto, estratégia e conhecimento acumulado ficam centralizados. 

12. **Consultar esse notebook nas próximas sessões**
    Depois, em novos projetos ou conversas, você orienta o Claude a sempre consultar esse notebook central quando for responder sobre estratégia, decisões ou contexto anterior. Isso evita reconstruir tudo do zero. 

13. **Resultado esperado**
    Com isso, o Claude passa a usar o NotebookLM como memória persistente e mecanismo de busca semântica. Segundo o vídeo, isso reduz custo com tokens, melhora continuidade entre sessões e amplia as capacidades de pesquisa e produção.

---

**INEMA** · 2026-04-03

https://www.youtube.com/watch?v=6t32nPxeJb8

---

**INEMA** · 2026-04-03

Como combinar o Claude com o Google NotebookLM para criar uma espécie de “memória infinita” de baixo custo. A ideia central é usar o NotebookLM como camada de memória e pesquisa persistente, resolvendo o problema de o Claude “esquecer” contexto entre sessões e consumir muitos tokens ao reler arquivos.O 

Aqui Dois usos principais. O primeiro é conectar Claude Code ou Claude Co-work ao NotebookLM por meio de uma skill, permitindo acessar cadernos, buscar informações, baixar ativos e reaproveitar contexto de forma mais eficiente. O segundo é usar essa integração para enriquecer análises e gerar ativos como infográficos, resumos estratégicos, pesquisas profundas e materiais de apoio, sem depender tanto do contexto interno do Claude.

Também é apresentado um “wrap-up skill”, que salva o conteúdo de conversas longas no NotebookLM como memória de longo prazo. Assim, sessões anteriores podem ser recuperadas depois por busca semântica, sem inflar a janela de contexto. A proposta é transformar o NotebookLM em um “segundo cérebro” para projetos, decisões, CRM pessoal, reuniões, onboarding e conhecimento institucional.

Em essência, a mensagem é que essa integração melhora memória, reduz custos com tokens, amplia capacidades práticas do Claude e permite criar um sistema mais duradouro para trabalho, pesquisa e produção de conteúdo.

---

**INEMA** · 2026-04-03

https://github.com/teng-lin/notebooklm-py

---

**INEMA** · 2026-04-03

NotebookLM  com o Claude Code

---

**INEMA** · 2026-04-03

https://chatgpt.com/c/69cf5d8f-0514-8327-b837-dc4ff0731cee
