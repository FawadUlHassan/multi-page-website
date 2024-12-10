pipeline {
    agent any

    environment {
        WEB_DIR = "/var/www/html"  // Directory to deploy website files
    }

    stages {
        stage('Clone Repository') {
            steps {
                // No credentials needed for public repos
                git url: 'https://github.com/FawadUlHassan/multi-page-website.git'
            }
        }

        stage('Deploy Website') {
            steps {
                // Copy website files to the web server's directory
                sh 'cp -r * $WEB_DIR/'
            }
        }

        stage('Restart Apache') {
            steps {
                // Restart Apache to apply the changes
                sh 'sudo systemctl restart apache2'
            }
        }
    }
}

