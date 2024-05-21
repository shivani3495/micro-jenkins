pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                script {
                    // Compile the Java source code
                    bat 'javac -d out App.java'
                }
            }
        }

        stage('Package') {
            steps {
                script {
                    // Create the JAR file
                    bat 'jar cfm SimpleJavaProject.jar manifest.mf -C out .'
                }
            }
        }

        stage('Archive') {
            steps {
                script {
                    // Define the local directory where you want to copy the JAR file
                    def localDir = 'C:\\Users\\chauhanarjit\\Desktop\\wsr-audit-report'

                    // Create the local directory if it doesn't exist
                    bat "if not exist \"${localDir}\" mkdir \"${localDir}\""

                    // Copy the JAR file to the local directory
                    bat "copy SimpleJavaProject.jar \"${localDir}\""
                }
            }
        }
    }
}
