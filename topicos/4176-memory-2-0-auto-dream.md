# Memory 2.0 - Auto Dream

> Tópico 4176 · 7 mensagens úteis de 23 totais

---

**INEMA** · 2026-03-26

https://youtu.be/wy9buu5wDhg

---

**INEMA** · 2026-03-25

Pelo que foi descoberto no código, o dream roda por projeto — ele consolida apenas os arquivos de memória do diretório .claude/projects/<projeto>/memory/ da sessão 
  onde foi disparado.                          
                                                                                                                                                                      
  Ou seja, com 140 projetos, ele só vai processar o projeto que você estiver usando na sessão que atingir as condições (5+ sessões, 24h+ desde o último dream). Não   
  roda em todos de uma vez.                                                                                                                                           
                                                                                                                                                                      
  Na prática, os projetos que você mais usa vão ser consolidados primeiro. Os que raramente abre provavelmente nunca vão disparar o dream automaticamente.

---

**INEMA** · 2026-03-25

Isso é consistente com o que a comunidade reportou — o feature flag parece estar sendo liberado gradualmente. Se você conseguiu ativar no /memory, provavelmente o  
  flag foi habilitado para sua conta por um tempo e depois revertido (rollout parcial/A-B testing).
                                                                                                                                                                      
  O /dream como slash command não é algo que você executa manualmente — ele roda automaticamente em background quando:                                                
  - Passaram 24h+ desde o último dream                                                                                                                                
  - Acumularam 5+ sessões                                                                                                                                             
                                                                  
  Se você ativou o toggle e ele ainda aparece como "on" no /memory, ele deve rodar sozinho quando as condições forem atendidas. O fato do /dream ter sumido da lista  
  de comandos sugere que a Anthropic está ajustando o rollout.                                                                                                        
   
  Não há nada que possamos fazer do nosso lado para forçar — é controlado server-side.

---

**INEMA** · 2026-03-24

Foi lançado o **Memory 2.0 com AutoDream** no Claude Code.**

Como us**ar

abrir **/memory**
ativar o **AutoDream**
rodar manualmente com **/dream** quando disponível
em alguns casos ele também pode ser acionado por linguagem natural

**Local x global**

a **memória fica ligada globalmente**
mas os **arquivos de memória são locais por projeto**
ou seja: o recurso existe em todos os projetos, porém cada projeto mantém suas próprias memórias e seu próprio histórico de consolidação

O **que ele faz

**revisa sessões passadas
consolida informações importantes
remove excessos
atualiza e compacta os arquivos de memória

Re**sultado

**arquivos de memória ficam **mais limpos, curtos e úteis**
o sistema mostra **quais memórias foram atualizadas**
também pode mostrar **o que foi adicionado e o que foi removido**
isso melhora a continuidade entre sessões, reduz repetição e diminui contexto inchado

---

**INEMA** · 2026-03-24

atingir determinada quantidade de sessões.

Claro que isso é uma inferência baseada em discussões no X/Twitter e Reddit, não em documentação oficial.

### 13. Estados possíveis do recurso

O sistema pode mostrar:

* que está rodando;
* que nunca rodou;
* quando rodou pela última vez;
* ou ficar ocioso, sem tarefas em andamento.

### 14. O que ele altera — e o que não altera

* O AutoDream **só mexe nos arquivos de memória**.
* Ele **não altera código, scripts ou lógica do projeto**.
* No exemplo, as alterações foram em arquivos `.md`.

### 15. Camadas do sistema no Claude Code

Uma visão se propõe em três camadas:

* **Sessões normais**
  Onde você conversa, programa, depura e refatora.

* **AutoMemory**
  Registra decisões, padrões e contexto importante do projeto/usuário.

* **AutoDream**
  Faz a manutenção automática dessa memória:
  limpa, compacta, reorganiza e melhora tudo em segundo plano.

### 16. Resultado após a execução

Depois de concluir:

* o sistema informa quantos arquivos de memória foram atualizados;
* mostra entradas adicionadas e seções removidas;
* o usuário pode revisar, restaurar ou editar manualmente, se quiser.

### 17. Aprendizado progressivo

A expectativa apresentada  é que, com o uso contínuo:

* o AutoDream fique melhor em distinguir

  * o que é contexto importante;
  * o que pode ser descartado.

## Conclusão 

A tese central é que o **AutoDream pode tornar o Claude Code mais consistente entre sessões**, com memória mais limpa, útil e durável. A promessa é menos repetição, menos contexto inflado e uma experiência mais próxima de trabalhar com um sistema que “lembra de você” de forma organizada, em vez de apenas acumular histórico bruto.

