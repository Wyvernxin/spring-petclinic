pipeline {
    agent any
    stages {
      stage("build & analysis") {
        agent any
        steps {
            withSonarQubeEnv('YuxinsSonar') {
//                 sh './mvnw clean verify package sonar:sonar -Dsonar.host.url=http://192.168.33.21:9000'
                sh './mvnw clean verify package sonar:sonar'

            }
        }
        post {
            success {
                archiveArtifacts 'target/*.jar'
            }
        }
      }
    }
}
