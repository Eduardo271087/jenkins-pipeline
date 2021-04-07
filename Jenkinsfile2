pipeline {
  agent {
    kubernetes {
      yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
            - name: framework-agent
              image: linux-environment:v1
          hostAliases:
            - ip: 172.17.4.194
              hostnames:
                - git.smartmatic.net
      '''
      defaultContainer 'framework-agent'
    }
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
