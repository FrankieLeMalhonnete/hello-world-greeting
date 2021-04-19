pipeline {
  agent none

  stages {
    
    stage('Compilation et tests') {
      agent {
        label 'agent_java'
      }
      stages {
        stage('Intégration continue') {
          steps {
            sh 'mvn test'
          }
        }
        stage('Compilation') {
          steps {
            sh 'mvn -B -DskipTests clean package'
          }
        }
      }
    }
    
    
    stage ('Tests et déploiement') {
      agent {
        label 'agent_tomcat'
      }
      stages {
        stage('Livraison continue') {
          steps {
            sh "curl -u admin:password --upload-file target/*.war 'http://http://10.10.20.31:8081/repository/depot_test/app.java_agent${BUILD_NUMBER}.war'"
          }
        }
      }
    }
  }
}
