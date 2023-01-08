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
                    branch "release-*"
                }
            }
            steps {
                sh ' cat README.md'
                sh ' echo branch is ${GIT_BRANCH} '
                sh ' echo git commit is ${GIT_COMMIT} '
                sh "ls -ltr"
                sh "whoami"
                sh "ls -ltr ~/"
              sh "mkdir -p /home/jenkins/.ssh/"
              sh "ssh-keyscan -t rsa github.com >> ~/.ssh/known_hosts"
               sh "ls -ltr ~/"
                sh "cat .git/config "
                
                script {
                sh ' date'
                nowd = new Date().format("yyMMddHHmmss")
                    nowd += "-${BUILD_ID}"
                println nowd
                
                GIThashTrunc = GIT_COMMIT.take(7)
                    GIThashTrunc += "-${BUILD_ID}"
                }
                println "same step "
                println nowd
                println GIThashTrunc
            }
            
        }
              
    
 
        stage('PrintQA'){
            when {
                    anyOf {
                        branch "baseQA"
                    branch "develop"
                    branch "PR-*"
                    }
                    }
            steps {
                script {
                    println "stage 222"
                println nowd
                    println GIThashTrunc
                  sh """ 
                  echo "inside echo is nowd as $nowd  and git as $GIThashTrunc "  
                  """
                
                }
                
            }
        }  
    
    
    stage('Tag Release') {
          when {
                    branch "release-*"
               }
          steps {
            script {
              println("Tagging Build")

                sshagent(['JENKINS-KEY']) {
                  sh """
                  echo "git url is $GIT_URL"
                  git remote -v
                  git remote set-url origin git@github.com:htgurukul/kantap.git
                  git remote -v
                     git config --global user.email 'himanshu.gurukul@gmail.com'
                     git config --global user.name 'htgurukul'
                     git tag -fa v`echo ${GIT_BRANCH}|awk -F"-" '{print \$2}'` -m 'Release ${GIT_BRANCH}'
                     export GIT_SSH_COMMAND="ssh -oStrictHostKeyChecking=no"
                      git push -f --tags
                      echo "git url is now $GIT_URL"
                   """
                }
            }
          }
        }
        
    }
}
