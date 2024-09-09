pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven'
                // sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JUnit'
                // sh 'mvn test'
                echo 'Running integration tests with Selenium'
                // sh 'mvn integration-test'
            }
            post {
                always {
                    emailext subject: "Test Stage Status: ${currentBuild.result}",
                             body: "The test stage has completed with status: ${currentBuild.result}",
                             attachLog: true,
                             to: 'thaaru1220@gmail.com'
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code with SonarQube'
                // sh 'mvn sonar:sonar'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan with OWASP ZAP'
                // sh 'zap-cli quick-scan --self-contained --start-options "-config api.disablekey=true" http://localhost:8080'
            }
            post {
                always {
                    emailext subject: "Security Scan Status: ${currentBuild.result}",
                             body: "The security scan stage has completed with status: ${currentBuild.result}",
                             attachLog: true,
                             to: 'thaaru1220@gmail.com'
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to AWS EC2 staging instance'
                // sh 'ansible-playbook -i inventory/staging deploy.yml'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment'
                // sh '.environment=staging'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to AWS EC2 production instance'
                // sh
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed'
        }
    }
}
