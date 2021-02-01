pipeline {
    agent none
    triggers {
        githubPush()
    }
    stages {
        stage('Build') {
            agent any
            steps {
                sh 'npm install'
                sh 'npm run tsc'
                sh 'nvm use v14.15.4'
                sh 'webpack build'
                sh 'npm run tsc'
                sh 'npm publish'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
