pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/FaridBayu/ppmpl_2200016048_muhammad-farid-bayu-hadi_prak8.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Unit Tests') {
            steps {
                sh 'npm test'
            }
        }
        stage('Run Integration Tests') { // Tahap baru untuk pengujian integrasi
            steps {
                echo 'Running integration tests...'
                sh 'npm run test:integration' // Sesuaikan dengan script integrasi di package.json
            }
        }
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Tambahkan perintah build jika diperlukan
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application to staging...'
                sh 'scp -r ./build user@staging-server:/path/to/deploy' // Otomatisasi deployment ke server staging
            }
        }
    }
    post {
        success {
            echo 'Pipeline finished successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
