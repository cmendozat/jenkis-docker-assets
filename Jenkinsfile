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
                    cd ~/opt/Alkosto_CCV2_2/alkosto-ccv2/core-customize/hybris/bin/platform
                    ls -la
                    . ./setantenv.sh
                    ant clean all
                    ant build
                '''
            }
        }
    }
}