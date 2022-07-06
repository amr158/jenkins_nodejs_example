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
                    docker login 192.168.49.2:30081 -u ${username} -p ${password}
                    docker tag nodejs-app 192.168.49.2:30081/repository/nodejs-app/nodejs-app
                    docker push 192.168.49.2:30081/repository/nodejs-app/nodejs-app
                    """
                }
            }
        }
    }
}
