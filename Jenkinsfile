pipeline {
  agent any
  stages {
    stage('Buid') {
      steps {
        bat 'mvn clean package'
      }
    }

    stage('war') {
      steps {
        archiveArtifacts '**/*.war'
      }
    }

    stage('Copy War') {
      steps {
        bat 'copy "target\\jenkins2.war" D:\\Programas\\apache-tomcat-9.0.88\\webapps\\jenkins2-dev.war'
      }
    }

    stage('Sonar') {
      withSonarQubeEnv() {
        bat "mvn clean verify sonar:sonar -Dsonar.projectKey=proyecto-jenkins -Dsonar.projectName='proyecto-jenkins'"
      }
    }

  }
}
