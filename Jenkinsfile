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

                    // Log the local directory path
                    echo "Local directory path: ${localDir}"

                    // Check if the destination directory already exists
                    def dirExists = fileExists(localDir)
                    echo "Directory exists: ${dirExists}"

                    // Ensure that the destination directory exists
                    if (!dirExists) {
                        bat "mkdir ${localDir}"
                    }

                    // Check if the JAR file exists
                    def jarExists = fileExists('SimpleJavaProject.jar')
                    echo "JAR file exists: ${jarExists}"

                    // Copy the JAR file to the local directory
                    bat "copy SimpleJavaProject.jar ${localDir}"

                    // List files in the local directory after copying
                    bat "dir ${localDir}"
                }
            }
        }
    }
}

def fileExists(filePath) {
    return fileExistsWindows(filePath) || fileExistsUnix(filePath)
}

def fileExistsWindows(filePath) {
    return bat(script: "if exist \"${filePath}\" (exit 0) else (exit 1)", returnStatus: true) == 0
}

def fileExistsUnix(filePath) {
    return sh(script: "[ -e \"${filePath}\" ]", returnStatus: true) == 0
}
