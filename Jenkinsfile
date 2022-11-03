pipeline {
    agent any
    parameters {
         string(name: 'PARA1', defaultValue: 'chal', description: 'Staging Server')
         string(name: 'PARA2', defaultValue: '', description: 'Production Server')
    }
stages{
        stage('Build'){
            steps {
                checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'HTGithub', url: 'https://github.com/htgurukul/kantap.git']]]
		sh ' cat README.md'
                sh ' echo params are PARA1 ${PARA1} PARA2 ${PARA2}'
            }
        }
    }
}
