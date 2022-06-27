pipeline {
    agent any
    stages {
        stage('Many tests') {
            agent {
                docker {
                    image 'mcr.microsoft.com/playwright:v1.17.2-focal'
                }
            }
            steps {
                sh 'npx playwright test'
            }
        }
    }
}
