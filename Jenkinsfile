pipeline {
    agent any
    stages { 
      stage('checkout SCM') {
        steps {
          bat "git clone https://github.com/Vikashsingh447/sonar-cubetest.git"
          }
      }
      stage('package') {
        steps {
          bat "mvn clean package"
        }
      }
      stage('Static Analysis') {
        steps {
          withSonarQubeEnv('sonarqube') {
            bat "mvn sonar:sonar -Dsonar.projectKey=sample-demo"
          }
        }
      }
      stage('test') {
        steps {
          bat "mvn clean test"
        }
      }
      stage('install') {
        steps {
          bat "mvn clean install"
        }
      }
  }
}
