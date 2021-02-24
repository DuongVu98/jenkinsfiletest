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
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
        stage("Build Docker image"){
            steps{
                script {
                    dockerImage = docker.build imagename
                }
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