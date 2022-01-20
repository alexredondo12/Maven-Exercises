pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean install -Dlicense.skip=true'
      }
    }

    stage('Prueba') {
      parallel {
        stage('Prueba de SonarQube') {
          steps {
            sh 'mvn sonar:sonar -Dsonar.host.url=http://<IP address>:8081 -Dlicense.skip=true'
          }
        }

        stage('Imprimir credenciales de probador') {
          steps {
            echo 'The tester is ${TESTER}'
            sleep 10
          }
        }

      }
    }

  }
}