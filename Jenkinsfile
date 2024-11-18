pipeline {
    agent any

    stages {
        stage('Clonar Repositorio') {
            steps {
                git url: 'https://github.com/fera1991/my-web-app', branch: 'main'
            }
        }
        stage('Construir Imagen Docker') {
            steps {
                script {
                    sh 'docker build -t mi-aplicacion .'
                }
            }
        }
        stage('Pruebas') {
            steps {
                script {
                    sh 'docker run mi-aplicacion npm test'
                }
            }
        }
        stage('Despliegue') {
            steps {
                script {
                    sh 'docker run -d -p 80:3000 mi-aplicacion'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline ejecutado correctamente.'
        }
        failure {
            echo 'Hubo un error en el pipeline.'
        }
    }
}

