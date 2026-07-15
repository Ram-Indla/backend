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
        choice(name: 'Stage to run', defaultValue: ['Init', 'Plan', 'Apply'] )
    }

    stages{
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
        post{
            always{
                echo "i will always say "
            }
            success{
                echo "i will say when success"
            }
            failure{
                echo "i will say when failure"
            }
        }
    }
}
