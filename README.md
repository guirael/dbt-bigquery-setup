# Setup do Ambiente — DBT + BigQuery

Este guia descreve como configurar um ambiente local para desenvolvimento com **dbt** utilizando **BigQuery** como Data Warehouse.

---

# 1. Pré-requisitos

Antes de iniciar, verifique se você possui instalado:

* Python **3.9 ou superior**
* Gerenciador de ambientes **uv**
* Conta no **Google Cloud Platform**
* Projeto criado no **BigQuery**
* **Service Account (.json)** com permissões de acesso ao BigQuery

---

# 2. Criar Ambiente Virtual e Instalar Dependências

Utilize o **uv** para criar o ambiente virtual e instalar todas as dependências:

```bash
uv sync
```

Esse comando irá:

* Criar o ambiente virtual `.venv`
* Instalar as dependências definidas no `pyproject.toml`

---

# 3. Ativar o Ambiente Virtual

### Linux / Mac

```bash
source .venv/bin/activate
```

### Windows (PowerShell)

```powershell
.venv\Scripts\Activate.ps1
```

---

# 4. Verificar Instalação do DBT

Após ativar o ambiente virtual, verifique se o **dbt** foi instalado corretamente:

```bash
dbt --version
```

Saída esperada (exemplo):

```
Core:
  - installed: 1.x.x
  - latest: 1.x.x

Plugins:
  - bigquery: 1.x.x
```

---

# 5. Criar um Projeto DBT

Inicialize um novo projeto:

```bash
dbt init <nome_projeto>
```

Exemplo:

```bash
dbt init dbt_lab
```

### Importante:
Nessa etapa siga as interações com o terminal, pois será criado a partir disso o `profiles.yaml`

Entre na pasta do projeto criado:

```bash
cd dbt_lab
```

---

# 6. Testar a Configuração

Execute o comando abaixo **dentro da pasta do projeto dbt**:

```bash
dbt debug
```

Se tudo estiver correto, você verá:

```
Connection test: OK
All checks passed!
```

---

# 7. Comandos Básicos do DBT

Após o setup, alguns comandos úteis:

```bash
dbt run
dbt test
dbt build
dbt docs generate
dbt docs serve
```

Descrição:

* `dbt run` → executa os modelos
* `dbt test` → executa testes definidos no projeto
* `dbt build` → executa run + tests
* `dbt docs generate` → gera documentação
* `dbt docs serve` → sobe servidor local da documentação

---

# 8. Fluxo Completo de Setup

```bash
uv sync

# ativar ambiente
source .venv/bin/activate
# ou
.venv\Scripts\Activate.ps1

# verificar instalação
dbt --version

# criar projeto
dbt init dbt_lab
cd dbt_lab

# testar conexão
dbt debug
```

---
