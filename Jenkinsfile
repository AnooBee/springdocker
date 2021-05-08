pipeline {
  agent any
  stages {
    stage('json') {
      steps {
        echo 'start'
        readMavenPom(file: 'pom.xml')
        writeJSON(json: '{"name":"kitsune"}', pretty: 2, file: 'out.json')
        }
     }
     stage('read json') {
        steps {
            script {
                def props = readJSON file: 'out.json', returnPojo: true
                assert props['name'] == 'kitsune'
                props.each { key, value ->
                    echo "Walked through key $key and value $value"
                }
            }
        }
     }


  }
  environment {
    name = 'val'
  }
}