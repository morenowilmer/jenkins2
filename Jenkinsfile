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

    stage('War Dev') {
      steps {
        bat 'copy "target\\jenkins2.war" D:\\Programas\\apache-tomcat-9.0.88\\webapps\\jenkins2-dev.war'
      }
    }

    stage('Sonar') {
      steps {
        bat 'mvn sonar:sonar -Dsonar.projectKey=proyecto-jenkins -Dsonar.host.url=http://localhost:9000 -Dsonar.login=6af35bab46cac7881140520f8e3590a71867b27d'
        mail(subject: 'Finalizo el análisis de sonar', body: 'El análisis de sonar finalizo satisfactoriamente.', to: 'morenowilmer115@gmail.com', from: 'morenowilmer115@outlook.com', cc: 'morenowilmer115@outlook.com')
      }
    }

    stage('War Pro') {
      steps {
        bat 'copy "target\\jenkins2.war" D:\\Programas\\apache-tomcat-9.0.88\\webapps\\jenkins2-pro.war'
      }
    }

    stage('Email') {
      steps {
        mail(cc: 'morenowilmer115@outlook.com', from: 'morenowilmer115@outlook.com', to: 'morenowilmer115@gmail.com', subject: 'Despliegue proyecto a producción', body: 'Se realizo el despliegue del proyecto al ambiente de producción.')
      }
    }

  }
}