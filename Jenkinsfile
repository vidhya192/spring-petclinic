
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git url: 'https://github.com/vidhya192/spring-petclinic.git',
                    branch: 'main'
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
        taskkill /F /IM java.exe >nul 2>&1
        for %%f in (target\\spring-petclinic*.jar) do (
            start "" /B java -jar "%%f" --server.port=8081
        )
        '''
    }
}



