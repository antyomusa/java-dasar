pipeline {
    agent none

    environment {
        AUTHOR = "Anthony Yoab"
        EMAIL = "anthonyyoabm@gmail.com"
    }
    stages{
        stage("Prepare"){
            environment{
                APP = credentials("antyomusa_rahasia")
            }
            agent {
                node {
                    label "Linux && java17"
                }
            }
            steps{
                echo("Author : ${AUTHOR}")
                echo("Author Mail : ${EMAIL}")
                echo("Start Job : ${env.JOB_NAME}")
                echo("Start Build : ${env.BUILD_NUMBER}")
                echo("Branch Name : ${env.BRANCH_NAME}")
                echo("App User : ${APP_USR}")
                sh('echo "App Password : $APP_PSW" > "rahasia.text"')
            }
        }

        stage("Build"){
            agent {
                node {
                    label "Linux && java17"
                }
            }
            steps{
                echo("Start Build")
                sh("mvn clean compile test-compile")
                echo("Finish Build")
            }
        }

        stage("Test"){
            agent {
                node {
                    label "Linux && java17"
                }
            }
            steps{
                echo("Start Test")
                sh("mvn test")
                echo("Finish Test")
            }
        }

        stage("Deploy"){
            agent {
                node {
                    label "Linux && java17"
                }
            }
            steps{
                echo("Hello Deploy 1")
                echo("Hello Deploy 2")
                echo("Hello Deploy 3")
            }
        }
    }

    post {
        always {
            echo "I will always say Hello again"
        }
        success {
            echo "Success"
        }
        failure {
            echo "Oh no, Failure"
        }
        cleanup {
            echo "Dont't care success or not"
        }
    }
}