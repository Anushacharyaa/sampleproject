pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build and Test') {
            steps {
                dir('/home/anusha/sampleproject') {
                    sh 'mkdir -p build'
                    sh 'cp sample.html build/'
                    sh 'cp sample.css build/'
                }
            }
        }
        stage('Deploy to S3') {
            steps {
                withCredentials([
                    [$class: 'AmazonWebServicesCredentialsBinding',
                     credentialsId: 'realawskey',
                     accessKeyVariable: 'AKIAW7IDMJGT46GFZLWC',
                     secretKeyVariable: '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']
                ]) {
                    sh 'aws s3 sync ./build/ s3://mystaticawsbucket/'
                }
            }
        }
    }
}

