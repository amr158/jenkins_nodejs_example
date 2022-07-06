pipeline {
    agent any
    stages {
        stage('Building our image') {
            steps{
                sh 'docker build -t nodejs-app .'
            }
        }
        stage('publishing into nexus') {
            steps{
                withCredentials([string(credentialsId: 'docker-nexus', variable: 'dockerpwd')]) {
                  sh "docker login -u admin -p ${dockerpwd} http://192.168.49.2:30081/repository/nodejs-app/"
                  sh 'docker push nodejs-app'
                }
            }
        }
    }
}
