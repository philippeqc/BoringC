pipeline {
  agent { label 'fizzbuzz' } 
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
    post {
        always {
            archiveArtifacts artifacts: "*", fingerprint: true
            emailext (
                subject: "${currentBuild.result}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: """<p>${currentBuild.result}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
                <p>Check console output at "<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>"</p>""",
                recipientProviders: [culprits(), requestor()]
            )
        }
    }
}
