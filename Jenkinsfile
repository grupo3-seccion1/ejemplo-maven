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
                    echo 'INFO Success'
                    slackSend color: "good", message: "Info Success"
                }
                failure {
                    echo 'INFO Failed'
                    slackSend color: "danger", message: "Info Failed"
                }
            }
        }
    }
}
