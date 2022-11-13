pipeline {
    agent any
    stages {
        stage('INFO'){
            steps{
                echo 'Info...'
                slackSend color: "warning", message: "INFO: Prueba Taller 2 - Modulo 4 Branch: ${GIT_BRANCH}"
                //sh './mvnw clean compile -e'

            }
            post {
                success {
                    echo 'Build Success'
                    slackSend color: "good", message: "Build Success"
                }
                failure {
                    echo 'Build Failed'
                    slackSend color: "danger", message: "Build Failed"
                }
            }
        }
    }
}
