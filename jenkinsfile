pipeline {
    agent any

    tools {
        // Vérifiez bien que ces noms sont IDENTIQUES à ceux dans 
        // "Administrer Jenkins" -> "Global Tool Configuration"
        jdk 'JDK17' 
        maven 'Maven3'
    }

    stages {
        stage('Compile and Test') {
            steps {
                // On utilise 'sh' pour Linux. Si Jenkins est sur Windows, utilisez 'bat'
                sh 'mvn clean install -DskipTests'
            }
        }
    }
}
