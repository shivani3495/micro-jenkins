pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                script {
                    // Compile the Java source code
                    sh 'javac -d out App.java'
                }
            }
        }

        stage('Package') {
            steps {
                script {
                    // Create the JAR file
                    sh 'jar cfm SimpleJavaProject.jar manifest.mf -C out .'
                }
            }
        }

        stage('Copy to Local Folder') {
            steps {
                script {
                    // Define the local directory where you want to copy the JAR file
                    def localDir = 'C:\\Users\\chauhanarjit\\Desktop\\wsr-audit-report'

                    // Copy the JAR file to the local directory using Windows batch command
                    bat "copy SimpleJavaProject.jar \"${localDir}\""
                }
            }
        }
    }
}
