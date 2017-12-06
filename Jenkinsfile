pipeline {
    agent any

    stages {
        stage('Get Dockerfile') {
            steps {
                echo 'Getting docker file'
		sh "export App_Name = build.environment.get("GIT_URL").replaceAll('https://github.com/', '').replaceAll('.git', '')"
		sh 'wget https://raw.githubusercontent.com/itamary/examples/master/Dockerfile'
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
		sh "export App_Name = build.environment.get("GIT_URL").replaceAll('https://github.com/', '').replaceAll('.git', '')"
		sh "docker build -t itamar/${App_Name}:${BUILD_NUMBER} ."
            }
        }
        stage('Push to registry') {
            steps {
                echo 'Pushing to registry..'
		sh "export App_Name = build.environment.get("GIT_URL").replaceAll('https://github.com/', '').replaceAll('.git', '')"
		sh "docker login -u itamar -p Aa123123"
		sh "docker push itamar/${App_Name}:${BUILD_NUMBER}"
            }
        }
    }
}
