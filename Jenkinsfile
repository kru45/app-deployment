pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // 'react-app' is the folder name created by 'npx create-react-app'
                dir('my-react-app') { 
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('Deploy') {
            steps {
                // Ensure you point to the build folder inside your app folder
                sh 'docker cp my-react-app/build/. my-web-server:/usr/share/nginx/html'
            }
        }
    }
}
