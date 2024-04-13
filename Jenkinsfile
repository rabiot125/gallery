pipeline{
    agent any
    tools{
        npm 'nodejs'
    }
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
        stage('Test Code'){
            steps{
                sh 'npm test'
            }
        }
        stage('Deploy Code'){
            steps{
                sh 'npm run build'
            }
        }
       
    }
}