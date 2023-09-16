pipeline {
    agent { docker { image 'maven:3.9.4-eclipse-temurin-17-alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
    }
    
    post {
      failure {
        discordSend description: "${currentBuild.fullDisplayName}", footer: "", link: env.BUILD_URL, result: currentBuild.currentResult, title: "SUCCEEDED", webhookURL: "${DISCORD_WEBHOOKURL}"
      }
      success {
        discordSend description: "${currentBuild.rawBuild.getLog(10)}", footer: "${currentBuild.fullDisplayName}", link: env.BUILD_URL, result: currentBuild.currentResult, title: "FAILED", webhookURL: "${DISCORD_WEBHOOKURL}"
      }
    }
}