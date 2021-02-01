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
                sh 'npm i webpack webpack-cli'
                sh 'export PATH=$PWD/node_modules/.bin:$PATH'
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
