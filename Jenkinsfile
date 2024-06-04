pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                dir('erik-time-zone-app') {
                    sh 'mvn clean install'
                }
            }
        }
        stage('Deploy Cloudhub') {
            steps {
                dir('erik-time-zone-app') {
                    sh 'mvn clean package mule:deploy -DmuleDeploy'
                }
            }
        }
        stage('Regression Testing') {
            steps {
                dir('erik-time-zone-app') {
                    sh 'newman run /var/jenkins_home/newman/erik-time-zone-sandbox.postman_collection.json --disable-unicode'
                }
            }
        }
    }
}