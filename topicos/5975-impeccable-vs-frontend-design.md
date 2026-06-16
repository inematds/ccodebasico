# Impeccable vs frontend-design

> Tópico 5975 · 4 mensagens úteis de 13 totais

---

**INEMA** · 2026-05-20

https://github.com/pbakaus/impeccable

---

**INEMA** · 2026-05-20

https://github.com/nexu-io/open-design

---

**INEMA** · 2026-05-20

● Impeccable vs frontend-design

  É fork enriquecido do frontend-design da Anthropic. O que ele tem a mais:

  Vantagens sobre frontend-design
  - 7 refs de domínio carregadas sempre: typography, color/contrast (OKLCH), spatial, motion, interaction, responsive, ux-writing — frontend-design tem guidance mais genérico.
  - 23 comandos verbais (/polish, /audit, /critique, /distill, /bolder, /quieter, /harden, /animate, /typeset, /layout, /overdrive, /live…) — vocabulário compartilhado pra iterar, não só
  "build me a page".
  - Detector determinístico (CLI + extensão): 27 regras anti-pattern + 12 críticas via LLM. Roda npx impeccable detect src/ sem API key, pega "AI slop" (gradiente purple→blue, Inter em tudo,
   card-em-card, bounce easing, glow dark, linha longa, padding apertado, touch target pequeno, headings pulados).
  - Brand-vs-product register que ajusta defaults conforme contexto.
  - Comando /teach que gera PRODUCT.md + DESIGN.md na raiz como design system vivo do projeto.
  - /extract puxa tokens/componentes reutilizáveis pro design system.
  - Apache 2.0, multi-harness (Claude Code, Cursor, Codex, Copilot, Gemini, etc).

  Onde frontend-design ainda ganha: já está no seu kit Anthropic local, sem instalação extra; suficiente pra UI "one-shot" sem precisar de vocabulário de iteração.

  Utilidade no Open Design

  OD é literalmente uma plataforma que gera UIs via skills + design-systems. Impeccable encaixa em três pontos:

  1. Design systems do OD (apps/daemon serve design-systems). As 7 refs do Impeccable (OKLCH, motion curves, spatial) são exatamente o tipo de conteúdo curado que OD distribui como
  design-system pros agentes. Dá pra absorver as 7 refs como um design-system "impeccable" embarcado.
  2. Skills protocol do OD (docs/skills-protocol.md). Os 23 comandos viram skills do catálogo OD — polish, critique, harden, distill são verbos de iteração que faltam no OD atual (que é mais
   "gera do zero").
  3. Detector determinístico como guardrail. O impeccable detect CLI pode rodar como post-generation lint nos artefatos que o daemon salva em .od/artifacts/ — fecha o loop "agente gerou →
  tem AI slop? → re-polish". Sem API key, sem custo.

  Pra fork pessoal seu: vale instalar global (~/.claude/) já que substitui/estende seu frontend-design atual com vocabulário muito mais granular. Pro repo OD upstream: o ângulo mais forte é
  absorver as 7 refs como design-system + o detector como verificador de qualidade, não copiar os 23 comandos crus.

---

**INEMA** · 2026-05-20

https://chatgpt.com/c/6a0d4ffd-a53c-832d-a811-275086ece8e4
