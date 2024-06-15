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
        bat(script: 'mvn clean verify sonar:sonar -Dsonar.projectKey=proyecto-jenkins -Dsonar.projectName=\'proyecto-jenkins\' -Dsonar.java.jdkHome=\'C:\\Program Files\\Java\\jdk-11\' -Dsonar.language=java -Dsonar.login -Dsonar.password=admin123456789 -Dsonar.sourceEncodign=UTF-8', returnStatus: true)
      }
    }

  }
}