pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
        git(url: 'https://github.com/kchutchesonltd/homelab-setup.git', branch: 'master')
      }
    }

    stage('Build') {
      steps {
        sh '''PATH=$PATH:/usr/local/bin
vagrant up

if $? -ne 0
then
vagrant destroy --force
fi 
'''
        catchError(buildResult: 'Failed', message: 'Build Failed') {
          sh '''PATH=$PATH:/usr/local/bin

vagrant destroy --force'''
        }

      }
    }

    stage('Test') {
      steps {
        sh '''PATH=$PATH:/usr/local/bin
vagrant status'''
      }
    }

    stage('Destroy') {
      steps {
        sh '''PATH=$PATH
vagrant destroy --force
'''
      }
    }

  }
}