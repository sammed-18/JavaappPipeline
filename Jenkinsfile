pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE = "sammed18/my-java-app"    // Update with the desired Docker image name
        DOCKER_CREDENTIALS = "sammed18"  // Update this after creating credentials
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building...'
                bat 'javac src/HelloWorld.java' // specify the correct path to your Java file
            }
        }
        
        stage('Run') {
            steps {
                echo 'Running...'
                bat 'java -cp src HelloWorld' // update if needed for the correct classpath
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}:${BUILD_NUMBER}")
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('', DOCKER_CREDENTIALS) {
                        docker.image("${DOCKER_IMAGE}:${BUILD_NUMBER}").push()
                    }
                }
            }
        }
    }
    
    post {
        always {
            sh "docker rmi ${DOCKER_IMAGE}:${BUILD_NUMBER} || true"
        }
    }
}
