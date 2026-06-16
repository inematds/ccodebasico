# Vazamento CLI 2026 - Fontes

> Tópico 4418 · 6 mensagens úteis de 16 totais

---

**Rui Oscar Muhlbach** · 2026-04-02

Pessoal me desculpem mas fiquei um pouco perdido e eu acabei perdendo de coletar no github os arquivos completos. Alguém pode me dar uma orientação?

---

**INEMA** · 2026-04-01

https://youtu.be/MS7Hj4tNBzY

---

**INEMA** · 2026-04-01

https://youtu.be/LsfAJcRwKR8

---

**INEMA** · 2026-04-01

O conteúdo explica que o Claude Code não deve ser visto apenas como um chatbot no terminal, mas sim como um sistema completo de agentes. A ideia central é que seu valor não está só nos prompts, mas principalmente na forma como ele organiza comandos, memória, permissões, contexto e integrações.

Um dos pontos principais é que existem muitos comandos internos úteis, e a maioria dos usuários aproveita só uma pequena parte deles. Comandos como `/init`, `/plan`, `/compact`, `/review`, `/context`, `/cost`, `/summary` e `/resume` ajudam a estruturar melhor o trabalho, planejar antes de executar, reduzir custo de contexto, revisar código e retomar sessões com mais eficiência.

Outro destaque é o arquivo `CLAUDE.md`, que funciona como uma espécie de manual operacional do projeto. Em vez de servir como documentação longa, ele deveria registrar regras práticas, padrões, restrições e convenções que orientam o comportamento do Claude Code em todas as sessões.

O texto também diz que a lentidão ou o excesso de confirmações muitas vezes não é problema de prompt, mas de permissões. A recomendação é configurar regras automáticas para ações recorrentes, evitando que o sistema peça autorização o tempo todo.

Além disso, o material sugere que a arquitetura foi pensada para trabalho multiagente, ou seja, para dividir tarefas complexas em etapas ou subtarefas paralelas, em vez de tentar resolver tudo com um único prompt enorme.

Também são destacados o MCP, plugins e skills como a verdadeira camada de extensão da ferramenta. Isso permitiria conectar o Claude Code a bancos de dados, APIs, ferramentas internas e fluxos repetitivos, tornando o sistema mais útil e adaptado ao contexto de uso.

Por fim, a conclusão é que usuários avançados não se destacam apenas por escrever prompts melhores, mas por montar um ambiente de operação melhor: manter o `CLAUDE.md` bem definido, dominar os comandos, ajustar permissões, dividir tarefas em fases, controlar contexto para economizar tokens e conectar ferramentas externas quando necessário.

---

**INEMA** · 2026-03-31

**aneiras de burlar as medidas de segurança e os pedidos de permissão.

Com**o o vazamento revelou a lógica exata de orquestração dos servidores Hooks e MCP, os atacantes agora podem projetar repositórios maliciosos especificamente adaptados para "enganar" o Claude Code, fazendo com que ele execute comandos em segundo pl`ano `ou exfiltre dados antes mesmo de você ver uma solicitação de confiança.

