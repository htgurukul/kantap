pipeline {
    agent any
    
stages{
        stage('Build'){
            steps {
                sh ' cat README.md'
                sh ' echo branch is ${GIT_BRANCH} '
                githubPRStatusPublisher buildMessage: message(failureMsg: githubPRMessage('Can\'t set status; build failed.'), successMsg: githubPRMessage('Can\'t set status; build succeeded.')), statusMsg: githubPRMessage('${GITHUB_PR_COND_REF} run ended'), unstableAs: 'FAILURE'
            }
        }
    }
}
