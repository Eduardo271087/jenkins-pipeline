@Library "k8sagent" _

pipeline {
  agent {
    kubernetes(k8sagent(name: 'mini+pg'))
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
