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
                sh 'npm i --save-dev webpack webpack-cli'
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
