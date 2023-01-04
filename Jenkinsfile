#!groovy

println("Testing with node ")

node {
    checkout scm
    docker.image('mysql').withRun('-e "MYSQL_ROOT_PASSWORD=my-secret-pw"') { c ->
        docker.image('mysql').inside("--link ${c.id}:db") {
            /* Wait until mysql service is up */
            sh 'while ! mysqladmin ping -hdb --silent; do sleep 1; done'
        }
        docker.image('centos:7').inside("--link ${c.id}:db") {
            /*
             * Run some tests which require MySQL, and assume that it is
             * available on the host name `db`
             */
            sh 'echo "hello world"'
        }
    }
}

//node { 
//    checkout scm
//    docker.image('python').withRun('-e "MYSQL_ROOT_PASSWORD=my-secret-pw"') { c ->
//      stage('Checkout') {
//        checkout scm
//      }
//      stage('build') {
//          sh 'python --version'
//      }
//      stage('Example') {
//        if (env.BRANCH_NAME == 'master') {
//            echo 'I only execute on the master branch'
//        } else {
//            echo 'I execute elsewhere'
//        }
//      } 
//    }
//}
        
        
        
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
