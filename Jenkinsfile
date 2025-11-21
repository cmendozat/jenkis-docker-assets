pipeline {
    agent {
        docker { 
            image 'cmendozat/jenkinsdocker-report:2211.44'
            args '-u root'
        }
    }
    stages {
        stage('update branch release-d1') {
            steps {
                sh '''
                    ls -la
                    cd ~/opt/Alkosto_CCV2_2/alkosto-ccv2
                    whoami
                '''
            }
        }
        stage('Build') {
            steps {
                sh '''
                    cd ~/opt/Alkosto_CCV2_2/alkosto-ccv2/core-customize/hybris/bin/platform
                    ant clean all
                    ant build
                '''
            }
        }
    }
}