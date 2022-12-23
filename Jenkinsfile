pipeline {
    agent any
    
stages{
        stage('Build'){
            steps {
                sh ' cat README.md'
                sh ' echo branch is ${GIT_BRANCH} '
            }
                post {
     always{
                githubPRStatusPublisher buildMessage: message(failureMsg: githubPRMessage('Can\'t set status; build failed.'), successMsg: githubPRMessage('Can\'t set status; build succeeded.')), statusMsg: githubPRMessage('${GITHUB_PR_COND_REF} run ended'), statusVerifier: allowRunOnStatus('SUCCESS'), errorHandler: statusOnPublisherError('FAILURE'), unstableAs: 'FAILURE'
     }
}
                
            
        }
    }
}
