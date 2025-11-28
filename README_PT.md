# Chat2DB - Instalação Simplificada com Docker

Este repositório é um fork do [Chat2DB](https://github.com/CodePhiliaX/Chat2DB) com configurações Docker Compose otimizadas para facilitar a instalação em diferentes ambientes.

## O que é o Chat2DB?

O Chat2DB é um cliente SQL inteligente e versátil que integra capacidades de IA (ChatGPT) para gerenciamento de bancos de dados. Ele suporta mais de 16 tipos de bancos de dados, incluindo MySQL, PostgreSQL, Oracle, SQL Server, MongoDB, Redis e muitos outros.

## Principais Recursos

- **Geração Inteligente de SQL**: Suporte a desenvolvimento SQL orientado por IA para escrever consultas mais rapidamente.
- **Gerenciamento de Banco de Dados**: Suporta mais de 16 bancos de dados diferentes.
- **Geração Inteligente de Relatórios**: Criação de dashboards com auxílio de IA.
- **Sincronização de Estrutura de Dados**: Sincronize estruturas de tabelas entre bancos de dados.
- **Editor Visual de Tabelas**: Interface gráfica para edição de dados.
- **Console SQL**: Execute e formate consultas SQL.

## Novidades deste Fork

Este fork adiciona configurações Docker Compose otimizadas para diferentes plataformas:

- **Easypanel**: Implantação simplificada em ambientes Easypanel.
- **Portainer**: Configuração pronta para uso via Portainer Stacks.
- **Windows (Docker Desktop/WSL)**: Suporte completo para Windows com Docker Desktop ou WSL 2.

## Arquivos Adicionados

- `docker-compose.easypanel.yml`: Configuração otimizada para Easypanel.
- `docker-compose.portainer.yml`: Configuração otimizada para Portainer.
- `docker-compose.windows.yml`: Configuração otimizada para Windows.
- `.env.example`: Arquivo de exemplo com variáveis de ambiente configuráveis.
- `INSTALL_GUIDE.md`: Guia completo de instalação para cada plataforma.

## Início Rápido

### 1. Clone o Repositório

```bash
git clone https://github.com/BrusCode/Chat2DB.git
cd Chat2DB
```

### 2. Configure as Variáveis de Ambiente

```bash
cp .env.example .env
```

Edite o arquivo `.env` e ajuste as configurações conforme necessário.

### 3. Escolha Seu Ambiente e Inicie

#### Para Easypanel

Siga as instruções no [Guia de Instalação](INSTALL_GUIDE.md#1-instalação-no-easypanel).

#### Para Portainer

Siga as instruções no [Guia de Instalação](INSTALL_GUIDE.md#2-instalação-no-portainer).

#### Para Windows (Docker Desktop)

```powershell
docker compose -f docker-compose.windows.yml up -d
```

#### Para Linux/WSL

```bash
docker compose -f docker-compose.windows.yml up -d
```

### 4. Acesse o Chat2DB

Abra seu navegador e acesse: `http://localhost:10824`

## Documentação Completa

Para instruções detalhadas de instalação e configuração, consulte o [Guia de Instalação](INSTALL_GUIDE.md).

## Requisitos do Sistema

- **Docker Engine**: Versão 20.10.0 ou superior
- **Docker Compose**: Versão 1.29.0 ou superior
- **CPU**: 2 núcleos ou mais (recomendado)
- **RAM**: 4 GB ou mais (recomendado)

## Configurações Disponíveis

Todas as configurações podem ser ajustadas através do arquivo `.env`:

- `CHAT2DB_PORT`: Porta de acesso à aplicação (padrão: 10824)
- `JAVA_MAX_MEMORY`: Memória máxima da JVM (padrão: 2g)
- `JAVA_MIN_MEMORY`: Memória mínima da JVM (padrão: 512m)
- `TIMEZONE`: Fuso horário do sistema (padrão: America/Sao_Paulo)
- `CHATGPT_API_KEY`: Chave da API do ChatGPT (opcional)

## Suporte

Para questões relacionadas ao Chat2DB original, consulte o [repositório oficial](https://github.com/CodePhiliaX/Chat2DB).

Para questões relacionadas às configurações Docker deste fork, abra uma issue neste repositório.

## Licença

Este projeto mantém a mesma licença do projeto original: [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0), complementada pela [Chat2DB License](./Chat2DB_LICENSE).

## Agradecimentos

Agradecimentos especiais à equipe do Chat2DB pelo excelente trabalho no projeto original.
