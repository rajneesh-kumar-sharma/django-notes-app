@Library("shared") _
pipeline {
    agent{label "raj"}
    stages{
        stage ("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage ("test"){
            steps{
                echo "hello Rajneesh"
            }
        }
        stage ("code"){
            steps{
                script{
                   clone("https://github.com/rajneesh-kumar-sharma/django-notes-app.git","main")
               }
            }
        }
        stage ("Build"){
            steps{
               script{
                   docker_build("notes_app","latest","coolrajnish")
               }
               }
            }
            
        stage ("Push to Docker Hub"){
            steps{
                script{
                   docker_push("notes_app","latest","coolrajnish")
               }
            }
        }
        stage ("Deploy"){
            steps{
                sh "docker compose down && docker compose up -d"
            }
        }
        
    }
}

