@Library("Shared") _

pipeline {
    agent any

    stages {

        stage("Code") {
            steps {
                script{
                    clone("https://github.com/ahmadali-114/django-notes-app.git","main")
                }
            }
        }

        stage("Build") {
            steps {
                script{
                    dockerbuild("notes-app","latest","ahmadalimalik")
                }
            }
        }

        stage("Push") {
            steps {
                script{
                    dockerpush("notes-app","latest","ahmadalimalik")
                }
            }
        }

        stage("Deploy") {
            steps {
                script{
                    try {
                        sh "docker-compose up -d"
                    }
                    catch(err) {
                        echo "Deploy error ignored for practice: ${err}"
                    }
                }
            }
        }

    }
}
