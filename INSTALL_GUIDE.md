# Guia de Instalação do Chat2DB com Docker

Este guia fornece instruções detalhadas para instalar o Chat2DB em diferentes ambientes usando Docker. Foram criados arquivos `docker-compose.yml` otimizados para cada plataforma, facilitando a implantação e o gerenciamento.

## Pré-requisitos

Antes de começar, certifique-se de que você tem o Docker e o Docker Compose instalados em seu sistema:

- **Docker Engine**: Versão 20.10.0 ou superior
- **Docker Compose**: Versão 1.29.0 ou superior (para `docker-compose`) ou Docker Engine 20.10.0+ (para `docker compose`)

## Estrutura do Repositório

Após as modificações, a estrutura do repositório inclui os seguintes arquivos principais:

```
/home/ubuntu/Chat2DB
├── docker-compose.easypanel.yml
├── docker-compose.portainer.yml
├── docker-compose.windows.yml
├── .env.example
└── INSTALL_GUIDE.md
```

- `docker-compose.easypanel.yml`: Configuração otimizada para implantação no Easypanel.
- `docker-compose.portainer.yml`: Configuração otimizada para implantação via Portainer.
- `docker-compose.windows.yml`: Configuração otimizada para Windows (Docker Desktop/WSL).
- `.env.example`: Arquivo de exemplo com variáveis de ambiente para configurar a aplicação.

## Configuração do Ambiente

Antes de iniciar a instalação, é recomendado criar um arquivo `.env` para gerenciar as configurações da aplicação. Copie o arquivo de exemplo:

```bash
cp .env.example .env
```

Edite o arquivo `.env` e ajuste as variáveis conforme necessário, como a porta da aplicação (`CHAT2DB_PORT`), limites de memória (`JAVA_MAX_MEMORY`, `JAVA_MIN_MEMORY`) e o timezone (`TIMEZONE`).

## 1. Instalação no Easypanel

O Easypanel simplifica a implantação de aplicações Docker. Siga os passos abaixo para instalar o Chat2DB.

1.  **Crie um Novo Projeto**: No painel do Easypanel, crie um novo projeto ou selecione um existente.

2.  **Adicione um Novo Serviço**:
    *   Clique em **+ New**.
    *   Selecione a opção para usar um **Docker Compose** file.

3.  **Configure o Serviço**:
    *   **Source**: Escolha a opção de colar o conteúdo do `docker-compose.yml`.
    *   **Conteúdo**: Copie o conteúdo do arquivo `docker-compose.easypanel.yml` e cole no campo de texto.

4.  **Configure as Variáveis de Ambiente**:
    *   Vá para a aba **Environment**.
    *   Copie o conteúdo do seu arquivo `.env` e cole no campo de texto. O Easypanel irá carregar as variáveis automaticamente.

5.  **Implante o Serviço**:
    *   Clique em **Create**.
    *   O Easypanel irá baixar a imagem do Chat2DB e iniciar o contêiner.

6.  **Acesse o Chat2DB**:
    *   Após a implantação, o Easypanel fornecerá um link para acessar a aplicação. A porta padrão é `10824`.

## 2. Instalação no Portainer

O Portainer oferece uma interface gráfica para gerenciar contêineres Docker. A instalação do Chat2DB pode ser feita usando a funcionalidade de "Stacks".

1.  **Acesse o Portainer**: Faça login no seu painel do Portainer.

2.  **Crie uma Nova Stack**:
    *   No menu lateral, clique em **Stacks**.
    *   Clique em **+ Add stack**.

3.  **Configure a Stack**:
    *   **Name**: Dê um nome para a sua stack (ex: `chat2db-stack`).
    *   **Build method**: Selecione **Web editor**.
    *   **Web editor**: Copie o conteúdo do arquivo `docker-compose.portainer.yml` e cole no editor.

