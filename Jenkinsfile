pipeline {
  agent any
  tools {
    maven 'Maven 3.6.3'
  }
  stages {
    stage('build' {
      steps {
        echo 'step 1 '
        sh 'mvn - f worker/pom.xml compile'
      }
    }
    stage ('test') {
      steps {
        echo 'step 2'
        sh 'mvn - f worker/pom.xml test'
      }
    }
    stage('package') {
      steps {
        echo 'step 3'
        sh 'mvn - f worker/pom.xml package - DskipTests'
        archiveArtifacts artifacts: '* */target/ * .jar',fingerprint: true
      }
    }
  }
  }
