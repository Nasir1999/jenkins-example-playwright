
pipeline {
  agent { 
    docker { 
      image 'mcr.microsoft.com/playwright:v1.17.2-focal'
        image 'node' 
        args '-u root'
    }
  }
   environment {
        HOME = '.'
    }
  stages {
    stage('install playwright') {
      steps {
        sh '''
          npm -v
          npm i -D @playwright/test
          npx playwright install
        '''
      }
    }
    stage('help') {
      steps {
        sh 'npx playwright test --help'
      }
    }
    stage('test') {
       agent {
                docker {
                    image 'mcr.microsoft.com/playwright:v1.17.2-focal'
                    // Run the container on the node specified at the
                    // top-level of the Pipeline, in the same workspace,
                    // rather than on a new node entirely:
                    reuseNode true
                }
            }
           steps {
              sh '''
                npx playwright test --list
                npx playwright test
              '''
            }
     
    }
  }
}
