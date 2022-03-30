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
        }
        stage('Post out built outcome'){
            post{
                success{
                    archiveArtifacts 'target/*.jar
                }
            }
        }
//         stage("build project") {
//             agent any
//             steps {
//                 withSonarQubeEnv('YuxinsSonar') {
// //                 sh './mvnw clean verify package sonar:sonar -Dsonar.host.url=http://192.168.33.21:9000'
//                     sh './mvnw clean install clean package'

//                 }
//             }
//         }

//         stage('run SonarQube scan') {
//             agent any
//             steps {
//                 withSonarQubeEnv('YuxinsSonar') {
//                     sh './mvnw clean package'
//                     sh './mvnw  sonar:sonar'
//                 }
//             }
//             post {
//                 success {
//                     archiveArtifacts 'target/*.jar'
//                 }
//             }
//         }
    }
}
