# /fork /by-the-way e Contexto fork

> Tópico 4072 · 3 mensagens úteis de 11 totais

---

**INEMA** · 2026-03-21

terminais ao mesmo tempo,
* tarefas paralelas,
* cada uma com seu próprio gerenciamento de contexto.

A ideia é combinar:

* paralelismo,
* forks,
* e separação de contexto
  para obter o máximo do Claude Code.

---

### 7. Boas práticas adicionais

Além desses 3 recursos, ele recomenda:

* manter o **`claude.md` enxuto**,
* evitar colocar informação demais nesse arquivo,
* usar regras para evitar inflar desnecessariamente o contexto.

Ou seja, os três recursos ajudam muito, mas fazem parte de uma disciplina maior de **higiene de contexto**.

---

### Conclusão 

A mensagem central é:

> Para usar bem o Claude Code em tarefas longas, você precisa gerenciar contexto ativamente.

Os **3 hábitos principais** que recomenda são:

* usar **`context fork`** em skills pesadas,
* usar **`****/by****-the-way`** para perguntas secundárias,
* usar **`****/fork****`** para explorar caminhos alternativos sem bagunçar a conversa principal.

O resultado é:

* menos ruído,
* menos desperdício de contexto,
* melhores respostas,
* mais controle sobre projetos longos.

---

**INEMA** · 2026-03-21

Em sessões longas no **Claude Code**, a qualidade percebida tende a cair não porque o modelo “fica pior”, mas porque o **contexto vai ficando poluído**. Leituras de arquivos, buscas, perguntas paralelas e tentativas sem sucesso ocupam espaço na janela de contexto e reduzem a clareza do modelo.

A solução apresentada é combinar **3 recursos** para manter o foco:

1. **`****/by****-the-way`**
2. **`****/fork****`**
3. **`context fork` em arquivos `skill.md`**

---

### 1. O problema central: excesso de contexto

Ao longo de uma sessão longa, o Claude acumula:

* leituras de arquivos,
* resultados de busca,
* perguntas secundárias,
* tentativas que deram errado.

Isso gera “ruído” dentro da janela de contexto. O modelo continua sendo o mesmo, mas passa a ter **menos espaço útil** para raciocinar sobre a tarefa principal.

---

### 2. `context fork` em `skill.md`

Esse é o recurso mais novo e o destaque 

#### Ideia principal

Ao adicionar **uma linha** no `skill.md`, uma skill pode rodar em **uma janela de contexto separada**.

#### O que isso resolve

Sem `context fork`:

* a skill faz pesquisas,
* usa ferramentas,
* traz notas brutas,
* e todo esse material vai parar no contexto principal.

Com `context fork`:

* outra instância do Claude faz o trabalho pesado em separado,
* executa buscas e tool calls fora do contexto principal,
* e devolve apenas **um resumo limpo**.

#### Benefício

Isso reduz o desperdício de tokens e evita que tarefas pesadas contaminem o fluxo principal.

---

###  Exemplo prático: criar uma apresentação

Ele usa um prompt para pedir ao Claude:

* buscar notas sobre **automação de workflow com IA para pequenos times**,
* e com isso montar uma **apresentação em PowerPoint**.

#### O que acontece

A skill roda em contexto separado, faz suas buscas e só devolve o necessário. Depois o Claude usa esse resultado para gerar os slides.

#### Vantagem observada

Se comparar o uso de `/context` antes e depois, ainda haverá consumo de tokens, mas **bem menor** do que seria sem `context fork`, especialmente em skills pesadas.

---

### 3. `/by-the-way` para perguntas paralelas

Esse comando serve para fazer perguntas auxiliares sem poluir a tarefa principal.

#### Exemplos do vídeo

* “Quantos slides usei no meu último workshop?”
* “Qual costuma ser a duração padrão do workshop?”
* “Qual é o link do Calendly que quero mandar para o cliente?”

#### Benefício

Essas perguntas:

* não desviam a conversa principal,
* não enchem o contexto com detalhes irrelevantes,
* ajudam a recuperar informação útil “de passagem”.

Isso funciona bem para dados guardados em arquivos como o `claude.md`.

---


### 4. `/fork` para criar uma ramificação da conversa

Esse comando cria uma **subconversa** a partir do ponto atual.

#### Como funciona

* você executa `/fork`,
* o sistema cria um novo caminho da conversa,
* fornece um identificador/oneliner para retornar ao estado anterior em outro terminal, se quiser.

#### Para que serve

Permite explorar uma nova direção sem estragar o fluxo principal.

No exemplo:

* a apresentação V1 existe,
* ele quer experimentar uma **V2 completamente diferente**,
* então cria um fork e segue por esse caminho novo.

---

###  Refazer a apresentação em uma nova direção

Dentro do fork, ele pede uma nova versão:

* com o mesmo número de slides,
* mas com abordagem visual e conceitual diferente.

No começo ele é vago, o Claude pede mais clareza, e então ele explica melhor que quer reimaginar tudo mantendo a estrutura geral.

#### Resultado

A **V2** pode ficar:

* muito melhor,
* mais limpa,
* mais clara,
* mais polida,
* com mais impacto visual.

---

### 5. Valor prático do `/fork`

O ponto não é só criar versões alternativas, mas permitir **exploração segura**.

Com o fork, você pode:

* testar caminhos arriscados,
* experimentar ideias,
* evitar que tentativas malsucedidas contaminem a conversa principal.

Se a nova versão for boa, você continua nela.
Se não for, a conversa original continua intacta.

---

### 6. Uso em múltiplos terminais e paralelo

Isso fica ainda mais poderoso quando você usa:

* vários

---

**INEMA** · 2026-03-21

https://chatgpt.com/c/69bddf83-97a4-8326-8e36-1835b450ad36
