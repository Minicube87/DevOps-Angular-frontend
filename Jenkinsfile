pipeline {
    agent any

    tools{
        nodejs "Node"
    }

    environment {
    NODE_OPTIONS = '--openssl-legacy-provider'
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

        stage('Fix ngcc lock') {
            steps {
                sh 'rm -f node_modules/@angular/compiler-cli/ngcc/__ngcc_lock_file__'
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
