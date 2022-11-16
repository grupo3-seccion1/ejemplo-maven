// def estadoStage = 'SI'
node {
    stage('INFO'){
        echo "Hello World"
        slackSend color: "warning", message: "INFO: Prueba Taller 3 - Modulo 4 Branch: " + env.BRANCH_NAME
        slackSend color: "good", message: "Info Success. hash commit : " + env.COMMIT
    }
    stage('Build'){
        try {
            echo "Building"
            sh './mvnw clean compile -e'
        } catch (e) {
            currentBuild.result = 'FAILURE'
            slackSend color: "danger", message: "Build Failure. commit"
            // estadoStage = 'NO'
        } finally {
            echo currentBuild.result
        }
        //     slackSend color: "good", message: "Build Success. commit"
        // if(currentBuild.result == 'FAILURE'){
        // }else{
        // }
        // echo 'Variable : ' + estadoStage
    }
}