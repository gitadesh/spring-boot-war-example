pipeline{
    agent any
     tools { 
        maven 'Maven' 
    }
    stages{
        stage("maven test"){
            steps{
                //mvn test
                sh 'mvn clean'
                echo "Test runned successfully"
            }
        }
        stage("maven build"){
            steps{
                //mvn install
                sh 'mvn package'
                echo "Test Build"
            }
        }
        stage("maven deploy"){
             input {
            message "shoud we go"
            ok "yes boss"
            }
            steps{
                //plugin deply on container
               deploy adapters: [tomcat9(credentialsId: '125c76f1-4d3c-4d74-8a65-f9e625cdebb8', path: '/app', url: 'http://192.168.0.107:8080/app/')], contextPath: null, war: '**/*.war'
                echo "Deploy Build"
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
