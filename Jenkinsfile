#!/usr/bin/env groovy

pipeline {
    agent any
    stages {
        stage('build app') {
            steps {
               script {
                   echo "building the application..."
               }
            }
        }
        stage('build image') {
            steps {
                script {
                    echo "building the docker image..."
                }
            }
        }
        stage('deploy') {
            steps {
                script {
                   echo 'deploying docker image...'
                   withCubeConfig([credentialsId: 'lke-credentials', serverUrl: 'https://5ef2401a-812c-48b2-8cf6-738c08d622dc.us-east-2.linodelke.net']) {
                        sh 'kubectl create deployment nginx-deployment --image=nginx'
                   }

                }
            }
        }
    }
}
