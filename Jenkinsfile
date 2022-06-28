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
                   npm installz
                   cd ${WORKSPACE}/client
                   npm run build
                '''
            }
        }
        stage('Deploy') {
            steps { 
                sh 'mv cd ${WORKSPACE}/client/dist /home/jmismail/jenkins-demo'
                //  sh 'sudo rsync -avr -e "ssh -l jmismail" --exclude="client" . jmismail@${SERVER_IP_ADDRESS}:/home/jmismail/jenkins-react-nginx'
            }
        }
    }
}