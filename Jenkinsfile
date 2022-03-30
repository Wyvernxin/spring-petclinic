pipeline {
    agent any
    stages {
        stage("build project") {
            agent any
            steps {
                withSonarQubeEnv('YuxinsSonar') {
//                 sh './mvnw clean verify package sonar:sonar -Dsonar.host.url=http://192.168.33.21:9000'
                    sh './mvnw clean install clean package'

                }
            }
        }

    stage('run SonarQube scan') {
        agent any
        steps {
            withSonarQubeEnv('YuxinsSonar') {
                sh './mvnw  sonar:sonar'
            }
        }
        post {
            success {
                archiveArtifacts 'target/*.jar'
            }
        }
    }
    // Wait for the timeout -- max time is 10 minutes
//     stage("Get Sonar Quality Gate") {
//         steps {
//             timeout(time: 10, unit: 'MINIUTES') {
//                 waitForQualityGate abortPipeline: true
//             }
//         }
//     }
}
