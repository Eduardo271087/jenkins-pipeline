NODE_NAME = null

node('master') {
    stage('Choose') {
      NODE_NAME = "${env.NODE_NAME}"
    }
}

pipeline {
  agent {
    label NODE_NAME 
  }
  
  stages {
    stage('SCM checkout') {
      steps {
        git branch: '${GIT_BRANCH}',
            credentialsId: 'Git_Credentials',
            url: '${GIT_REPO_URL}'
      }
    }

    stage('Build') {
      steps {
        sh './scripts/clean.sh'
        sh './scripts/create-debug-makefiles.sh'
        sh './scripts/make.sh'
        sh './scripts/create-deb-package.sh'
      }
    }
  }
}
