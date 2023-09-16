pipeline {
    agent { docker { image 'maven:3.9.4-eclipse-temurin-17-alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --quatsch-mit-soße'
            }
        }
    }
    
    post {
      success {
        discordSend description: "${currentBuild.fullDisplayName}", footer: "", link: env.BUILD_URL, result: currentBuild.currentResult, title: "SUCCEEDED", webhookURL: "${DISCORD_WEBHOOKURL}"
      }
      failure {
        buildFailure = tm('${BUILD_FAILURE_ANALYZER}')
        discordSend description: buildFailure, footer: "${currentBuild.fullDisplayName}", link: env.BUILD_URL, result: currentBuild.currentResult, title: "FAILED", webhookURL: "${DISCORD_WEBHOOKURL}"
      }
    }
}