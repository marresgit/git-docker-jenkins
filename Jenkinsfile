pipeline {
    agent any
 
    options {
        skipDefaultCheckout(true)
    }
 
    stages {
        stage('Destroy container') {
            steps {
                script {
                    if docker ps -a | grep test-web {
                        docker rm -f test-web
                    } else {
                        echo "Nothing to remove"
                    }
                }
            }
        }
        stage('Destroy container') {
            steps {
                echo '> Checking out the source control ...'
                checkout scm
            }
        }
        stage('Docker run') {
            steps {
                echo '> Building the docker containers ...'
                sh 'docker run -d --name test-web -p 5000:5000 flask-tutorial'
            }
        }
    }
}