---

**INEMA** · 2026-03-24

**Memory 2.0 / AutoDream no Claude Code**:

## Resumo geral

O novo recurso experimental do Claude Code chamado **AutoDream**, que funciona como um processo automático de consolidação da memória do sistema. A ideia é parecida com o sono humano: periodicamente, o sistema revisa sessões anteriores, organiza o que aprendeu, remove excessos e mantém apenas o que é mais útil para o futuro.

## Tópicos abordados

### 1. O que é o AutoDream

* É um recurso novo e ainda em rollout/experimental.
* Ele executa um tipo de **subagente em segundo plano** para revisar e reorganizar arquivos de memória.
* O objetivo é melhorar o **armazenamento de memória de longo prazo**.

### 2. Comparação com memória humana

* A analogia com o sono:

  * humanos consolidam memórias enquanto dormem;
  * o Claude faria algo parecido ao “sonhar” para reorganizar o que aprendeu.

### 3. Como o recurso aparece na prática

O status exibe **“dreaming”** quando o processo está rodando.
* Ao abrir as tarefas, dá para ver que ele:

  * procura feedbacks e preferências do usuário;
  * revisa sessões recentes;
  * identifica informações relevantes do projeto;
  * consolida tudo nos arquivos de memória.

### 4. O que o processo faz

* Lê várias sessões anteriores.
* Revisa arquivos de memória existentes.
* Consolida descobertas novas.
* **Mescla, poda, atualiza e compacta** os conteúdos.
* Melhora a organização dos arquivos `.md` de memória.

### 5. Diferença entre AutoMemory e AutoDream

* **AutoMemory** já existia e grava contexto do projeto em arquivos como `memory.md`.
* Esse conteúdo costuma ser injetado no começo das sessões para dar contexto ao Claude.
* **AutoDream** vai além:

  * não apenas adiciona memória;
  * ele **limpa, compacta, reorganiza e melhora** continuamente essas memórias.

### 6. Benefícios esperados

Quatro ganhos principais:

* **Menos repetição**
  O usuário precisa reexplicar menos coisas entre sessões.

* **Menos bloat (inchaço)**
  O sistema remove excesso de informação e reduz “gordura” contextual.

* **Melhor recall**
  Fica mais fácil recuperar o que importa porque há menos ruído.

* **Contexto mais limpo e útil**
  Em vez de centenas de linhas desnecessárias, ficam só os pontos duráveis e relevantes.

### 7. Onde ativar e usar

* O caminho é **`****/memory****`**.
* Dentro dessa área aparece a opção de editar arquivos de memória do Claude.
* O usuário pode ver:

  * se o AutoDream está ligado;
  * quando foi executado pela última vez;
  * se nunca rodou.
* Também é citado o comando **`****/dream****`** para tentar executar manualmente.

### 8. Comportamento confuso da execução manual

* Em alguns casos, digitar **`****/dream****`** retorna algo como **“unknown skill”**.
* Mesmo assim, o sistema parece começar o processo em segundo plano.
* Também é possível acionar com linguagem natural, como “run your autodream”.

### 9. Escopo por projeto

* A memória parece estar **ativada globalmente**, mas cada projeto tem seus **próprios arquivos de memória**.
* Em projetos diferentes, o AutoDream trabalha sobre conjuntos diferentes de arquivos.
* Em alguns projetos ele já rodou; em outros aparece como nunca executado.

### 10. Tempo de execução

* Em exemplos , o processo levou cerca de **8 a 10 minutos**.
* Um projeto pequeno revisou cerca de **13 sessões**.
* Um projeto maior revisou cerca de **285 sessões**.
* Mesmo com mais sessões, o tempo não aumentou tanto quanto o esperado.

### 11. Como o AutoDream provavelmente funciona internamente

Um fluxo assim:

1. Coleta informações das sessões.
2. Lê os arquivos de memória atuais.
3. Envia isso para um subagente com um “dream prompt”.
4. Esse prompt pede para:

   * sintetizar aprendizados recentes;
   * transformar isso em memórias duráveis e organizadas;
   * manter limites de tamanho;
   * tratar `memory.md` como índice, não como despejo completo de dados.
5. Depois disso, o sistema:

   * consolida;
   * poda;
   * salva o resultado final.

### 12. Gatilhos possíveis do AutoDream

Algumas hipóteses, mas sem confirmação oficial:

* **Por tempo**
  Ex.: a cada 12 horas.

* **Por número de sessões**
  Ex.: ao

---

**INEMA** · 2026-03-24

https://chatgpt.com/c/69c2f7ed-18bc-8332-888a-bae7910066a2
