pipeline {
    agent any

    stages {

      stage('Checkout') {
    steps {
        git url: 'https://github.com/spring-projects/spring-petclinic.git',
            branch: 'master'
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
                bat '''
                echo Stopping old application if running
                taskkill /F /IM java.exe > nul 2>&1

                echo Starting new application
                start "" /B java -jar target\\spring-petclinic-*.jar --server.port=8081
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}


