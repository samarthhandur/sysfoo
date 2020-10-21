pipeline {
  agent {
    docker {
      image 'maven:3.6.3-jdk-11-slim'
    }

  }
  stages {
    stage('build') {
      agent {
        docker {
          image 'maven:3.6.3-jdk-11-slim'
        }

      }
      steps {
        echo 'step 1 '
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'step 2'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'step 3'
        sh 'mvn package -DskipTests'
      }
    }

    stage('Docker build and push') {
      steps {
        script {
          docker.withRegistry('https://index.docker.io/v1/', 'dockerlogin') {
            def dockerImage = docker.build("samarthh/sysfoo${env.BUILD_ID}", "./")
            dockerImage.push()
            dockerImage.push("latest")
          }
        }

      }
    }

  }
}