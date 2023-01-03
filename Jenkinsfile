#!groovy

println("Testing with node ")

node { 
    /*
     * In order to communicate with the MySQL server, this Pipeline explicitly
     * maps the port (`3306`) to a known port on the host machine.
     */
    docker.image('python:3.10.7-alpine').withRun('-e "MYSQL_ROOT_PASSWORD=my-secret-pw"' +
                                    ' -p 3306:3306') { c ->
        sh 'make check'
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
