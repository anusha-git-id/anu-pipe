pipeline {
    agent none
    stages {
        stage('Build') {
            agent { label 'slave1' }
            steps {
                // Checkout the code manually
                git branch: 'main', url: 'https://github.com/your-repo/springapp.git', credentialsId: 'your-credentials-id'
                // Run Maven install
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            agent { label 'slave2' }
            steps {
                sh 'mvn test'
            }
        }
    }
    post {
        success {
            echo 'Build and Test stages completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
