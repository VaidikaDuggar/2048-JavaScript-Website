pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Use withCredentials to securely provide the GitHub token for checkout
                    withCredentials([string(credentialsId: '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', variable: 'GITHUB_TOKEN')]) {
                        checkout([
                            $class: 'GitSCM',
                            branches: [[name: '*/main']],
                            extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'src']],
                            userRemoteConfigs: [[url: 'https://github.com/VaidikaDuggar/2048-JavaScript-Website.git', credentialsId: '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']]
                        ])
                    }
                }
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
                script {
                    // Use the GITHUB_TOKEN variable to access the token value
                    withCredentials([string(variable: 'GITHUB_TOKEN', credentialsId: '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')]) {
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
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
