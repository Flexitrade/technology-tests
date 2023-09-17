pipeline {
    agent { docker { image 'maven:3.9.4-eclipse-temurin-17-alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'exit 0'
            }
        }
    }
    
    post {
      success {
        discordSend description: "build took ${currentBuild.durationString}", footer: "", link: env.BUILD_URL, result: currentBuild.currentResult, title: "${currentBuild.fullDisplayName} SUCCEEDED", webhookURL: "${DISCORD_WEBHOOKURL}"
      }
      failure {
        discordSend description: "build id is ${currentBuild.displayName}\nbuild took ${currentBuild.durationString}\n\nPlease check log output for error message!", footer: "", link: env.BUILD_URL, result: currentBuild.currentResult, title: "FAILED ${currentBuild.fullDisplayName}!", webhookURL: "${DISCORD_WEBHOOKURL}"
      }
    }
}