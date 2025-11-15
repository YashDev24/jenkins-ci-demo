pipeline {
    agent { label 'yash' }  // Your Mac agent label

    environment {
        NODE_HOME = "/Users/yashbaviskar/.nvm/versions/node/v24.4.1/bin"
        PATH = "${NODE_HOME}:${env.PATH}"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/<youruser>/jenkins-ci-demo.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Run Application') {
            steps {
                sh 'nohup node index.js > app.log 2>&1 &'
                sh 'echo "Application is running on agent at port 3000"'
            }
        }
    }
}
