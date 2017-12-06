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
		sh "export App_Name = `echo ${GIT_URL}  | awk -F / '{print $NF}' | awk -F . '{print $1}'` 
		sh "docker build -t itamar/${App_Name}:${BUILD_NUMBER} ."
            }
        }
        stage('Push to registry') {
            steps {
                echo 'Pushing to registry..'
		sh "export App_Name = `echo ${GIT_URL}  | awk -F / '{print $NF}' | awk -F . '{print $1}'`
		sh "docker login -u itamar -p Aa123123"
		sh "docker push itamar/${App_Name}:${BUILD_NUMBER}"
            }
        }
    }
}
