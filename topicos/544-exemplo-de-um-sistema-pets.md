# Exemplo de um Sistema PETS

> Tópico 544 · 10 mensagens úteis de 25 totais

---

**INEMA** · 2025-08-30

:\Users\neima\ong_pets

# 2) subir banco
.\start_postgres_pets.ps1 -ContainerName postgres-pets -Port 5433 -Password senha123

# 3) aplicar schema
.\apply_schema_pets.ps1 -SchemaPath .\schema_pets.sql -ContainerName postgres-pets

# 4) gerar config MCP
.\make_mcp_config_pets.ps1 -DbHost localhost -Port 5433 -Database postgres -User postgres -Password senha123 -Ssl $false
```
# exemplos de consultas úteis (para o Painel/Claude.md)

• vacinas vencidas

```sql
SELECT p.id, p.nome, v.nome_vacina, v.data_proxima
FROM pets p
JOIN vacinacoes v ON v.pet_id = p.id
WHERE v.data_proxima < CURRENT_DATE
ORDER BY v.data_proxima ASC;```

• perdidos abertos por bairro

S```ELECT local_perdido, COUNT(*) qtd
FROM perdidos_achados
WHERE status = 'perdido'
GROUP BY local_perdido
ORDER BY qtd DESC;
```
• doações no mês atual

S```ELECT DATE_TRUNC('day', data) dia, SUM(valor) total
FROM doacoes
WHERE DATE_TRUNC('month', data) = DATE_TRUNC('month', CURRENT_DATE)
GROUP BY dia ORDER BY dia;
```
# notificações

• regra padrão: toda ação relevante gera um evento → T`elegram BOT `interno recebe um resumo (novo perdido, encontrado, doação registrada, vacina vencida).
• opcional: disparo para o tutor via WhatsApp (Evolution API) com template curto.

# o que já posso entregar de imediato

1. schema\_pets.sql (acima)
2. versões “pets” dos seus scripts, mantendo o padrão de mensagens/validações que você já usa
3. Claude.md novo com exemplos em linguagem de pets (substitui o atual )
4. checklist de variáveis de “Segredos” para colar no .env

# confirme para eu ajustar os arquivos agora

1. quer usar p`ostgres-pets `na porta 5433?
2. prefere o nome do produto como “ONG Pets” ou outro da lista?
3. quer que eu já gere o Claude.md novo com as perguntas/SQL de exemplo acima e adapte seus scripts para os nomes “pets”?

se disser “sim, porta 5433, nome ONG Pets”, eu já te devolvo o kit completo (schema\_pets.sql + scripts .ps1 ajustados + Claude.md pronto).

---

**INEMA** · 2025-08-30

“ONG de Pets” com web + WhatsApp + e-mail + Telegram + RAG. Vou partir do kit que você já tem (schema.sql, Claude.md, mcp.config.json) e propor a versão “pets” mantendo o mesmo estilo de automação e validação que você usou no projeto anterior   .

# resumo

• um login simples (e-mail ou WhatsApp) + senha
• painel estilo corporativo (KPIs, listas e filtros)
• integrações centralizadas em Segredos (.env e/ou tabela)
• fluxo completo: cadastro pessoas/pets → perdidos/achados → vacinação → doações PIX → notificações (Telegram interno + WhatsApp/e-mail externo)
• base RAG em português para dúvidas de cuidados, treinamento e medicamentos

# nomes sugeridos (módulos/serviços)

| área             | nomes sugeridos                                                                                                            |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------- |
| produto          | ONG Pets, Inema Pets Hub, PetSinal, PataFácil                                                                              |
| backend/api      | PetsCore API, PetBridge, PataAPI                                                                                           |
| web app          | Painel PataDesk, Console ONG Pets                                                                                          |
| whatsapp         | ChatPets WA (instância Evolution), Fluxo Resgate Rápido                                                                    |
| e-mail           | PetMail                                                                                                                    |
| telegram interno | PetAlert BOT                                                                                                               |
| RAG              | PetKnowledge, CuidaRAG                                                                                                     |
| segredos         | SecretsVault (tabela + .env)                                                                                               |
| banco Docker     | postgres-pets                                                                                                              |
| scripts          | start\_postgres\_pets.ps1, apply\_schema\_pets.ps1, make\_mcp\_config\_pets.ps1, verify\_db\_pets.ps1, test\_pets\_env.ps1 |

# modelo de dados proposto (schema\_pets.sql)

```sql
-- pessoas e autenticação
CREATE TABLE IF NOT EXISTS pessoas (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  email TEXT UNIQUE,
  whatsapp TEXT UNIQUE,
  cpf TEXT,
  endereco TEXT,
  data_cadastro TIMESTAMP DEFAULT now()
);

