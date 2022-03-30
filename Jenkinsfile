pipeline {
    agent any
    stages {
        stage('Build Project') {
            steps {
                withMaven {
                    sh './mvnw clean install'
                }
            }
        }
        stage('SonarQube analyze') {
            steps {
                withSonarQubeEnv('YuxinsSonar') {
                    withMaven {
                        sh './mvnw sonar:sonar'
                    }
                }
            }  
            post{
                success{
                    archiveArtifacts 'target/*.jar
                }
            }
        }
    }
}
