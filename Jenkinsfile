pipeline {
    agent any

    parameters {
        string(name: 'TEST_URL', defaultValue: 'http://13.233.163.72:8080/student-reg-webapp/', description: 'URL to test')
    }

    environment {
        TEST_URL = "${params.TEST_URL}"
    }

    tools {
        maven 'Maven-3.9.10'
    }

    stages {
    


        stage('Checkout') {
            steps {
                git url: 'https://github.com/Devops-Practice-Ismail/webapp-selenium-test.git', branch: 'main'
            }
        }

        stage('Run Tests') {
            steps {
                sh  "echo App URL ${TEST_URL}"
                sh "mvn clean test -DTEST_URL=${TEST_URL}"
            }
        }
    }

    post {
        always {
            cleanWs()
        }

        failure {
            echo "Test failed for $TEST_URL"
        }

        success {
            echo "Test passed for $TEST_URL"
        }
    }
}