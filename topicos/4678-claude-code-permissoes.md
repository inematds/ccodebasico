# Claude Code - Permissoes

> Tópico 4678 · 5 mensagens úteis de 17 totais

---

**INEMA** · 2026-04-05

# 🧠 🔥 Modo 3 – Hooks (controle total)

Aqui você não usa só regras fixas…
👉 você cria **lógica inteligente** pra decidir o que pode ou não

---

# 📁 Estrutura

Crie:

```.claude/hooks/protect-system.sh```

---

# 🧾 Exemplo de script (bloqueio inteligente)

```#!/bin/bash

cmd="$1"

# Bloquear remoção de diretórios
if [[ "$cmd" == *"rm -rf"* ]]; then
  echo "❌ Bloqueado: tentativa de deletar diretório"
  exit 2
fi

# Bloquear qualquer rm
if [[ "$cmd" == rm* ]]; then
  echo "❌ Bloqueado: comando rm não permitido"
  exit 2
fi

# Permitir o resto
exit 0```

---

# 🔗 Conectar no settings.json

```{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": ".claude/hooks/protect-system.sh"
          }
        ]
      }
    ]
  }
}```

---

# 🔍 Como funciona na prática

### Claude tenta:

```rm -rf projeto```

👉 Hook intercepta → bloqueia antes de executar

---

### Claude tenta:

```ls -la```

👉 Hook deixa passar

---

# 🧠 Por que isso é MUITO poderoso

Você pode fazer coisas que os outros modos não fazem:

---

## 🔒 Bloquear só pastas críticas

```if [[ "$cmd" == *"/etc"* ]]; then
  echo "❌ Área protegida"
  exit 2
fi```

---

## 👤 Permitir só certos caminhos

```if [[ "$cmd" == *"/meu-projeto"* ]]; then
  exit 0
else
  echo "❌ Fora do escopo"
  exit 2
fi```

---

## 🧾 Logar tudo

```echo "$(date) - $cmd" >> logs.txt```

---

## ⚠️ Bloquear sudo

```if [[ "$cmd" == *"sudo"* ]]; then
  echo "❌ sudo proibido"
  exit 2
fi```

---

# ⚠️ Regra importante

👉 `exit 2` = bloqueia
👉 `exit 0` = permite

---

# 🧱 Diferença dos 3 modos

| Modo        | Nível          |
| ----------- | -------------- |
| 1 (deny)    | básico         |
| 2 (dontAsk) | seguro         |
| 3 (hooks)   | controle total |

---

# 💡 Quando usar hooks

Use quando você quer:

* regras dinâmicas
* segurança por contexto
* proteção avançada de sistema
* auditoria (logs)

---

# 🧾 Resumo direto

Modo 3 = você vira o “firewall” do Claude

✔ intercepta tudo
✔ analisa o comando
✔ decide permitir ou bloquear

--

---

**INEMA** · 2026-04-05

**Modo 2: Modo de permissão (defaultMode)** 👇

---

# 🔒 🧱 Modo 2 – “Travar tudo por padrão”

Aqui a lógica muda completamente:

👉 Em vez de bloquear alguns comandos…
👉 você **bloqueia TUDO** e só libera o que quiser

---

# 📁 Exemplo básico

```{
  "defaultMode": "dontAsk",
  "permissions": {
    "allow": [
      "Bash(ls *)",
      "Bash(cat *)"
    ]
  }
}```

---

# 🔍 O que isso significa

## 🚫 Tudo bloqueado por padrão:

* `rm`
* `git`
* `npm`
* qualquer comando

## ✅ Só funciona o que está em `allow`:

* `ls`
* `cat`

---

# 💥 Exemplo real

### Se o Claude tentar:

```rm -rf projeto```

👉 Resultado:

```❌ Bloqueado (não está no allow)```

---

### Se tentar:

```git status```

👉 Resultado:

```❌ Bloqueado```

---

### Se tentar:

```ls -la```

👉 Resultado:

```✅ Executa```

---

# 🧠 Diferença do Modo 1 vs Modo 2

| Modo             | Como funciona                      |
| ---------------- | ---------------------------------- |
| Modo 1 (deny)    | Bloqueia só o que você lista       |
| Modo 2 (dontAsk) | Bloqueia tudo e libera manualmente |

👉 Modo 2 = MUITO mais seguro

---

# 🛡️ Exemplo mais realista (uso prático)

```{
  "defaultMode": "dontAsk",
  "permissions": {
    "allow": [
      "Bash(ls *)",
      "Bash(cat *)",
      "Bash(git status)",
      "Bash(git diff)"
    ]
  }
}```

