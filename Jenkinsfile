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
				sh "git clean -fdx"
				script{
					def scm = checkout([$class: 'GitSCM', branches: [[name: '**']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/naryansingh/SpringCodacyTest.git']]])
					echo "${scm}"
					env.GIT_COMMIT = scm.GIT_COMMIT
					echo "${env.GIT_COMMIT}"
				}
			}
		}
	}
}
