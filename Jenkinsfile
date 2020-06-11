pipeline {

  agent any

  stages {
    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }

    stage('Security Scan') {
      steps { 
        aquaMicroscanner imageName: 'alpine:latest', notCompilesCmd: 'exit 1', onDisallowed: 'fail', outputFormat: 'html'
      }
    }
  }
}
