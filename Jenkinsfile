pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Deploy Cloudhub') {
            steps {
                sh 'mvn clean package mule:deploy -DmuleDeploy'
            }
        }
        stage('Regression Testing') {
            steps {
                sh 'newman run /var/jenkins_home/newman/erik-time-zone-sandbox.postman_collection.json --disable-unicode'
            }
        }
    }
}
