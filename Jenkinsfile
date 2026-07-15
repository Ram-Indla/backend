pipeline{
    agent{
        label 'Agent-1'
    }

    environment{
        greetings = 'Good morning'
        appVersion = ''
    }

    options{
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }

    parameters{
        choice(name: 'Stage_to_run', choices: ['All', 'test', 'Init', 'Plan', 'Apply'] )
    }
    stages{
        stage('Test'){
            when{
                anyOf{
                    expression{params.Stage_to_run == 'All'}
                    expression{params.Stage_to_run == 'test'}
                }
            }
            steps{
                sh """
                  echo "hellow this is test"
                  ls -lrt
                """
            }
        }
        stage('Read the Version'){
            steps{
                script{
                    def packageJSONFile = readJSON file : 'package.json'
                    def appVersion = packageJSONFile.version
                    echo "appVersion is ${appVersion}"
                }
            }
        }
        stage('install depedencies'){
            when{
                anyOf{
                    expression{params.Stage_to_run == 'All'}
                    expression{params.Stage_to_run == 'Apply'}
                }
            }
            steps{
                sh """
                npm install
                ls -ltr
                echo "appVersion is ${appVersion}"
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
