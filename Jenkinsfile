pipeline {
  agent {
    label 'framework-agent'
  }
  
  environment {
    PATH = "/usr/local/bin:$PATH"
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
