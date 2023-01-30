pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        sh './mvnw clean compile'
      }
    }

    stage('Static Analysis') {
      steps {
        sh '''./mvnw clean verify sonar:sonar -Dsonar.projectKey=Petclinic -Dsonar.host.url=http://localhost:9000  -Dsonar.login=sqp_74a7ef9aab18e31768261a94596e69af3c21f1b7
'''
      }
    }

  }
}