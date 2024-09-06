pipeline { 
    agent any 
    stages { 
        stage('Checkout') { 
            steps { 
                git branch: 'master', url: 'https://github.com/LEEWAILUN/unleash.git' 
            } 
        } 
        stage('Build') { 
            steps { powershell 'gradle clean build'} 
        } 
        stage('Test') { 
            steps { powershell 'gradle test'} 
        } 
        stage('Deploy') { 
            steps { powershell 'java -jar build/libs/unleash-test-V1.jar'}            
        }     
	} 
	post { 
		always { 
		echo 'Cleaning up workspace' 
		deleteDir()
		} 
		success { 
			echo 'Build succeeded!!!' 
		} 
		failure { 
			echo 'Build failed!' 
		} 
	} 
} 