pipeline {
   agent any
   stages {
        stage('Git clone') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github-password', url: 'https://github.com/balavenkateshnp/test-react.git']]])

            }
        }  
       stage('Approval') {
            steps {
                input "Proceed with the Deployment?"
            }
        } 
        
       stage ('Prod codes receiving!') {
            steps{
                sshagent(credentials : ['ssh-node']) {
                sh 'ssh -o StrictHostKeyChecking=no blaze@192.151.159.205 git -C /var/www/html/test-react/ pull'
                 }
                 }
                         }   
           }
           }
