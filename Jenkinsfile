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
                '''
            }
        }
        stage('install npm') {
            steps {
                sh '''
                    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
                    \. "$HOME/.nvm/nvm.sh"
                    nvm install 24
                    node -v
                    npm -v
                '''
            }
        }
        stage('install grunt') {
            steps {
                sh '''
                    npm install -g grunt-cli
                    grunt --version
                '''
            }
        }
        stage('generate assets') {
            steps {
                sh '''
                    cd /opt/Alkosto_CCV2_2/alkosto-ccv2/core-customize/hybris/bin/custom/alkostostorefront/
                    grunt create-aws-assets
                    cd /web/webroot/release/
                    ls -la
                '''
            }
        }
    }
}