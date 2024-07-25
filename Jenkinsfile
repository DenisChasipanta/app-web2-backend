pipeline {
    agent any

    stages {
        stage('Revisión') {
            steps {
                checkout scm
            }
        }
        stage('Instalación de dependencias') {
            steps {
                bat 'mvn clean install'
            }
        }
        stage('Construir') {
            steps {
                bat 'mvn package'
            }
        }
        stage('Pruebas') {
            steps {
                bat 'mvn test'
            }
        }
        stage('Limpiar') {
            steps {
                bat 'rd /s /q C:\\servidor\\spring'
            }
        }
        stage('Mover al servidor') {
            steps {
                bat 'xcopy C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\spring1-pipeline\\target\\*.jar C:\\servidor\\spring /E /I /Y'
            }
        }
    }

    post {
        success {
            echo 'El pipeline se completó con éxito.'
        }
        failure {
            echo 'El pipeline falló.'
        }
    }
}