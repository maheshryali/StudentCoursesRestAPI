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
                cd ~/remote_repo/workspace/student
                docker image ls
                docker image build -t studentcourse:1.0 .
                docker container run -d -P studentcourse:1.0
                docker tag studentcourse:1.0 maheshryali/latestimage:2.0
                docker push maheshryali/latestimage:2.0
                cat ~/file.txt | docker login --username maheshryali --password-stdin
                """
            }
        }
    }
}