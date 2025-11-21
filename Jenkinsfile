pipeline {
    agent {
        docker { 
            image 'cmendozat/jenkinsdocker-report:2211.44'
            args '-u root:sudo -v /var/lib/jenkins/workspace/docker-assets:/var/lib/jenkins/workspace/docker-assets:rw,z'
        }
    }
    stages {
        stage('checkout') {
            steps {
                sh '''
                    cd /opt/Alkosto_CCV2_2/alkosto-ccv2
                    git checkout release-d1
                    git pull
                '''
            }
        }
        stage('Build') {
            steps {
                sh '''
                    cd /opt/Alkosto_CCV2_2/alkosto-ccv2/core-customize/hybris/bin/platform
                    . ./setantenv.sh
                    ant clean all
                    ant build
                '''
            }
        }
    }
}