CREATE TABLE IF NOT EXISTS usuarios (
  id SERIAL PRIMARY KEY,
  pessoa_id INT REFERENCES pessoas(id) ON DELETE CASCADE,
  login TEXT UNIQUE NOT NULL,              -- email OU whatsapp
  password_hash TEXT NOT NULL,
  ativo BOOLEAN DEFAULT TRUE,
  ultimo_login TIMESTAMP
);

-- pets e status
CREATE TYPE pet_status AS ENUM ('disponivel','adotado','perdido','achado','em_lar_temporario');
CREATE TABLE IF NOT EXISTS pets (
  id SERIAL PRIMARY KEY,
  pessoa_id INT REFERENCES pessoas(id),    -- tutor atual (quando houver)
  nome TEXT,
  especie TEXT,                            -- cão, gato...
  raca TEXT,
  sexo TEXT,
  idade_anos NUMERIC,
  cor TEXT,
  microchip TEXT,
  status pet_status DEFAULT 'disponivel',
  foto_url TEXT
);

-- perdidos e achados
CREATE TYPE pa_status AS ENUM ('perdido','encontrado','devolvido');
CREATE TABLE IF NOT EXISTS perdidos_achados (
  id SERIAL PRIMARY KEY,
  pet_id INT REFERENCES pets(id) ON DELETE CASCADE,
  status pa_status NOT NULL,
  data_perdido TIMESTAMP,
  local_perdido TEXT,
  data_encontrado TIMESTAMP,
  local_encontrado TEXT,
  observacao TEXT
);

-- vacinação
CREATE TABLE IF NOT EXISTS vacinacoes (
  id SERIAL PRIMARY KEY,
  pet_id INT REFERENCES pets(id) ON DELETE CASCADE,
  nome_vacina TEXT NOT NULL,
  data_aplicacao DATE NOT NULL,
  data_proxima DATE,
  veterinario TEXT,
  observacao TEXT
);

-- doações
CREATE TABLE IF

---

**INEMA** · 2025-08-30

vacinação, doações e comunicação multicanal, transformando-as em SQL auditável e texto claro.

Regras
- login é único por `usuarios.login` (email ou whatsapp) + `password_hash`
- pet “em atenção” = vacina vencida OU próxima em <= 7 dias
- perdidos abertos = registros com status = 'perdido' sem data_encontrado
- doações do mês = DATE_TRUNC('month', data) = DATE_TRUNC('month', CURRENT_DATE)
- sempre explique a lógica em 1–2 frases antes dos dados
- limitar a 100 linhas por padrão

Exemplos

Usuário: listar pets com vacina vencida
SQL:
SELECT p.id, p.nome, v.nome_vacina, v.data_proxima
FROM pets p
JOIN vacinacoes v ON v.pet_id = p.id
WHERE v.data_proxima < CURRENT_DATE
ORDER BY v.data_proxima ASC
LIMIT 100;

Usuário: perdidos por bairro (abertos)
SQL:
SELECT local_perdido, COUNT(*) qtd
FROM perdidos_achados
WHERE status = 'perdido'
GROUP BY local_perdido
ORDER BY qtd DESC
LIMIT 100;

