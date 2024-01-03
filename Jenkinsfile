pipeline {
    agent any

    environment {
        DOCKER_IMAGE_NAME = "elnabatshy/bake"
    }

    stages {
        
	stage('Build Docker Image') {
            steps {
                echo 'Build'
                withCredentials([usernamePassword(credentialsId: 'Nexus-cred', usernameVariable: 'USERNAME_MG', passwordVariable: 'PASSWORD_MG')]) {
                    sh '''
			docker login http://15.206.81.210:9001/repository/bake-house/ -u ${USERNAME_MG} -p ${PASSWORD_MG}
                        docker build -t bake:v${BUILD_NUMBER} .
                    '''
                }
            }
        }

        stage('Push Docker Image') {
            steps {  
                echo 'Push'
		   sh 'docker push 15.206.81.210:9001/repository/bake-house/'
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
