pipeline{
    agent any
    stages{
        stage('Create Cluster') {
            steps {
                withAWS(region:'ap-southeast-2',credentials:'aws-static') {
                    sh 'echo "Create the create cluster "'
                    sh '''
                       eksctl create cluster \
                       --name capstonecluster \
                       --region ap-southeast-2 \
                       --version 1.14 \
                       --nodegroup-name standard-workers \
                       --node-type t3.medium \
                       --nodes 2 \
                       --nodes-min 1 \
                       --nodes-max 4 \
                       --node-ami auto
                    '''
                }
            }
        }
        stage('Create a kubectl configuration file') {
            steps{
                withAWS(region:'ap-southeast-2',credentials:'aws-static') {
                    sh 'echo "Create a kubectl configuration file"'
                    sh 'aws eks --region ap-southeast-2 update-kubeconfig --name capstonecluster'
                }
            }
        }
    }
}
