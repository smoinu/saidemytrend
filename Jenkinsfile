pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
 
    stages {

        stage("build") {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarQube analysis') {
            environment {
                ScannerHome = tool 'smoinu-sonar-scanner'

            }

            steps {
                withSonarQubeEnv('smoinusonarqubeserver') {

                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }

}
