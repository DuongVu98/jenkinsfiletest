pipeline{
    agent any

    environment {
        registry = "tony16019/buildfromjnenkins"
        registryCredential = "dockerhub"
        dockerImage = ''
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
                    dockerImage = docker.build(registry + ":latest", "-f docker/Dockerfile", ".")
                }

                script {
                    docker.withRegistry("", registryCredential) {
                        dockerImage.push("latest")
                    }
                }
                
                sh "docker rmi -f tony16019/buildfromjnenkins"
                sh "docker image prune"
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