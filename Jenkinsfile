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
'''
      }
    }

    stage('Test') {
      steps {
        sh '''PATH=$PATH:/usr/local/bin
vagrant status'''
      }
    }

  }
}