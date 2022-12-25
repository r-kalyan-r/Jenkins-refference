pipeline{
    agent any
    stages {
        stage("Checkout"){
        steps {
            checkout scm: [$class: 'GitSCM', userRemoteConfigs: [[url: 'https://github.com/r-kalyan-r/javaproject.git',credentialsId: 'git-token']], branches: [[name: 'main']]], poll: false
          }
        }
        stage("QA-Stage") {
            when {
                changeset "QA/*.html"
            }
            steps {
                echo "executing QA script"
            }
        }
        stage("Prod-Stage"){
            when {
                changeset "Prod/*.html"
                    
            }
            steps {
                 echo "executing Prod script"
		 }          
        }
	stage("Dev-Stage"){
            when {
                changeset "Dev/*.html"

            }
            steps {
                 echo "executing Dev script"
                 }
        }
    }
}
