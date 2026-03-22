pipeline {
    agent any // Use any available agent
    tools {
        gradle 'Gradle' // Ensure this matches the name configured in Jenkins
        jdk 'JDK17'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/ankitjha100/GradleJenkinsPipeline.git'
            }
        }
        stage('Build') {
            steps {
                withEnv(["JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64"]) {
                    sh 'java -version'
                    sh 'gradle build'
                }
            }
        }
        stage('Test') {
            steps {
                sh 'gradle test' // Run unit tests
            }
        }
        stage('Run Application') {
            steps {
                // Start the JAR application
                sh 'gradle run'
            }
        }
    }
    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
