pipeline {
    agent {
        docker { image 'ubuntu:18.04' 
                  args '-u root:root -v $HOME/workspace/myproject:/myproject'
            
        }
    }
    triggers {
        githubPush()
    }    
    stages {
        stage('Checkout SCM') {
          steps {
            checkout([
              $class: 'GitSCM',
              branches: [[name: ":^(?origin/master|origin/develop.*)" ]],
              userRemoteConfigs: [[
                url: 'https://github.com/hwchiu/test.git',
                credentialsId: '',
              ]]
             ])
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
