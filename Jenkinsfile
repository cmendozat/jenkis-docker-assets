pipeline {
    agent {
        docker { 
            image 'cmendozat/jenkinsdocker-report:2211.44'
            args '-u 1000:1000'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                    java --version
                '''
            }
        }
    }
}