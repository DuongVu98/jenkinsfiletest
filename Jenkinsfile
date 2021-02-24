pipeline{
    agent any

    environment {
        dockerImage = ''
        imagename = "tony16019/buildfromjnenkins"
    }

    stages{
        stage("A"){
            steps{
                echo "========executing A========"
            }
        }
        stage("Build Docker image"){
            steps{
                script {
                    dockerImage = docker.build imagename
                }
            }
            steps{
                echo "docker push"
            }
            steps{
                sh 'docker images -q -f dangling=true | xargs --no-run-if-empty docker rmi'
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}