pipeline{
    agent { label 'APPLICATION' }
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('git') {
            steps {
                git branch: 'master',
                       url: 'https://github.com/maheshryali/StudentCoursesRestAPI.git'
            }
        }
        stage('docker_process') {
            steps {
                sh """
                cd StudentCoursesRestAPI
                docker image ls
                docker image build -t studentcourse:1.0 .
                docker container run -d -P studentcourse:1.0
                """
            }
        }
    }
}