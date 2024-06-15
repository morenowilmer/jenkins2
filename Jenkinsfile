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
      steps {
        bat 'mvn clean verify sonar:sonar -Dsonar.projectKey=proyecto-jenkins -Dsonar.projectName=\'proyecto-jenkins\' -Dsonar.host.url=http://localhost:9090 -Dsonar.token=sqp_cf49272857244404388a9c41ce9f89c27587a647'
      }
    }

  }
}