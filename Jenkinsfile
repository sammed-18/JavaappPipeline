pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                bat 'javac src/HelloWorld.java' // specify the correct path
            }
        }
        stage('Run') {
            steps {
                echo 'Running...'
                bat 'java -cp src HelloWorld' // add the src directory to the classpath
            }
        }
    }
}
