pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image2 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image2 jutooruvineela14/paytm:bus'
            }
        }
      stage('push') {
            steps {
                script {
               withDockerRegistry(credentialsId: 'new-docker', url: 'https://github.com/jutooruvineela14/multibranch-docker.git') {
                   sh 'docker push vineela0714/paytm:bus'
              }  
            }
        }
    }

        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus-app -p 2222:80 jutooruvineela14/paytm:bus'
            }
        }
    }
}
