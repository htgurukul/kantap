pipeline {
    agent any
    
stages{
        stage('Build'){
            steps {
                sh ' cat README.md'
                sh ' echo branch is ${GIT_BRANCH} '
                sh 'curl "https://api.GitHub.com/repos/htgurukul/kantap/statuses/$GIT_COMMIT?access_token=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" \
  -H "Content-Type: application/json" \
  -X POST \
  -d "{\"state\": \"success\",\"context\": \"continuous-integration/jenkins\", \"description\": \"Jenkins\", \"target_url\": \"https://e511-49-36-187-26.in.ngrok.io/job/<JenkinsProjectName>/$BUILD_NUMBER/console\"}" '
            }
        }
              
        
    }
}
