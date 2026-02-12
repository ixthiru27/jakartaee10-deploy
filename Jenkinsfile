pipeline {
    agent any

    tools {
        maven 'local_maven'
        jdk 'java25'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }

        stage('Deploy') {
    steps {
        bat """
            copy /Y target/jakartaee10-starter-boilerplate.war "C:/Program Files/Apache Software Foundation/Tomcat 11.0/webapps/"
        """
    }
}

    }

    post {
        success {
            echo 'Deployment Successful!'
        }
        failure {
            echo 'Build or Deployment Failed!'
        }
    }
}
