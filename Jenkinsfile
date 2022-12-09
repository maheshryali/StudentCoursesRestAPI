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
                docker image ls
                docker image build -t studentcourse:1.0 .
                docker container run -d -P studentcourse:1.0
                """
            }
        }
    }
}