O perigo ma`is imediato, no entanto, `é um ataque simultâneo e independente à cadeia de suprimentos do axiospacote npm, que ocorreu horas antes do vazam[ento.

Se você instalou ou](https://x.com/Fried_rice/status/2038894956459290963) atualizou o Claude Code via npm em 31 de março de 2026, entre 00:21 e 03:29 UTC, você pode ter instalado inadvertidamente uma versão maliciosa do axios (1.14.1 ou 0.30.4) que contém um Trojan de Acesso Remoto (RAT). Você deve procurar imediatamente nos arquivos de bloqueio do seu projeto ( package-lock.json, yarn.lock, ou bun.lockb) por essas versões específicas ou pela dependência plain-crypto-js. Se encontradas, consi[dere a máquina host como totalmente compromet](https://www.theinformation.com/newsletters/ai-agenda/anthropics-success-sparks-server-crunch)ida, rotacione todos os segredos e realize uma reinstalação limpa do sistema operacional.

Para mitigar riscos futuros, você deve migrar completamente da instalação baseada em npm. A Anthropic designou o Native Installer ( curl -fsSL https://claude.ai/install.sh | bash) como o método recomenda[do porque ele usa um binário independente que não depende d](https://www.anthropic.com/news/anthropic-raises-30-billion-series-g-funding-380-billion-post-money-valuation)a cadeia de dependências volátil do npm.

A versão nativa também oferece suporte a atualizações automáticas em segundo plano, garantindo que você receba patches de segurança (provavelmente a versão 2.1.89 ou superior) assim que forem lançados. Se você precisar continuar usando o npm, certifique-se de desinstalar a versão vazada 2.1.88 e fixar sua instalação em uma versão segura e verificada, como a 2.1.86.

Por fim, adote uma postura de conf__iança zero ao usar o Claude Code em ambientes desconhecidos. Evite executar o agente em repositórios recém-clonados ou não confiáveis ​​até que você tenha inspecionado manualmente o arquivo de .claude/config.jsonconfiguração e quaisquer hooks personalizados.

Como medida de defesa em profundidade, alterne suas chav__es** de API da Anthropic por meio **do console do desenvolvedor e monitore seu uso em busca de anomalias. Embora seus dados armazenados na nuvem permaneçam seguros, a vulnerabilidade do seu ambiente local aumentou agora que as defesas internas do agente são de conhecimento público; manter-se atualizado com a versão oficial instalada nativamente** é sua melhor d**efesa.

---

**INEMA** · 2026-03-31

**O código-fonte de Claude Code parece ter vazado: aqui está o que sabemos.**
31 de março de 2026

A Anthropic parece ter revelado acidentalmente ao público o funcionamento interno de um de seus produtos de IA mais populares e lucrativos, o sistema de IA Claude Code.

Um arquivo de mapa de origem JavaScript de 59,8 MB ( `.map`), destinado à depuração interna, foi incluído inadvertidamente na versão 2.1.88 do `@anthropic-ai/claude-code`pacote no registro público do npm, publicada no início desta manhã.

Às 4h23 da manhã (horário do leste dos EUA), [Chaofan Shou (@Fried_rice)](https://x.com/Fried_rice/status/2038894956459290963) , estagiário da Solayer Labs, divulgou a descoberta no X (antigo Twitter). A publicação, que incluía um link direto para download de um arquivo hospedado, serviu como um alerta digital. Em poucas horas, o código-fonte em TypeScript, com cerca de 512.000 linhas, estava replicado no GitHub e analisado por milhares de desenvolvedores.

Para a Anthropic, uma empresa que atualmente experimenta uma ascensão meteórica com uma [receita anualizada estimada em US$ 19 bilhões](https://www.theinformation.com/newsletters/ai-agenda/anthropics-success-sparks-server-crunch) em março de 2026, o vazamento representa mais do que uma falha de segurança; é uma perda estratégica significativa de propriedade intelectual. O momento é particularmente crítico, dada a velocidade de comercialização do produto.

Os dados de mercado indicam que somente a Claude Code alcançou [uma receita recorrente anualizada (ARR) de US$ 2,5 bilhões,](https://www.anthropic.com/news/anthropic-raises-30-billion-series-g-funding-380-billion-post-money-valuation) um valor que mais que dobrou desde o início do ano.

Com a adoção empresarial representando 80% de sua receita, o vazamento fornece aos concorrentes — desde gigantes consolidados até rivais ágeis como a Cursor — um modelo literal de como construir um agente de IA altamente eficaz, confiável e comercialmente viável.

A Anthropic confirmou o vazamento em um comunicado enviado por e-mail por um porta-voz ao VentureBeat, que diz o seguinte:

" __Hoje mais cedo, uma versão do Claude Code continha código-fonte interno. Nenhum dado ou credencial sensível de clientes foi envolvido ou exposto. Trata-se de um problema de empacotamento causado por erro humano, e não uma violação de segurança. Estamos implementando medidas para evitar que isso aconteça novamente."__

**A anatomia da memória agentiva**
A principal vantagem para os concorrentes reside em como a Anthropic resolveu o problema da "entropia contextual" — a tendência dos agentes de IA ficarem confusos ou alucinatórios à medida que as sessões de longa duração se tornam mais complexas.

A fonte vazada revela uma arquitetura de memória sofisticada **de três camadas** que se afasta da recuperação tradicional do tipo "armazenar tudo".

Conforme analisado por desenvolvedores , a arquitetura utiliza um sistema de "Memória Auto-Recuperável".

Em sua essência `MEMORY.md`, trata-se de um índice leve de ponteiros (aproximadamente 150 caracteres por linha) que é carregado perpetuamente no contexto. Esse índice não armazena dados; ele armazena localizações.

O conhecimento real do projeto é distribuído em "arquivos de tópicos" obtidos sob demanda, enquanto as transcrições brutas nunca são totalmente lidas de volta ao contexto, mas simplesmente "buscadas" por identificadores específicos.

Essa "Disciplina de Escrita Rigorosa" — em que o agente deve atualizar seu índice somente após uma gravação de arquivo bem-sucedida — impede que o modelo polua seu contexto com tentativas falhas.

Para os concorrentes, o "plano" é claro: construir uma memória cética. O código confirma que os agentes da Anthropic são instruídos a tratar sua própria memória como uma "dica", exigindo que o modelo verifique os fatos em relação à base de código real antes de prosseguir.

K**AIROS e o demônio autônomo
**O vazamento também revela o **" **[KAIROS ](https://en.wikipedia.org/wiki/Kairos)**",** o conceito grego antigo de "no momento certo", um recurso mencionado mais de 150 vezes no código-fonte. O KAIROS representa uma mudança fundamental na experiência do usuário: um modo daemon autônomo.

Embora as ferramentas de IA atuais sejam em grande parte reativas, o KAIROS permite que o Claude Code opere como um agente em segundo plano sempre ativo. Ele gerencia sessões em segundo plano e utiliza um processo chamado
