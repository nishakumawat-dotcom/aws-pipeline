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
                echo 'Building Weather Forecast Project...'
                sh '''
                ls -la
                test -f index.html
                test -f style.css
                test -f script.js
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                sudo rm -rf /var/www/html/*
                sudo cp -r ./* /var/www/html/
                sudo systemctl restart httpd
                '''
            }
        }
    }

    post {
        success {
            echo 'Build and Deployment Successful!'
        }

        failure {
            echo 'Build or Deployment Failed!'
        }
    }
}
