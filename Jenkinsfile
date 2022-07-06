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
                withCredentials([usernamePassword(credentialsId: 'docker-nexus' , usernameVariable: 'username', passwordVariable: 'password')]) {
                    sh """
                    docker build  -t nodeapp-rds:v1 .
                    docker login -u ${username} -p ${password} http://192.168.49.2:30081/repository/nodejs-app/
                    docker push nodejs-app
                    """
                }
            }
        }
    }
}