Usuário: total de doações no mês atual
SQL:
SELECT SUM(valor) total
FROM doacoes
WHERE DATE_TRUNC('month', data) = DATE_TRUNC('month', CURRENT_DATE);
"""

env_example = r"""# .env.example — Segredos
EVOLUTION_API_URL=
EVOLUTION_API_TOKEN=
WA_BUSINESS_NUMBER_ID=
SMTP_HOST=
SMTP_USER=
SMTP_PASS=
TELEGRAM_BOT_TOKEN=
TELEGRAM_CHAT_ID_INTERNO=
PIX_CHAVE=
DB_HOST=localhost
DB_PORT=5433
DB_USER=postgres
DB_PASS=senha123
DB_NAME=postgres
"""

files = {
  "schema_pets.sql": schema_pets,
  "start_postgres_pets.ps1": start_ps,
  "apply_schema_pets.ps1": apply_ps,
  "make_mcp_config_pets.ps1": make_ps,
  "verify_db_pets.ps1": verify_ps,
  "test_pets_env.ps1": test_ps,
  "Claude.md": claude_md,
  ".env.example": env_example
}

for name, content in files.items():
  with open(os.path.join(base, name), "w", encoding="utf-8") as f:
    f.write(content)

base

---

**INEMA** · 2025-08-30

) ===" -ForegroundColor Cyan

try { docker --version | Out-Null } catch { ERR "Docker não encontrado"; exit 1 }
try { docker info | Out-Null } catch { ERR "Docker Engine não está em execução"; exit 1 }

$exists = docker ps -a --filter "name=$ContainerName" --format "{{.Names}}"
if (-not $exists) { ERR "Container '$ContainerName' não encontrado"; exit 1 }
$running = docker inspect -f "{{.State.Running}}" $ContainerName
if ($running -ne "true") { docker start $ContainerName | Out-Null }

# checar tabelas principais
$tables = @"
SELECT 
  to_regclass('public.pessoas'),
  to_regclass('public.pets'),
  to_regclass('public.vacinacoes'),
  to_regclass('public.perdidos_achados'),
  to_regclass('public.doacoes');
"@
$tbl = docker exec -i $ContainerName psql -U postgres -At -c "$tables"
if ($LASTEXITCODE -ne 0) { ERR "Falha ao consultar tabelas"; exit 1 }
OK "Tabelas essenciais ok"

# consultas de sanidade
$query1 = "SELECT p.id, p.nome, v.nome_vacina, v.data_proxima FROM pets p JOIN vacinacoes v ON v.pet_id = p.id WHERE v.data_proxima < CURRENT_DATE ORDER BY v.data_proxima ASC LIMIT 50;"
$query2 = "SELECT local_perdido, COUNT(*) qtd FROM perdidos_achados WHERE status = 'perdido' GROUP BY local_perdido ORDER BY qtd DESC;"
$query3 = "SELECT DATE_TRUNC('day', data) dia, SUM(valor) total FROM doacoes WHERE DATE_TRUNC('month', data) = DATE_TRUNC('month', CURRENT_DATE) GROUP BY dia ORDER BY dia;"

Write-Host "`n-- Vacinas vencidas --" -ForegroundColor DarkCyan
docker exec -i $ContainerName psql -U postgres -F "," -A -c "$query1"

Write-Host "`n-- Perdidos por bairro --" -ForegroundColor DarkCyan
docker exec -i $ContainerName psql -U postgres -F "," -A -c "$query2"

Write-Host "`n-- Doações no mês --" -ForegroundColor DarkCyan
docker exec -i $ContainerName psql -U postgres -F "," -A -c "$query3"

# exportar csvs
if (-not (Test-Path $OutDir)) { New-Item -Path $OutDir -ItemType Directory | Out-Null }
docker exec -i $ContainerName psql -U postgres -c "COPY (SELECT * FROM pets ORDER BY id) TO '/tmp/pets.csv' WITH CSV HEADER"
docker cp "${ContainerName}:/tmp/pets.csv" (Join-Path $OutDir "pets.csv") | Out-Null
OK ("CSV salvo em " + (Join-Path $OutDir "pets.csv"))
"""

