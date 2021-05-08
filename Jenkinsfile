pipeline {
  agent any
  stages {
    stage('json') {
      steps {
        step{
            echo 'start'
            String inJson = '{"name": "kit"}'
            echo inJson
        }

      }
    }

  }
  environment {
    name = 'val'
  }
}