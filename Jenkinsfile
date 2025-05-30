pipeline {
    agent any

    environment {
        // Nome da credencial do Azure no Jenkins
        AZURE_AUTH = credentials('azure-sp')

        // Variáveis do Azure
        RESOURCE_GROUP = 'meu-resource-group'
        APP_SERVICE_NAME = 'meuapp-compose'
    }

    stages {
        stage('Clonar repositório') {
            steps {
                git url: 'https://github.com/seuusuario/seurepo.git'
            }
        }

        stage('Verificar docker-compose.yml') {
            steps {
                script {
                    if (!fileExists('docker-compose.yml')) {
                        error "Arquivo docker-compose.yml não encontrado no repositório!"
                    }
                }
            }
        }

        stage('Login no Azure') {
            steps {
                writeFile file: 'azureauth.json', text: AZURE_AUTH

                sh '''
                    az logout || true

                    az login --service-principal \
                        --username $(jq -r .clientId azureauth.json) \
                        --password $(jq -r .clientSecret azureauth.json) \
                        --tenant $(jq -r .tenantId azureauth.json)

                    az account set --subscription $(jq -r .subscriptionId azureauth.json)
                '''
            }
        }

        stage('Deploy no Azure App Service (Docker Compose)') {
            steps {
                sh '''
                    az webapp config container set \
                      --resource-group $RESOURCE_GROUP \
                      --name $APP_SERVICE_NAME \
                      --multicontainer-config-type compose \
                      --multicontainer-config-file docker-compose.yml
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Deploy realizado com sucesso no Azure!'
        }
        failure {
            echo '❌ Falha no deploy. Verifique os logs para detalhes.'
        }
    }
}
