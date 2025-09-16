pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image1 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image1 shaikmustafa/paytm:bank'
            }
        }
       stage('push') {
            steps {
                script {
               withDockerRegistry(credentialsId: 'new-docker', url: 'https://github.com/jutooruvineela14/multibranch-docker.git') {
                   sh 'docker push vineela0714/paytm'
               }  
            }
        }
    }

        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 1111:80 shaikmustafa/paytm:bank'
            }
        }
    }
}
