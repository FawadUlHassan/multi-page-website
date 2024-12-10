pipeline {
    agent any

    environment {
        WEB_DIR = "/var/www/html"
    }

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the repository from GitHub
                git 'https://github.com/FawadUlHassan/multi-page-website.git'
            }
        }

        stage('Build Website') {
            steps {
                // You can add any build steps here if necessary
                echo 'Building the multi-page website...'
            }
        }

        stage('Deploy to Apache') {
            steps {
                // Copy website files to Apache server's web root
                sh 'sudo cp -r * ${WEB_DIR}/'

                // Restart Apache to apply changes
                sh 'sudo systemctl restart apache2'
            }
        }
    }

    post {
        success {
            echo 'Build and Deployment completed successfully!'
        }

        failure {
            echo 'Build or Deployment failed.'
        }
    }
}

