pipeline {
    agent {
        node {
            label 'AGENT-1'
        }
    }
    environment {
        GREETING = 'Hello Jenkins'
    }
    options {
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
        //This pipeline should complete in 1hour. Timeout counter starts AFTER agent is allocated
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
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
        stage ('check params') {
            steps {
                sh """
                    echo "Hello ${params.PERSON}"

                    echo "Biography: ${params.BIOGRAPHY}"

                    echo "Toggle: ${params.TOGGLE}"

                    echo "Choice: ${params.CHOICE}"

                    echo "Password: ${params.PASSWORD}"
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