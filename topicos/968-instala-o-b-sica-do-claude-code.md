# Instalação Básica do Claude Code

> Tópico 968 · 19 mensagens úteis de 46 totais

---

**INEMA** · 2026-05-15

https://claude-agent-2.vercel.app/

---

**INEMA** · 2026-04-06

# 🧩 ORDEM CERTA pra instalar Claude Code no Windows

## ✅ 1. Instalar o Git (IMPORTANTE)

👉 [https://git-scm.com/download/win](https://git-scm.com/download/win)

* Instala tudo padrão (Next → Next)
* Isso instala o **Git Bash**, que o Claude precisa

---

## ✅ 2. Instalar o Node.js

👉 [https://nodejs.org](https://nodejs.org/)

* Baixa a versão **LTS**
* Instala normal

---

## ✅ 3. Testar Node

Abra o terminal e roda:

```node -v
npm -v```

Se aparecer versão → ok ✅

---

## ✅ 4. Instalar o Claude Code

No terminal:

```npm install -g @anthropic-ai/claude-code```

--- Se vc tem assinatura usa o OAuth

## ✅ 5. Configurar a API Key

No PowerShell:

```setx ANTHROPIC_API_KEY "SUA_CHAVE_AQUI"```

(Depois fecha e abre o terminal)

---

## ✅ 6. Testar o Claude

```claude```

---

## ⚠️ 7. Se aparecer erro do Git Bash

Só roda isso:

```setx CLAUDE_CODE_GIT_BASH_PATH "C:\Program Files\Git\bin\bash.exe"```

Reabre o terminal e testa de novo.

---

# 💻 (Opcional, mas MUITO recomendado)

## Instalar VS Code

👉 [https://code.visualstudio.com/](https://code.visualstudio.com/)

---

# 🧠 RESUMO RÁPIDO

Ordem é:

1. Git ✅
2. Node.js ✅
3. Claude Code ✅
4. API Key ✅
5. Testar ✅

---

**Tiza** · 2026-02-21

https://www.youtube.com/live/oR7vkdgnPus?si=rIoWhKCTMOVmI43n

---

**INEMA** · 2026-02-07

linux

sudo npm install -g @anthropic-ai/claude-code@latest

---

**INEMA** · 2026-02-07

npm install -g @anthropic-ai/claude-code@latest

---

**INEMA** · 2026-02-07

**claude --model "opus[1m]"**

---

**INEMA** · 2026-01-31

Guia para o Claude Code fazer manutencao no N8N Docker inclusive

---

**INEMA** · 2025-11-17

https://claudecode.io/install

---

**INEMA** · 2025-11-17

no Linux

sudo apt update && sudo apt upgrade -y
sudo apt install -y nodejs
# Verifique:
node --version
npm --version
npm install -g @anthropic-ai/claude-code
claude

---

**INEMA** · 2025-09-15

Quando você roda `claude-code init`, ele cria uma **pasta oculta `.claude-code`** dentro do diretório onde você está.

A estrutura básica costuma ser algo assim (pode variar conforme a versão):

```.claude-code/
│
├── config.json        → Arquivo de configuração principal do workspace
├── history.json       → Histórico das interações no projeto
├── state.json         → Estado atual da sessão (contexto, arquivos em uso)
└── logs/              → Pasta com registros locais```

---

## O que cada arquivo faz

* c**onfig.json
**  Guarda informações de configuração do workspace: permissões, preferências e metadados do projeto.

* h**istory.json
**  Mantém um histórico das conversas e ações feitas dentro daquele workspace (ajuda a retomar contexto depois).

* s**tate.json
**  Armazena o estado atual da sessão (ex.: arquivos abertos, último comando rodado).

* l**ogs/
**  Pode conter registros detalhados de operações (depende da versão e se o log está ativado).

---

## Importante

* Esses arquivos n**ão interferem em outros workspaces.**
* Se você apagar a pasta .`claude-code,` o Claude Code perde o histórico/configuração daquele projeto, mas nada acontece com seus arquivos de código — só precisa rodar c`laude-code init `de novo para recriar.

---

---

**INEMA** · 2025-09-15

No momento em que você inicializa o Claude Code dentro de uma pasta com o comando:

```claude-code init```

---

## O que ele cria

* Um diretório oculto chamado .`claude-code `dentro da pasta onde você rodou o comando.
* Dentro dele ficam arquivos de configuração e histórico local daquele w**orkspace.**
* Ele só cria esses arquivos no d**iretório onde você roda o `init` **— nunca espalha pelo sistema todo.

---

## Quando ele cria

1. Você entra numa pasta (exemplo):

    ```  cd C:\Users\Nei\projetos\site
   
```2. Roda:

     ``` claude-code init
   
3```. Nesse momento ele cria o .cl`aude-code na` pasta sit`e.
 `  Essa pasta é invisível no Windows Explorer por padrão (porque começa com `.`), mas você pode ver se habilitar “mostrar arquivos ocultos”.

---

## Observações

* Cada pasta que você inicializar terá o seu .cl**aude-code pr**óprio.
* Se você nunca rodar ini`t, e`le não cria nada.
* Mesmo que você apague esse diretório oculto, dá pra rodar cla`ude-code init de` novo e recriar.

---

**INEMA** · 2025-09-15

O **WSL** significa **Windows Subsystem for Linux**.

Ele é um recurso do Windows que permite você **rodar um sistema Linux dentro do Windows**, sem precisar de máquina virtual ou dual boot.

---

## Explicando simples

* Normal: você teria que instalar o Linux separado em outra partição ou em uma máquina virtual.
* Com o **WSL**, você abre um terminal no Windows e já está dentro do Linux.
* É como se o Linux rodasse “dentro” do Windows, integrado, rápido e leve.

---

## Para que serve

* Rodar comandos Linux direto no Windows.
* Usar ferramentas e bibliotecas que só existem no Linux.
* Desenvolver programas que precisam de ambiente Linux (servidores, Node.js, Python, Docker etc).

---

## Exemplo

No Windows PowerShell você digita:

`wsl`

E o Windows abre um terminal Linux (Ubuntu, Debian, Fedora, etc).

Dentro dele você pode rodar:

l```s
pwd
sudo apt update
```
Tudo igual a um Linux de verdade.

---

## Instalação rápida

Se você tem Windows 10/11 atualizado:

ws```l --install

```Depois reinicia o PC, e o Windows instala automaticamente o Ubu**ntu co**mo padrão.

---

**INEMA** · 2025-09-15

Vou resumir de forma direta e simples como instalar o **Claude Code** em diferentes sistemas operacionais.

---

## Windows

Pré-requisito: já ter **Node.js + npm** instalado.
No PowerShell:

```npm install -g claude-code
claude-code login```

Cole sua A**PI key da Anthropic **quando pedir.

---

## macOS

1. Instale Node.js (via s[ite oficial ](https://nodejs.org/)ou Homebrew: `brew install node`).
2. No terminal:

n```pm install -g claude-code
claude-code login
```
---

## Linux (Ubuntu/Debian)

1. Instale Node.js:

su```do apt update
sudo apt install nodejs npm -y

```(ou use nvm para versões mais novas).
2\. Depois:

npm``` install -g claude-code
claude-code login

-```--

## WSL (Windows Subsystem for Linux)

1. Instale o WSL no Windows:

wsl ```--install

(p```recisa reiniciar).
2\. Entre no WSL (`wsl` no PowerShell).
3\. Dentro do WSL, siga os mesmos passos do Linux:

sudo ```apt update
sudo apt install nodejs npm -y
npm install -g claude-code
claude-code login

---```

Resumindo:

* Windows → npm in`stall -g claude-code
* mac`OS → igual ao Windows, só precisa ter Node.
* Linux/WSL → instale Node e depois o mesmo comando.

---

**INEMA** · 2025-09-15

se o claude-code init nao funcionar teste so claude init

---

**INEMA** · 2025-09-15

No Claude Code, você pode ter quantos **workspaces** quiser na mesma máquina, porque cada um fica associado a uma **pasta diferente**.

---

## Como funciona

1. **Cada pasta = 1 workspace**
   O Claude Code não mistura os projetos. Se você rodar `claude-code init` dentro de uma pasta, ele só vai trabalhar ali.

2. **Separação automática**
   Ele cria arquivos de configuração locais (como `.claude-code/`) dentro da pasta. Isso garante que o histórico, contexto e permissões sejam separados.

3. **Múltiplos workspaces na mesma máquina**
   Você pode ter, por exemplo:

   `   C:\Users\Nei\projetos\site-pessoal
   C:\Users\Nei\projetos\app-mobile
   C:\Users\Nei\projetos\api-backend
   `

   Em cada pasta, você roda:

    `  claude-code init
   
`
   e pronto, cada uma vira um workspace independente.

---

## Passo a passo para ter vários workspaces

1. Crie uma nova pasta para cada projeto:

     ``` mkdir site-pessoal
   mkdir app-mobile
   mkdir api-backend
   
2```. Entre em uma pasta de cada vez e inicialize:

      `cd site-pessoal
   claude-code init
   

 `  Repita isso nas outras pastas.
3. Sempre que quiser voltar a trabalhar em um projeto, entre na pasta e rode:

      c`laude-code chat
   

--`-

## Dica

Se você quiser abrir** dois workspaces ao mesmo tempo, pod**e:

* Abrir dois terminais diferentes (um em cada pasta).
* O Claude Code vai manter o contexto separado em cada janela.

---

**INEMA** · 2025-09-15

O **workspace** no Claude Code é como uma “pasta de trabalho” onde ele vai atuar.

Pensa assim:

* Se você só digitar `claude-code chat`, ele conversa de forma solta, sem saber nada dos seus arquivos.
* Mas quando você roda `claude-code init` dentro de uma pasta do seu PC, ele cria um **workspace** nessa pasta.

Esse workspace significa que:

1. O Claude Code passa a conhecer os arquivos desse diretório (código, docs, configs).
2. Ele pode **ler, editar e sugerir mudanças** nos arquivos.
3. Ele guarda **um histórico local** das interações, para manter o contexto daquele projeto.

---

### Exemplo prático

* Você cria uma pasta para seu projeto:

  ```  mkdir meu-projeto
  cd meu-projeto
  ```
* Depois inicializa:

   ` claude-code init
  
`* Agora, se você rodar:

    `claude-code chat
  

`  Ele vai conversar já “dentro do projeto”, podendo abrir e modificar arquivos da pasta meu`-projeto.

`---

### Em resumo

Um wor**kspace é:**

* Um con**texto de projeto.
*** Onde o Claude Code entende seus arquivos e ajuda você a pro**gramar, editar, ou documentar de**ntro daquela pasta.
* Você pode ter vários workspaces diferentes (um por projeto).

---

---

**INEMA** · 2025-09-15

Instalar o **Claude Code** no Windows agora que já tem o Node.js.

---

## 1. Pré-requisitos

Você já tem o **Node.js** instalado. Isso já inclui o **npm** (gerenciador de pacotes do Node).
Para conferir, abra o **PowerShell** e digite:

```node -v
npm -v```

Se aparecer as versões, está tudo certo.

---

## 2. Instalar o Claude Code CLI

No terminal (PowerShell ou Prompt de Comando), rode:

n`pm install -g claude-code

OU

`npm install -g @anthropic-ai/claude-code 

Esse comando instala a li**nha de comando do Claude Code d**e forma global no Windows.

---

## 3. Configurar o Claude Code

Depois de instalar, você precisa configurar sua AP**I Key da Anthropic (**Claude).
No mesmo terminal:

cl`aude-code login

`Ele vai pedir sua API** Key.

*** Se ainda não tem, você cria uma conta na Anthropic (htt[ps://console.anthropic.com/).
](https://console.anthropic.com/)* Lá no Das**hboard → API Keys, g**ere sua chave.
* Copie e cole no terminal quando ele pedir.

---

## 4. Testar se está funcionando

Rode:

cla`ude-code --help

o`u

clau`de-code chat

Is`so deve abrir o prompt de conversa direto no terminal.

---

## 5. (Opcional) Usar junto com pastas/projetos

Você pode iniciar um workspace dentro de um projeto:

claud`e-code init

Iss`o permite o Claude Code acessar seus arquivos e ajudar direto no seu código.

---

**INEMA** · 2025-09-15

Instalação Básica do Claude Code

---

**INEMA** · 2025-09-15

https://chatgpt.com/c/68c89c68-b998-8323-a133-af15b73025f4
