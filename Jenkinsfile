pipeline {
    agent any

    environment {
        WEB_DIR = "/var/www/html"  // Location where you want to deploy the website
        SOURCE_DIR = "/path/to/your/local/website"  // Path to the directory containing your website files
    }

    stages {
        stage('Copy Files') {
            steps {
                // Copy website files to the web server's directory
                sh 'cp -r $SOURCE_DIR/* $WEB_DIR/'
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

