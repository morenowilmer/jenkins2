pipeline {
  agent any
  stages {
    stage('Buid') {
      steps {
        sh 'clean package'
      }
    }

    stage('war') {
      steps {
        archiveArtifacts '**/*.war'
      }
    }

  }
}