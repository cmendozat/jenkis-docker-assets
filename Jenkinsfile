pipeline {
    agent {
        docker { image 'cmendozat/jenkinsdocker-report:2211.44' }
    }
    stages {
        stage('update branch release-d1') {
            steps {
                sh '''
                    cd ~/opt/Alkosto_CCV2_2/alkosto-ccv2/core-customize/hybris/bin/platform
                    chmod u+rw ~/opt/Alkosto_CCV2_2/alkosto-ccv2/.gitconfig
                    git config --global --add safe.directory /opt/Alkosto_CCV2_2/alkosto-ccv2
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