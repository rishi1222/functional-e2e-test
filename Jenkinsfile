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
  - name: maven
    image: localhost:5000/my-maven:latest
    command:
    - cat
    tty: true
  - name: shopfront  
    image: localhost:5000/shopfront:latest
    imagePullPolicy: ""
    ports:
    - containerPort: 8010
    resources: {}
  restartPolicy: Always
  serviceAccountName:     
  imagePullSecrets:
  - name: regcred    
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