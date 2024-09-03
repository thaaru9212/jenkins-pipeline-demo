pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Building the code using Maven...'
                // Here you would use: sh 'mvn clean install'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Running unit tests with JUnit and integration tests...'
                // : sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Running code analysis using SonarQube...'
                // sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Stage 4: Performing security scan using OWASP Dependency-Check...'
                // sh 'dependency-check.sh --project myproject --scan .'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploying to Staging server (AWS EC2 instance)...'
                //  sh 'aws deploy --application-name MyApp --deployment-group MyStagingGroup'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Running integration tests on staging environment...'
                // Integration 
        }
        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploying to Production server (AWS EC2 instance)...'
                // Production deployment 
            }
        }
    }

    post {
        always {
            emailext(
                subject: "Build ${currentBuild.fullDisplayName} - ${currentBuild.currentResult}",
                body: "Build ${currentBuild.fullDisplayName} finished with status: ${currentBuild.currentResult}. Check the logs attached.",
                to: "tharaka@wow.com",  //  email
                attachLog: true
            )
        }
    }
}
