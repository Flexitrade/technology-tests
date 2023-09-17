pipeline {
    agent { docker { image 'maven:3.9.4-eclipse-temurin-17-alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'exit 1'
            }
        }
    }
    
    post {
      success {
        discordSend description: "id: ${currentBuild.displayName}\build-time: ${currentBuild.durationString}", footer: "", link: env.BUILD_URL, result: currentBuild.currentResult, title: "[${currentBuild.fullDisplayName}] SUCCEEDED", webhookURL: "${DISCORD_WEBHOOKURL}"
      }
      failure {
        discordSend description: "id: ${currentBuild.displayName}\nbuild-time: ${currentBuild.durationString}\nPlease check log output for error message!", footer: "", link: env.BUILD_URL, result: currentBuild.currentResult, title: "[${currentBuild.fullDisplayName}] FAILED!", webhookURL: "${DISCORD_WEBHOOKURL}"
      }
    }
}