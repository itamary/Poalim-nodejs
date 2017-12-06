pipeline {
    agent any

    stages {
        stage('Get Dockerfile') {
            steps {
                echo 'Getting docker file'
		sh 'wget https://raw.githubusercontent.com/itamary/examples/master/Dockerfile'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
		source var_file
		sh "docker build -t itamar/${App_Name}:${BUILD_NUMBER} ."
            }
        }
        stage('Push to registry') {
            steps {
                echo 'Pushing to registry..'
		source var_file
		sh "docker login -u itamar -p Aa123123"
		sh "docker push itamar/${App_Name}:${BUILD_NUMBER}"
            }
        }
    }
}
