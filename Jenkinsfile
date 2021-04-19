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
        sh "curl -u admin:{MOT_DE_PASSE} --upload-file target/*.war 'http://{ADRESSE_IP_SERVEUR_NEXUS}/repository/{NOM_DU_DEPOT}/app${BUILD_NUMBER}.war'"
      }
    }
  }
}
