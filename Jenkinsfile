pipeline {
    agent any

    environment {
        TOMCAT_USER = 'jenkins'
        TOMCAT_PASSWORD = 'jenkins123'
        TOMCAT_URL = 'http://16.16.65.230:8081/manager/text'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/kalpeshdharkar/maven-webapp.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                sh '''
                curl -u $TOMCAT_USER:$TOMCAT_PASSWORD -T target/*.war "$TOMCAT_URL/deploy?path=/myapp"
                '''
            }
        }
    }
}
