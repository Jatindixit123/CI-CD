pipeline {
    agent any

    environment {
        VERCEL_TOKEN = credentials('vercel_token')
    }

    stages {
        stage('Install') {
            steps {
                dir('frontend') {
                    bat 'npm install'
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Skipping tests - no test script found'
            }
        }
        stage('Build') {
            steps {
                dir('frontend') {
                    bat 'npm run build'
                }
            }
        }
        stage('Deploy') {
            steps {
                dir('frontend') {
                    bat 'npx vercel --prod --yes --token=%VERCEL_TOKEN%'
                }
            }
        }
    }
}
