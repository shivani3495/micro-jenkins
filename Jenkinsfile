pipeline {
    agent { 
        label 'windows' 
    }

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
                    // Archive the JAR file as a build artifact
                    archiveArtifacts artifacts: 'SimpleJavaProject.jar', fingerprint: true

                    // Define the local directory where you want to store the JAR file
                    def localDir = 'C:\\Users\\chauhanarjit\\Desktop\\jarfile'

                    // Ensure the directory exists and copy the JAR file to the local directory
                    bat """
                        if not exist "${localDir}" mkdir "${localDir}"
                        copy SimpleJavaProject.jar "${localDir}"
                    """
                }
            }
        }
    }
}
