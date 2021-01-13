pipeline {
  agent { any }
  stages {
    stage('First Stage') {
      steps {
        echo "Yay! First stage is executed"
      }
    }
    stage('Build') {
      steps {
        bat 'gcc main.c'
      }
    }
  }
}
