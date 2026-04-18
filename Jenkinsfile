pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Now that npm is installed globally in the container, these will work
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                // This copies your build files to the web server container
                sh 'docker cp build/. my-web-server:/usr/share/nginx/html'
            }
        }
    }
}
