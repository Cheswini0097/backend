pipeline {
    agent {
        label 'AGENT-1'
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
    }
}
