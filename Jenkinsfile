pipeline {
    agent any
    environment {
	    EMAIL_INFORM = 'krishna.raj@tisteps.co;'
    }
    stages {
        stage('api docker build') {
        steps {
            sh '''
                echo "Docker build api "
                '''
            }
        }
        stage('api docker image push') {
            steps {
                sh '''
                    echo "completed"
                    '''
            }
        }
        stage('api deployment') {
            steps {
                script {
                        if ( (env.BRANCH_NAME).startsWith('feature-stag') ) {
                            sh '''
                                echo "Deploying to Staging Environment...."
                            '''
                        } 
                        else if (env.BRANCH_NAME == 'main') {
                            input message: 'Do you want deploy in production? (Click "Proceed" to continue)'
                                sh '''
                                    echo "Deploying to Production Environment...."
                                ''' 
                        }
                        else {
                                echo "Deployment skipped ..No valid branch to deploy"
                        } 
                        
                    }
            
            }
        }
    }
}

