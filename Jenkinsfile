pipeline {
  agent {
    kubernetes {
      yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: python
            image: python:latest
            command:
            - cat
            tty: true

          - name: docker
            image: docker:latest
            command:
            - cat
            tty: true
        '''
    }
  }
  stages {
    stage('Check python version') {
      steps {
        container('python') {
          sh """
            python --version
            pwd
          """
        }
      }
    }

    stage('Check docker images') {
      steps {
        container('docker') {
          sh """
            docker image ls
          """
        }
      }
    }
  }
}
