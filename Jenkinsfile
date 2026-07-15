pipeline{
    agent{
        lable 'Agent-1'
    }

    environment{
        greetings = 'Good morning'
    }

    options{
        disableConcurrentBuilds()
        ansiColor('xterm')
    }

    parameters{
        choice(name: 'Stage to run', defaultValue: ['test', 'Init', 'Plan', 'Apply'] )
    }

    stages{
        stage('Test'){
            steps{
                sh """
                  echo "hellow this is test"
                """
            }
        }
        stage('Init'){
            steps{
                sh """
                """
            }
        }
        stage('plan'){
            steps{
                sh """
                """
            }
        }
        stage('apply'){
            steps{
                sh """
                """
            }
        }
    }
    post{
        always{
            echo "i will always say hellow"
        }
        success{
            echo "i will say hellow when success"
        }
        failure{
            echo "i will say when hellow failure"
        }
    }
}
