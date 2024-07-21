pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    sh "rm -f /opt/jenkins/project11/index.html && mkdir /opt/jenkins/project11"
                    sh "git clone https://github.com/iunfed/project11.git /opt/jenkins/project11"
                    sh "docker run -d -p 9889:80 -v /opt/jenkins/project11:/var/www/html --name nginx nginx"
                }
            }
        }
   }
    post {
        always {
            script {
                sh "docker stop nginx || true"
                sh "docker rm nginx || true"
            }
        }
    }
}
