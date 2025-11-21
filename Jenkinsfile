pipeline {
    agent {
        docker { 
            image 'cmendozat/jenkinsdocker-report:2211.44'
            args '-u root:sudo -v /var/lib/jenkins/workspace/docker-assets:/var/lib/jenkins/workspace/docker-assets:rw,z'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                    java --version
                    whoami
                    ls -la
                    pwd
                    cd /opt/Alkosto_CCV2_2/alkosto-ccv2/core-customize/hybris/bin/platform
                    ls -la
                    git status
                '''
            }
        }
    }
}