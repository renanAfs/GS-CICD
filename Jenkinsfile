pipeline {
    agent any         // Define que a pipeline roda em qualquer executor disponível

    tools {
        maven 'maven' // Usa o Maven que você configurou no Jenkins (Global Tool Configuration)
        jdk 'jdk-11'  // Usa o JDK que você configurou (opcional se já tiver no sistema)
    }

    environment {
        SONARQUBE = 'SonarQube-Server' // Nome que você deu ao SonarQube em "Configurar o Sistema"
        AZURE_CREDENTIALS = credentials('azure-sp') // ID das credenciais do Azure (veremos como criar)
    }

    stages {
        ...
    }

    post {
        success {
            echo 'Pipeline executado com sucesso!'
        }
        failure {
            echo 'Pipeline falhou.'
        }
    }
}
