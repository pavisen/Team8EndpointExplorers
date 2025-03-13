pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/pavisen/Team8EndpointExplorers.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install -g newman'
            }
        }

        stage('Run Postman Tests') {
            steps {
                sh '''
                newman run "C:\\Users\\Pavithra\\Api\\Team8EndpointExplorers\\gitdemocollection.json" \
                -e "C:\\Users\\Pavithra\\Api\\Team8EndpointExplorers\\Team8EndpointExplorers_QA.postman_environment.json" \
                -d "C:\\Users\\Pavithra\\Api\\Team8EndpointExplorers\\integration.json" \
                -r cli,json,junit,html,allure \
                --reporter-json-export "C:\\Users\\Pavithra\\Api\\Team8EndpointExplorers\\newman-report.json" \
                --reporter-junit-export "C:\\Users\\Pavithra\\Api\\Team8EndpointExplorers\\newman-report.xml" \
                --reporter-html-export "C:\\Users\\Pavithra\\Api\\Team8EndpointExplorers\\newman-report.html" \
                --reporter-allure-export "C:\\Users\\Pavithra\\Api\\Team8EndpointExplorers\\allure-results"
                '''
            }
        }

        stage('Publish Reports') {
            steps {
                junit 'C:\\Users\\Pavithra\\Api\\Team8EndpointExplorers\\newman-report.xml'
            }
        }
    }
}
