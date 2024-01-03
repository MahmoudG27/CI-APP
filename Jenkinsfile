pipeline {
    agent any

    environment {
        DOCKER_IMAGE_NAME = "elnabatshy/bake"
    }

    stages {
        
	stage('Build Docker Image') {
            steps {
                echo 'Build'
                withCredentials([usernamePassword(credentialsId: 'docker-cred', usernameVariable: 'USERNAME_MG', passwordVariable: 'PASSWORD_MG')]) {
                    sh '''
			docker login -u ${USERNAME_MG} -p ${PASSWORD_MG}
			docker build -t ${DOCKER_IMAGE_NAME}:v${BUILD_NUMBER} .
                    '''
                }
            }
        }

        stage('Push Docker Image') {
            steps {  
                echo 'Push'
		    sh 'docker push ${DOCKER_IMAGE_NAME}:v${BUILD_NUMBER}'
            }
        }

	stage('Trigger CD job ') {
            steps {
                echo "triggering CD"
                build job: 'CD', parameters: [string(name: 'FROM_BUILD', value: env.BUILD_NUMBER)]
            }
        }
    }
}
