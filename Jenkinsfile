pipeline {
    agent any

    environment {
        MAVEN_HOME = 'C:\Users\sainishivani\Downloads\apache-maven-3.9.6-bin\apache-maven-3.9.6'  // Update this to your Maven installation path
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Move JAR') {
            steps {
                script {
                    def jarFile = findFiles(glob: '**/target/*.jar')[0].path
                    def destinationDir = 'D:\\Shivani Devops\\my-java-project'
                    bat "copy ${jarFile} ${destinationDir}"
                }
            }
        }
    }
}
