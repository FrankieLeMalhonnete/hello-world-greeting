pipeline {
  agent {
    label 'agent_java'
  }

  stages {
    stage('Test unitaires') {
      steps {
        sh 'mvn test'
      }
    }
    stage('Compilation') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }
    stage ('Publication du binaire') {
      steps {
        sh "curl -u admin:password --upload-file target/*.war 'http://http://10.10.20.31:8081/repository/agent_java/app${BUILD_NUMBER}.war'"
      }
    }
  }
}
