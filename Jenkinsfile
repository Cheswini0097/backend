pipeline {
    agent {
        label 'Agent-1'
    }
    options {
        timeout(time: 30, unit: 'MINUTES') // Correct timeout option
        disableConcurrentBuilds() // Ensures no overlapping builds
        // retry(1) // Uncomment if retry logic is needed
    }
    environment {
        DEBUG = 'true'
        appVersion = '' // Global variable for use across the pipeline
    }
    stages {
        stage('Read the version') {
            steps {
                script {
                    def packageJson = readJSON file: 'package.json' // Corrected variable name
                    echo "App version: ${env.appVersion}" // Use env.appVersion for consistency
                }
            }
        }
        stage('Install Dependencies') { // Added missing curly braces for stage block
            steps {
                sh 'npm install'
            }
        }
        stage('Docker build') { // Added missing curly braces for stage block
            steps {
                
                sh """
                docker build -t chethankumar6/backend:${appVersion} .
                docker images
                """
            }
        }
    }
    post {
        always {
            echo "this section runs always"
            deleteDir()
        }
        sucess {
            echo "this section runs when pipeline succeds"
        }
        failure {
            echo  "this section runs when pipeline fails"
        }
    }
}
