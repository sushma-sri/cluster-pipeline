pipeline {
  agent any
  stages {
    stage('Create a kubectl configuration file') {
      steps {
        withAWS(region: 'ap-southeast-2', credentials: 'aws-static') {
          sh 'echo "Create a kubectl configuration file"'
          sh '/home/jenkins/.local/bin/aws eks --region ap-southeast-2 update-kubeconfig --name capstonecluster'
        }

      }
    }

  }
}
