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
        sh './mvnw clean verify sonar:sonar -Dsonar.projectKey=Petclinic -Dsonar.host.url=http://localhost:9000  -Dsonar.login=sqp_0c2e771128f1d37c8e3dadd7b75195fd0bca9066'
      }
    }

  }
}