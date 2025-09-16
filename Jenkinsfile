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
                sh 'docker tag image1  push vineela0714/paytm:bank' 
            }
        }
         stages {
        stage('push') {
            steps {
                withDockerRegistry(credentialsId: 'dockertoken') {
                    sh 'docker push vineela0714/paytm:bank'
               }
            }
        }
    }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 1111:80 vineela0714/paytm:bank'
            }
        }
    }
}
