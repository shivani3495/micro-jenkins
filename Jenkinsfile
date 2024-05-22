pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Clean and build the project using Maven
                    if (isUnix()) {
                        sh 'mvn clean package'
                    } else {
                        bat 'mvn clean package'
                    }
                }
            }
        }

        stage('Move JAR Files') {
            steps {
                script {
                    // Define source and target directories
                    def sourceDir = 'target'
                    def destDir = 'D:\\Shivani Devops\\my-java-project'
                    
                    // Create destination directory if it does not exist
                    if (isUnix()) {
                        sh "mkdir -p ${destDir}"
                    } else {
                        bat "if not exist \"${destDir}\" mkdir \"${destDir}\""
                    }

                    // Copy the JAR file to the destination directory
                    def jarFile = 'my-java-project-1.0-SNAPSHOT.jar'
                    if (isUnix()) {
                        sh "cp ${sourceDir}/${jarFile} ${destDir}/"
                    } else {
                        bat "copy \"${sourceDir}\\${jarFile}\" \"${destDir}\\\""
                    }
                }
            }
        }
    }
}
