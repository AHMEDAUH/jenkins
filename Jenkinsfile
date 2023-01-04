#!groovy

println("Testing with node ")

node('python:3.10.7-alpine') { 
        checkout scm
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
