# Instalação do Node.js

> Tópico 978 · 5 mensagens úteis de 16 totais

---

**INEMA** · 2025-09-15

Vou te passar o **passo a passo direto** para instalar o **Node.js no Windows** partindo do zero.

---

### Instalação Node.js no Windows (passo a passo)

1. Acesse o site oficial:
   [https://nodejs.org](https://nodejs.org/)

2. Clique em **LTS (Long Term Support)** → é a versão estável recomendada.

3. Baixe o arquivo instalador `.msi` para Windows.

4. Dê **dois cliques** no arquivo baixado.

5. Clique em **Next**.

6. Marque **I accept the terms** → **Next**.

7. Local de instalação → deixe o padrão `C:\Program Files\nodejs\` → **Next**.

8. Componentes → mantenha todos selecionados (especialmente **npm package manager**) → **Next**.

9. Ferramentas adicionais → pode desmarcar se não precisar compilar pacotes (opcional) → **Next**.

10. Clique em **Install** e aguarde.

11. Ao terminar, clique em **Finish**.

12. Abra o **Prompt de Comando** (ou PowerShell).
    Digite:

    ```    node -v
    ```

    Vai mostrar a versão do Node.js.

    Depois:

    ```    npm -v
    ```

    Vai mostrar a versão do npm.

---

Pronto! O Node.js e o npm já estão instalados e prontos para usar.

---

**INEMA** · 2025-09-15

Guia bem direto e passo a passo para instalar o **Node.js** no Windows.

---

### Instalação do Node.js no Windows

1. **Baixar o instalador**

   * Acesse o site oficial: [https://nodejs.org](https://nodejs.org/)
   * Você verá duas opções:

     * **LTS (Long Term Support)** → mais estável, recomendada.
     * **Current** → versão mais nova, mas pode ter bugs.
   * Clique na **LTS** (arquivo `.msi`).

2. **Abrir o instalador**

   * Dê dois cliques no arquivo baixado.
   * Vai abrir a tela de instalação do Node.js.
   * Clique em **Next**.

3. **Aceitar os termos**

   * Marque a caixinha "I accept the terms..."
   * Clique em **Next**.

4. **Escolher local de instalação**

   * Normalmente o instalador sugere `C:\Program Files\nodejs\`
   * Pode deixar padrão e clicar em **Next**.

5. **Selecionar componentes**

   * Deixe todas as opções marcadas, especialmente **npm package manager**.
   * Clique em **Next**.

6. **Ferramentas adicionais (opcional)**

   * Ele pode perguntar se você quer instalar também ferramentas de compilação (Python, Visual Studio Build Tools).
   * Se você não for compilar pacotes nativos, pode ignorar.
   * Clique em **Next**.

7. **Instalar**

   * Clique em **Install**.
   * Aguarde a instalação terminar.
   * Clique em **Finish**.

8. **Testar instalação**

   * Abra o **Prompt de Comando** (CMD) ou PowerShell.
   * Digite:

     ```     node -v
     ```

     Deve aparecer a versão do Node.js (ex: `v20.11.1`).
   * Depois digite:

     ```     npm -v
     ```

     Deve aparecer a versão do npm (ex: `10.2.4`).

Se essas duas versões aparecerem, está tudo pronto!

---

---

**INEMA** · 2025-09-15

Para usar o **npm**, você precisa instalar primeiro o **Node.js**, porque o npm já vem junto. Aqui vai um passo a passo simples para instalar no Windows (funciona parecido no Linux e Mac, mas muda o instalador):

---

### Passo a passo – Windows

1. **Baixar o instalador**

   * Vá no site oficial: [https://nodejs.org](https://nodejs.org/)
   * Você verá duas versões:

     * **LTS (Long Term Support)** → recomendada para a maioria dos usuários (mais estável).
     * **Current** → versão mais nova, mas pode ter mudanças recentes.
   * Clique e baixe a versão **LTS**.

2. **Executar o instalador**

   * Dê dois cliques no arquivo `.msi` baixado.
   * Aceite os termos, deixe as opções padrão e prossiga.
   * Ele vai instalar tanto o **Node.js** quanto o **npm**.

3. **Verificar se deu certo**

   * Abra o **Prompt de Comando** (ou PowerShell).
   * Digite:

     ```     node -v
     ```

     Isso mostra a versão do Node.js.
   * Depois:

     ```     npm -v
     ```

     Isso mostra a versão do npm.

Se aparecer os números das versões, está instalado com sucesso.

---

### No Linux (Ubuntu/Debian)

```sudo apt update
sudo apt install nodejs npm -y```

### No Mac

* Pode instalar via site oficial ou usando o **Homebrew**:

```brew install node```

---

**INEMA** · 2025-09-15

NPM é a sigla para **Node Package Manager**.

Ele é o **gerenciador de pacotes oficial do Node.js**, usado para instalar, atualizar e compartilhar bibliotecas e ferramentas de JavaScript.

### Para que serve

* **Instalar pacotes**: bibliotecas prontas para usar em projetos (ex.: React, Express).
* **Gerenciar dependências**: controla versões das bibliotecas do seu projeto.
* **Executar scripts**: você pode automatizar tarefas como `npm start`, `npm test` ou `npm run build`.
* **Publicar pacotes**: desenvolvedores podem compartilhar suas próprias bibliotecas com a comunidade.

### Como funciona na prática

1. Você precisa ter o **Node.js** instalado (o NPM já vem junto).
2. No terminal, pode rodar comandos como:

   * `npm init -y` → cria um arquivo `package.json` que descreve seu projeto.
   * `npm install express` → instala a biblioteca Express.
   * `npm install` → instala todas as dependências listadas no `package.json`.
   * `npm update` → atualiza os pacotes.

### Exemplo

Suponha que você quer usar o Express (um framework para criar servidores web com Node.js):

```npm init -y
npm install express```

Depois, dentro do seu código `index.js`:

```const express = require('express');
const app = express();

app.get('/', (req, res) => res.send('Olá, mundo!'));
app.listen(3000);```

Executando `node index.js`, você já tem um servidor rodando na porta 3000.

---

**INEMA** · 2025-09-15

https://chatgpt.com/c/68c899f1-261c-8332-91a0-558ebd36e040
