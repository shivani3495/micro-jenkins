pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                script {
                    // Compile the Java source code
                    if (isUnix()) {
                        sh 'javac -d out App.java'
                    } else {
                        bat 'javac -d out App.java'
                    }
                }
            }
        }

        stage('Package') {
            steps {
                script {
                    // Create the JAR file
                    if (isUnix()) {
                        sh 'jar cfm SimpleJavaProject.jar manifest.mf -C out .'
                    } else {
                        bat 'jar cfm SimpleJavaProject.jar manifest.mf -C out .'
                    }
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

                    // Copy the JAR file to the local directory based on the operating system
                    if (isUnix()) {
                        sh "mkdir -p ${localDir} && cp SimpleJavaProject.jar ${localDir}"
                    } else {
                        bat """
                            if not exist "${localDir}" mkdir "${localDir}"
                            copy SimpleJavaProject.jar "${localDir}"
                        """
                    }
                }
            }
        }
    }
}
