podTemplate {
    node(POD_LABEL) {
      stage('SCM checkout') {
        git branch: '${GIT_BRANCH}',
            credentialsId: 'Git_Credentials',
            url: '${GIT_REPO_URL}'
      }

      stage('Build') {
          sh 'whereis cmake'
          sh 'echo $PATH'
          sh './scripts/clean.sh'
          sh './scripts/create-debug-makefiles.sh'
          sh './scripts/make.sh'
          sh './scripts/create-deb-package.sh'
      }
    }
}
