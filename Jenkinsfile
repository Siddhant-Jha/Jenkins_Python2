pipeline {
    agent any
    environment{
        DOCKERHUB_CREDENTIALS=credentials('siddhant1751')
    }
    stages {
        stage('Building Image') {
            steps {
                sh 'docker build -t siddhant1751/jenkins_python2:latest .'
                
            }
        }
        stage('Running Container') {
            steps {
                echo "Step 2: Running Container"
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('deploy') {
            steps {
                echo "Step 3: Deploying"
                sh 'docker push siddhant1751/jenkins_python2:latest'
            }
        }
    }
    post{
        always{
            echo 'I always Run'
            sh 'docker logout'
        }
        success{
            echo 'I run when the job is successful'
        }
        failure{
            echo 'I run when the job fails'
        }
    }
}
