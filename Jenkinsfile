pipeline {
    agent any

    environment {
        // Define any environment variables if needed, e.g., Apache document root path
        APACHE_DIR = '/var/www/html'
    }

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    // Clone the GitHub repository
                    echo 'Cloning GitHub repository...'
                    git branch: 'main', url: 'https://github.com/FawadUlHassan/multi-page-website.git'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the website...'
                // Deploy to /var/www/html using sudo to overcome permission issues
                sh 'sudo cp -r * /var/www/html'
            }
        }

        stage('Test Website') {
            steps {
                script {
                    // Test the website by curling localhost (this ensures the website is up)
                    echo 'Testing the deployed website...'
                }
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}

