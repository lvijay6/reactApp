pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
                sh 'ls'
                sh 'cd build'
                sh 'ls'
            }
        }
        stage('S3 Upload') {
            steps {
                withAWS(region: 'ap-south-1', credentials: '4d84d530-f2b2-4a8e-aef9-bab210895d26') {
                    sh 'ls -la build'
                    sh 'aws s3 cp build s3://react-app29/ --recursive'
                }
            }
        }
    }
}

