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
          failure {
            emailext (
                subject: "Test Failure: ${currentBuild.fullDisplayName}",
                body: "There were test failures in the build. Please check the Jenkins console output for details.",
                to:"test@gmail.com"
            )
        }



            success{
                script {
                      def renderUrl = "https://gallery-zr59.onrender.com/"

                      slackSend (
                        channel: '#slack-integration',
                        color: 'good', 
                        message: "Build Successful: ${currentBuild.fullDisplayName}\nRender URL: ${renderUrl}\nBuild URL: ${env.BUILD_URL}" 
                        )
                }
                
            }
        }
}