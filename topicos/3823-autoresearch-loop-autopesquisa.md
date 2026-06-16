# AutoResearch Loop - AutoPesquisa

> Tópico 3823 · 6 mensagens úteis de 22 totais

---

**INEMA** · 2026-03-15

https://youtu.be/4Cb_l2LJAW8?si=4GddKE1XkeCmeTVn

---

**INEMA** · 2026-03-15

git clone https://github.com/karpathy/auto-research.git

---

**INEMA** · 2026-03-15

Vou te mostrar **como instalar e usar o Auto Research (IA que se auto-aperfeiçoa)** de forma simples. 💻🤖

---

# 1️⃣ Pré-requisitos (instalar antes)

Você precisa ter instalado:

### 1. Python

Baixe:

* [https://www.python.org/downloads/](https://www.python.org/downloads/)

Verifique se instalou:

```python --version```

---

### 2. Git

Baixe:
[https://git-scm.com/downloads](https://git-scm.com/downloads)

Teste:

```git --version```

---

### 3. VS Code (opcional, mas recomendado)

Baixe:
[https://code.visualstudio.com/](https://code.visualstudio.com/)

---

# 2️⃣ Baixar o projeto (clone do repositório)

Abra o terminal e rode:

```git clone https://github.com/karpathy/auto-research.git```

Depois entre na pasta:

```cd auto-research```

---

# 3️⃣ Criar ambiente virtual

No terminal:

```python -m venv venv```

Ativar:

### Windows

```venv\Scripts\activate```

### Linux / Mac

```source venv/bin/activate```

---

# 4️⃣ Instalar dependências

Dentro da pasta do projeto:

```pip install -r requirements.txt```

---

# 5️⃣ Configurar API da IA

Você precisa de uma chave de IA, por exemplo:

### Claude

[https://console.anthropic.com/](https://console.anthropic.com/)

ou

### OpenAI

[https://platform.openai.com/](https://platform.openai.com/)

Crie um arquivo `.env`:

```ANTHROPIC_API_KEY=sua_chave_aqui```

ou

```OPENAI_API_KEY=sua_chave_aqui```

---

# 6️⃣ Criar seu experimento

No projeto existe um arquivo tipo:

```test.md```

Exemplo:

```Goal: melhorar taxa de resposta de emails

Metric: reply_rate

Method:
- gerar novas versões do email
- testar campanhas
- comparar resultados```

---

# 7️⃣ Rodar o sistema

Execute:

```python orchestrator.py```

Agora o agente vai:

1️⃣ criar experimento
2️⃣ testar
3️⃣ medir resultados
4️⃣ gerar nova versão
5️⃣ repetir

---

# 8️⃣ Automação (opcional)

Para rodar sozinho:

### usando cron (Linux/Mac)

```crontab -e```

exemplo:

```0 * * * * python orchestrator.py```

(rodar a cada hora)

---

# 🔥 Exemplo de coisas que você pode otimizar

* emails de vendas
* anúncios
* landing pages
* títulos de YouTube
* SEO
* preços
* copywriting
* prompts de IA

---

✅ **Resultado:**
a IA fica **testando melhorias sozinha 24h por dia**.

---

---

**INEMA** · 2026-03-15

laboratórios de IA **já usam esse tipo de sistema**.
* Agora qualquer pessoa pode aplicar isso:

  * em negócios
  * marketing
  * produtos
  * IA.

---

✅ **Resumo em uma frase:**

O vídeo mostra como usar um sistema de IA que **executa experimentos automaticamente para melhorar qualquer processo com métricas claras**, criando pipelines de otimização contínua sem intervenção humana.

---

**INEMA** · 2026-03-15

# 1. Ideia central: IA que se autoaperfeiçoa

* Andrej Karpathy lançou um projeto **open source chamado “Auto Research”**.
* A ideia é permitir que **um agente de IA experimente sozinho para melhorar um sistema**.
* O processo:

  1. IA modifica código ou parâmetros
  2. Treina/testa por alguns minutos
  3. Mede resultado com uma métrica
  4. Mantém ou descarta a mudança
  5. Repete o ciclo automaticamente

👉 Resultado: **o sistema melhora sozinho ao longo do tempo.**

---

# 2. Como funciona o ciclo de auto-melhoria

O processo segue um **loop experimental parecido com método científico**:

1. **Hipótese**

   * Fazer uma pequena mudança.

2. **Experimento**

   * Rodar teste automaticamente.

3. **Medição**

   * Avaliar resultado com uma métrica.

4. **Seleção**

   * Escolher o melhor resultado.

5. **Iteração**

   * Repetir o processo continuamente.

Quanto **mais rápido o loop**, mais rápido o sistema melhora.

---

# 3. Estrutura básica necessária

Para usar esse sistema, você precisa de **3 coisas**:

### 1️⃣ Uma métrica clara

Exemplos:

* Taxa de resposta
* Conversão
* Cliques
* Vendas
* Loss do modelo

### 2️⃣ Algo que possa ser modificado

Exemplos:

* Texto de email
* Landing page
* Parâmetros de modelo
* Criativos de anúncios

### 3️⃣ Acesso via API

Para que o agente possa:

* coletar dados
* alterar o sistema
* rodar novos testes automaticamente

---

# 4. Exemplo real mostrado no vídeo (Cold Email)

O autor usa o sistema para **otimizar emails de vendas**.

### Métrica

* **Reply rate (taxa de resposta)**

### O que muda

* Texto do email

### Processo

1. Criar versão **baseline**
2. Gerar **challenger** (variação)
3. Enviar os dois
4. Comparar resultados
5. O vencedor vira o novo baseline
6. Criar nova variação

Esse processo roda **automaticamente a cada 4 horas**.

---

# 5. Aprendizado acumulado

A IA registra aprendizados em um arquivo:

```resources.md```

Isso cria uma **base de conhecimento crescente**, que ajuda a gerar versões melhores no futuro.

---

# 6. Arquitetura do sistema

Componentes principais:

### Orchestrator

Agente principal que:

* coordena experimentos
* cria variações
* coleta métricas
* decide vencedor

### APIs

Para coletar dados (ex: Instantly API).

### Scripts auxiliares

* deploy
* coleta
* geração de testes

### GitHub Actions

Executa tudo automaticamente em intervalos.

---

# 7. Automação completa

O sistema funciona sozinho:

* cria experimentos
* testa versões
* coleta resultados
* gera novas versões
* repete o ciclo

💡 O criador nem precisa participar do processo.

---

# 8. Exemplos de aplicações

A técnica pode ser usada em **várias áreas**.

### Marketing

* Cold email
* Títulos de YouTube
* Subject lines de newsletter
* Landing pages
* Copy de anúncios
* SEO

### Negócios

* Pricing pages
* Descrição de produtos
* Scripts de atendimento
* Conversão de vendas

### IA e engenharia

* Treino de modelos
* Ajuste de hiperparâmetros

---

# 9. Vantagens do sistema

* roda **24h por dia**
* executa **centenas de testes**
* melhora continuamente
* elimina trabalho manual
* cria aprendizado acumulado

---

# 10. Limitações do método

Nem tudo funciona bem com esse sistema.

É necessário:

### 1️⃣ Feedback rápido

Exemplo ideal:

* testes em minutos ou horas

Não ideal:

* experimentos que demoram meses.

---

### 2️⃣ Métrica objetiva

Boa métrica:

* cliques
* conversão
* replies

Métrica ruim:

* “qualidade”
* “felicidade”
* coisas subjetivas.

---

### 3️⃣ Capacidade de alterar o sistema

Precisa ter:

* API
* automação
* acesso ao sistema

Sem isso o agente não consegue experimentar.

---

# 11. Configuração técnica resumida

Passos para usar o sistema:

1️⃣ Clonar o repositório Auto Research
2️⃣ Definir um teste (`test.md`)
3️⃣ Configurar métricas
4️⃣ Conectar APIs
5️⃣ Criar automação (ex: GitHub Actions)
6️⃣ Deixar rodando em loop.

---

# 12. Conceito importante

Isso é basicamente:

**Automação do método científico.**

Antes:

* humanos fazem experimentos

Agora:

* **IA faz milhares automaticamente**

---

# 13. Impacto

Segundo o autor:

* Grandes

---

**INEMA** · 2026-03-15

https://chatgpt.com/c/69b60e57-7018-8327-b52d-5231e39850fe
