pipeline {
    agentName = "application"
    stages {
        stage('Building our image') {
            steps{
                sh 'docker build -t nodejs-app .'
            }
        }
        stage('run image') {
            steps{
                sh 'docker run -p 3000:3000 -d --name nodejs-app nodejs-app'
            }
        }
    }
}
