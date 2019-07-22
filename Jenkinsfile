pipeline{
	agent{
		label "master"
	}
	tools{
		nodejs "NODEJS_10.16.0"
	}	
	environment {
		CODACY_PROJECT_TOKEN = credentials('CODACY_TAVANT_GITHUB_ANGULAR')
		CODACY_API_BASE_URL="https://api.codacy.com"

	}
	
	options {
		skipDefaultCheckout true
	}

	stages{
		stage('CheckOut'){
			steps{
				script{
					def scm = checkout([$class: 'GitSCM', branches: [[name: '**']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/vishabnarayansingh/angulardemo.git']]])
					echo "${scm}"
					env.GIT_COMMIT = scm.GIT_COMMIT
					echo "${env.GIT_COMMIT}"
				}
			}
		}
		
		stage('Prepare') {
		    steps{
			  sh "npm install -g yarn"
    		          sh "yarn install"
			  sh "npm install codacy-coverage --save"
			  sh "npm install -g istanbul"
			  //sh "npm install -g jasmine"
			  sh "npm install jasmine-node -g"
			  
			}
		}
		 stage('Test') {
		      steps {
			 //sh 'npm test'
			   sh "npm run test-with-coverage"
		      }
		  } 
	}
}
