pipeline {
    agent any

    tools{
        nodejs "Node"
    }

    stages {
        //stage("Cleanup"){ 
        //    steps{ 
        //        sh "rm -rf ./*"
        //    }       
        //}

        stage('Install') {
            steps {
                dir('angular-frontend') {
                    sh 'npm --version'
                    sh 'node --version'
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                dir('angular-frontend') {
                    sh 'npm run build'
                }
            }
        }

        stage('Test') {
            steps {
                dir('angular-frontend') {
                    sh 'npm test'
                }
            }
        }

        stage('Deploy') {
            steps {
                dir('angular-frontend') {
                    echo "Frontend deployed (simulated)"
                }
            }
        }

        
    }

    post {
        always {
            echo '-----------------------'
        }
        success {
            cleanWs()
        }
        failure {
            echo 'Build failed'
        }
    }
}
