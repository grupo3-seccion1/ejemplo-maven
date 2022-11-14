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
                    slackSend color: "good", message: "Info Success. commit ${GIT_COMMIT}"
                }
                failure {
                    echo 'INFO Failed'
                    slackSend color: "danger", message: "Info Failed."
                }
            }
        }
        stage('Sonar'){
            steps{
                echo 'Sonar...'
                withSonarQubeEnv('sonar-public') { // If you have configured more than one global server connection, you can specify its name
                    sh './mvnw clean package sonar:sonar'
                }
            }
            post {
                success {
                    echo 'SONAR Success'
                    slackSend color: "good", message: "Sonar Success. Branch: ${GIT_BRANCH}"
                }
                failure {
                    echo 'SONAR Failed'
                    slackSend color: "danger", message: "Sonar Failed."
                }
            }
        }
        stage('Build'){
            steps{
                echo 'Building...'
                slackSend color: "warning", message: "Building..."
                sh './mvnw clean compile -e'

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
        stage('Test'){
            steps{
                echo 'Testing...'
                slackSend color: "warning", message: "Testing..."
                sh './mvnw test -e'
            }
            post {
                success {
                    echo 'Test Success'
                    slackSend color: "good", message: "Test Success"
                }
                failure {
                    echo 'Test Failed'
                    slackSend color: "danger", message: "Test Failed"
                }
            }
        }
        stage('Package'){
            steps{
                echo 'Packaging...'
                slackSend color: "warning", message: "Packaging..."
                sh './mvnw package -e'
            }
            post {
                success {
                    echo 'Package Success'
                    slackSend color: "good", message: "Package Success"
                }
                failure {
                    echo 'Package Failed'
                    slackSend color: "danger", message: "Package Failed"
                }
            }
        }
        stage('Run'){
            steps{
                echo 'Running...'
                slackSend color: "warning", message: "Running..."
                sh '#./mvnw spring-boot:run -e'
            }
            post {
                success {
                    echo 'Run Success'
                    slackSend color: "good", message: "Run Success"   
                    cleanWs()                 
                }
                failure {
                    echo 'Run Failed'
                    slackSend color: "danger", message: "Run Failed"
                }
            }
        }
    }
}
