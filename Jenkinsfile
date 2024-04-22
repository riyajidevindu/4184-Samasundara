pipeline {
    agent any 
   
    
    stages { 
        stage('SCM Checkout') {
            steps {
                retry(3) {
                    git branch: 'main', url: 'https://github.com/riyajidevindu/4184-Samasundara.git'
                }
            }
        }
        stage('Build Docker Image') {
            steps {  
                bat 'docker build -t riyaji/node-app:%BUILD_NUMBER% .'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                
                bat 'docker login -u riyaji -p Chamila6283'
               
            }
        }

        stage('Push Image') {
            steps {
                bat 'docker push riyaji/node-app:%BUILD_NUMBER%'
            }
        }
    }
    post {
        always {
            bat 'docker logout'
        }
    }
}