test_ps = r"""# test_pets_env.ps1 — Etapa 0 (checagem geral)
Param(
  [switch]$AutoCreateContainer = $false,
  [string]$ContainerName = "postgres-pets",
  [string]$PostgresPassword = "senha123",
  [int]$Port = 5433
)

$ErrorActionPreference = "Stop"
function OK($m){ Write-Host "[OK] $m" -ForegroundColor Green }
function ERR($m){ Write-Host "[ERRO] $m" -ForegroundColor Red }
function INFO($m){ Write-Host "[INFO] $m" -ForegroundColor Yellow }

Write-Host "===== Teste do Ambiente: ONG Pets =====" -ForegroundColor Cyan

# docker
try { docker --version | Out-Null; OK "Docker encontrado" } catch { ERR "Docker não encontrado"; exit 1 }
try { docker info | Out-Null; OK "Docker em execução" } catch { ERR "Docker não está em execução"; exit 1 }

# container
$container = (docker ps -a --filter "name=$ContainerName" --format "{{.Names}}|{{.Status}}")
if (-not $container) {
  if ($AutoCreateContainer) {
    INFO "Criando container $ContainerName na porta $Port..."
    docker run --name $ContainerName -e POSTGRES_PASSWORD=$PostgresPassword -p ${Port}:5432 -d postgres:latest | Out-Null
  } else {
    ERR "Container ausente. Rode start_postgres_pets.ps1 ou use -AutoCreateContainer"; exit 1
  }
} else { OK "Container encontrado: $container" }

# pg pronto
docker exec $ContainerName pg_isready -U postgres

# arquivos locais
$root = (Get-Location).Path
foreach ($f in @("schema_pets.sql","make_mcp_config_pets.ps1","apply_schema_pets.ps1")) {
  if (Test-Path (Join-Path $root $f)) { OK "$f encontrado" } else { ERR "$f não encontrado" }
}

Write-Host "===== Fim do teste =====" -ForegroundColor Cyan
"""

claude_md = r"""# ONG de Pets — Guia de Perguntas (Claude)

Você está conectado a um Postgres com tabelas: pessoas, usuarios, pets, perdidos_achados, vacinacoes, doacoes, notificacoes, mensagens_whatsapp, base_conhecimento, segredos.

Objetivo
Responder perguntas sobre cadastro, perdidos/achados,

---

**INEMA** · 2025-08-30

e.Running}}" $ContainerName
  if ($running -ne "true") {
    docker start $ContainerName | Out-Null
    Write-Host "[OK] Container iniciado" -ForegroundColor Green
  } else {
    Write-Host "[OK] Container já em execução" -ForegroundColor Green
  }
} else {
  docker run --name $ContainerName -e POSTGRES_PASSWORD=$Password -p ${Port}:5432 -d postgres:latest | Out-Null
  if ($LASTEXITCODE -ne 0) { Write-Host "[ERRO] Falha ao criar container" -ForegroundColor Red; exit 1 }
  Write-Host "[OK] Container criado e em execução" -ForegroundColor Green
}

Start-Sleep -Seconds 3
docker exec $ContainerName pg_isready -U postgres
"""

