pipeline {
    agent any
    stages {
        stage('Build Project and Run Sonar Scan') {
            steps {
                withMaven {
                    sh './mvnw clean install'
                }
            }
        }
        stage('Run SonarQube Scan') {
            steps {
                withSonarQubeEnv('YuxinsSonar') {
                    withMaven {
                        sh './mvnw sonar:sonar'
                    }
                }
            }
        }
    }
}
