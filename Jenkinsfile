
pipeline {
  agent { 
    docker { 
      image 'mcr.microsoft.com/playwright:v1.23.0-focal'
        image 'node' 
        args '-u root'
      reuseNode true
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
     steps {
        sh '''
          npx playwright test --list
          npx playwright test
        '''
      }
    }
  }
}
