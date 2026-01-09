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
                // Change 'vite-project' to whatever your folder is named in GitHub
                dir('vite-project') { 
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }

        stage('Deploy') {
            steps {
                sh 'sudo rm -rf /var/www/html/*'
                // Ensure the path below matches your folder structure
                sh 'sudo cp -R vite-project/dist/. /var/www/html/'
                sh 'sudo chown -R apache:apache /var/www/html'
                sh 'sudo chmod -R 755 /var/www/html'
                echo "Ben10 is Live!"
            }
        }
    }
}