apply_ps = r"""# apply_schema_pets.ps1 — Etapa 2
Param(
  [string]$SchemaPath = ".\schema_pets.sql",
  [string]$ContainerName = "postgres-pets"
)

$ErrorActionPreference = "Stop"
function OK($m){ Write-Host "[OK] $m" -ForegroundColor Green }
function ERR($m){ Write-Host "[ERRO] $m" -ForegroundColor Red }
function INFO($m){ Write-Host "[INFO] $m" -ForegroundColor Yellow }

Write-Host "=== Aplicando schema_pets.sql e validando ===" -ForegroundColor Cyan

try { docker --version | Out-Null } catch { ERR "Docker não encontrado"; exit 1 }
try { docker info | Out-Null } catch { ERR "Docker não está em execução"; exit 1 }

$exists = docker ps -a --filter "name=$ContainerName" --format "{{.Names}}"
if (-not $exists) { ERR "Container '$ContainerName' não existe. Rode start_postgres_pets.ps1"; exit 1 }

if (-not (Test-Path $SchemaPath)) { ERR "Arquivo não encontrado: $SchemaPath"; exit 1 }
OK "schema encontrado: $SchemaPath"

INFO "Copiando schema para o container..."
docker cp $SchemaPath "${ContainerName}:/tmp/schema_pets.sql" | Out-Null

INFO "Aplicando schema dentro do container..."
$apply = docker exec -i $ContainerName psql -U postgres -f /tmp/schema_pets.sql
if ($LASTEXITCODE -ne 0) { ERR "Falha ao aplicar schema"; Write-Host $apply; exit 1 } else { OK "Schema aplicado" }

$tables = @"
SELECT
  to_regclass('public.pessoas'),
  to_regclass('public.usuarios'),
  to_regclass('public.pets'),
  to_regclass('public.perdidos_achados'),
  to_regclass('public.vacinacoes'),
  to_regclass('public.doacoes'),
  to_regclass('public.notificacoes'),
  to_regclass('public.mensagens_whatsapp'),
  to_regclass('public.base_conhecimento'),
  to_regclass('public.segredos');
"@

$tbl = docker exec -i $ContainerName psql -U postgres -At -c "$tables"
if ($LASTEXITCODE -ne 0) { ERR "Falha ao validar tabelas"; exit 1 }
OK "Tabelas criadas/ok:"
Write-Host $tbl
"""

make_ps = r"""# make_mcp_config_pets.ps1 — Etapa 3
Param(
  [string]$DbHost = "localhost",
  [int]$Port = 5433,
  [string]$Database = "postgres",
  [string]$User = "postgres",
  [string]$Password = "senha123",
  [bool]$Ssl = $false,
  [string]$OutPath = ".\mcp.config.json"
)

$ErrorActionPreference = "Stop"
function OK($m){ Write-Host "[OK] $m" -ForegroundColor Green }
function ERR($m){ Write-Host "[ERRO] $m" -ForegroundColor Red }

Write-Host "=== Gerando mcp.config.json (pets) ===" -ForegroundColor Cyan

$jsonObj = @{
  servers = @{
    postgres = @{
      type = "postgres"
      host = $DbHost
      port = $Port
      database = $Database
      user = $User
      password = $Password
      ssl = $Ssl
    }
  }
}

try {
  $json = $jsonObj | ConvertTo-Json -Depth 6
  $json | Out-File -FilePath $OutPath -Encoding UTF8 -Force
  OK ("Arquivo salvo: " + $OutPath)
  $check = Get-Content $OutPath -Raw | ConvertFrom-Json
  if ($null -eq $check.servers.postgres) { ERR "Bloco servers.postgres ausente"; exit 1 }
  OK ("JSON válido host=" + $check.servers.postgres.host + " port=" + $check.servers.postgres.port)
} catch {
  ERR ("Falha: " + $_.Exception.Message); exit 1
}
"""

verify_ps = r"""# verify_db_pets.ps1 — Etapa 4
Param(
  [string]$ContainerName = "postgres-pets",
  [string]$OutDir = ".\out"
)

$ErrorActionPreference = "Stop"
function OK($m){ Write-Host "[OK] $m" -ForegroundColor Green }
function ERR($m){ Write-Host "[ERRO] $m" -ForegroundColor Red }
function INFO($m){ Write-Host "[INFO] $m" -ForegroundColor Yellow }

Write-Host "=== Verificando DB e exportando amostras (pets

---

**INEMA** · 2025-08-30

# Create project files for ONG Pets
import os, textwrap, json, pathlib

base = "/mnt/data/ong_pets_kit"
os.makedirs(base, exist_ok=True)

schema_pets = r"""-- schema_pets.sql — ONG de Pets (PT-BR)

