pipeline {
    agent {
        docker {
            image 'laradock_workspace:latest'
            args '-u root:root -v /Users/hoangnvh/Documents/projects/minden_src/admin.minden.jp:/var/www'
        }
    }
    stages {
        stage('Test') {
            steps {
                sh '/var/www/vendor/bin/phpmd /var/www/app xml cleancode,codesize,controversial,design,naming,unusedcode --reportfile $WORKSPACE/pmd.xml'
            } 
       }    
    }
    post {
        always {
            recordIssues enabledForFailure: true, tool: pmdParser(pattern: '**/pmd.xml')
        }
    }
}
