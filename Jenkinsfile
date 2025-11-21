pipeline {
    agent {
        docker { 
            image 'cmendozat/jenkinsdocker-report:2211.44'
        }
    }
    stages {
        stage('update branch release-d1') {
            steps {
                sh '''
                    cd ~/opt/Alkosto_CCV2_2/alkosto-ccv2
                    ls -la
                    git config --global --add safe.directory ~/opt/Alkosto_CCV2_2/alkosto-ccv2
                    git checkout release-d1
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