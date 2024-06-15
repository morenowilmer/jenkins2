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
      steps {
        bat 'D:\\Programas\\apache-tomcat-9.0.88\\bin\\shutdown.bat'
      }
    }

    stage('Catch Stop tomcat') {
      parallel {
        stage('Catch Stop tomcat') {
          steps {
            warnError(message: 'Tamcot no esta activo', catchInterruptions: true) {
              bat 'D:\\Programas\\apache-tomcat-9.0.88\\bin\\startup.bat'
            }

          }
        }

        stage('Imprimir') {
          steps {
            echo 'Prueba tomcat'
          }
        }

      }
    }

  }
}