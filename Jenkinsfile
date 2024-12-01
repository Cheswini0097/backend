pipeline {
    agent {
        label 'Agent-1' // Ensures this pipeline runs on an agent with the label 'Agent-1'
    }
    options {
        timeout(time: 30, unit: 'MINUTES') // Corrected syntax for the timeout option
        disableConcurrentBuilds() // Corrected method name spelling
        // retry(1) // Uncomment if needed
    }
    environment { // Fixed typo from "envinorment" to "environment"
        DEBUG = 'true'
        appVersion = '' // Declaring appVersion as an environment variable
    }
    stages {
        stage('Read the version') {
            steps {
                script { // Wrapping the script block properly
                    def packageJson = readJSON file: 'package.json' // Fixed variable name
                    env.appVersion = packageJson.version // Accessing the version field from the package.json
                    echo "App version: ${env.appVersion}" // Corrected variable interpolation syntax
                }
            }
        }
    }
}
