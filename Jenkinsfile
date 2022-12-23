pipeline {
    agent any
    
stages{
        stage('Build'){
            steps {
                sh ' cat README.md'
                sh ' echo branch is ${GIT_BRANCH} '
                sh ' echo git commit is ${GIT_COMMIT} '
                sh """
                curl "https://api.GitHub.com/repos/htgurukul/kantap/statuses/${GIT_COMMIT}" \
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: Bearer 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"\
  -H "X-GitHub-Api-Version: 2022-11-28" \
  -H "Content-Type: application/json" \
  -X POST \
  -d "{\"state\": \"failure\",\"context\": \"continuous-integration/jenkins\", \"description\": \"Jenkins\", \"target_url\": \"https://e511-49-36-187-26.in.ngrok.io/job/multip2/$BUILD_NUMBER/console\"}" 
  """
            }
        }
              
        
    }
}
