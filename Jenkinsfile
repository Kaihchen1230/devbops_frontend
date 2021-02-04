pipeline {
    agent any
    tools {nodejs "nodejs"}
    
    stages {

        stage('Git checkout'){
            steps {
                git credentialsId: 'kai-github', url: 'https://github.com/Kaihchen1230/devbops_frontend'
            }
        }

        stage('Build') {
            steps {
                echo "installing required packages" 
                sh 'npm ci'
            }
        }

        stage('Test') {
            steps {
                echo "in the test stage"
                sh 'npm run test-once'
            }
        }

    }
}
