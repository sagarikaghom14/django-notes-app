@Library("Shared") _
pipeline{
    
    agent any
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/sagarikaghom14/django-notes-app.git","main")
                }
                
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("django-notes-app","latest","sagarikaghom")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("django-notes-app","latest","sagarikaghom")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                bat 'docker compose down && docker compose up -d'
            }
        }
    }
}
