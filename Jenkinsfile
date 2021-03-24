pipeline {
  agent {
    label 'linux-agent-one || linux-agent-two'
  }
  
  stages {
    stage('SCM checkout') {
      steps {
        git branch: '${GIT_BRANCH}',
            credentialsId: 'credenciales-git',
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