👉 Aqui você permite:

* leitura de arquivos
* inspeção do git

👉 Mas NÃO permite:

* deletar
* modificar
* instalar coisas

---

# ⚠️ Pegadinha importante

Se você esquecer de colocar algo no `allow`:

👉 o Claude NÃO consegue usar

Isso inclui coisas básicas tipo:

* `pwd`
* `echo`
* etc.

---

# 💡 Resumo direto

Modo 2 (`dontAsk`):

* 🔒 bloqueia tudo por padrão
* ✅ só roda o que você liberar
* 🛡️ é o mais seguro possível

---

**INEMA** · 2026-04-05

**Modo 1 (Regras de permissão)** com um exemplo real e claro 👇

---

# 🧱 📁 Exemplo completo – `settings.json`

Crie o arquivo:

```.claude/settings.json```

E coloque:

```{
  "permissions": {
    "allow": [
      "Bash(ls *)",
      "Bash(cat *)"
    ],
    "deny": [
      "Bash(rm *)",
      "Bash(rm -*)",
      "Bash(rmdir *)",
      "Bash(dd *)",
      "Bash(mkfs*)"
    ]
  }
}```

---

# 🔍 O que isso faz na prática

## ✅ Permitido:

* `ls` → listar arquivos
* `cat` → ler arquivos

## ❌ Bloqueado:

* `rm` → apagar arquivos
* `rm -rf` → apagar diretórios
* `rmdir` → remover pastas
* `dd`, `mkfs` → comandos perigosos

---

# 💥 Exemplo real de comportamento

### Se o Claude tentar:

```rm -rf /projeto```

👉 Resultado:

```❌ Bloqueado pelas regras de permissão```

---

### Se tentar:

```ls -la```

👉 Resultado:

```✅ Executa normalmente```

---

# 🧠 Dica importante (muito usada)

Você pode ser ainda mais específico:

```{
  "permissions": {
    "deny": [
      "Bash(rm -rf /)",
      "Bash(rm -rf ~)",
      "Bash(rm -rf /home/*)"
    ]
  }
}```

👉 Isso protege áreas críticas do sistema

---

# ⚠️ Ordem de prioridade

* `deny` SEMPRE vence
* mesmo que esteja em `allow`

---

# 💡 Versão mínima (só pra bloquear delete)

Se quiser algo simples:

```{
  "permissions": {
    "deny": [
      "Bash(rm *)",
      "Bash(rmdir *)"
    ]
  }
}```

---

# 🧾 Resumo

Modo 1 = **regras diretas no settings.json**

Você define:

* o que pode (`allow`)
* o que nunca pode (`deny`)

👉 É o jeito mais simples e direto de proteger

---

**INEMA** · 2026-04-05

Arquivo de config no Claude Code em 2026** e é exatamente isso que você estava procurando.

---

# 📁 Arquivo de configuração correto

Você pode usar:

* Global:

```~/.claude/settings.json```

* Por projeto:

```.claude/settings.json```

---

# 🔒 Como proibir deletar diretórios

Você coloca regras de **deny** assim:

```{
  "permissions": {
    "deny": [
      "Bash(rm -*)",
      "Bash(rm *)",
      "Bash(rmdir *)"
    ]
  }
}```

👉 Isso bloqueia qualquer comando tipo:

* `rm`
* `rm -rf`
* `rmdir`

✔ Mesmo que o modelo tente → NÃO executa

---

# ⚠️ Importante (muito bom saber)

👉 As regras `deny` têm prioridade máxima
Ou seja:

* Mesmo que algo esteja permitido em outro lugar
* O `deny` sempre vence 

---

# 🧱 Modo mais seguro ainda

Você pode travar tudo e só liberar o necessário:

```{
  "defaultMode": "dontAsk"
}```

👉 Nesse modo:

* tudo é bloqueado por padrão
* só roda o que estiver em `allow`

---

# 🧠 Controle avançado (hooks)

Se quiser algo mais inteligente (ex: bloquear só certos caminhos):

Crie:

```.claude/hooks/protect-system.sh```

E conecte no config:

```{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": ".claude/hooks/protect-system.sh"
          }
        ]
      }
    ]
  }
}```

👉 Esse script pode analisar o comando e bloquear antes de executar 

---

# 🔎 Ver o que está ativo

Dentro do Claude Code:

```/permissions```

---

**INEMA** · 2026-04-05

Claude Code - Permissões
