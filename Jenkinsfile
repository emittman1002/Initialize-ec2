// Initialize AWS EC2
library 'aws-lib'

pipeline {
    agent {
        label 'java'
    }
    parameters {
        choice(name: 'usage_tag', choices: ['jenkins-agent', 'sas', 'general'], description: 'What the instance will be used for')
        choice(name: 'instance_profile', choices: ['jenkins-agent-role', 'jenkins-job-role', 'sas-agent-role', 'sas-job-role'], description: 'The instance profile/role to assume in the instance')
    }
    stages {
        stage('ensure-ec2') {
            steps {
                script {
                    awsLib.startEc2(params.usage_tag, params.instance_profile)
                }
            }
        }
    }
}
