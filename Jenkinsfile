pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from the repository
                git 'https://your-repository-url.git'
            }
        }

        stage('Compile') {
            steps {
                // Compile the Java source code
                sh 'javac -d out App.java'
            }
        }

        stage('Package') {
            steps {
                // Create the JAR file
                sh 'jar cfm SimpleJavaProject.jar manifest.mf -C out .'
            }
        }

        stage('Archive') {
            steps {
                // Archive the JAR file as a build artifact
                archiveArtifacts artifacts: 'SimpleJavaProject.jar', fingerprint: true
            }
        }
    }
}
