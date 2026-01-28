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
                bat 'mvn package -DskipTests'
            }
        }

        stage('Deploy') {
            steps {
                bat """
                taskkill /F /IM java.exe >nul 2>&1
                cd target
                for %%f in (spring-petclinic*.jar) do start "" /B java -jar %%f --server.port=8081
                """
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed'
        }
        success {
            echo 'Pipeline success'
        }
    }
}

 



