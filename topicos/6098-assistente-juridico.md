# Assistente Juridico

> Tópico 6098 · 5 mensagens úteis de 15 totais

---

**INEMA** · 2026-05-23

Você coloca o documento **no seu próprio computador/projeto**, e passa o **caminho do arquivo** no comando.

Exemplo:

```/legal review contrato.pdf```

ou, se estiver em uma pasta:

```/legal review ./documentos/contrato.pdf```

Ele **não parece “varrer uma pasta automaticamente” sozinho**. Pelo que o projeto mostra, os comandos recebem um **arquivo específico**, uma **URL** ou texto colado, dependendo do comando. Por exemplo, o skill de comparação é ativado com `/legal compare <file1> <file2>`, onde cada entrada pode ser caminho de arquivo, URL ou texto colado. ([RuleSkill][1])

Então o fluxo seria:

1. Instalar o projeto no Claude Code.
2. Abrir o Claude Code dentro da pasta onde estão seus documentos, ou informar o caminho completo.
3. Rodar algo como:

```/legal review contrato-cliente.pdf```

ou

```/legal risks contrato-cliente.docx```

O README diz que ele instala skills, agentes e scripts para o Claude Code, incluindo revisão de contratos, análise de riscos e geração de relatórios PDF. 

Se você quer que ele analise **todos os PDFs de uma pasta**, provavelmente teria que criar um script ou adaptar o comando para rodar em lote, por exemplo:

```for file in ./contratos/*.pdf; do
  claude "/legal review $file"
done```

Mas isso já seria uma automação extra; o projeto, pelo que aparece, trabalha principalmente com **um documento por comando**.

---

**INEMA** · 2026-05-23

Esse projeto é um **assistente jurídico para Claude Code**. Ele instala um conjunto de “skills” e agentes para analisar contratos, gerar documentos legais simples e criar relatórios em PDF. O README descreve o objetivo como: revisar contratos, apontar riscos, gerar NDAs, checar compliance, sugerir estratégias de negociação e produzir relatórios prontos para cliente.  

Na prática, ele oferece comandos como:

* `/legal review <file>`: revisão completa de contrato, com pontuação de segurança, análise cláusula por cláusula e recomendações.
* `/legal risks <file>`: análise profunda de riscos e possível exposição financeira.
* `/legal compare <file1> <file2>`: comparação entre duas versões de contrato.
* `/legal plain <file>`: tradução de “juridiquês” para linguagem simples.
* `/legal negotiate <file>`: gera contrapropostas e textos alternativos para cláusulas desfavoráveis.
* `/legal nda <description>`: gera NDA.
* `/legal terms <url>` e `/legal privacy <url>`: gera termos de uso e política de privacidade para sites.
* `/legal compliance <url>`: checa lacunas de compliance como GDPR, CCPA, ADA, PCI-DSS, CAN-SPAM e SOC 2.
* `/legal report-pdf`: gera relatório profissional em PDF.  

O diferencial anunciado é o comando `/legal review`, que roda **5 agentes em paralelo**: analista de cláusulas, avaliador de riscos, verificador de compliance, mapeador de obrigações e motor de recomendações. Esses resultados são agregados em um relatório único com um “Contract Safety Score”. 

Tecnicamente, o repositório tem pastas para `skills`, `agents`, `scripts`, `templates` e um instalador `install.sh`. Ele depende de **Claude Code**, uma chave ativa da Anthropic, Python 3.8+ e `reportlab` para geração de PDF.  

Importante: ele **não é um advogado** nem substitui assessoria jurídica. O próprio projeto diz que é apenas para fins educacionais/informativos e recomenda revisão por advogado qualificado antes de assinar qualquer contrato.

---

**INEMA** · 2026-05-23

https://github.com/zubair-trabzada/ai-legal-claude

---

**INEMA** · 2026-05-23

**Assistente jurídico para Claude Code**

---

**INEMA** · 2026-05-23

https://chatgpt.com/c/6a122ec4-7b40-8327-8915-ea285f085168
