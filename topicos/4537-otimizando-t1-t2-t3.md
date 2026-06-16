# OTIMIZANDO T1, T2, T3

> Tópico 4537 · 3 mensagens úteis de 13 totais

---

**INEMA** · 2026-04-03

# NÍVEL 1

## 1. Começar chats novos

* separa assuntos diferentes
* reduz histórico acumulado
* evita releitura desnecessária
* baixa custo por mensagem
* prolonga a sessão

## 2. Desconectar MCPs não usados

* corta contexto invisível
* reduz definições carregadas
* economiza tokens por turno
* deixa o ambiente mais leve
* evita overhead desnecessário

## 3. Agrupar pedidos em uma mensagem

* evita múltiplos turnos
* reduz releitura do histórico
* concentra instruções no mesmo prompt
* diminui custo acumulado
* melhora eficiência da sessão

## 4. Usar Plan Mode antes de executar

* define caminho antes de agir
* evita retrabalho
* reduz erros de direção
* economiza código descartado
* aumenta assertividade

## 5. Usar `/context` e `/cost`

* mostra consumo atual
* revela fontes de gasto
* expõe peso do histórico
* ajuda a corrigir excessos
* dá visibilidade real

## 6. Configurar status line

/statusline
* acompanha uso em tempo real
* mostra contexto ocupado
* ajuda a prever limite
* melhora monitoramento
* evita surpresas

## 7. Manter o dashboard aberto

* facilita acompanhar o limite
* ajuda a dosar uso
* mostra proximidade do reset
* melhora tomada de decisão
* evita bloqueio inesperado

## 8. Colar só o trecho necessário

* reduz volume de contexto
* evita arquivos inteiros sem necessidade
* deixa o prompt mais preciso
* melhora foco da análise
* economiza tokens

## 9. Observar o Claude trabalhando

* detecta desvios cedo
* interrompe loops inúteis
* evita saídas ruins longas
* reduz desperdício de sessão
* melhora controle da execução

---

# NÍVEL 2

## 10. Manter o `claude.md` enxuto

* reduz contexto fixo
* evita instruções inchadas
* deixa regras mais claras
* melhora carregamento recorrente
* economiza tokens em todo turno

## 11. Referenciar arquivos com precisão

* aponta o alvo certo
* evita exploração ampla do projeto
* reduz leitura desnecessária
* acelera a resposta
* melhora a qualidade do foco

## 12. Compactar por volta de 60%

* preserva contexto útil
* evita degradação tardia
* reduz acúmulo excessivo
* melhora continuidade
* prolonga qualidade da sessão

## 13. Evitar pausas longas sem limpar

* evita perda de cache
* reduz reprocessamento total
* controla picos de custo
* melhora retomada do trabalho
* impede gasto inesperado

## 14. Cuidar de outputs grandes de comandos

* evita inserir muito texto no contexto
* reduz poluição da conversa
* corta custo invisível
* melhora legibilidade
* mantém foco no essencial

---

# NÍVEL 3

## 15. Escolher o modelo certo

* Sonnet para padrão
* Haiku para tarefas leves
* Opus para profundidade
* reduz custo desnecessário
* equilibra qualidade e gasto

## 16. Usar subagentes com moderação

* eles custam mais
* recarregam contexto próprio
* são úteis em casos pontuais
* funcionam melhor com objetivo claro
* exigem uso estratégico

## 17. Aproveitar horários fora de pico

* sessões rendem melhor
* uso pesado fica mais eficiente
* reduz drenagem acelerada
* melhora aproveitamento do plano
* ajuda no planejamento de tarefas

## 18. Usar o `claude.md` como constituição

* guarda decisões estáveis
* reduz repetição futura
* encurta prompts
* mantém regras importantes salvas
* melhora consistência entre sessões

---

**INEMA** · 2026-04-03

**Tier 1**

1. **Começar conversas novas** para tarefas não relacionadas (`/clear`).
2. **Desconectar servidores MCP** que não estiver usando.
3. **Agrupar vários pedidos em uma única mensagem**.
4. **Usar plan mode antes de tarefas reais** para evitar retrabalho.
5. **Usar `****/context****` e `****/cost****`** para enxergar de onde vêm os tokens.
6. **Configurar uma status line** no terminal para acompanhar uso/contexto.
7. **Manter o dashboard aberto** para monitorar o limite.
8. **Ser inteligente ao colar conteúdo**: mandar só o trecho necessário.
9. **Observar o Claude trabalhando** para interromper loops ou caminhos errados cedo. 

**Tier 2**
10. **Manter o arquivo `claude.md` enxuto**.
11. **Ser cirúrgico nas referências de arquivos**: apontar função/arquivo exato.
12. **Compactar a conversa por volta de 60% da capacidade**, não só no automático.
13. **Evitar pausas longas sem limpar/compactar**, porque o cache expira.
14. **Tomar cuidado com saída de comandos**, porque output grande também vira contexto. 

**Tier 3**
15. **Escolher o modelo certo para cada tarefa**

* Sonnet: padrão
* Haiku: subtarefas e tarefas simples
* Opus: planejamento profundo

16. **Entender o custo dos subagentes**, que podem gastar muito mais tokens.
17. **Entender os horários de pico e fora de pico** para planejar tarefas pesadas.
18. **Usar o `claude.md` como uma “constituição do sistema”**, guardando decisões estáveis, regras e resumos de progresso. 

Um **“hack 3.5”** dentro da dica sobre horários:

* **Se estiver perto do reset e ainda tiver saldo, usar pesado.**
* **Se estiver perto do limite e ainda faltar muito tempo, parar e voltar depois.**

---

**INEMA** · 2026-04-03

https://chatgpt.com/c/69cf2814-a7e4-8327-9860-7415a090bac8
