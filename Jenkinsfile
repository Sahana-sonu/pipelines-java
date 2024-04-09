pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the project...'
                    sh 'mvn clean package' // Example Maven build command
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo 'Running tests...'
                    sh 'mvn test' // Example Maven test command
                }
            }
        }

        when {
            branch 'dev'
        }
        stage('Install') {
            steps {
                script {
                    echo 'Installing JAR to local Maven repository...'
                    sh 'mvn install' // Example Maven install command for dev branch
                }
            }
        }

        when {
            branch 'main'
        }
        stage('Deploy') {
            steps {
                script {
                    echo 'Deploying WAR file to Tomcat...'
                    sh 'cp target/*.war /path/to/tomcat/webapps' // Example deployment command for main branch
                }
            }
        }
    }
}
