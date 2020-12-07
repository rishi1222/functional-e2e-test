#!/usr/bin/env groovy
pipeline {
    agent {
        kubernetes {
            yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    app: jenkins
spec:
  containers:
  -name: jnlp
   env:
   - name: CONTAINER_ENV_VAR
     value: jnlp
  - name: maven
    image: maven:latest
    command:
    - cat
    tty: true
"""
        }
    }
    stages {
        stage('Run maven') {
            steps {
                container('maven') {
                    sh 'mvn -version'
                }
            }
        }
    }
}