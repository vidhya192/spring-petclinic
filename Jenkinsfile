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

stage('Deploy') {
    steps {
        echo "Deploying application on Windows at port 8081..."

        bat '''
        echo Stopping old application if running...
        taskkill /F /IM java.exe > nul 2>&1

        echo Starting new application...
        start "" /B java -jar target\\*.jar --server.port=8081
        '''
    }
}
