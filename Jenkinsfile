node {
    def siguiente = false;
    stage('INFO'){
        echo "Hello World"
        slackSend color: "warning", message: "INFO: Prueba Taller 3 - Modulo 4 Branch: " + env.BRANCH_NAME
        slackSend color: "good", message: "Info Success. hash commit : " + env.COMMIT
    }
    stage('Build'){
        echo "Building"
        sh './mvnw clean compile -e'
        if(currentBuild.result == 'FAILURE'){
            slackSend color: "danger", message: "Build Failure. commit"
        }else{
            slackSend color: "good", message: "Build Success. commit"
        }
        echo siguiente
    }
}