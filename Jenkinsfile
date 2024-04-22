pipeline {
    agent any 
   
    
    stages { 
        stage('SCM Checkout') {
            steps {
                retry(3) {
                    git branch: 'main', url: 'https://github.com/Nadasara/4266-Weerasekara-.git'
                }
            }
        }
        stage('Build Docker Image') {
            steps {  
                bat 'docker build -t nada450/nodeapp-4266:%BUILD_NUMBER% .'
            }
        }
        stage('Login to Docker Hub') {
            steps {
                
                bat 'docker login -u nada450 -p nada450@123'
               
            }
        }

        stage('Push Image') {
            steps {
                bat 'docker push nada450/nodeapp-4266:%BUILD_NUMBER%'
            }
        }
    }
    post {
        always {
            bat 'docker logout'
        }
    }
}