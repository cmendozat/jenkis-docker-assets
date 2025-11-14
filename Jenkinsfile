pipeline {
    agent {
        docker { 
            image 'cmendozat/jenkinsdocker-report:2211.44'
        }
    }
    stages {
        stage('Fix Git Safe Directory') {
            steps {
                sh 'git config --system --add safe.directory `pwd`'
        }
        stage('update branch release-d1') {
            steps {
                sh '''
                    cd ~/opt/Alkosto_CCV2_2/alkosto-ccv2
                    ls -la
                    git checkout release-d1
                    git pull 
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