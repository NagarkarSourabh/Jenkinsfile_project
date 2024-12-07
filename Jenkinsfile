pipeline {
    agent any  // This defines the agent where the pipeline will run (any available agent in the environment)

    tools {
        // Here 'mymaven' is the name of the tool configured in Jenkins Global Tool Configuration
        maven 'mymaven'
    }

    stages {
        stage('Clone repo') {
            steps {
                // Clone the repository from GitHub
                git 'https://github.com/github-simplilearn-net/MavenBuild.git'
            }
        }

        stage('Compile Code') {
            steps {
                // Run the Maven compile command to compile the code
                sh 'mvn compile'
            }
        }

        stage('Test Code') {
            steps {
                // Run the Maven test command to execute tests
                sh 'mvn test'
            }
            post {
                success {
                    // Collect the test results
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }

        stage('Package Code') {
            steps {
                // Run the Maven package command to create the build artifacts
                sh 'mvn package'
            }
        }
    }
}
