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
                    docker login 10.101.125.248:8081/repository/nodejs-app/ -u ${username} -p ${password}
                    docker tag nodejs-app 10.101.125.248:30081/repository/nodejs-app/nodejs-app
                    docker push 10.101.125.248:8081/repository/nodejs-app/nodejs-app
                    """
                }
            }
        }
    }
}
