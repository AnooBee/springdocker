pipeline {
  agent any
  stages {
    stage('json') {
      steps {
        echo 'start'
        readMavenPom(file: 'pom.xml')
        writeJSON(json: '"name":"kitsune"', pretty: 2, returnText: true)
      }
    }

  }
  environment {
    name = 'val'
  }
}