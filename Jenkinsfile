pipeline {
  agent {
    node {
      label 'test'
    }

  }
  stages {
    stage('Compile') {
      steps {
        sh './mvnw clean compile'
      }
    }

    stage('Static Analysis') {
      steps {
        sh '''./mvnw  clean verify sonar:sonar -DskipTests=true -Dsonar.projectKey=Petclinic -Dsonar.host.url=http://172.31.31.56:9000  -Dsonar.login=sqp_74a7ef9aab18e31768261a94596e69af3c21f1b7
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

    stage('QA') {
      parallel {
        stage('Delpoy') {
          steps {
            sh '''./mvnw spring-boot:run </dev/null &>/dev/null &
'''
          }
        }

        stage('ntegration and Performance Tests') {
          steps {
            sh './mvnw verify'
          }
        }

      }
    }

  }
}