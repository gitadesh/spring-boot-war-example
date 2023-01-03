pipeline{
    agent any
     tools { 
        maven 'Maven' 
    }
    stages{
        stage("maven test"){
            steps{
                //mvn test
                sh 'mvn test'
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
                deploy adapters: [tomcat9(credentialsId: '3c2d8288-2802-49e4-8838-668f97bc15f2', path: '', url: 'http://192.168.0.108:8080')], contextPath: '/app', war: '**/*.war'
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
