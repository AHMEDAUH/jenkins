#!groovy

println("Testing with node ")

node { 
      checkout scm
    docker.image('python:3.10.7-alpine').withRun('-e "MYSQL_ROOT_PASSWORD=my-secret-pw"' +
                                    ' -p 3306:3306') { c ->
        stages {
            stage('Checkout') {
              steps {
                checkout scm
              }
            }

            stage('build') {
                steps {
                    sh 'python --version'
                }
            }
        }
    }
    
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
