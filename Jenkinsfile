pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'npm install'
            }
        }
        stage('Test') { 
            steps {
                bat 'jenkins\\scripts\\test.bat'
            }
        }
        stage('OWASP Dependency-Check Vulnerabilities') {
              steps {
                dependencyCheck additionalArguments: ''' 
                            -o './'
                            -s './'
                            -f 'ALL' 
                            --prettyPrint''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
                            -ApiKey "2609324e-ec20-4afe-bb35-e16a0439fadd"""", 
        
                dependencyCheckPublisher pattern: 'dependency-check-report.xml'
              }
        }
    }
}
