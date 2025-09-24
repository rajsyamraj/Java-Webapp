pipeline {
    agent { label 'your-agent-label' }

    environment {
        DEPLOY_DIR = '/apps' // Change as needed
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/rajsyamraj/Java-Webapp.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                sh 'cp target/*.jar $DEPLOY_DIR/'
                echo 'App deployed to $DEPLOY_DIR'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
