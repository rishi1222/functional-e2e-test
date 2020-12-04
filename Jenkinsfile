pipeline {
    agent { kubernetes { image 'maven:latest' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
    }
}