-- pessoas e autenticação
CREATE TABLE IF NOT EXISTS pessoas (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  email TEXT UNIQUE,
  whatsapp TEXT UNIQUE,
  cpf TEXT,
  endereco TEXT,
  data_cadastro TIMESTAMP DEFAULT now()
);

CREATE TABLE IF NOT EXISTS usuarios (
  id SERIAL PRIMARY KEY,
  pessoa_id INT REFERENCES pessoas(id) ON DELETE CASCADE,
  login TEXT UNIQUE NOT NULL,              -- email OU whatsapp
  password_hash TEXT NOT NULL,
  ativo BOOLEAN DEFAULT TRUE,
  ultimo_login TIMESTAMP
);

-- pets e status
DO $$ BEGIN
  CREATE TYPE pet_status AS ENUM ('disponivel','adotado','perdido','achado','em_lar_temporario');
EXCEPTION
  WHEN duplicate_object THEN NULL;
END $$;

CREATE TABLE IF NOT EXISTS pets (
  id SERIAL PRIMARY KEY,
  pessoa_id INT REFERENCES pessoas(id),
  nome TEXT,
  especie TEXT,
  raca TEXT,
  sexo TEXT,
  idade_anos NUMERIC,
  cor TEXT,
  microchip TEXT,
  status pet_status DEFAULT 'disponivel',
  foto_url TEXT
);

-- perdidos e achados
DO $$ BEGIN
  CREATE TYPE pa_status AS ENUM ('perdido','encontrado','devolvido');
EXCEPTION
  WHEN duplicate_object THEN NULL;
END $$;

CREATE TABLE IF NOT EXISTS perdidos_achados (
  id SERIAL PRIMARY KEY,
  pet_id INT REFERENCES pets(id) ON DELETE CASCADE,
  status pa_status NOT NULL,
  data_perdido TIMESTAMP,
  local_perdido TEXT,
  data_encontrado TIMESTAMP,
  local_encontrado TEXT,
  observacao TEXT
);

-- vacinação
CREATE TABLE IF NOT EXISTS vacinacoes (
  id SERIAL PRIMARY KEY,
  pet_id INT REFERENCES pets(id) ON DELETE CASCADE,
  nome_vacina TEXT NOT NULL,
  data_aplicacao DATE NOT NULL,
  data_proxima DATE,
  veterinario TEXT,
  observacao TEXT
);

-- doações
CREATE TABLE IF NOT EXISTS doacoes (
  id SERIAL PRIMARY KEY,
  pessoa_id INT REFERENCES pessoas(id),
  valor NUMERIC(12,2) NOT NULL,
  data TIMESTAMP DEFAULT now(),
  metodo TEXT DEFAULT 'PIX',
  tx_id TEXT,
  descricao TEXT
);

-- notificações e mensagens
DO $$ BEGIN
  CREATE TYPE notif_canal AS ENUM ('email','whatsapp','telegram');
EXCEPTION
  WHEN duplicate_object THEN NULL;
END $$;

CREATE TABLE IF NOT EXISTS notificacoes (
  id SERIAL PRIMARY KEY,
  pessoa_id INT REFERENCES pessoas(id),
  canal notif_canal NOT NULL,
  mensagem TEXT NOT NULL,
  data_envio TIMESTAMP DEFAULT now(),
  status TEXT
);

CREATE TABLE IF NOT EXISTS mensagens_whatsapp (
  id SERIAL PRIMARY KEY,
  pessoa_id INT REFERENCES pessoas(id),
  conteudo TEXT,
  data_hora TIMESTAMP DEFAULT now(),
  direcao TEXT,
  status TEXT
);

-- base de conhecimento (RAG)
CREATE TABLE IF NOT EXISTS base_conhecimento (
  id SERIAL PRIMARY KEY,
  titulo TEXT,
  corpo TEXT,
  tags TEXT[]
);

