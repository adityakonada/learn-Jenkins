pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment {
        GREETING = 'Hello Jenkins'
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
                sh """
                    echo "Here I wrote in shell script"
                    env 
                """
            }
        // this loc gave the added many lines in output, to get external system urls and access them in desired stages.
        }    
        stage ('shell-env combo variable') {
            steps {
                sh """
                    echo "Here I wrote in shell script"
                    echo "$GREETING"
                """
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