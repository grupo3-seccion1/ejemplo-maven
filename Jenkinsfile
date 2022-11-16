// def estadoStage = 'SI'
node {
    stage('INFO'){
        echo "Hello World"
        slackSend color: "warning", message: "INFO: Prueba Taller 3 - Modulo 4 Branch: " + env.BRANCH_NAME
        // slackSend color: "good", message: "Info Success. hash commit : " + e
    }
        try {
            stage('Build'){
                echo "Building"
                sh './mvnw clean compile -e'
            }
        } catch (e) {
            slackSend color: "danger", message: "Build Failure. commit"
            throw e
        } finally {
            slackSend color: "good", message: "Build Success. commit"
        }
}