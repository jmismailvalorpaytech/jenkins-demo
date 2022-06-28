pipeline {
    agent any
    tools { nodejs 'Node16.15.0' }
    stages {    
        stage('Test') {
            steps {
                sh '''
                    npm --version
                    node --version
                '''
            }
        }
        stage('Build') {
            steps {
                sh '''
                   npm install
                   cd ${WORKSPACE}/client
                   npm install
                   npm run build
                '''
            }
        }
        stage('Deploy') {
            steps { 

                sh '''
                    cd ${WORKSPACE}/client/dist
                    sudo mv * /home/jmismail/jenkins-demo/client/       

                    cd ${WORKSPACE}/
                    rsync -avr --progress * /home/jmismail/jenkins-demo/  --exclude client
                '''
                //                     sudo cp -r  * /home/jmismail/jenkins-demo/      

                // sh 'cd ${WORKSPACE}/client/dist'
                // sh 'sudo mv * /home/jmismail/jenkins-demo'
                //  sh 'sudo rsync -avr -e "ssh -l jmismail" --exclude="client" . jmismail@${SERVER_IP_ADDRESS}:/home/jmismail/jenkins-react-nginx'
            }
        }
    }
}
