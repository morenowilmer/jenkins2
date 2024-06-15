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
        bat 'mvn sonar:sonar -Dsonar.projectKey=proyecto-jenkins -Dsonar.host.url=http://localhost:9000 -Dsonar.login=6af35bab46cac7881140520f8e3590a71867b27d'
        waitForQualityGate true
        warnError(message: 'Error en pruebas de sonar') {
          mail(subject: 'Error Sonar', body: 'El proyecto no paso las pruebas de sonar', from: 'morenowilmer115@outlook.com', to: 'morenowilmer115@gmail.com', cc: 'morenowilmer115@outlook.com')
        }

        mail(subject: 'Correo de prueba', body: 'Correo de prueba', to: 'morenowilmer115@gmail.com', from: 'morenowilmer115@outlook.com', cc: 'morenowilmer115@outlook.com')
      }
    }

  }
}