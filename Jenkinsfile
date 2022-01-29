pipeline{
    agent any
     tools {
        maven 'Maven' 
        slackSend channel: 'jenkins-project1', message: 'job started'
    }
    stages{
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                echo "========executing A========"
            }
        }
        stage("Build"){
            steps{
                // mvn package
                sh "mvn package"
                echo "========executing A========"
            }
        }
        stage("deploy to test"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcat0details', path: '', url: 'http://13.232.192.101:8080')], contextPath: '/app', war: '**/*.war'
                echo "========executing A========"
            }
        }
        stage("deploy to prod"){
            input {
                message "should we continue?"
				ok "Yes we should"
            }
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'asdfasd', path: '', url: 'http://3.108.237.183:8080')], contextPath: '/app', war: '**/*.war'
                echo "========executing A========"
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
            slackSend channel: 'jenkins-project1', message: 'success'
        }
        failure{
            echo "========pipeline execution failed========"
            slackSend channel: 'jenkins-project1', message: 'failed'
            
        }
    }
}
