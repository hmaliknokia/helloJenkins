pipeline {
  agent {
    kubernetes {
      yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: python
            image: python
            command:
            - cat
            tty: true
        '''
    }
  }
  stages {
    stage('Check python version') {
      steps {
        container('maven') {
          sh 'mvn -version'
        }
      }
    }
  }
}
