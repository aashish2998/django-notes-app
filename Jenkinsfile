@Library("Shared") _
pipeline{
    
    agent {label "vinod"}
    
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
               
                 clone("https://github.com/aashish2998/django-notes-app.git","main")
                
                }
                    
                
               
            }
            
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest","aashish29")
                }
               
            }
            
        }
        stage("Push to docker hub"){
            steps{
                script{
                    docker_push("notes-app","latest","aashish29")
                }
            }
            
        }
        stage("Deploy"){
            steps{
                echo "This is Deploying the code"
                sh "docker compose down && compose up -d"
            }
            
        }
    }
}
