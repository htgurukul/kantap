pipeline {
    environment {
     GITT = credentials('GITOKEN')
}
    agent any
    
stages{
        stage('Build'){
            when {
                anyOf {
                    branch "develop"
                    branch "PR-*"
                }
            }
            steps {
                sh ' cat README.md'
                sh ' echo branch is ${GIT_BRANCH} '
                sh ' echo git commit is ${GIT_COMMIT} '
                sh """
                curl "https://api.GitHub.com/repos/htgurukul/kantap/statuses/${GIT_COMMIT}" \
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: Bearer ${env.GITT}"\
  -H "X-GitHub-Api-Version: 2022-11-28" \
  -H "Content-Type: application/json" \
  -X POST \
  -d '{"state": "failure","context": "continuous-integration/jenkins", "description": "Jenkins", "target_url": "${BUILD_URL}"}'
  """
            }
        }
              
    
 
        stage('PrintQA'){
            when {
                    branch "baseQA"
                  }
            steps {
                sh ' IAM QA GUYS'
                
            }
        }  
    
        
    }
}
