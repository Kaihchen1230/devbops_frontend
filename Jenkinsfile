pipeline {
    agent any
    tools {nodejs "npm"}
    stages {

        stage('Git checkout'){
            steps {
                git credentialsId: 'kai-github', url: 'https://github.com/Kaihchen1230/devbops_frontend'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo "installing required packages" 
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo "in the test stage"
                sh 'npm run test-once'
            }
        }

        stage('Build Application') {
            steps {
                echo "in the build stage"
                sh 'npm run build'
            }
        }

        stage('Connect to AWS S3') {
            steps {
                withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-cli-configure', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                    sh 'aws s3 cp ./build s3://devbops.com/ --recursive'
                }
            }
        }

    }
}
