pipeline {
  agent {
    docker { image 'maven:3.6.3-jdk-11-slim'}
   }
  stages {
    stage('build') {
      steps {
        echo 'step 1 '
        sh 'mvn compile'
      }
    }
    stage ('test') {
      steps {
        echo 'step 2'
        sh 'mvn clean test'
      }
    }
    stage('package') {
      steps {
        echo 'step 3'
        sh 'mvn package -DskipTests'
        //archiveArtifacts artifacts: '**/target/*.jar',fingerprint: true
      }
    }
  }
  }
