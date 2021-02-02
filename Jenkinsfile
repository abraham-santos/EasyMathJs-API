pipeline {
    agent none
    triggers {
        githubPush()
    }
    environment {
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "192.168.160.128:8081"
        NEXUS_REPOSITORY = "npm-repository"
        NEXUS_CREDENTIAL_ID = "nexus-user-credentials"
    }
    stages {
        stage('Build') {
            agent any
            steps {
                sh 'npm install'
                sh 'npm run tsc'
                sh 'export PATH=$PWD/node_modules/.bin:$PATH'
                sh 'npm publish'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