-- segredos/configurações centralizadas
CREATE TABLE IF NOT EXISTS segredos (
  chave TEXT PRIMARY KEY,
  valor TEXT NOT NULL,
  atualizado_em TIMESTAMP DEFAULT now()
);

-- índices
CREATE INDEX IF NOT EXISTS idx_pessoas_nome ON pessoas(nome);
CREATE INDEX IF NOT EXISTS idx_pets_status ON pets(status);
CREATE INDEX IF NOT EXISTS idx_pa_status ON perdidos_achados(status);
CREATE INDEX IF NOT EXISTS idx_vac_proxima ON vacinacoes(data_proxima);
CREATE INDEX IF NOT EXISTS idx_doacoes_data ON doacoes(data);
"""

start_ps = r"""# start_postgres_pets.ps1 — Etapa 1
Param(
  [string]$ContainerName = "postgres-pets",
  [string]$Password = "senha123",
  [int]$Port = 5433
)

Write-Host "=== Subindo Postgres '$ContainerName' na porta $Port ===" -ForegroundColor Cyan

try { docker --version | Out-Null; Write-Host "[OK] Docker encontrado" -ForegroundColor Green } catch { Write-Host "[ERRO] Docker não encontrado" -ForegroundColor Red; exit 1 }
try { docker info | Out-Null; Write-Host "[OK] Docker Engine em execução" -ForegroundColor Green } catch { Write-Host "[ERRO] Docker não está em execução" -ForegroundColor Red; exit 1 }

