pipeline {
    agent any
    
stages{
        stage('Build'){
            steps {
                sh ' cat README.md'
                sh ' echo branch is ${GIT_BRANCH} '
            }
        }
    }
}
