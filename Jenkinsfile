pipeline {
  agent {
    label 'linuxdos || linuxtres'
  }
  
  stages {
    stage('SCM checkout') {
      steps {
        git branch: '${GIT_BRANCH}',
            credentialsId: 'credenciales-git',
            url: 'ssh://git@git.smartmatic.net:32323/engineering_client_side_b/esbu_dev_saes_cpp_framework.git'
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
