#!groovy

println("Testing with node ")
node {
    agent { docker { image 'python:3.10.7-alpine' } }
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
