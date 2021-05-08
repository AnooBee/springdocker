#!/usr/bin/env groovy
import groovy.json.JsonBuilder
import groovy.json.JsonSlurper

pipeline {
  agent any
  stages {
    stage('json') {
      steps {
          script {
              echo 'start'
              readMavenPom(file: 'pom.xml')
              //writeJSON(json: '{\"name\":\"kitsune\",\"age\":22,\"artifacts\":[\"id: 1.0\",\"group: groupname\"]}', pretty: 2, file: 'out.json')
              String jsonStr = '''{"name":"kitsune","age":"22","artifacts":[{"id": "1.0","group": "groupname1"}]'''
              writeJSON(json: jsonStr, pretty: 2, file: 'out.json')
          }
        }
     }
     stage('read json') {
        steps {
            script {
                def props = readJSON file: 'out.json'
                assert props['name'] == 'kitsune'
                props.each { key, value ->
                    echo "Walked through key $key and value $value  "

                }


                String currName = "${props.artifacts[1]}"
                echo "group is: $currName"



                // The code below does not
                props['artifacts[1]'] = "1.2.0"
                writeJSON file: "newJson.json", json: props

                def newProps = readJSON file: 'newJson.json'

                echo newProps.toString()
            }
        }
     }


  }
  environment {
    name = 'val'
  }
}