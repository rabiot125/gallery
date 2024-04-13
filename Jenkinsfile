pipeline{
    agent any
    stages{
        stage('Clone the Repository'){
            steps{
                git branch: 'master', url: 'https://github.com/rabiot125/gallery.git'
            }
        }
        stage('Build Code'){
            steps{
                sh 'npm install'
            }
        }
        
        stage('Deploy Code'){
            steps{
                sh 'node server'
            }
        }
    }
}