node{
	stage('Build'){
		checkout([$class: 'GitSCM', 				
							branches: [[name: "origin/master"]], 
							userRemoteConfigs: [[
							url: 'https://github.com/pipelineascode/node-when-changerequest.git']]
							])


		def changesetFound = false					
		def changeLogSets = currentBuild.changeSets
		println "${currentBuild.getClass().getName()}"
		println "-----"
		println "${env.TAG_NAME}" 
		println "${env.BRANCH_NAME}"
		println "${env.BUILD_TAG}"
		println "${env.CHANGE_ID}"
		println "${env.CHANGE_URL}"
		println "CHANGE_TITLE ${env.CHANGE_TITLE}"
		println "${env.CHANGE_AUTHOR}"
		println "${env.CHANGE_AUTHOR_DISPLAY_NAME}"
		println "${env.CHANGE_AUTHOR_EMAIL}"
		println "${env.CHANGE_TARGET}"
		println "${env.BUILD_NUMBER}"
		println "${env.BUILD_ID}"
		println "${env.BUILD_DISPLAY_NAME}"
		echo "changesetFound:${changesetFound}"
	}
}







pipeline {
    agent any
	
    stages {
        stage('Build') {
		
			when{
				changeRequest title:"when-pr"
			}
		
            steps {                
                echo 'Hello World changing request'
            }
        }
    }
}
