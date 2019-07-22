pipeline{
	agent{
		label "master"
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
		stage('Yarn Install') {
		    steps {
			sh "yarn install"
		    }
		}

		stage('Build UI') {
		    steps {
			sh "npm run test"
		    }
		}
	}
}
