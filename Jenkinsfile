pipeline {
    agent any
    tools {
        dockerTool "docker"
    }

    stages {
        stage('clone repo') {
            steps {
                git 'https://github.com/Vishnu44d/ci_test.git'

            }
        }
        stage('test jenkinsfile') {
            steps {
                sh 'echo "in the jenkingsfile"'

            }
        }
        stage('Buid and push to hub') {
            steps {

                script {
                    withDockerRegistry(
                        credentialsId: 'c0acf894-d8a4-11ea-94f3-74e5f9e5188e',
                        toolName: 'docker') {
                        def echoServerImage = docker.build("vishnu44d/hello-world-webapp:latest");
                        echoServerImage.push();
                    }
                }
            }
        }
    }
    post {
        success {
            echo "Success"
        }
        failure {
            echo "Failed"
        }
    }
}
