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

    stage('Stop tomcat') {
      parallel {
        stage('Stop tomcat') {
          steps {
            bat 'D:\\Programas\\apache-tomcat-9.0.88\\bin\\shutdown.bat'
          }
        }

        stage('prueba') {
          steps {
            echo 'Mensaje de prueba'
          }
        }

      }
    }

    stage('Start tomcat') {
      steps {
        bat 'D:\\Programas\\apache-tomcat-9.0.88\\bin\\startup.bat'
      }
    }

  }
}