pipeline {
    agent any

    tools {
        jdk 'JDK17'
        maven 'Maven3'
    }

    environment {
        SONAR_TOKEN = credentials('sonar-token') 
        // 'sonar-token' must match the ID you created in Jenkins Credentials
    }

    stages {

        stage('Compile and Test') {
            steps {
                sh 'mvn clean install -DskipTests'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarScanner') 
                // Must match the name configured in Jenkins → Global Tool Configuration

                sh """
                mvn sonar:sonar \
                -Dsonar.projectKey=MyProject \
                -Dsonar.host.url=http://http://192.168.56.10:9000 \
                -Dsonar.login=$SONAR_TOKEN
                """
            }
        }
    }
}
