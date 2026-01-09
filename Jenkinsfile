pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/mennanvijay/ben10.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                // Assuming your vite project is in the root or a subfolder
                // If it's in a subfolder, use dir('folder-name')
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                sh 'sudo rm -rf /var/www/html/*'
                // This copies the production build to Apache
                sh 'sudo cp -R dist/. /var/www/html/' 
                sh 'sudo chown -R apache:apache /var/www/html'
                sh 'sudo chmod -R 755 /var/www/html'
                echo "Ben10 is Live!"
            }
        }
    }
}
