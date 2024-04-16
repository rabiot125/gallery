pipeline{
    agent any
    environment {

        EMAIL_BODY = 
        """<p>Failed to Execute: Job <b>\'${env.JOB_NAME}:${env.BUILD_NUMBER})\'
                    </b></p><p>View console output at "<a href="${env.BUILD_URL}">
                    ${env.JOB_NAME}:${env.BUILD_NUMBER}</a>"</p>
                    <p><i>(Build log is attached.)</i></p>"""


        EMAIL_SUBJECT_FAILURE = "Status: 'FAILURE' -Job \'${env.JOB_NAME}:${env.BUILD_NUMBER}\'" 

        EMAIL_RECEPIENT = 'test@gmail.com'

    }
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
                sh '''
                curl --request POST \
                     --url https://api.render.com/v1/services/srv-codd6ra0si5c738ub17g/deploys \
                     --header 'accept: application/json' \
                     --header 'authorization: Bearer rnd_Jf3xyynLoo4MyoMjvTSiIMUxI13J' \
                     --header 'content-type: application/json' \
                     --data '
                    {
                      "clearCache": "do_not_clear"
                    }
                    '
            '''
                //echo 'Deploying the code'
                
            }
        }
        
    }
    post {
          failure {
            emailext attachLog: true, 
                body: EMAIL_BODY, 
                subject: EMAIL_SUBJECT_FAILURE,
                to: EMAIL_RECEPIENT
            
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