pipeline {
    agent {
        label 'Agent-1'
    }
    options {
        timeout ( time:30, unit : 'MINUTE')
        diableConcuranteBuilds ()
        //retry (1)
    }
    envinorment {
        DEBUG = 'true'
        appVersion = ''
    }
    stages {
        stage ('Read the version') {
            steps {
                script def pakage.Json = readJSON file: 'package.json'
                appVersion = pakage.Json
                echo "Appversion  $ {appVersion}"
           }
        }
    }
}
