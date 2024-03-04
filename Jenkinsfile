pipeline {
    agent {label 'docker-vm'}

    stages {
        stage('Git Clone') {
            steps {
                checkout scm
            }
        }
        stage('Build and Push') {
            steps {
                script {
                   def DockerImage="abhibhardwaj4907/docker-app"
                   def DockerTag="v1"
                   def dockerCredentials="dockerhub-cred"
                   def dockerBuild=docker.build("${DockerImage}:${DockerTag}",".")
                   docker.withRegistry("",dockerCredentials) {
                      dockerBuild.push()
            }
            }
        }
    }
 }
}
