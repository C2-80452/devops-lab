pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/C2-80452/devops-lab.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_vIV7zX6UYNu0aE6XC4_SFr-Gi84 | /usr/bin/docker login -u shivendra013 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t shivendra013/imyimagess .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push shivendra013/imyimagess'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservices'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name iservices -p 9090:80 --replicas 5 shivendra013/imyimagess'
            }
        }
    }
}
