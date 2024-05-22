pipeline {
    agent any

    tools {
        maven 'Maven 3.9.6' // This should match the name given in Global Tool Configuration
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
                    bat "copy ${jarFile} \"${destinationDir}\""
                }
            }
        }
    }
}
