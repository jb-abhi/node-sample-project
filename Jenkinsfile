pipeline {
  agent any

  environment {
    INVENTORY = 'inventory'
    PRIVATE_KEY = 'ansible-key'
  }

	triggers {
			pollSCM '* * * * *'
	}

  stages {
    stage('Run Ansible Playbook for Dev and QA') {
      steps {
        sshagent (credentials: ['ubuntu']) {
					sh '''
							cd /ansible-setup
							ansible-playbook -i inventory playbook.yml
					'''
       }
      }
    }
  }
}
