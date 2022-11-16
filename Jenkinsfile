pipeline {
    agent any
    stages {
        stage('INFO'){
            steps{
                echo 'Info...'
                slackSend color: "warning", message: "INFO: Prueba Taller 3 - Modulo 4 Branch: ${GIT_BRANCH}"
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
        stage('uploadNexus'){
            steps{
                echo 'Uploading to Nexus...'
                slackSend color: "warning", message: "Uploading to Nexus..."
                sh './mvnw clean install -e'
                nexusPublisher nexusInstanceId: 'nexus01', nexusRepositoryId: 'devops-usach-nexus', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: './build/DevOpsUsach2020-0.0.1.jar']], mavenCoordinate: [artifactId: 'fancyWidget', groupId: 'com.devopsusach2020', packaging: 'jar', version: '0.0.1']]], tagName: '0.0.1'
                // nexusPublisher nexusInstanceId: 'nexus01', nexusRepositoryId: 'devops-usach-nexus', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: './build/DevOpsUsach2020-0.0.1.jar']], mavenCoordinate: [artifactId: 'fancyWidget', groupId: 'com.devopsusach2020', packaging: 'jar', version: '0.0.1']]]
                // nexusPublisher nexusInstanceId: 'nexus01', nexusRepositoryId: 'devops-usach-nexus', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: '${WORKSPACE}/build/DevOpsUsach2020-0.0.1.jar']], mavenCoordinate: [artifactId: 'fancyWidget', groupId: 'com.devopsusach2020', packaging: 'jar', version: '0.0.1']]]
                // nexusPublisher nexusInstanceId: 'nexus', nexusRepositoryId: 'devops-usach-nexus', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: '${WORKSPACE}/build/DevOpsUsach2020-0.0.1.jar']], mavenCoordinate: [artifactId: 'fancyWidget', groupId: 'com.devopsusach2020', packaging: 'jar', version: '0.0.1']]]
                
                //, tagName: 'build-125'

            }
            post {
                success {
                    echo 'Upload Success'
                    slackSend color: "good", message: "Upload Success"
                }
                failure {
                    echo 'Upload Failed'
                    slackSend color: "danger", message: "Upload Failed"
                }
            }

        }
        // stage('downloadNexusArtefact'){
        //     steps{
        //         cleanWs()    
        //         echo 'Download...'
        //         slackSend color: "warning", message: "Download..."
        //         sh 'curl -X GET -u admin:admin https://nexus.danilovidalm.com/repository/com/devopsusach2020/DevOpsUsach2020/0.0.1/DevOpsUsach2020-0.0.1.jar -O'
        //     }
        //     post {
        //         success {
        //             echo 'Deploy Success'
        //             slackSend color: "good", message: "Deploy Success"
        //         }
        //         failure {
        //             echo 'Deploy Failed'
        //             slackSend color: "danger", message: "Deploy Failed"
        //         }
        //     }
        // }

        
        // stage('Run'){
        //     steps{
        //         echo 'Running...'
        //         slackSend color: "warning", message: "Running..."
        //         sh '#./mvnw spring-boot:run -e'
        //     }
        //     post {
        //         success {
        //             echo 'Run Success'
        //             slackSend color: "good", message: "Run Success"   
        //             // cleanWs()                 
        //         }
        //         failure {
        //             echo 'Run Failed'
        //             slackSend color: "danger", message: "Run Failed"
        //         }
        //     }
        // }
    }
}
