pipeline {
    agent {
        docker { image "${params.buildNode}"
                  args '-u root:root -v $HOME/workspace/myproject:/myproject'
            
        }
    }
    options {
        skipDefaultCheckout(true)
    }
    stages {
       stage('Checkout SCM') {
            steps {
                echo '> Checking out the source control ...'
                checkout scm
            }
        }
        stage('Test') {
            steps {
                sh '''
                apt-get update -y
                apt-get install -y shellcheck jq
                pwd
                env
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
