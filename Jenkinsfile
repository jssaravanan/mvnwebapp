pipeline{
    //agent any
    agent{
           label 'windows_node'
    }
    stages{
         stage('checkout'){
            steps{
                git credentialsId: '14519e58-aa4e-447e-accc-f4443d7d5292', url: 'https://github.com/jssaravanan/mvnwebapp.git'
                echo "fetching code from github"
            }
        }
        stage ('package'){
            steps{
                    bat 'mvn package'
                    echo "complie stage completed"
            }
        }
         stage ('deploy'){
            steps{
                    deploy adapters: [tomcat8(credentialsId: 'e9b5f201-08b4-499f-a76b-7e5aa73307d5', path: '', url: 'http://localhost:8081')], contextPath: 'mvnwebapp', war: '**/*.war'
                    echo "deployment completed"
                }
        }
    }
    post{
        always{
            echo "This stage always run"
        }
        success{
            echo "This stage for Success"
        }
        failure{
            echo "This stage for failure"
        }
    }
}
