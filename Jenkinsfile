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
        sh '''./mvnw sonar:sonar -DskipTests=true
 -Dsonar.projectKey=Petclinic -Dsonar.host.url=http://3.7.250.188:9000  -Dsonar.login=sqp_74a7ef9aab18e31768261a94596e69af3c21f1b7
'''
      }
    }

    stage('Unit Test') {
      steps {
        sh './mvnw "-Dtest=**/petclinic/*/*.java" test'
      }
    }

    stage('Package') {
      steps {
        sh './mvnw package -DskipTests=true'
      }
    }

  }
}