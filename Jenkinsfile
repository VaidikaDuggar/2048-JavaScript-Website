pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Replace with your build commands (npm, webpack, etc.)
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                // Replace with your deployment commands (copy files, push to GitHub Pages, etc.)
                // For GitHub Pages deployment example:
                sh 'git checkout gh-pages'
                sh 'cp -r dist/* .'
                sh 'git add .'
                sh 'git commit -m "Update site"'
                sh 'git push origin gh-pages'
            }
        }
    }

    environment {
        GITHUB_TOKEN = credentials('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')
    }

    post {
        always {
            cleanWs()
        }
    }
} check this
