pipeline {
    agent any

    environment {
        // Nome da credencial do Azure no Jenkins (do tipo "Secret text", JSON do SP)
        AZURE_AUTH = credentials('azure-sp')
        SONAR_TOKEN = credentials('sonar-token')

        // Informações do App Service
        RESOURCE_GROUP = 'gs-cicd'
        APP_SERVICE_NAME = 'cicd'
    }

    stages {

        stage('Clonar repositório') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/renanAfs/GS-CICD.git'
                    ]]
                ])
            }
        }

        stage('Verificar docker-compose.yml') {
            steps {
                script {
                    if (!fileExists('docker-compose.yml')) {
                        error "❌ Arquivo docker-compose.yml não encontrado no repositório!"
                    } else {
                        echo "✅ docker-compose.yml encontrado"
                    }
                }
            }
        }

        stage('Análise SonarQube') {
            steps {
                withSonarQubeEnv('SonarQube_Local') {
                    sh '''
                        sonar-scanner \
                          -Dsonar.projectKey=meu_projeto \
                          -Dsonar.sources=. \
                          -Dsonar.host.url=http://localhost:9000 \
                          -Dsonar.login=$SONAR_TOKEN
                    '''
                }
            }
        }

        stage('Login no Azure') {
            steps {
                writeFile file: 'azureauth.json', text: AZURE_AUTH

                sh '''
                    echo "🔐 Realizando login no Azure..."
                    az logout || true

                    az login --service-principal \
                        --username $(jq -r .clientId azureauth.json) \
                        --password $(jq -r .clientSecret azureauth.json) \
                        --tenant $(jq -r .tenantId azureauth.json)

                    az account set --subscription $(jq -r .subscriptionId azureauth.json)
                    echo "✅ Login no Azure realizado com sucesso"
                '''
            }
        }

        stage('Deploy no Azure App Service (Docker Compose)') {
            steps {
                sh '''
                    echo "🚀 Iniciando deploy no App Service..."
                    az webapp config container set \
                        --resource-group $RESOURCE_GROUP \
                        --name $APP_SERVICE_NAME \
                        --multicontainer-config-type compose \
                        --multicontainer-config-file docker-compose.yml

                    echo "✅ Deploy aplicado com sucesso"
                '''
            }
        }
    }

    post {
        success {
            echo '🎉 Pipeline finalizado com sucesso! Aplicação implantada no Azure App Service.'
        }
        failure {
            echo '❌ Ocorreu uma falha no pipeline. Verifique os logs acima.'
        }
    }
}
