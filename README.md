# CI/CD Pipeline com Jenkins, SonarQube e Azure App Service

Este projeto implementa um pipeline completo de **Integração Contínua e Entrega Contínua (CI/CD)** para uma aplicação Python com Docker Compose, usando **Jenkins** como orquestrador, **SonarQube** para análise de qualidade e **Azure App Service** para deploy.

## 🛠️ Tecnologias Utilizadas

- **Azure for Students** – Hospedagem da infraestrutura e do App Service
- **Jenkins** – CI/CD automation server
- **SonarQube** – Análise estática de código
- **Docker Compose** – Gerenciamento de serviços da aplicação
- **GitHub** – Repositório da aplicação
- **Azure CLI** – Deploy automatizado

---

## 📦 Estrutura da Infraestrutura

- **VM única no Azure** (Linux - B1s ou B2s) com:
  - Jenkins
  - SonarQube
  - Azure CLI
  - Docker + Docker Compose
- **Azure App Service for Linux (Docker Compose)** para deploy

---


## 🚀 Pipeline CI/CD – Etapas

1. **Clonar Repositório**  
   Jenkins clona o repositório do GitHub (`main`).

2. **Validação do `docker-compose.yml`**  
   Verifica se o arquivo está presente.

3. **Análise de Qualidade com SonarQube**  
   Usa `sonar-scanner` para analisar o código com base no `sonar.projectKey`.

4. **Login no Azure via Service Principal (JSON)**  
   Jenkins autentica via `azure-sp` (Secret Text).

5. **Deploy via Azure CLI**  
   Atualiza o App Service com o `docker-compose.yml`.

## 📈 Verificando a análise no SonarQube
Acesse: http://localhost:9000

Vá para Projects > gs-cicd

Verifique:

Bugs

Code Smells

Duplicações

Coverage (se testes forem configurados)

O projeto aparece após a 1ª análise se o sonar.projectKey for único e o token for válido.

🎤 Pitch e Aprendizados
Objetivos Atendidos
✅ Jenkins configurado para orquestrar CI/CD

✅ SonarQube realizando análise de código

✅ Deploy automático no Azure App Service

✅ Pipeline 100% automatizado com validações
