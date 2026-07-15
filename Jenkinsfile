pipeline{
    agent{
        label 'Agent-1'
    }

    environment{
        greetings = 'Good morning'
        def appVersion = ''
    }

    options{
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }

    parameters{
        choice(name: 'Stage_to_run', choices: ['All', 'Install', 'Build'] )
    }
    stages{
        stage('Read the Version'){
            steps{
                script{
                    def packageJSONFile = readJSON file : 'package.json'
                    appVersion = packageJSONFile.version
                    echo "appVersion is ${appVersion}"              
                }
            }
        }
        stage('install depedencies'){
            when{
                anyOf{
                    expression{params.Stage_to_run == 'All'}
                    expression{params.Stage_to_run == 'Build'}
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
        
        stage('Build'){
            when{
                anyOf{
                    expression{params.Stage_to_run == 'All'}
                    expression{params.Stage_to_run == 'Build'}
                }
            }
            steps{
                sh """
                    zip -q -r backend-${appVersion}.zip * -x Jenkinsfile -x backend-${appVersion}.zip  
                    ls -lrt
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
