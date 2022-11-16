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
        slackSend color: "good", message: "Build Success. commit"
    } catch (e) {
        slackSend color: "danger", message: "Build Failure. commit"
        throw e
    } finally {}
    try {
        stage('Test'){
            echo "Testing"
            sh './mvnw test -e'
        }
        slackSend color: "good", message: "Test Success. commit"
    } catch (e) {
        slackSend color: "danger", message: "Test Failure. commit"
        throw e
    } finally {}
    try {
        stage('Package'){
            echo "Packaging"
            sh './mvnw package -e'
        }
        slackSend color: "good", message: "Packaging Success. commit"
    } catch (e) {
        slackSend color: "danger", message: "Packaging Failure. commit"
        throw e
    } finally { }
    try {
        stage('Sonar'){
            echo 'Sonar...'
            withSonarQubeEnv('sonar-public') { // If you have configured more than one global server connection, you can specify its name
                sh './mvnw clean package sonar:sonar'
            }
        }
        slackSend color: "good", message: "Sonar Success. commit"
    }catch (e) {
        slackSend color: "danger", message: "Sonar Failure. commit"
        throw e
    } finally { }
    
}