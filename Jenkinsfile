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
                // Replace this with your deployment strategy
                // For example, copying files to /var/www/html:
                sh 'cp -r * /var/www/html'
            }
        }
        stage('Test Website') {
            steps {
                script {
                    // Test the website by curling localhost (this ensures the website is up)
                    echo 'Testing the deployed website...'
                    def result = sh(script: 'curl -s -o /dev/null -w "%{http_code}" http://localhost', returnStdout: true).trim()

                    if (result != '200') {
                        error("Website deployment failed with HTTP status: ${result}")
                    } else {
                        echo 'Website deployed successfully!'
                    }
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

