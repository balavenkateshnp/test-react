Production : 

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
                script {
                    def userInput = input(
                        id: 'userInput',
                        message: 'Please review and provide approval for production',
                        parameters: [
                            string(name: 'comments', defaultValue: '', description: 'Comments'),
                           // booleanParam(name: 'proceed', defaultValue: true, description: 'Proceed with the next stage?'),
                           // booleanParam(name: 'abort', defaultValue: false, description: 'Abort the pipeline?')
                        ],
                        submitter: 'user1, user2',
                        submitterParameter: 'APPROVER'
                    )
                    // Access the input values using userInput['<parameter-name>']
                    def comments = userInput['comments']
                    def proceed = userInput['proceed']
                    def abort = userInput['abort']
                    
                    // Add custom logic based on the input values
                    if (proceed) {
                        echo 'Proceeding to the next stage'
                    } else if (abort) {
                        error('Pipeline aborted based on user input')
                    }
                    echo "Comments: ${comments}"
                }
            }
        }
        
       stage ('Prod codes receiving!') {
            steps{
                sshagent(credentials : ['ssh-node']) {
                sh 'ssh -o StrictHostKeyChecking=no blaze@192.151.159.205 git -C /var/www/html/test-react/ pull origin main'
                 }
                 }
                         }   
           }
           }
