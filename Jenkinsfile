pipeline {
    agent any

    stages {

        stage('Checkout from GitHub') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/SwathiPriyaKasarapu/node-docker-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t node-docker-app:${BUILD_NUMBER} .
                docker tag node-docker-app:${BUILD_NUMBER} SwathiPriyaKasarapu/node-docker-app
                '''
            }
        }

         stage('Push Docker Image') {
             steps {
               sh 'docker push SwathiPriyakasarapu/node-docker-app'
           }
         }
        
        stage('Create container') {
            steps {
                sh 'docker run -d -p 3000:8080 SwathiPriyaKasarapu/node-docker-app'
            }
        }



    }
}
