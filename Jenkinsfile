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
        stage('Install Node via NVM and Generate assets') {
            steps {
                sh '''
                    cd /opt/Alkosto_CCV2_2/alkosto-ccv2/core-customize/hybris/bin/custom/alkostostorefront/
                    apt-get install curl -y

                    # Instalar NVM
                    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash

                    # Cargar NVM correctamente
                    export NVM_DIR="$HOME/.nvm"
                    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"

                    # Instalar Node 24
                    nvm install 24

                    node -v
                    npm -v
                    npm install -g grunt-cli

                    grunt create-aws-assets
                    cd /web/webroot/release/
                    ls -la
                '''
            }
        }
    }
}