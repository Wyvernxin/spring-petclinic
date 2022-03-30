pipeline {
    agent any
    stages {
        stage('Build Project') {
            steps {
                withSonarQubeEnv('YuxinsSonar') {
                    withMaven {
                        sh './mvnw clean install'
                    }
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
        }
        stage('Post out built outcome') {
            steps{
                archiveArtifacts 'target/*.jar'
            }
        }
    }
}
