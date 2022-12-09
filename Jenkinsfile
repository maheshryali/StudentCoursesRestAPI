pipeline{
    agent { label 'APPLICATION' }
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('docker_process') {
            steps {
                sh """
                git clone https://github.com/maheshryali/StudentCoursesRestAPI.git
                cd StudentCoursesRestAPI
                docker image build -t studentcourse:1.0 .
                docker container run -d studentcourse:1.0
                docker tag studentcourse:1.0 maheshryali/latestimage:1.0
                docker push maheshryali/latestimage:1.0
                """
            }
        }
    }
}