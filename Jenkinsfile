pipeline {
    agent {
        docker { image 'cmendozat/jenkinsdocker-report:2211.44' }
    }
    stages {
        stage('update branch') {
            steps {
                git pull
            }
        }
    }
}