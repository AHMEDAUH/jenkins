#!groovy

println("Testing with node ")

node { 
        checkout scm
        docker.image('mysql:5').withRun('-e "MYSQL_ROOT_PASSWORD=my-secret-pw"' +
                                    ' -p 3306:3306') { c ->
                 stage('Checkout') {
                    checkout scm
                  }

                  stage('build') {
                      sh 'python --version'
                  }
                  stage('Example') {
                    if (env.BRANCH_NAME == 'master') {
                        echo 'I only execute on the master branch'
                    } else {
                        echo 'I execute elsewhere'
                    }
                  } 
        }
// withCredentials([string(credentialsId: 'mytoken', variable: 'TOKEN')]) {
// sh /* WRONG! */ """
//   set +x
//   curl -H 'Token: $TOKEN' https://some.api/
// """
// sh /* CORRECT */ '''
//   set +x
//   curl -H 'Token: $TOKEN' https://some.api/
// '''
// }
        
    
}


//pipeline {
//    agent { docker { image 'python:3.10.7-alpine' } }
//    stages {
//        stage('Checkout') {
//          steps {
//            checkout scm
//          }
//        }
//    
//        stage('build') {
//            steps {
//                sh 'python --version'
//            }
//        }
//    }
//}
