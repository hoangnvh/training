pipeline {
    agent {
        docker {
            image 'laradock_workspace:latest'
            args '-u root:root -v /Users/hoangnvh/Documents/projects/minden_src/admin.minden.jp:/var/www'
        }
    }
    stages {
        stage('Test') {
            sh '/var/www/vendor/bin/phpmd /var/www/app xml cleancode,codesize,controversial,design,naming,unusedcode --reportfile $WORKSPACE/pmd.xml'
        }
        stage ('Analysis') {
            def pmd = scanForIssues tool: pmdParser(pattern: '**/pmd.xml')
            publishIssues issues: [pmd]
        }

    }
}
