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
                echo in build mode
  """
            }
        }
              
    
 
        stage('PrintQA'){
            when {
                    branch "baseQA"
                  }
            steps {
                sh 'echo IAM QA GUYS'
                
            }
        }  
    
        
    }
}
