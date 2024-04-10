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

        stage('Install') {
            when {
                branch 'dev'
            }
            steps {
                script {
                    echo 'Installing JAR to local Maven repository...'
                    sh 'mvn install' // Example Maven install command for dev branch
                }
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
           steps {
            echo "deploy stage"
            deploy adapters: [tomcat9 (
                    credentialsId: 'tomcat_deploy_credentials',
                    path: '',
                    url: 'http://52.167.200.192:8088/'
                )],
                contextPath: 'pipjob',
                onFailure: 'false',
                war: '**/*.war'
           }
        }

        
    }
}
