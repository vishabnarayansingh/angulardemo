pipeline{
	agent{
		label "master"
	}
	tools{
		nodejs "NODEJS_10.16.0"
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
			   sh 'npm install'
			}
		}
		 stage('Test') {
		      steps {
			 sh 'npm test'
		      }
		  } 
		stage('Build UI') {
		    steps {
			sh "npm run"
		    }
		}
	}
}
