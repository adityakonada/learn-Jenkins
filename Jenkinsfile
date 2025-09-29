pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    // build 
    stages{
        
        stage('Build') {
            steps{
                echo 'Building..'
            }
        }
        stage ('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage ('Deploy') {
            steps {
                echo 'Deploying..'
            }
        }
        
    }
    // post is post build
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
        failure { 
            echo 'This runs when pipeline is failed, used generally to send some alerts!'
        }
        success { 
           echo 'I will say hello only when pipeline is success!'
        }
    }
}