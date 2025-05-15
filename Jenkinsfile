pipeline {
    agent any  // Use any available agent

    tools {
        maven 'Maven'  // Ensure this matches the Maven name configured in Jenkins (Manage Jenkins -> Global Tool Configuration)
    }

    stages {
        stage('Checkout') {
            steps {
                // Clean workspace to avoid Git cache/stale branch issues
                deleteDir()
                git branch: 'main', url: 'https://github.com/Testing2000-04/SVITCSEMavenApp.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'  // Run Maven build
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'  // Run unit tests
            }
        }

        stage('Run Application') {
            steps {
                // Run the built JAR application
                sh 'java -jar target/SVITCSEMavenApp-1.0-SNAPSHOT.jar'
            }
        }
    }

    post {
        success {
            echo '✅ Build and deployment successful!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}

