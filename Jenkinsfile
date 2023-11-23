pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/tanmayy2xx1/Jenkins'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_kdCg8GisGtHc7gyoaCguzj2H6iE  | /usr/bin/docker login -u tanmay8180 --password-stdin'
            }
        }
         stage ('docker build image') {
            steps {
                sh '/usr/bin/docker build -t tanmay8180/mywebsite .'
            }
        }
         stage ('docker push image') {
            steps {
                sh '/usr/bin/docker push tanmay8180/mywebsite'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice -p 9091:80 --replicas 5 tanmay8180/mywebsite'
            }
        }
        
    }
}

