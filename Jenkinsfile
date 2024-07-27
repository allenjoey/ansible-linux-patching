/* groovylint-disable-next-line CompileStatic */
pipeline {
    agent any

    stages {
        stage('Execute Ansible Playbook') {
            steps {
                ansiblePlaybook credentialsId: 'private-key',
                                 disableHostKeyChecking: true,
                                 installation: 'Ansible',
                                 inventory: 'inventory',
                                 playbook: 'update-by-group.yml'
            }
        }
    }

    post {
        always {
            step([$class: 'Mailer', notifyEveryUnstableBuild: true,
                recipients: 'youremail@youremail.com'])
        }
    }
}
