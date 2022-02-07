pipeline {
    agent any
    
    parameters {
        choice(choices: ['Deployment' , 'Rollback'], description: '',name: 'Process')
        choice(choices: ['QA' , 'Pre-prod'], description: '',name: 'REQUESTED_ACTION')
        string(name: 'IP', description: 'Please enter you backend IP')
    }
    stages {
        stage ("process") {
            when {
            expression { params.Process == 'Deployment' }
            }
   
   
    stages {
        stage("Git checkout") {
            steps {
                script {
                    if (params.BRANCH == 'main') {
                        echo 'I only execute on the main branch'
                    //    git branch: "${params.BRANCH}", url: "https://github.com/vikirand/vikirand.git" , poll: true
                    } 
                    else {
                        echo 'This is not correct branch'
                    }
                }    
            }
        }
        
    
        stage("IP") {
            steps {
                script {
                    //try {
                        echo "Print the workspave path"
                        echo "Hello ${params.NAME}"
                        sh "echo $WORKSPACE"
                        sh '''
                        #!/bin/bash
                        echo "welcome"
                        exit 0
                        EOF'''
                    //    currentBuild.status = 'SUCCESS'
                   // } catch (Exception err) {
                  //      currentBuild.resulut = 'FAILURE'
                   //     echo "FAILED: ${err}"
                  //  }

                }
            }
        }

        stage("Deploy-tomcat-server") {
            steps {
                script {
                    def userInput = input(id: 'userInput', message: 'Ready for Deployment?')
                    echo "Deploy into tomcat server"
                    sh "cd $WORKSPACE/target/"
               // sh "cd $WORKSPACE/target/ && scp -r *.war tomcat@3.109.56.173:/opt/apache-tomcat-9.0.56/webapps/"
                
                    echo " Deployment has been completed successfully"
                }
            }    
        }
    }

}

    stage("process-rollback") {
        when {
        expression { params.Process == 'Rollback' }
        }
        stages {
            stage("Rollback") {
                steps {
                echo "Rollback-process"
                //git branch: "${params.BRANCH}", url: "https://github.com/vennavenkatesh/devops-sample.git" , poll: true
                }
            }        
        }
    }
}

}
