pipeline {
    agent any

    stages {
        
	stage('Build Docker Image') {
            steps {
                echo 'Build'
                withCredentials([usernamePassword(credentialsId: 'docker-cred', usernameVariable: 'USERNAME_MG', passwordVariable: 'PASSWORD_MG')]) {
                    sh '''
                        docker login -u ${USERNAME_MG} -p ${PASSWORD_MG}
                        docker build -t elnabatshy/bake:v${BUILD_NUMBER} .
                    '''
                }
            }
        }

        stage('Push Docker Image') {
            steps {  
                echo 'Push'
                   sh 'docker push elnabatshy/bake:v${BUILD_NUMBER}'
            }
        }

	stage('Trigger CD job ') {
                steps {
                     echo "triggering CD"
                     build job: 'CD', parameters: [string(name: 'BUILD_NUMBER', value: env.BUILD_NUMBER)]
        	}
        }
	
	stage('Trigger CD Job') {
            steps {
                script {
                    def triggeredBuild = build job: 'CD', parameters: [string(name: 'BUILD_NUMBER', value: env.BUILD_NUMBER)]
                }
            }
        }
    }
}
