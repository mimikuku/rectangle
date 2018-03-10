
pipeline {
  agent any
  tools {
    maven 'Maven3'
  }

  stages {
    stage('Build') {
      steps {
	sh 'mvn clean package'
      }
    }
  }

  stages {
    stage('Unit tests') {
      steps {
        sh 'mvn clean test'
      }
    }
  }
  
  post {
    always {
      junit 'target/surefire-reports/*.xml'
    }
  }
  
  post {
    always {
      archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
    }
  }
  options {
    buildDiscarder(logRotator(numToKeepStr: '2', artifactNumToKeepStr: '1'))
  } 

}
