pipeline {
    agent any
    environment {
        path = "/opt/maven/bin:$PATH"
    }
    stages {
        stage("build") {
            steps {
                sh 'mvn clean deploy'
            }
        }

        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'vishva-sonarqube-scanner'
            }
            steps {
                withSonarQubeEnv('vishva-sonarqube-server') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
