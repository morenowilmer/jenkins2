pipeline {
  agent any
  stages {
    stage('Buid') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage('war') {
      steps {
        archiveArtifacts '**/*.war'
      }
    }

  }
}