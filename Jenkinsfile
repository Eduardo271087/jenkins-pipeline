pipeline {
  agent none
  
  stages {
    stage('SCM checkout') {
      agent {
        label 'framework-agent' 
      }
      
      steps {
        git branch: '${GIT_BRANCH}',
            credentialsId: 'Git_Credentials',
            url: '${GIT_REPO_URL}'
      }
    }

    stage('Build') {
      agent {
        label 'framework-agent' 
      }
      
      steps {
        sh 'whereis cmake'
        sh 'echo $PATH'
        sh './scripts/clean.sh'
        sh './scripts/create-debug-makefiles.sh'
        sh './scripts/make.sh'
        sh './scripts/create-deb-package.sh'
      }
    }
  }
}