4.  **Configure as Variáveis de Ambiente**:
    *   Abaixo do editor, clique em **Advanced options**.
    *   Na seção **Environment variables**, você pode adicionar as variáveis do seu arquivo `.env` uma por uma, ou pode criar um arquivo `.env` no servidor onde o Portainer está rodando e referenciá-lo.
    *   Para uma configuração mais simples, adicione as variáveis manualmente. Clique em **Add environment variable** para cada variável que deseja configurar (ex: `CHAT2DB_PORT`, `JAVA_MAX_MEMORY`, etc.).

5.  **Implante a Stack**:
    *   Clique em **Deploy the stack**.
    *   O Portainer irá baixar a imagem e iniciar os serviços definidos no Docker Compose.

6.  **Acesse o Chat2DB**:
    *   Após a implantação, você pode acessar o Chat2DB no endereço IP do seu host Docker, na porta `10824` (ou na porta que você configurou em `CHAT2DB_PORT`).

## 3. Instalação no Windows (Docker Desktop / WSL)

A instalação no Windows pode ser feita tanto com o Docker Desktop quanto diretamente no WSL (Windows Subsystem for Linux).

### Opção A: Usando o Docker Desktop

Esta é a abordagem mais comum para usuários do Windows.

1.  **Pré-requisitos**:
    *   Instale o [Docker Desktop for Windows](https://www.docker.com/products/docker-desktop).
    *   Certifique-se de que o backend do WSL 2 está ativado no Docker Desktop para melhor performance.

2.  **Clone o Repositório**:
    *   Abra o PowerShell ou o Prompt de Comando.
    *   Clone o seu fork do repositório:
        ```powershell
        git clone https://github.com/BrusCode/Chat2DB.git
        cd Chat2DB
        ```

3.  **Configure o Ambiente**:
    *   Crie o arquivo `.env` a partir do exemplo:
        ```powershell
        copy .env.example .env
        ```
    *   Edite o arquivo `.env` com um editor de texto (como o `notepad` ou `VS Code`) e ajuste as configurações conforme necessário.

4.  **Inicie o Contêiner**:
    *   No mesmo terminal, execute o comando abaixo para iniciar o Chat2DB em segundo plano:
        ```powershell
        docker compose -f docker-compose.windows.yml up -d
        ```

5.  **Acesse o Chat2DB**:
    *   Abra o seu navegador e acesse `http://localhost:10824`.

### Opção B: Usando o WSL 2

Se você prefere trabalhar diretamente no ambiente Linux do WSL, siga estes passos.

1.  **Pré-requisitos**:
    *   Tenha o [WSL 2](https://learn.microsoft.com/pt-br/windows/wsl/install) instalado com uma distribuição Linux (como o Ubuntu).
    *   Instale o Docker e o Docker Compose dentro da sua distribuição WSL.

2.  **Abra o Terminal do WSL**:
    *   Inicie a sua distribuição Linux (ex: `wsl` no PowerShell).

3.  **Clone o Repositório**:
    *   Execute os comandos para clonar o seu fork:
        ```bash
        git clone https://github.com/BrusCode/Chat2DB.git
        cd Chat2DB
        ```

4.  **Configure o Ambiente**:
    *   Crie e edite o arquivo `.env`:
        ```bash
        cp .env.example .env
        nano .env
        ```

5.  **Inicie o Contêiner**:
    *   Execute o comando para iniciar o serviço:
        ```bash
        docker compose -f docker-compose.windows.yml up -d
        ```

6.  **Acesse o Chat2DB**:
    *   O WSL 2 compartilha a rede com o Windows. Você pode acessar o Chat2DB diretamente no navegador do Windows em `http://localhost:10824`.

## Gerenciando o Serviço

Para parar o serviço, navegue até o diretório do projeto e use o comando `down`:

```bash
# Use o arquivo .yml correspondente ao seu ambiente
docker compose -f docker-compose.<seu-ambiente>.yml down
```

Para ver os logs do contêiner:

```bash
docker logs chat2db
```
