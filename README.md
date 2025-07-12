## 🧩 Projeto de Automação N8N

Este repositório contém uma configuração Docker Compose para executar o **n8n**, uma ferramenta de automação de fluxo de trabalho, com uma configuração personalizada.

---

## 🚀 Primeiros Passos

Para colocar este projeto em funcionamento, você precisará ter alguns pré-requisitos instalados em seu sistema.

---

## ✅ Pré-requisitos

Você precisará ter o seguinte instalado:

- **Git**: Para clonar o repositório.
- **Docker Desktop** (Windows/macOS) ou **Docker Engine** (Linux): Para executar o serviço n8n em um ambiente conteinerizado.
- **Make**: Para implantar facilmente a configuração do Docker Compose usando o Makefile fornecido.

---

## 🛠️ Guia de Instalação

### 🔵 Windows

#### Instalar Git
1. Baixe o instalador do Git: [https://git-scm.com/downloads](https://git-scm.com/downloads)
2. Execute o instalador e siga as instruções na tela (aceite as opções padrão).

#### Instalar Docker Desktop
1. Baixe: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
2. Durante a instalação, certifique-se de habilitar o **WSL 2**.
3. Após a instalação, inicie o Docker Desktop.

#### Instalar Make

**Opção 1 (Recomendado - via Chocolatey):**
```bash
choco install make
```

### ⚙️ Opção 2 (Manual) – Instalar `make` no Windows

- Baixe o binário do `make` [aqui](http://gnuwin32.sourceforge.net/packages/make.htm)
- Adicione o executável ao `PATH` do sistema

---

### 🔵 Windows (Sem WSL / Usando Hyper-V)

Se você prefere usar o Docker Desktop **sem o WSL 2** e habilitar **Hyper-V**, siga este guia:

---

## 🧰 Requisitos para Habilitar o Hyper-V

Antes de ativar o Hyper-V, certifique-se de que seu sistema atende aos seguintes critérios:

- **Sistema compatível**: Windows 10 ou 11 nas edições **Pro**, **Enterprise** ou **Education**  
- **Processador**: 64 bits com suporte a **SLAT (Second Level Address Translation)**
- **Virtualização ativada**: Verifique na BIOS/UEFI se a virtualização está habilitada
- **Memória RAM mínima**: 4 GB

> ❌ *O Hyper-V não está disponível nas edições Home do Windows*

---

## 🖥️ Método 1: Interface Gráfica (GUI)

1. Abra o menu **Iniciar** e pesquise por `Recursos do Windows`
2. Clique em **Ativar ou desativar recursos do Windows**
3. Marque a opção **Hyper-V** incluindo:
   - Ferramentas de gerenciamento
   - Plataforma Hyper-V
4. Clique em **OK** para instalar
5. Reinicie o computador quando solicitado

---

## 💻 Método 2: PowerShell (Admin)

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```
---

#### ✅ Pré-requisitos

- **Docker Desktop para Windows** com suporte a Hyper-V
- **Git** instalado
- **Make** instalado

---

#### ⚙️ Passo a passo

1. **Instalar Docker Desktop**:

   - Baixe: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
   - Durante a instalação:
     - **Desmarque a opção WSL 2**
     - **Habilite a opção Hyper-V** (o instalador tentará ativar automaticamente)
   - Após instalar, reinicie o computador se solicitado
   - Abra o Docker Desktop e verifique se está funcionando

2. **Instalar Git**:

   - Baixe: [https://git-scm.com/downloads](https://git-scm.com/downloads)
   - Instale usando configurações padrão

3. **Instalar Make** (OPICIONAL):

## 🧰 Instalando Make no Windows via Chocolatey

O [Chocolatey](https://chocolatey.org/) é um gerenciador de pacotes para Windows que facilita a instalação de ferramentas como o `make`.

---

### ✅ Passo 1: Instalar o Chocolatey

Abra o **Prompt de Comando como Administrador** e execute o seguinte comando:

```cmd
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -ExecutionPolicy Bypass -Command "Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = 'Tls12'; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))"
```

### ✅ Passo 2: Instalar o Make
Após instalar o Chocolatey, abra um novo Prompt de Comando como Administrador e execute:

```bash
   choco install make
   ```
### 💡 Para verificar se a instalação foi bem sucedida, execute:

   ```bash
   make --version

   ```
   Você verá a versão instalada no make terminal.
   
---

### 🐧 Linux (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install git docker.io docker-compose make -y
sudo systemctl start docker
sudo systemctl enable docker
```
### ✅ Para permitir que seu usuário execute o Docker sem `sudo`:

```bash
sudo usermod -aG docker $USER
```

==================================================

### 🍎 macOS
Área de trabalho do DockerInstalar o Docker Desktop
Baixe oDocker Desktop para Mac

Instalar o Homebrew (caso ainda não tenha)
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```


```bash
brew install make
```

### 📂 Clonando o Repositório

```bash
git clone https://github.com/seu-usuario/n8n-docker.git
cd n8n-docker
```

### 📦 Executando o Projeto
No diretório do projeto, execute:

```bash
make deploy
```

### CASO TENHA OPTADO POR NÃO USAR O MAKE

```bash
docker compose down -v && docker compose up -d
```

Esse comando irá:

Encerrar containers e volumes existentes

Iniciar o serviço n8n em segundo plano ( modo desanexado )

### 🌐 Acessando uma Interface Web
Abra seu navegador e acesse: [http://localhost:5678](http://localhost:5678)

Você verá a interface do n8n pronta para uso 👀✨

### 📌 Observações Finais
Os dados são persistidos localmente na pasta atual ( ./)

O fuso horário está definido comoAmerica/Sao_Paulo

O contêiner será reiniciado automaticamente em caso de falha