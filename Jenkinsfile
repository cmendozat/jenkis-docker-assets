pipeline {
    agent {
        docker { image 'cmendozat/jenkinsdocker-report:2211.44' }
    }
    stages {
        stage('alkosto-ccv2 folder') {
            steps {
                sh 'cd alkosto-ccv2' 
            }
        }
        stage('update branch release-d1') {
            steps {
                sh '''
                    git checkout release-d1
                    git pull 
                '''
            }
        }
        stage('Build') {
            steps {
                sh '''
                    cd core-customize/hybris/bin/platform
                    ant clean all
                    ant build
                '''
            }
        }
    }
}