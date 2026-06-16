# Custos e Configurando Claude Code

> Tópico 3926 · 9 mensagens úteis de 37 totais

---

**INEMA** · 2026-03-18

o texto inicial é para deixar o claude code original e os outros para vc poder usar o openrouter ou qq outro

---

**INEMA** · 2026-03-18

Switch Claude Code to use this model: openrouter/free

Open ~/.claude/settings.json and change only the ANTHROPIC_MODEL value inside the "env" block to:
"ANTHROPIC_MODEL": "openrouter/free"

Do not change any other keys. Do not modify shell config files.

After saving, I will quit my terminal and open a new one for the change to take effect.

---

**INEMA** · 2026-03-18

Switch Claude Code to use this model: deepseek/deepseek-v3

Open ~/.claude/settings.json and change only the ANTHROPIC_MODEL value inside the "env" block to:
"ANTHROPIC_MODEL": "deepseek/deepseek-v3"

Do not change any other keys. Do not modify shell config files.

After saving, I will quit my terminal and open a new one for the change to take effect.

---

**INEMA** · 2026-03-18

Switch Claude Code to use this model: qwen/qwen3-coder-480b

Open ~/.claude/settings.json and change only the ANTHROPIC_MODEL value inside the "env" block to:
"ANTHROPIC_MODEL": "qwen/qwen3-coder-480b"

Do not change any other keys. Do not modify shell config files.

After saving, I will quit my terminal and open a new one for the change to take effect.

---

**INEMA** · 2026-03-18

Switch Claude Code to use this model: mistralai/devstral-small

Open ~/.claude/settings.json and change only the ANTHROPIC_MODEL value inside the "env" block to:
"ANTHROPIC_MODEL": "mistralai/devstral-small"

Do not change any other keys. Do not modify shell config files.

After saving, I will quit my terminal and open a new one for the change to take effect.

---

**INEMA** · 2026-03-18

Switch Claude Code to use this model: google/gemini-2.5-pro-preview

Open ~/.claude/settings.json and change only the ANTHROPIC_MODEL value inside the "env" block to:
"ANTHROPIC_MODEL": "google/gemini-2.5-pro-preview"

Do not change any other keys. Do not modify shell config files.

After saving, I will quit my terminal and open a new one for the change to take effect.

---

**INEMA** · 2026-03-18

Task: Revert Claude Code back to using Claude (Anthropic) as the model.
Do the following steps in order. Do nothing else.

## Step 1: Clean up ~/.zshrc (or ~/.bashrc)

Open the user's shell config file (~/.zshrc or ~/.bashrc) and remove the following environment variable exports if they exist:

export ANTHROPIC_BASE_URL
export ANTHROPIC_AUTH_TOKEN
export ANTHROPIC_API_KEY
export ANTHROPIC_MODEL
export OPENROUTER_API_KEY

Remove only these exact lines. Do not remove any other lines or exports. If none of these exist, skip this step.

## Step 2: Clean up ~/.claude/settings.json

Open ~/.claude/settings.json and remove the following keys from inside the "env" block if they exist:

ANTHROPIC_BASE_URL
ANTHROPIC_AUTH_TOKEN
ANTHROPIC_API_KEY
ANTHROPIC_MODEL

Do not remove any other keys. Do not delete the file. If the "env" block becomes empty, remove the empty block too.
Also remove the top-level "model" key if it is set to "sonnet[1m]".

## Step 3: Unset variables in the current shell

Run these commands to clear any active environment variables from the current session:

unset ANTHROPIC_BASE_URL
unset ANTHROPIC_AUTH_TOKEN
unset ANTHROPIC_API_KEY
unset ANTHROPIC_MODEL
unset OPENROUTER_API_KEY

## Step 4: Confirm what you did

List exactly which keys you removed from each file, and which variables you unset. If you found nothing to remove in a step, say so.

Stop there. Do not install anything, do not modify any other files, do not run claude login.

---

**INEMA** · 2026-03-18

ja mudou o Claude tem 1m

---

**INEMA** · 2026-03-18

Custos e  Configurando Claude Code
