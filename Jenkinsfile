node {
    stage('INFO'){
        echo "Hello World"
        slackSend color: "warning", message: "INFO: Prueba Taller 3 - Modulo 4 Branch: " + env.BRANCH_NAME
        slackSend color: "good", message: "Info Success. hash commit : " + env.COMMIT
    }
}