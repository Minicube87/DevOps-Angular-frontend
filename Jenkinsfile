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
                sh 'npm --version'
                sh 'node --version'
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                echo "Frontend deployed (simulated)"
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
