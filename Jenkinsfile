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

        stage('Archive') {
            steps {
                script {
                    // Archive the JAR file as a build artifact
                    archiveArtifacts artifacts: 'SimpleJavaProject.jar', fingerprint: true

                    // Define the local directory where you want to store the JAR file
                    def localDir = 'C:\\Users\\chauhanarjit\\Desktop\\wsr-audit-report'

                    // Copy the JAR file to the local directory
                    bat "copy SimpleJavaProject.jar ${localDir}"
                }
            }
        }
    }
}
