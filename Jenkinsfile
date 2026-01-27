pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Code checkout done'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }
    }
}
