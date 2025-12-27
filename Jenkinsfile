pipeline {
    agent any

    environment {
        IMAGE_NAME = "shrinikha05/myapp:latest"
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(IMAGE_NAME)
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    sh "docker rm -f myapp-container || true"
                    sh "docker run -d --name myapp-container -p 5000:5000 ${IMAGE_NAME}"
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline completed successfully!"
        }
    }
}
