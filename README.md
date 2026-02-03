# Ambiente de Estudo n8n (Docker)
Este repositório contém a infraestrutura necessária para subir um ambiente completo de automação com n8n, utilizando PostgreSQL como banco de dados principal e Redis para gerenciamento de filas (Queue Mode).

## 🚀 Estrutura do Projeto
O ambiente é composto pelos seguintes serviços:

* n8n: Ferramenta de automação baseada em nós.
* PostgreSQL: Banco de dados relacional para persistência de dados.
* Redis: Utilizado para otimizar a performance via queue mode.

## 🛠️ Pré-requisitos
* Docker Desktop instalado (Windows 11 recomendado).
* WSL2 configurado e atualizado.

## ⚙️ Configuração Inicial
Antes de subir os containers, você deve configurar suas variáveis de ambiente:

* Renomeie o arquivo .env-TEMPLATE para .env.
* Edite o arquivo .env e substitua as informações de exemplo pelas credenciais do seu projeto:
  * N8N_USER e N8N_PASSWORD: Credenciais para acesso ao painel do n8n.
  * POSTGRES_DB, POSTGRES_USER e POSTGRES_PASSWORD: Dados de conexão para o banco de dados.

[!IMPORTANT]
Segurança: Nunca realize o commit do arquivo .env no Git. Utilize senhas fortes contendo letras, números e símbolos.

## 📦 Como rodar
Com o terminal aberto na pasta raiz do projeto, execute os comandos abaixo na sequência:

### PowerShell
1. Construir a imagem customizada
docker-compose build --no-cache
2. Subir os serviços em segundo plano
docker-compose up -d

## 📋 Informações Técnicas
* Persistência: Foram configurados volumes locais nomeados (n8n_data, postgres_data, redis_data) para garantir que seus fluxos e dados não sejam perdidos ao reiniciar os containers.
* Performance: O ambiente já conta com limites de CPU e Memória definidos para evitar travamentos no Docker Desktop.
* Modo de Execução: Configurado por padrão em queue mode para suportar maior volume de execuções simultâneas.
