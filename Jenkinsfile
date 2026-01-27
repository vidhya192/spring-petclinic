
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/spring-projects/spring-petclinic.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying application on Windows at port 8081..."

                bat '''
                taskkill /F /IM java.exe > nul 2>&1
                start "" /B java -jar target\\*.jar --server.port=8081
                '''
            }
        }
    }
}
