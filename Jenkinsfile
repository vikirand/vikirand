pipeline {
    agent any
    
    parameters {
        choice(name:'version', choices: ['1.1', '2.1'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    stages {
        stage("build") {
            steps {
                echo 'hi building'
            }
        }
        stage("test") {
            when {
                expression {
                    params.executeTests
                }
            }
            
            steps {
                echo 'testing....'
            }
        }
        stage("deploy") {
            steps {
                echo "deploy ${version}"
            }
        }        
    }
}
