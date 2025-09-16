pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image3 jutooruvineela14/paytm:movie'
            }
        }
         stage('Push') {
            steps {
                script {
                     withDockerRegistry(credentialsId: 'dockerhub', url: 'https://github.com/jutooruvineela14/multibranch-docker.git') {
                          sh 'docker push jutooruvineela14/paytm:movie '
                    }     
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movie-app -p 3333:80 jutooruvineela14/paytm:movie'
            }
        }
    }
}
