pipeline{
    agent any
    tools{
        nodejs 'npm'
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
                echo 'Deploying the code'
                //sh 'node server'
            }
        }
        
    }
    post {
            success{
                slackSend (
                    baseUrl: 'https://kipkoechip1.slack.com/services/6958190106707',
                    subdomain: 'kipkoechip1',
                    channel: '#slack-integration',
                    color: 'good', 
                    message: "Build Successful: ${currentBuild.fullDisplayName}",
                    token:'al98YsngJ1xmRFZnvf4OQ3W2'
                    )
            }
        }
}