$exists = docker ps -a --filter "name=$ContainerName" --format "{{.Names}}"
if ($exists -eq $ContainerName) {
  $running = docker inspect -f

---

**INEMA** · 2025-08-30

Gerei um kit completo com schema, scripts e guia prontos para rodar.

download do kit
baixar pasta ong\_pets\_kit (zip manual: clique e navegue)

o que vem no kit

1. schema\_pets.sql
2. start\_postgres\_pets.ps1
3. apply\_schema\_pets.ps1
4. make\_mcp\_config\_pets.ps1
5. verify\_db\_pets.ps1
6. test\_pets\_env.ps1
7. Claude.md
8. .env.example

como rodar (Windows PowerShell)

1. criar pasta do projeto e copiar o kit
   Copie o conteúdo da pasta baixada para C:\Users\neima\ong\_pets

2. subir o banco

   ```   cd C:\Users\neima\ong_pets
   .\start_postgres_pets.ps1 -ContainerName postgres-pets -Port 5433 -Password senha123
   ```

3. aplicar o schema

   ```   .\apply_schema_pets.ps1 -SchemaPath .\schema_pets.sql -ContainerName postgres-pets
   ```

4. gerar mcp.config.json

   ```   .\make_mcp_config_pets.ps1 -DbHost localhost -Port 5433 -Database postgres -User postgres -Password senha123 -Ssl $false
   ```

5. validar e exportar amostras

   ```   .\verify_db_pets.ps1 -ContainerName postgres-pets -OutDir .\out
   ```

6. teste rápido do ambiente

   ```   .\test_pets_env.ps1 -AutoCreateContainer
   ```

resumo
• login único por email ou whatsapp + senha
• painel poderá usar as consultas já prontas (vacinas vencidas, perdidos abertos, doações do mês)
• segredos centralizados via .env e/ou tabela segredos
• RAG em português com base\_conhecimento e tags simples

---

**INEMA** · 2025-08-30

**projeto ONG Pets** com os arquivos e scripts que montamos:

## 1. Estrutura do banco (schema\_pets.sql)

* **pessoas** → cadastro de voluntários, adotantes e doadores.
* **usuarios** → login único (email ou WhatsApp) + senha.
* **pets** → informações dos animais (nome, espécie, status, tutor etc.).
* **perdidos\_achados** → registro de animais perdidos/encontrados.
* **vacinacoes** → controle de vacinas (data aplicada, próxima, veterinário).
* **doacoes** → doações via PIX (valor, data, tx\_id).
* **notificacoes** → disparos internos/externos (email, WhatsApp, Telegram).
* **mensagens\_whatsapp** → histórico de conversas (Evolution API).
* **base\_conhecimento** → conteúdo para RAG (cuidados, medicamentos, treinamento em português).
* **segredos** → chave PIX, tokens de API, SMTP etc.

## 2. Scripts PowerShell

* **start\_postgres\_pets.ps1** → sobe container Docker com Postgres.
* **apply\_schema\_pets.ps1** → aplica schema no banco e valida tabelas.
* **make\_mcp\_config\_pets.ps1** → gera `mcp.config.json` para integração.
* **verify\_db\_pets.ps1** → roda consultas de sanidade (vacinas vencidas, perdidos por bairro, doações do mês) e exporta CSV.
* **test\_pets\_env.ps1** → checa se Docker, banco e arquivos estão prontos.

## 3. Configuração

* **.env.example** → modelo para guardar segredos (WhatsApp Evolution API, Telegram BOT, SMTP, chave PIX).
* **Claude.md** → guia para transformar perguntas em SQL (ex.: “listar pets com vacina vencida”).

## 4. Funcionalidades principais

* **Login**: apenas um por usuário (email ou WhatsApp).
* **Painel web**: estilo corporativo, com métricas (pets cadastrados, vacinas vencidas, perdidos ativos, doações do mês).
* **Integrações**:

  * WhatsApp (Evolution API) → atendimento e notificações externas.
  * Telegram BOT → alertas internos para equipe.
  * E-mail (SMTP) → recibos e comunicações.
  * PIX → registro de doações.
* **RAG em português**: base de conhecimento para consultas sobre saúde, cuidados e treinamento de pets.

---

Em resumo → você terá uma **plataforma de gestão para ONG de Pets**, com banco organizado, scripts para subir o ambiente em minutos, painel web de administração, integrações multicanal (WA, e-mail, Telegram) e inteligência com RAG em português.

---

**INEMA** · 2025-08-30

**sistema de gestão da sua ONG de Pets**.

Em outras palavras, ele é um **pacote completo** (banco de dados + scripts + configurações + integrações) que permite você organizar e automatizar tudo que a ONG precisa:

### o que ele faz

* **Cadastro de pessoas** → voluntários, doadores, adotantes.
* **Cadastro de pets** → informações gerais, fotos, status (adotado, perdido, disponível).
* **Controle de perdidos e achados** → registrar quando um animal some ou é encontrado.
* **Controle de vacinas** → datas aplicadas, próximas doses, alertas de vencimento.
* **Gestão de doações (PIX)** → registrar valor, data, transação, gerar relatórios.
* **Notificações** → via WhatsApp, e-mail e Telegram (avisos internos para a equipe e externos para tutores/adotantes).
* **Histórico de mensagens WhatsApp** → todas as conversas ficam registradas no banco.
* **Base de conhecimento (RAG em português)** → repositório de informações sobre cuidados, medicamentos e treinamentos para responder dúvidas automaticamente.
* **Segredos centralizados** → tokens e chaves de APIs (WhatsApp Evolution API, Telegram BOT, SMTP, PIX) ficam guardados em um só lugar.

### como ele funciona

1. **scripts PowerShell** sobem o banco no Docker, aplicam o schema e geram as configs (tudo automatizado).
2. **painel web estilo corporativo** mostra KPIs (pets cadastrados, perdidos ativos, vacinas vencidas, total de doações).
3. **integrações multicanal**:

   * WhatsApp via Evolution API para comunicação com público.
   * Telegram BOT para alertas internos.
   * E-mail para recibos e confirmações.
   * PIX para doações.
4. **inteligência artificial (RAG)**: perguntas sobre cuidados de pets são respondidas com base na sua própria base de conhecimento em português.

### em resumo

É uma **plataforma completa de administração da ONG de Pets**, que combina banco de dados, painel web, integrações de comunicação e automação inteligente.

---

**INEMA** · 2025-08-30

https://chatgpt.com/c/68b35fbb-5e44-8328-9beb-908bd7a44590
