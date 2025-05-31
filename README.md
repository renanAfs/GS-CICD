# Usuários Service

Um serviço web simples para cadastro de usuários, desenvolvido com Flask. Permite cadastrar novos usuários via formulário web e consultar o status do serviço.

## Índice

- [Descrição](#descrição)
- [Funcionalidades](#funcionalidades)
- [Rotas da API](#rotas-da-api)
- [Como Executar Localmente](#como-executar-localmente)
- [Execução com Docker](#execução-com-docker)
- [Integração Contínua (CI/CD)](#integração-contínua-cicd)
- [Exemplo de Uso](#exemplo-de-uso)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Dependências](#dependências)
- [Licença](#licença)

## Descrição

Este projeto é um serviço web para cadastro de usuários. Ele oferece uma interface simples para inserir nome e e-mail, armazenando os dados temporariamente (em memória). Também possui uma rota para verificar o status do serviço.

## Funcionalidades

- Cadastro de usuários via formulário web.
- Exibição de mensagem de sucesso após cadastro.
- Rota de status para monitoramento do serviço.

## Rotas da API

- `GET /`  
  Exibe o formulário de cadastro de usuários.

- `POST /`  
  Processa os dados enviados pelo formulário e retorna uma mensagem de sucesso.

- `GET /status`  
  Retorna um JSON com o status do serviço.

## Como Executar Localmente

1. Certifique-se de ter o Python 3.x instalado.
2. Instale as dependências:
   ```powershell
   pip install -r requirements.txt
   ```
3. Inicie o servidor Flask:
   ```powershell
   python app.py
   ```
4. Acesse `http://localhost:8080` no navegador.

## Execução com Docker

1. Construa a imagem Docker:
   ```powershell
   docker build -t usuarios-service .
   ```
2. Execute o container:
   ```powershell
   docker run -p 8080:8080 usuarios-service
   ```
3. O serviço estará disponível em `http://localhost:8080`.

Ou utilize o Docker Compose:
```powershell
docker-compose up --build
```

## Integração Contínua (CI/CD)

Este projeto inclui um `Jenkinsfile` para automação de build, testes e deploy utilizando Jenkins. Para utilizar:
- Configure um pipeline no Jenkins apontando para este repositório.
- O pipeline executará as etapas definidas no `Jenkinsfile`.

## Exemplo de Uso

1. Acesse `http://localhost:8080`.
2. Preencha o formulário com nome e e-mail.
3. Clique em "Cadastrar".
4. Veja a mensagem de sucesso com os dados cadastrados.

## Estrutura do Projeto

- `app.py` — Código principal do serviço Flask.
- `requirements.txt` — Lista de dependências Python.
- `Dockerfile` — Configuração para containerização com Docker.
- `docker-compose.yml` — Orquestração de containers.
- `Jenkinsfile` — Pipeline de CI/CD para Jenkins.
- `README.md` — Documentação do projeto.

## Dependências

- Flask

Instale todas as dependências com:
```powershell
pip install -r requirements.txt
```

## Licença
... (6 linhas)
Recolher
README.md
3 KB
﻿
# Usuários Service

Um serviço web simples para cadastro de usuários, desenvolvido com Flask. Permite cadastrar novos usuários via formulário web e consultar o status do serviço.

## Índice

- [Descrição](#descrição)
- [Funcionalidades](#funcionalidades)
- [Rotas da API](#rotas-da-api)
- [Como Executar Localmente](#como-executar-localmente)
- [Execução com Docker](#execução-com-docker)
- [Integração Contínua (CI/CD)](#integração-contínua-cicd)
- [Exemplo de Uso](#exemplo-de-uso)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Dependências](#dependências)
- [Licença](#licença)

## Descrição

Este projeto é um serviço web para cadastro de usuários. Ele oferece uma interface simples para inserir nome e e-mail, armazenando os dados temporariamente (em memória). Também possui uma rota para verificar o status do serviço.

## Funcionalidades

- Cadastro de usuários via formulário web.
- Exibição de mensagem de sucesso após cadastro.
- Rota de status para monitoramento do serviço.

## Rotas da API

- `GET /`  
  Exibe o formulário de cadastro de usuários.

- `POST /`  
  Processa os dados enviados pelo formulário e retorna uma mensagem de sucesso.

- `GET /status`  
  Retorna um JSON com o status do serviço.

## Como Executar Localmente

1. Certifique-se de ter o Python 3.x instalado.
2. Instale as dependências:
   ```powershell
   pip install -r requirements.txt
   ```
3. Inicie o servidor Flask:
   ```powershell
   python app.py
   ```
4. Acesse `http://localhost:8080` no navegador.

## Execução com Docker


Utilize o Docker Compose:
```powershell
docker-compose up --build
```

## Integração Contínua (CI/CD)

Este projeto inclui um `Jenkinsfile` para automação de build, testes e deploy utilizando Jenkins. Para utilizar:
- Configure um pipeline no Jenkins apontando para este repositório.
- O pipeline executará as etapas definidas no `Jenkinsfile`.

## Exemplo de Uso

1. Acesse `http://localhost:8080`.
2. Preencha o formulário com nome e e-mail.
3. Clique em "Cadastrar".
4. Veja a mensagem de sucesso com os dados cadastrados.

## Estrutura do Projeto

- `app.py` — Código principal do serviço Flask.
- `requirements.txt` — Lista de dependências Python.
- `Dockerfile` — Configuração para containerização com Docker.
- `docker-compose.yml` — Orquestração de containers.
- `Jenkinsfile` — Pipeline de CI/CD para Jenkins.
- `README.md` — Documentação do projeto.

## Dependências

- Flask

Instale todas as dependências com:
```powershell
pip install -r requirements.txt
```
